---
layout : default
title : API - Color, Depth and Stencil Buffers
packages :
  - GL.Buffers
  - GL.Blending
weight: 11
---

# Accessing OpenGL Buffers

The package `GL.Buffers` gives access to the OpenGL color buffers, as
well as the depth and stencil buffer. There are four color buffers:

 * Front left
 * Front right
 * Back left
 * Back right

Front and back are for double-buffered rendering (rendering in one buffer
while displaying the other one), left and right are for stereoscopic
rendering. Which of the buffers are available depends on your context setup.

You can render to one or more color buffers at a time by setting the current
buffer(s) with `Set_Active_Buffer(s)`. You can clear the color buffers with
`Clear` or `Clear_Color_Buffers` (since OpenGL 3).

To use the depth buffer, you need to create your OpenGL context with more
than 0 color depth buffer bits. You also need to enable the depth test
with `GL.Toggles.Enable (GL.Toggles.Depth_Test);`. Same goes for the stencil
buffer and test (use `GL.Toggles.Stencil_Test`).

`GL.Blending` enables you to setup alpha blending in the color buffer. A
typical setup would be:

<?prettify lang=ada?>

    GL.Toggles.Enable (GL.Toggles.Blend);
    GL.Blending.Set_Blend_Func
      (GL.Blending.Src_Alpha, GL.Blending.One_Minus_Src_Alpha);