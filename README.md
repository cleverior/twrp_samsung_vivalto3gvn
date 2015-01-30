# twrp_samsung_vivalto3gvn
Device configuration for Samsung Galaxy vivalto3gvn

===================================

                       instruction how to build

I think you already set up build enviroment so I will skip this.

First go to your working dir/build/tools/device and open in gedit makerecoveries.sh

Find line 
        make -j16 recoveryzip
and replace it with
        make recoveryzip
beacause it wont eat your RAM and build will be faster


After you finshed repo sync go in your working dir/device/
and create folder /samsung/vivalto3gvn and copy content of vivalto3gvn
that you downloaded from here.
Replace android/bootable/recovery whit this one (omni 4.4 for v2.8.1.0) : https://github.com/Y300-0100/android_bootable_recovery
And make changes if you like.

Than run comannd in terminal from your working dir

        . build/envsetup.sh
        lunch omni_vivalto3gvn-eng
        make recoveryimage

Your build will start and you will find your recovery. img in
your working dir/out/target/product/vivalto3gvn

To make it flashable via ODIN you have to make it recovery.tar.md5
Navigate with terminal where your recovey.img is.
For example cd android/out/target/product/vivalto3gvn
where android is name of your working dir
and run comands:

        tar -H ustar -c recovery.img > recovery.tar
        md5sum -t recovery.tar >> recovery.tar
        mv recovery.tar recovery.tar.md5
        
An now you got recovery.tar.md5 ready to be flashed usin ODIN selected as PDA file

Happy building.




