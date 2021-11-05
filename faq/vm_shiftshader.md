---
description: Get Waydroid to work through a VM
---

Get Waydroid to work through a VM

In order to get Waydroid to work through a VM, you may need to adjust a couple things in waydroid_base.prop.  


Change both these to what is shown below: 
ro.hardware.gralloc=default  
ro.hardware.egl=swiftshader  

Restart the container afterwards  
