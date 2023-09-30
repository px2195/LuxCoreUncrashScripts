LuxCoreUncrashScripts - quick LuxCore workaround for the normality in the process of rendering repetitive or complex, for example scientific, scenes. Tested in Blender v 2.8 and 3x. 

•On my older GT610, renders animation fast, even if in theory 'd be need to reload graphic card kernel buffer – that means, at least in my types of renderings.

•Requirements:
– Blender v. >= 2.80
– LuxCore v. >= 2.2
— LUXCORE UI PROGRAM
— Python
— wmctrl
— xdotool (or you maximize it yourself)

•How it works? Makes LuxCore running in its own LuxCore UI window, ****after the saving of Blender-opened .blend file /OR/ an arbitrary .blend*** - thus _stabilizes_ (WORKAROUNDS) rendering, moving it outside Blender program. This isolation allows even closing of Blender process, when LuxCore Render starts in its UI part - reducing RAM. **IMPORTANT:** 1. You need first to replace executables' paths/directories in order to run this free suite. 2. Check chmod a+x also.
/usr/local/bin/lux_render — renders animation.
/usr/local/bin/lux_render_current_one - opens currently openen Blender scene file, converts and renders it.
/usr/local/bin/lux_render_current — render currently opened Blender scene
/usr/local/bin/lux_render_one - 

and window-op helper scripts below:
/usr/local/bin/waitforwin
*******
#!/bin/bash

r=1
until [ $r -eq 0 ]; do
   sleep .1
   wmctrl -l |grep -E 0x0*$(printf '%x\n' `xdotool getactivewindow`) |grep $1
   r=$?
done

******/usr/local/bin/maximize 
*****
wmctrl -r :ACTIVE: -b toggle,maximized_vert,maximized_horz

