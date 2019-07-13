# NoodlesPlate

This repo wil contain Samples, Doc, Tutos, and Releases of NoodlesPlate

# ChangeLog :

[Version 0.1.955](releases)

## [ADD] Settings dialog :
  * proxy settings move from import bar to here
  * same for ShaderToy api key
  
## [ADD] Transparant window support :
  * activate or not in Settings Dialog
  * control tranparancy with alpha value of the current buffer
  * ex [here](https://twitter.com/aiekick/status/1126280207105765376)
  
## [ADD] you can save pictures of UI and FBO after each code modification
  * let you create a video of your shader like, ex : [here](https://twitter.com/aiekick/status/1124527172306206720)
  
## [ADD] you can get metrics and infos about your GPU :
  * only support for nvidia for the moment.
  * you get temperature, load, etc..
  * you can get infos of your opengl
  * acces it in menu Infos, [video](https://twitter.com/aiekick/status/1123654277623373825)
  
## [ADD] FullScreen support
  * [video](https://twitter.com/aiekick/status/1125906159825817605)
  * windowed or not, see F11 / F12 infos in title bar
  
## [ADD] Pixel Debugging Capability :
  * Pixel debug value under mouse cursor : [video](https://twitter.com/aiekick/status/1119402970347712513)
    * for all buffers attachments, let your record in a graph
    * you can record in value change and/or if mouse pose change
    * youc an define the measure frequency
  * Pixel debug values under a line : [video](https://twitter.com/aiekick/status/1121917531458031616)
    * you can configure the line, and record graph of change of whole line
    * you can check where you are on the line on creen when mouseover the graph
  * Pixel Debug tool for show 2d/3d normal under mouse cursor : [video](https://twitter.com/aiekick/status/1149811160927080454)
    * you need to use the world camera for ray origin and ray direction
  * Pixel debug tool for use gizmo for : [video](https://twitter.com/aiekick/status/1135012575299739648)
    * you can move a gizmo with the current buffer value.
    * with that you can vizualize a virtual position
    * you can move a shape by the buffer value under mouse
    * you need to use the world camera for ray origin and ray direction
	
## [ADD] GamePad Support
  * [video](https://twitter.com/aiekick/status/1143665171661021184)
  * you get uniforms and widgets :
    * vec4 with value for : left and right thumb and trigger
    * vec4 for cross pad and buttons down => true is > to 0.5, release => false is < to 0.5 (like checkbox widget)
    * fully compatible with PS4 GamePad, not tested with others, but NoodlesPlate use glfw binding
    * see Settings Dialog for affect you gamepad items to uniforms
	
## [ADD] Uniforms Config Load / Save
  * [video](https://twitter.com/aiekick/status/1138999841969856512)
  * you can save / load at a moment the curent uniforms config
  * NoodlesPlate will create one conf file per config
  * indeed if you chnage your sahder or uniforms, maybe an past conf will not prduce same shader :)
  * all uniforms not currently in the config file will be not changed
  * the uniforms values are just repalce with the content of the conf file, there is no overwrite, unitl you decide to overwrite conf file
  
## [ADD] for Heavy Shader, play/pause shader but listening inputs :
  * each modif of input like mouse camera, gizmo will refresh the frame
  * you can code heavy shader without overload the Ui and your system
  
## [ADD] ca, enable or not Input using :
  * CAMERA, GIZMO, MOUSE, and Gamepad, each with a check button
  
## [ADD] Culling System : 
  * [video 1](https://twitter.com/aiekick/status/1140404208560160771), [video 2](https://twitter.com/aiekick/status/1141042801783844864)
  * used if you have a heavy shader, or if you want to explore your sdf
  * you need to use the world camera for ray origin and ray direction
  * you need also to modify your raymarch loop, a example is provided in File -> new -> Gizmo_Culling_related menu
  * you can enable or disable the culling of select culling primitive (sphere / cube) in menu Gizmo
  
## [ADD] new widget of type radio buttons, like a checkbox, but with vec2, vec3, vec4. and one check at true at same time
  
## [ADD] a mesh sahder can be selected : menu settings -> show mesh
  * for load a mesh and superpose whit you sdf if you want comapred and simplify modeling fo your sdf 
  * support olny the loading of a obj file and with only triangles for the moment
  * you sahder need to use the world camera and depth buffer, for have good sdf / mesh merge
  
## [ADD] Check version of app at start, you can disable it in settings
  
## [ADD] changelog visualization in file menu

---
 
## [BREACK] i have disabled the nodegraph because i have many issue and crash. need more time. will comeback in a future release)
  
## [BREACK] i have disabled the help pane (need a better system). for the moment the help is on the [wiki](https://github.com/aiekick/NoodlesPlate/wiki), will be updated as you go

---

## [CHANGE] the framebuffer definition is not any mosre in sampler uniforms :
  * you will define that in the FRAMEBUFFER SECTION : 
    * buffer count (1-8)
    * wrap mode (clamp,repeat,mirro)
    * filter mode (linear,nearest)
    * mipmap mode (true,false)
    * format (byte,float)
    * size (x,y or picture file)
    * ratio (value or picture file)
  * for use a buffer in a sampler, juste set the target tag :
  * uniform sampler2d(buffer:target=0) name; if you want to target the buffer attachment of the current fbo
  * uniform sampler2d(buffer:target=0:file=toto) name; if you want to target the buffer attachment of the file fbo
  
## [CHANGE] simplification of uniform sections :
  * for contol visibility of an unfiorm you just need to target another uniform and define a condition :
    * section : name (string and space), order (nurmber only), condition (accepted operator are ==, !=, < or >)
    * uniform(section0:0) float(checkbox:false) activation;
    * uniform(section0:1:activation==true) float(0:2:1);
	
## [CHANGE] combobox and checkbox default params are string now and not numbers
  
## [CHANGE] Slider widgets can be stepped : 
  * with the step increment in the last optionnal params
  * uniform float(inf:sup:default:step) toto;

---

## [RELEASES] you have two type of release :
  * release standard for X86 and X64
  * release with profiler for X86  and X64 ( open profiler in html directory profiler with package)

---

Many bug fixs, and perf improvments

if you found other bugs and want featrue request, go [here](https://github.com/aiekick/NoodlesPlate/issues)
