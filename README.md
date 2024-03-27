# 따라하면서 배우는 유니티5 셰이더와 이펙트 입문
따라하면서 배우는 유니티5 셰이더와 이펙트 입문 책을 읽으며 메모한 것들
## 01 표준 셰이더의 이해
* 금속 맵에서 금속성(metallicity 또는 metalness)값은 RBGA 텍스처 파일의 빨강 채널에 정의된다. 금속에 가까운 표면일수록 빨강 값이 높고 초록이나 파랑과 같은 다른 채널은 무시된다. 평활도(smoothness)는 금속 텍스처의 알파 채널에 정의되며, 정의된 값이 없으면 최대 평활도가 머터리얼에 할당된다.
* <span style="background-color:yellow; color:black;">노멀 맵(Normal Map)</span>은 모델에서 빛을 반사하는 방향을 정의하는 면법서(surface normal)을 재정의한다. 이 기법은 모델 표면에 가짜 고해상도 디테을을 묘사하는 데 자주 사용된다. Normal Map 슬롯은 RGB 맵을 사용하며, 각 채널이 법선 표면의 방향을 정의한다.
* 오클루전(occlusion)이나 주변 오클루전(ambient occlusion)은 옷의 접힌 부분이나 홈과 같이 빛이 완전히 들지 않아서 어둡게 보이는 부분에 적용할 조명 효과다. 이 맵은 노멀이나 금속 등의 다른 맵과 함께 복잡한 모델을 더 현실적으로 표현하는 데 사용된다. 표준 셰이더에서 오클루전에는 그레이스케일 RGB 맵이 사용된다.
    * 기본적으로 머터리얼은 맵이 적용될 때 최대 주변 오클루전을 사용한다.
* 머터리얼 그룹이 하나인 메시에 추가 머터리얼을 할당하면 머터리얼이 다른 머터리얼 위에 겹쳐서 표시된다.
    * 다른 머터리얼 위에 겹쳐서 표시되게 하려면 렌더링 모드로 반투명(transparent), 컷아웃(cutout), 페이드(fade)를 사용해야 한다.
* <span style="color: cyan;">**tip**</span> : 머터리얼의 Tiling X값을 -7로 Y값을 7로 설정하면 텍스처의 크기가 원래 크기의 1/7로 줄어듬. 임포트 설정에서 텍스처를 고정했다면 텍스처가 반복되지 않는다.
* **표준 스페큘러(Standard Specular)**
    ```
     표면이 가지는 정반사(specular) 특징을 정의할 수 있는 유니티 표준 셰이더
    ```
    * 실용적인 관점에서 보면 머터리얼에 대한 자유를 좀 더 많이 제공함.
    * Material의 Shader 유형을 Standard (Specular setup)으로 설정
    * 표준 셰이더와 비슷하게 머터리얼의 표면 색상(알베도), 반사도, 반짝이는 정도(평활도와 정반사)를 정의할 수 있게 해준다.
    * 표준 셰이더와 가장 큰 차이는 스페큘러 값을 정의하는 데 RGB 전체를 이용하므로 표면에 반사되는 색상을 할당할 수 있다는 점.
    * Smoothness 값을 낮추면 하이라이트의 크기가 커져서 행성 표면이 빛을 난반사하는 것처럼 보인다.
* **스카이박스**
    * 유니티에는 스카이박스에 사용되는 여러 고유한 셰이더가 있다.
    * Material의 Shader 드롭다운 리스트> Skybox
## 02 커스텀 셰이더 만들기
* 유니티는 셰이더의 주 기능으로 셰이더랩(ShaderLab)을 사용하며, 복잡한 기능에는 Cg를 사용한다.
* 괄호를 누락하거나 잘못된 위치에 넣으면 셰이더 실행되지 않음.
### 커스텀 셰이더 만들기
* Project > Create > Shader > Standard Surface Shader
#### 셰이더의 이름 정의
* 셰이더 에셋의 이름과 셰이더 리스트에 나오는 이름은 서로 다르다. 셰이더 리스트의 나올 이름은 나중에 코드에서 정의한다.
 * 셰이더 리스트에 나올 셰이더의 이름 정의 코드
   * 셰이더의 이름 앞에 폴더 이름을 추가해 새로운 셰이더를 정리할 수 있으며, 다른 셰이더에서 폴더 이름을 정의하지 않았다면 폴더가 새로 생김.
        * 아래 소스코드는 폴더를 PACKT으로 지정 
    * <span style="color: cyan;">**tip**</span>: 셰이더의 **실제 이름은 코드에서 정의**하며, Project 뷰에서 지정한 셰이더 파일 이름과 다를 수 있지만, 두 이름이 다르면 나중에 셰이더를 변경하려고 할 때 혼동이 될 수 있다.
    ```c#
    Shader "PACKT/Moon" {

    }
    ```
  

#### 셰이더의 프로퍼티 정의
* Propertices 블록은 머터리얼에서 조정할 수 있는 슬라이더, 디퓨즈 텍스처, 정의된 색상과 같은 셰이더의 원시 머터리얼을 포함한다.
* 프로퍼티는 C#이나 유니티 스크립트 코드의 public 변수와 비슷하다.
* 아래 소스는 _Color 프로퍼티 정의.
    * 코드를 시작하는 행에 있는 **프로퍼티 이름에는 일반적으로 밑줄을 접두사로 붙이며,** 이 프로퍼티 이름이  셰이더 본체에 사용됨.
    * **큰 따옴표 안에 있는 이름은 Material Inspector 뷰에서 나올 프로퍼티 이름.**
    * Color 프로퍼티는 네 개의 십진수 값인 R,G,B,A로 정의
```C#
Shader "PACKT/Moon" {
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)	
	}

}
```
#### SubShader
* 주 본체를 포함하며 입력 색상, 텍스처 또는 다른 값을 모두 처리한다.
* **모든 셰이더에 하나 이상 포함된다.**
* 주요 기능은 **다른 셰이더 정의를 분리하는 것**이다. 이를 통해 셰이더가 여러 장치에서 작동하게 만들 수 있다.
* 애플리케이션에서 셰이더가 사용될 때 첫 번째 셰이더가 GPU와 호환되지 않는 경우, 시스템은 적합한 다음 subShader를 실행한다.
```c#
Shader "PACKT/Moon" {
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)
	}
	SubShader {
		Pass {
			Color[_Color]
		}
	}
}
```
#### 셰이더 작동 확인
* Material을 생성 > Shader 유형 > 위에서 정의한 PACKT > Moon으로 설정하면 됨.
* 설정 후 머터리얼을 보면 Color라는 프로퍼티가 하나 존재한다.
* 해당 머터리얼을 게임오브젝트에 적용하면 됨.
* **무조명 셰이더(unlit shader)** : 그림자나 하이라이트가 없는 균일한 색상 표면을 가지는 셰이더로 성능 면에서 비용이 아주 적게 든다.
#### 셰이더에 텍스처 추가
```c#
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)
		_MainTex ("Albedo (RGB)", 2D) = "white" {}
	}
```
* **_MainTex는 유니티가 주 텍스처 맵에 사용하는 표준 이름**으로서, 일반적으로 셰이더의 알베도 컴포넌트로 사용된다.
```c#
	SubShader {
		Pass {
			Color[_Color]
			SetTexture[_MainTex] {
				Combine Primary * Texture
			}
		}
	}
```
* 위 코드는 프로퍼티 이름을 지정해 텍스처를 설정한다. 그런 다음 원래(또는 Primary) 내용과 곱해서 적용한다.
* 셰이더를 저장하고 Inspector 뷰를 보면 프로퍼티 영역에 새로운 텍스처 슬롯이 생긴 걸 볼 수 있다.

#### 셰이더가 씬 조명에 반응하게 만들기
* 대부분의 유니티 셰이더는 Cg를 사용한다. Cg를 이용해 기존의 Pass를 대체
* CGPROGRAM/ENDCG : Cg 블록의 시작/끝 태그
```C#
Shader "PACKT/Moon" {
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)
		_MainTex ("Albedo (RGB)", 2D) = "white" {}
	}
	SubShader {
		CGPROGRAM
        /*
        컴파일 지시자이다.
        이러한 코드는 항상 여는 Cg 태그 다음에 오며, 셰이더가 실행될 때 컴파일될 셰이더 함수와 조명 모델을 지정한다. 
        아래 코드에선 음영을 지원하는 **램버트(Lambert)**모델을 사용한다.
        */
		#pragma surface surf Lambert
		
        /*
        해당 구조체는 텍스처를 모델 표면에 올바르게 적용하기 위한 UV 데이터를 담는다.
        여기에 포함된 UV 데이터는 float 값 두 개로 구성된 float2
        */
		struct Input {
			float2 uv_MainTex;
		};

        /*
        프로퍼티를 셰이더에서 계산할 수 있는 Cg 변수로 지정.
        _MainTex는 텍스처이며 _Color는 R,G,B,A채널 값으로 구성되는 float4변수
        */
		sampler2D _MainTex;
		float4 _Color;

        /*
         surf 함수는 변수 o로 지정한 입력 데이터를 조합해 셰이더 출력을 지정한다.
         
         이 경우 셰이더는 출력으로서 알베도 텍스처만 처리하면 된다.
         조명은 앞에서 지정한 조명 모델에 의해 정의됐다.
         여기서는 _MainTex rgb 데이터와 _Color rgb 데이터를 곱해 출력 색상을 얻었다.
        */
		void surf (Input IN, inout SurfaceOutput o) {
			o.Albedo = tex2D (_MainTex, IN.uv_MainTex).rgb * _Color.rgb;
		}
		ENDCG
	}
}
```


