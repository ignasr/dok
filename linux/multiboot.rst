multiboot
=========

.. code-block:: none

   # grub2
   # =====
   # 
   # search --file SysRescCD
   # sudo grub2-install --force --no-floppy --boot-directory=/run/media/ignas/MULTIBOOT/boot /dev/sdb
   # 
   # qemu-kvm
   # ========
   # 
   # sudo qemu-kvm -m 512 /dev/sdb
   # 
   # web
   # ===
   # 
   # http://www.circuidipity.com/multi-boot-usb.html
   # https://help.ubuntu.com/community/Grub2/ISOBoot/Examples
   # https://wiki.archlinux.de/title/Multiboot_USB_Stick
   # 
   # 
   # clonezilla
   # ==========
   # 
   # http://clonezilla.org/livehd.php
   
   # Fedora
   # ======
   #
   # https://github.com/thias/glim/blob/master/grub2/inc-fedora.cfg
   
   # Timeout for menu
   set timeout=30
   
   # Default boot entry
   set default=0
   
   # Menu Colours
   set menu_color_normal=white/black
   set menu_color_highlight=white/green
   
   # Boot ISOs
   menuentry "Clonezilla" {
     set isofile="/iso/clonezilla-live-2.2.4-12-i686-pae.iso"
     set gfxpayload=800x600x16
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/live/vmlinuz boot=live live-config noswap nolocales edd=on nomodeset ocs_live_run=\"ocs-live-general\" ocs_live_extra_param=\"\" keyboard-layouts=\"\" ocs_live_batch=\"no\" locales=\"\" ip=frommedia nosplash toram=filesystem.squashfs findiso=$isofile i915.blacklist=yes radeonhd.blacklist=yes nouveau.blacklist=yes vmwgfx.enable_fbdev=1
     initrd (loop)/live/initrd.img
   }
   
   menuentry "KAV neveikia" {
      loopback loop /iso/kav_rescue_10.iso
     set gfxpayload=800x600x16
      set root=(loop)
      linux /boot/rescue root=live:/dev/well/this/is/nonsense rootfstype=auto init=/init initrd=rescue.igz kav_lang=${kav_lang} udev liveimg splash quiet doscsi nomodeset
      initrd /boot/rescue.igz
   }
   
   menuentry "DBAN ISO" {
     set isofile="/iso/dban-2.2.8_i586.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/DBAN.BZI nuke="dwipe" iso-scan/filename=${isofile} silent --
   }
   
   menuentry "SystemRescueCD 64bit" {
     set isofile="/iso/systemrescuecd-x86-4.3.0.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/isolinux/rescue64 isoloop=${isofile} setkmap=us
     initrd (loop)/isolinux/initram.igz
   }
   
   menuentry "SystemRescueCD 64bit to RAM" {
     set isofile="/iso/systemrescuecd-x86-4.3.0.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/isolinux/rescue64 isoloop=${isofile} setkmap=us docache
     initrd (loop)/isolinux/initram.igz
   }
   
   menuentry "SystemRescueCD 32bit" {
     set isofile="/iso/systemrescuecd-x86-4.3.0.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/isolinux/rescue32 isoloop=${isofile} setkmap=en
     initrd (loop)/isolinux/initram.igz
   }
   
   menuentry "Fedora 20 64bit Live Gnome" {
     set isoname="Fedora-Live-Desktop-x86_64-20-1.iso"
     set isofile="/iso/$isoname"
     echo "Using ${isoname}..."
     loopback loop $isofile
     linux (loop)/isolinux/vmlinuz0 root=live:CDLABEL=Fedora-Live-Desktop-x86_64-20-1 rootfstype=auto ro rd.live.image quiet rhgb rd.luks=0 rd.md=0 rd.dm=0 iso-scan/filename=${isofile}
     initrd (loop)/isolinux/initrd0.img
   }
   
   menuentry "Fedora 20 64bit Live Xfce" {
     set isoname="Fedora-Live-Xfce-x86_64-20-1.iso"
     set isofile="/iso/$isoname"
     echo "Using ${isoname}..."
     loopback loop $isofile
     linux (loop)/isolinux/vmlinuz0 root=live:CDLABEL=Fedora-Live-Xfce-x86_64-20-1 rootfstype=auto ro rd.live.image quiet rhgb rd.luks=0 rd.md=0 rd.dm=0 iso-scan/filename=${isofile}
     initrd (loop)/isolinux/initrd0.img
   }
   
   menuentry "Debian 7.6 - 64bit netinst" {
     set isofile="/iso/debian-7.6.0-amd64-netinst.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/install.amd/vmlinuz boot=live findiso=${isofile} config quiet splash
     initrd (loop)/install.amd/initrd.gz
   }
   
   menuentry "Debian 7.6 - 64bit CD1" {
     set isofile="/iso/debian-7.6.0-amd64-CD-1.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/install.amd/vmlinuz boot=live findiso=${isofile} config quiet splash
     initrd (loop)/install.amd/initrd.gz
   }
   
   menuentry "Ubuntu 14.04 LTS - 64bit Mini-Installer" {
     set isofile="/iso/ubuntu-14.04-amd64-mini.iso"
     echo "Using ${isofile}..."
     loopback loop $isofile
     linux (loop)/linux boot=casper iso-scan/filename=$isofile noprompt noeject
     initrd (loop)/initrd.gz
   }
   
