# obs-shaderfilter-debug-float
obs-shaderfilter shader capable of displaying float variables

![alt text](https://github.com/Lokno/obs-shaderfilter-debug-float/blob/main/media/screenshot.png "Screenshot of black raspberry ice cream post-processed with a glitch shader and debug float shader")

The file `debug_float.shader` is a working `obs-shaderfilter` shader which includes the function `displayFloat()`.
This function will take a float value within a shader and render it as digit characters onto your OBS source.
This is incredibly useful for displaying values while debugging shaders. 
It can also be used to display text, see the Shadertoy section at the bottom of this README.

The  characters are stored in integers as Millitext. Millitext is a subpixel font created by Matt Sarnoff (https://www.msarnoff.org/millitext/)

At `scale=1.0` this text is rendered subpixel. If the OBS source is displayed pixel perfect on your monitor, the characters will be legible (although it helps to use a phone)

![alt text](https://github.com/Lokno/obs-shaderfilter-debug-float/blob/main/media/subpixel.png "Close-up screenshot of a monitor demostrating how millitext looks when displayed using subpixels")

## Installation 

1. Update your graphics drivers
2. Update OBS
3. Download and install the latest version of [`obs-shaderfilter`](https://github.com/exeldro/obs-shaderfilter/releases/)
4. Download this repo or its [single source file](https://raw.githubusercontent.com/Lokno/obs-shaderfilter-debug-float/refs/heads/main/debug_float.shader).

## Using the Example Shader Filter

1. Right click a source in OBS and select 'Filters'
2. Click the plus button to add a new effect filter to the source.
3. Select 'User-defined shader'. Rename it if desired.
4. With your new filter highlighted, select "Load shader text from file" in the lower right portion of the window.
5. Browse your file system for where you placed `debug_float.shader`, select it and click open.

Please see the documentation for obs-shaderfiler for more information

## How to add this to your own shader

Copy the functions `displayFloat()` and `getDigit()` from `debug_float.shader` to your own shader. 
So, everything between the `Debug Float Code` comments.

```
float4 mainImage(VertData v_in) : TARGET
{
    float2 bottomLeft = float2(10.0f,10.0f);  // Offset in pixel from lower-left corner
    int displaySign   = 0;                    // Whether or not to display sign [0,1]
    float myFloat     = 42.0;                 // Number to display
    float2 fragCoord  = float2(v_in.x,1.0-v_in.y) * uv_size; // get coordinates in pixels (and flip y)
    integerLength     = 2;                    // characters left of decimal point
    int decimalLength = 1;                    // characters right of decimal point
    float scale       = 4.0;                  // scaling factor (1.0 is subpixel, larger will be bigger)

    // call that actual function
    float3 textColor = displayFloat(bottomLeft, fragCoord, myFloat, displaySign, integerLength, decimalLength, scale);

    float4 src = image.Sample(textureSampler, v_in.uv);            // get source
    return clamp(float4(textColor,textColor.r) + src, 0.0f, 1.0f); // additive combine
}
```

## Shadertoy (GLSL)

I originally developed this in GLSL using Shadertoy (https://www.shadertoy.com)

- Debug Float: https://www.shadertoy.com/view/lfXfzl
- Millitext: https://www.shadertoy.com/view/lfXfWH
- Millitruisms: https://www.shadertoy.com/view/XflBWH
