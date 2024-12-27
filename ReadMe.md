## 27 Dec 2024
## Skybox Blend Shader README

> Overview
> The Skybox Blend Shader is a custom shader designed for smooth transitions between two cubemap-based skyboxes (e.g., day and night). 
This shader allows dynamic blending controlled by a single property, making it ideal for creating immersive day-night cycles in Unity.

> Features
> Cubemap Blending. Supports two cubemaps (day and night).
> Smooth transitions based on a blend factor.

> Efficient Rendering:
> Optimized for real-time performance.
> Customizable Inputs: Easy to adjust cubemaps and blend factor via material properties.

> Shader Properties
> _DayCubemap. Cubemap texture for the daytime skybox.
> _NightCubemap. Cubemap texture for the nighttime skybox.
> _Blend. Blend factor (0 = night, 1 = day).

> Setup Instructions
1. Import Package
2. Configure Material
i. Assign a daytime cubemap to the _DayCubemap property.
ii. Assign a nighttime cubemap to the _NightCubemap property.
iii. Adjust the _Blend value (0 for night, 1 for day) to see the transition effect.
3. Integration with Scripts

public class SkyboxBlendController : MonoBehaviour
{
    public Material skyboxMaterial;
    public float blendSpeed = 0.01f;
    private float blendFactor = 0f;

    void Update()
    {
        // Example: Cycle the blend factor between 0 and 1
        blendFactor = Mathf.PingPong(Time.time * blendSpeed, 1f);
        skyboxMaterial.SetFloat("_Blend", blendFactor);
        DynamicGI.UpdateEnvironment();
    }
}

> Notes
> This shader is specifically for cubemap-based skyboxes.