  
frameworks/av/services/audiopolicy/AudioPolicyManager.cpp, for weidongshan's android video tutorial.  
  
to support Multi AudioRecord at same time.  
 
Usage:  
  
1. copy AudioPolicyManager.cpp to frameworks/av/services/audiopolicy/,  
  
2. on ubuntu:   
  
. setenv  
  
lunch full_tiny4412-eng    
  
mmm   frameworks/av/services/audiopolicy  
  
and you can get three new so files: libaudiopolicymanagerdefault.so libaudiopolicymanager.so libaudiopolicyservice.so
    
3. on android board:  
  
3.1 remount rootfs as rw:  
  
  su  
  
  mount -o remount /system  
  
3.2 copy the three so files to /system/lib and reboot   
   
3.3 now you can run two or more apps to record sound at one time
     
  
