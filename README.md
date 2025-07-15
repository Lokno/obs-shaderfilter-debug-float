# obs-shaderfilter-debug-float
obs-shaderfilter shader capable of displaying float variables

The file `debug_float.shader` is a working `obs-shaderfilter` shader which includes the function `displayFloat()`.
This function will take a float value within a shader and render it as digit characters onto your OBS source.
This is incredibly useful for displaying values while debugging shaders. 
It can also be used to display text, see the Shadertoy section at the bottom of this README.

The digit characters are stored in integers as Millitext. Millitext is a subpixel font created by Matt Sarnoff (https://www.msarnoff.org/millitext/)

At `scale=1.0` this text is render subpixel. 

## Installation 

1. Update your graphics drivers
2. Update OBS
3. Download and install the latest version of obs-shaderfilter (https://github.com/exeldro/obs-shaderfilter/releases/)
4. Download this repo or its single source file (https://raw.githubusercontent.com/Lokno/obs-shaderfilter-debug-float/refs/heads/main/debug_float.shader)

## Usage

1. Right click a source in OBS and select 'Filters'
2. Click the plus button to add a new effect filter to the source.
3. Select 'User-defined shader'. Rename it if desired.
4. With your new filter highlighted, select "Load shader text from file" in the lower right portion of the window.
5. Browse your file system for where you placed `debug_float.shader`, select it and click open.

Please see the documentation for obs-shaderfiler for more information

## Shadertoy (GLSL)

I originally developed for Shadertoy (https://www.shadertoy.com)

- Debug Float: https://www.shadertoy.com/view/lfXfzl
- Millitext: https://www.shadertoy.com/view/lfXfWH
- Millitruisms: https://www.shadertoy.com/view/XflBWH