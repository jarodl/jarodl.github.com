---

title: Eliminate iPhone OpenGLES project warnings
layout: default

---

When starting a new universal iOS OpenGL project I usually select the 'Window-based Application' template and then copy over the files from the 'OpenGL ES Application' template. After doing this a few warnings show up regarding the OpenGL ES 2.0 shader files.

    warning: no rule to process file '$(PROJECT_DIR)/Shader.fsh' of type sourcecode.glsl for architecture i386
    warning: no rule to process file '$(PROJECT_DIR)/Shader.vsh' of type sourcecode.glsl for architecture i386

I noticed a few other people having this issue on
[idevgames.com](http://inkubator.idevgames.com/forums/thread-397.html) and [iphonedevsdk.com](http://www.iphonedevsdk.com/forum/iphone-sdk-game-development/39349-opengl-es-shader-bug-only-iphone-3gs.html) so here is how to fix it.

When you add the two shader files (Shader.fsh and Shader.vsh) add them to the application target. After they are copied into your project click the dropdown arrow next to the application target in the Targets folder of the group tree.  You will see three folders. If you are getting the above warnings the shader files are probably in the 'Compile Sources' folder. Move them to the 'Copy Bundle Resources' folder and the warning should go away.
