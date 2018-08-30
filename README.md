  
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
cp out/target/product/tiny4412/system/lib/libaudiopolicymanagerdefault.so /work/nfs_root/android_fs/alsa/multi_record  
cp out/target/product/tiny4412/system/lib/libaudiopolicymanager.so        /work/nfs_root/android_fs/alsa/multi_record  
cp out/target/product/tiny4412/system/lib/libaudiopolicyservice.so        /work/nfs_root/android_fs/alsa/multi_record  
  
   
3.3 now you can run two or more apps to record sound at one time
./AudioRecordTest 44100 2 1.pcm  &  
./AudioRecordTest 44100 2 2.pcm  &  
./AudioRecordTest 8000  2 3.pcm  &  
  
killall AudioRecordTest  
  
./pcm2wav 1.pcm 44100 2 1.wav  
./pcm2wav 2.pcm 44100 2 2.wav  
./pcm2wav 3.pcm 8000  2 3.wav  
  
tinyplay 1.wav  
tinyplay 2.wav  
tinyplay 3.wav  
 
  
