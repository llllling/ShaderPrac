# �����ϸ鼭 ���� ����Ƽ5 ���̴��� ����Ʈ �Թ�
* �����ϸ鼭 ���� ����Ƽ5 ���̴��� ����Ʈ �Թ� å�� ������ �޸��� �͵�
* �� é�� ���� �ǽ��� *Chapter1_Start*�� ����_Start�� ���� scene
## 01 ǥ�� ���̴��� ����
* �ݼ� �ʿ��� �ݼӼ�(metallicity �Ǵ� metalness)���� RBGA �ؽ�ó ������ ���� ä�ο� ���ǵȴ�. �ݼӿ� ����� ǥ���ϼ��� ���� ���� ���� �ʷ��̳� �Ķ��� ���� �ٸ� ä���� ���õȴ�. ��Ȱ��(smoothness)�� �ݼ� �ؽ�ó�� ���� ä�ο� ���ǵǸ�, ���ǵ� ���� ������ �ִ� ��Ȱ���� ���͸��� �Ҵ�ȴ�.
* <span style="background-color:yellow; color:black;">��� ��(Normal Map)</span>�� �𵨿��� ���� �ݻ��ϴ� ������ �����ϴ� �����(surface normal)�� �������Ѵ�. �� ����� �� ǥ�鿡 ��¥ ���ػ� �������� �����ϴ� �� ���� ���ȴ�. Normal Map ������ RGB ���� ����ϸ�, �� ä���� ���� ǥ���� ������ �����Ѵ�.
* ��Ŭ����(occlusion)�̳� �ֺ� ��Ŭ����(ambient occlusion)�� ���� ���� �κ��̳� Ȩ�� ���� ���� ������ ���� �ʾƼ� ��Ӱ� ���̴� �κп� ������ ���� ȿ����. �� ���� ����̳� �ݼ� ���� �ٸ� �ʰ� �Բ� ������ ���� �� ���������� ǥ���ϴ� �� ���ȴ�. ǥ�� ���̴����� ��Ŭ�������� �׷��̽����� RGB ���� ���ȴ�.
    * �⺻������ ���͸����� ���� ����� �� �ִ� �ֺ� ��Ŭ������ ����Ѵ�.
* ���͸��� �׷��� �ϳ��� �޽ÿ� �߰� ���͸����� �Ҵ��ϸ� ���͸����� �ٸ� ���͸��� ���� ���ļ� ǥ�õȴ�.
    * �ٸ� ���͸��� ���� ���ļ� ǥ�õǰ� �Ϸ��� ������ ���� ������(transparent), �ƾƿ�(cutout), ���̵�(fade)�� ����ؾ� �Ѵ�.
* <span style="color: cyan;">**tip**</span> : ���͸����� Tiling X���� -7�� Y���� 7�� �����ϸ� �ؽ�ó�� ũ�Ⱑ ���� ũ���� 1/7�� �پ��. ����Ʈ �������� �ؽ�ó�� �����ߴٸ� �ؽ�ó�� �ݺ����� �ʴ´�.
* **ǥ�� ����ŧ��(Standard Specular)**
    ```
     ǥ���� ������ ���ݻ�(specular) Ư¡�� ������ �� �ִ� ����Ƽ ǥ�� ���̴�
    ```
    * �ǿ����� �������� ���� ���͸��� ���� ������ �� �� ���� ������.
    * Material�� Shader ������ Standard (Specular setup)���� ����
    * ǥ�� ���̴��� ����ϰ� ���͸����� ǥ�� ����(�˺���), �ݻ絵, ��¦�̴� ����(��Ȱ���� ���ݻ�)�� ������ �� �ְ� ���ش�.
    * ǥ�� ���̴��� ���� ū ���̴� ����ŧ�� ���� �����ϴ� �� RGB ��ü�� �̿��ϹǷ� ǥ�鿡 �ݻ�Ǵ� ������ �Ҵ��� �� �ִٴ� ��.
    * Smoothness ���� ���߸� ���̶���Ʈ�� ũ�Ⱑ Ŀ���� �༺ ǥ���� ���� ���ݻ��ϴ� ��ó�� ���δ�.
* **��ī�̹ڽ�**
    * ����Ƽ���� ��ī�̹ڽ��� ���Ǵ� ���� ������ ���̴��� �ִ�.
    * Material�� Shader ��Ӵٿ� ����Ʈ> Skybox
## 02 Ŀ���� ���̴� �����
* ����Ƽ�� ���̴��� �� ������� ���̴���(ShaderLab)�� ����ϸ�, ������ ��ɿ��� Cg�� ����Ѵ�.
* ��ȣ�� �����ϰų� �߸��� ��ġ�� ������ ���̴� ������� ����.
### Ŀ���� ���̴� �����
* Project > Create > Shader > Standard Surface Shader
#### ���̴��� �̸� ����
* ���̴� ������ �̸��� ���̴� ����Ʈ�� ������ �̸��� ���� �ٸ���. ���̴� ����Ʈ�� ���� �̸��� ���߿� �ڵ忡�� �����Ѵ�.
 * ���̴� ����Ʈ�� ���� ���̴��� �̸� ���� �ڵ�
   * ���̴��� �̸� �տ� ���� �̸��� �߰��� ���ο� ���̴��� ������ �� ������, �ٸ� ���̴����� ���� �̸��� �������� �ʾҴٸ� ������ ���� ����.
        * �Ʒ� �ҽ��ڵ�� ������ PACKT���� ���� 
    * <span style="color: cyan;">**tip**</span>: ���̴��� **���� �̸��� �ڵ忡�� ����**�ϸ�, Project �信�� ������ ���̴� ���� �̸��� �ٸ� �� ������, �� �̸��� �ٸ��� ���߿� ���̴��� �����Ϸ��� �� �� ȥ���� �� �� �ִ�.
    ```c#
    Shader "PACKT/Moon" {

    }
    ```
  

#### ���̴��� ������Ƽ ����
* Propertices ����� ���͸��󿡼� ������ �� �ִ� �����̴�, ��ǻ�� �ؽ�ó, ���ǵ� ����� ���� ���̴��� ���� ���͸����� �����Ѵ�.
* ������Ƽ�� C#�̳� ����Ƽ ��ũ��Ʈ �ڵ��� public ������ ����ϴ�.
* �Ʒ� �ҽ��� _Color ������Ƽ ����.
    * �ڵ带 �����ϴ� �࿡ �ִ� **������Ƽ �̸����� �Ϲ������� ������ ���λ�� ���̸�,** �� ������Ƽ �̸���  ���̴� ��ü�� ����.
    * **ū ����ǥ �ȿ� �ִ� �̸��� Material Inspector �信�� ���� ������Ƽ �̸�.**
    * Color ������Ƽ�� �� ���� ������ ���� R,G,B,A�� ����
```C#
Shader "PACKT/Moon" {
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)	
	}

}
```
#### SubShader
* �� ��ü�� �����ϸ� �Է� ����, �ؽ�ó �Ǵ� �ٸ� ���� ��� ó���Ѵ�.
* **��� ���̴��� �ϳ� �̻� ���Եȴ�.**
* �ֿ� ����� **�ٸ� ���̴� ���Ǹ� �и��ϴ� ��**�̴�. �̸� ���� ���̴��� ���� ��ġ���� �۵��ϰ� ���� �� �ִ�.
* ���ø����̼ǿ��� ���̴��� ���� �� ù ��° ���̴��� GPU�� ȣȯ���� �ʴ� ���, �ý����� ������ ���� subShader�� �����Ѵ�.
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

#### ���̴� �۵� Ȯ��
* Material�� ���� > Shader ���� > ������ ������ PACKT > Moon���� �����ϸ� ��.
* ���� �� ���͸����� ���� Color��� ������Ƽ�� �ϳ� �����Ѵ�.
* �ش� ���͸����� ���ӿ�����Ʈ�� �����ϸ� ��.
* **������ ���̴�(unlit shader)** : �׸��ڳ� ���̶���Ʈ�� ���� ������ ���� ǥ���� ������ ���̴��� ���� �鿡�� ����� ���� ���� ���.
#### ���̴��� �ؽ�ó �߰�
```c#
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)
		_MainTex ("Albedo (RGB)", 2D) = "white" {}
	}
```
* **_MainTex�� ����Ƽ�� �� �ؽ�ó �ʿ� ����ϴ� ǥ�� �̸�**���μ�, �Ϲ������� ���̴��� �˺��� ������Ʈ�� ���ȴ�.
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
* �� �ڵ�� ������Ƽ �̸��� ������ �ؽ�ó�� �����Ѵ�. �׷� ���� ����(�Ǵ� Primary) ����� ���ؼ� �����Ѵ�.
* ���̴��� �����ϰ� Inspector �並 ���� ������Ƽ ������ ���ο� �ؽ�ó ������ ���� �� �� �� �ִ�.

#### ���̴��� �� ���� �����ϰ� �����
* ��κ��� ����Ƽ ���̴��� Cg�� ����Ѵ�. Cg�� �̿��� ������ Pass�� ��ü
* CGPROGRAM/ENDCG : Cg ����� ����/�� �±�
```C#
Shader "PACKT/Moon" {
	Properties {
		_Color ("Color", Color) = (1, 1, 1, 1)
		_MainTex ("Albedo (RGB)", 2D) = "white" {}
	}
	SubShader {
		CGPROGRAM
        /*
        ������ �������̴�.
        �̷��� �ڵ�� �׻� ���� Cg �±� ������ ����, ���̴��� ����� �� �����ϵ� ���̴� �Լ��� ���� ���� �����Ѵ�. 
        �Ʒ� �ڵ忡�� ������ �����ϴ� ����Ʈ(Lambert)���� ����Ѵ�.
        */
		#pragma surface surf Lambert
		
        /*
        �ش� ����ü�� �ؽ�ó�� �� ǥ�鿡 �ùٸ��� �����ϱ� ���� UV �����͸� ��´�.
        ���⿡ ���Ե� UV �����ʹ� float �� �� ���� ������ float2
        */
		struct Input {
			float2 uv_MainTex;
		};

        /*
        ������Ƽ�� ���̴����� ����� �� �ִ� Cg ������ ����.
        _MainTex�� �ؽ�ó�̸� _Color�� R,G,B,Aä�� ������ �����Ǵ� float4����
        */
		sampler2D _MainTex;
		float4 _Color;

        /*
         surf �Լ��� ���� o�� ������ �Է� �����͸� ������ ���̴� ����� �����Ѵ�.
         
         �� ��� ���̴��� ������μ� �˺��� �ؽ�ó�� ó���ϸ� �ȴ�.
         ������ �տ��� ������ ���� �𵨿� ���� ���ǵƴ�.
         ���⼭�� _MainTex rgb �����Ϳ� _Color rgb �����͸� ���� ��� ������ �����.
        */
		void surf (Input IN, inout SurfaceOutput o) {
			o.Albedo = tex2D (_MainTex, IN.uv_MainTex).rgb * _Color.rgb;
		}
		ENDCG
	}
}
```
### ���ΰ� ����� ������ ȿ�� ����
#### Ŀ���� ���� ���̴� �����
* Project > Create > Shader > Standard Surface Shader �̸��� Glass�� ���� �� Material�� ���� > Shader ���� > Custom > Glass���� �� ����
* Glass.shader
    * subshader ��Ͽ����� �پ��� ���̴� Ư���� �����ϸ�, ������ �����ϴ� ���� ä���̳� �ٸ� ������Ƽ�� ������ �� �ִ�.
    ```c#
    SubShader
    {
        Tags { "RenderType"="Transparent" }
    }
    ```
    * Cg ��Ͽ��� ������ ������ ������ �ڿ� alpha �߰�
    ```c#
    #pragma surface surf Standard fullforwardshadows alpha
    ```
* Inspector �信�� ����
    * color ���� ä�� : 128
    * Smoothness : 0.9 => ��� ǥ���� ���� �ݻ���.
    * Metallic : 0.188 => �������ϸ� �ణ ��¦�̰� ��.
* ���
    <div><img src="./readmeimg/a1.png" width="300"/></div>
#### ����� ��ǥ�� �����
* �� ���������� �ϸ� ��� ��ǥ�鸸 ��¦�δ�.
* **����Ƽ ���̴��� ���ɻ��� ������ �⺻������ �޽��� �ܸ鸸 �������ϸ� ����<sup>back face</sup>�� �ڵ����� ���ŵȴ�.**
* ���� �⺻ ������ �����ϴ� �ڵ� 
    * LOD �� �ڿ� Cull Off �߰�
    ```c#
    SubShader
    {
        Tags { "RenderType"="Transparent" }
        LOD 200
        Cull Off
    }
    ```
* ���
    <div><img src="./readmeimg/a2.png" width="300"/></div>
    
    * ��� ������ ������������ �ܸ�� ���� ��ġ�� �������Ǹ鼭 �ణ�� ��Ƽ��Ʈ�� ������.
        ```
        "��Ƽ��Ʈ(artifact)"�� �Ϲ������� ��ǻ�� �׷��Ƚ��� ���������� ���Ǵ� ����, �ǵ����� ���� �����̳� �ұ�Ģ�� ����� ����Ų��.
        
        Ư��, �ȼ��̳� �ٰ��� ���� �׷��� ��ҿ��� ����� ����ġ ���� ������ �ǹ��� �� �ִ�. ���� ��� �����̳� �ܸ�� ���� ��ġ���� �������Ǵ� ���� �߻��ϴ� �ణ�� ��Ƽ��Ʈ�� ������ �������� �߻��ϴ� ����, ���� ���� ����, �Ǵ� ������ ������ �Ѱ�� ���� ���������� �׷��� ������ ����.
        ``` 
    * ����� �ܸ�� ������ ������ �������ϵ��� ���̴��� �����ϸ� �� ����� ������ �� �ִ�.
##### �ܸ�� ���� �и�
* ���̴����� ����� �β��� ��¥�� ǥ���ϰ� ����� ������ ����� �� ���������� ���̰� �� �� �ִ�.
* Glass.shader ����
    1. Propertices ��Ͽ� �ڵ� �߰�
        ```c#
        _Thickness ("Thickness", Range(-1,1)) = 0.5
        ```
    2. ������ �߰��� Cull Off => Cull Back���� ����

    3. �Ʒ� �ڵ带 ���� �ڵ��� ENDCG ������ �߰��Ѵ�. 
        * �� �ڵ�� ù ��° ���̴��� ����� �߰� ���̴��μ� **������ ����� �����ϴ� ����**�� �Ѵ�. 
        * ����, �� ���̴��� ���� ��ġ�� �ʵ��� ������ �����Ѵ�.
        ```c#
                Cull Front
                
                CGPROGRAM
                /*���̴��� ����Ǵ� ���ؽ��� ������ �� �ְ� vertex:vert �߰�*/
                #pragma surface surf Standard fullforwardshadows alpah vertex:vert

                struct Input {
                    float2 uv_MainTex;
                };

                float _Thickness;
                /*���ؽ��� ��ġ ����*/
                void vert (inout appdata_full v) {
                    v.vertex.xyz += v.normal * _Thickness;
                }

                sampler2D _MainTex;
                half _Glossiness;
                half _Metallic;
                fixed4 _Color;

                void surf (Input IN, inout SurfaceOutputStandard o) {
                    fixed4 c = tex2D (_MainTex, IN.uv_MainTex) * _Color;
                    o.Albedo = c.rgb;
                    o.Metallic = _Metallic;
                    o.Smoothness = _Glossiness;
                    o.Alpha = c.a;
                }
                ENDCG
        ```
        4. Inspector �信�� Thickness -0.2�� ����
* ��������� Inspector�信�� _Thickness�� �����ϴ� ����ŭ ���� ǥ���� �β��� ���� ��ó�� ǥ����.
    <div><img src="./readmeimg/a3.png" width="300"/></div>
* **�� ����� ����̳� ������, �Ȱ� ��� ���� ���� ������ ��Ÿ���� �� ����������, �β��� ������ �е��� ���� ������ ���͸����� ǥ���ϴ� �� �ʿ��� ������ �ùķ��̼������� ���Ѵ�.**
### �༱�� ��� ����
* �༺ ����� ���� ���� ������ ��ü�� ���� �ݻ��ϴ� �Ͱ��� �޸� �ֺ��ο��� ����ó�� ���̴� ������ ����Ų��. �̸� Ŀ���� ���̴��� ����� ȿ���� ǥ���Ѵ�.
#### Ŀ���� �༺ ���̴� �����
* Project > Create > Shader > Standard Surface Shader �̸� Planet ����
    ```c#
    Shader "PACKT/Planet_falloff"
    ```
* ���͸��� Planet_falloff���� > ���̴� ���� Planet_falloff ����
* �� ���� ridleyVI�� �ش� ���͸��� �巡���ؼ� ����
##### �༺ ���̴� ����
* Propertics�� _Thickness,_AtmosColor �߰�
```c#
    Properties
    {
        _Color ("Color", Color) = (1,1,1,1)
        _MainTex ("Albedo (RGB)", 2D) = "white" {}
        _Thickness("Thickness", Range(-1, 1)) = 0.5
        _AtmosColor (" Atmosphere Color", Color) = (1,1,1,1)
    }
    SubShader
    {
        Tags { "RenderType"="Opaque" }
        LOD 200

        CGPROGRAM
        #pragma surface surf Standard fullforwardshadows

        #pragma target 3.0

        sampler2D _MainTex;

        struct Input
        {
            float2 uv_MainTex;
        };

        fixed4 _Color;

        UNITY_INSTANCING_BUFFER_START(Props)
        UNITY_INSTANCING_BUFFER_END(Props)

        void surf (Input IN, inout SurfaceOutputStandard o)
        {
            fixed4 c = tex2D (_MainTex, IN.uv_MainTex) * _Color;
            o.Albedo = c.rgb;
            o.Alpha = c.a;
        }
        ENDCG
```
##### ��� ���̴� �н� �߰� 
* �༺ ���̴� �ڵ� �Ʒ��ʿ� ���ο� �н� �ڵ� �߰�
* ���ؽ� �Լ��� �̿��� ������Ʈ���� �����Ų��.
* ��⸦ ��Ÿ���� �� ����� ���� ������ �����ϰ� �� ������ ���� ä���� �̿��� ����� �������� �����Ѵ�.
```c#
        Cull Front

        CGPROGRAM
        #pragma surface surf Standard fullforwardshadows alpha vertex:vert
        struct Input {
            float2 uv_MainTex;
        };

        float _Thickness;
        void vert (inout appdata_full v) {
            v.vertex.xyz += v.normal * _Thickness;
        }

        fixed4 _AtmosColor;
        void surf (Input IN, inout SurfaceOutputStandard o) {
            o.Albedo = _AtmosColor.rgb;
            o.Alpha =_AtmosColor.a;
        }
        ENDCG
```
* ���
<div><img src="./readmeimg/a4.png" width="300"></div>