# Ubuntu MATE 21.10 Impish Indri Nexus 7 2012 rev. E1565 kernel-5.15.0-rc4
Nexus 7 2012

Link tải trên Gdrive:



Ubuntu MATE 21.10 Impish Indri ext4 kernel-5.15.0-rc4-next-20211011-postmarketos-grate

https://drive.google.com/drive/u/1/folders/1Ib3Xdz0oG1EiWU2MDjyr7o6LxN8xHWCt



Ubuntu 21.10 Impish Indri preinstalled server ext4 kernel-5.15.0-rc4-next-20211011-postmarketos-grate

https://drive.google.com/drive/u/0/folders/1GC9I_hZl3H6LVd2IG_XYJLHrq6Bj-c6C



default user was kim, default passwd was possible



default user was ubuntu, default passwd was ubuntu



Đã thử và thành công boot được Ubuntu 21.10 Impish Indri lên Nexus 7 2012, tạo local user/passwd theo bài viết này cho cloud-init như 1 phần bổ sung khi bị cloud-init: used fallback datasource thì module cuối trong cloud.cfg không chạy để khởi tạo user/passwd ubuntu:ubuntu

https://stackoverflow.com/questions/61591885/how-do-i-set-a-custom-password-with-cloud-init-on-ubuntu-20-04



Đây là bản preinstalled nên không có GUI và cần có micro usb-otg keyboard để nhập lệnh



Cách kiểm tra Nexus 7 2012 là mã cũ PM269 hay E1565. Tham khảo:

https://wiki.postmarketos.org/wiki/Google_Nexus_7_2012_(asus-grouper)



Variants

grouper rev. PM269 - without GSM (oldest)
grouper rev. E1565 - without GSM (modern revision)
tilapia rev. E1565 - with GSM



Do I have grouper or tilapia?



TWRP (adb shell) $ grep androidboot.baseband=unknown /proc/cmdline && echo grouper || echo tilapia



Which hardware revision of grouper do I have?





TWRP (adb shell) $ find /sys/devices/ | grep -c max776 && echo You have E1565



TWRP (adb shell) $ find /sys/devices/ | grep -c tps6591 && echo You have PM269



Install Alpine Linux on Virtualbox:

[MEDIA=youtube]1_bsycXrFcI[/MEDIA]



Đặt máy về bootloader, để flash boot.img qua fastboot hoặc dùng method của postmarketOS. Kết nối Nexus 7 vào máy tính qua cáp usb chuẩn 1.0 → 2.0



$ sudo adb start-server



$ sudo adb reboot bootloader



$ sudo fastboot flash boot <boot_filename>.img



Vào TWRP for grouper 3.3.1-0 trở lên https://dl.twrp.me/grouper/

Dùng adb shell trên PC/laptop hoặc Advance/Terminal trong twrp để umount mmcblk0p9 (làm 2 lần cho chắc ăn) [với tilapia (bản 3G) là mmcblk0p10]



1. TWRP(Advance → Terminal): $ df

2. TWRP(Advance → Terminal): $ umount /dev/block/mmcblk0p__  <- fill partition number

3. TWRP(Advance → Terminal): $ umount /dev/block/mmcblk0p__  <- fill partition number



On PC/Laptop terminal:



$ adb push <rootfs_filename>.img /dev/block/mmcblk0p__  <- fill partition number



grouper has likely data on /dev/block/mmcblk0p9 but make sure!
tilapia has likely data on /dev/block/mmcblk0p10 but make sure!



remove cloud-init, snapd, needrestart service

https://askubuntu.com/questions/1346874/failed-to-check-for-processor-microcode-upgrades-at-the-end-of-apt-get-how-ca



# sudo apt --purge remove  needrestart



Rotate fbcon



# sudo su



# echo 1 | sudo tee /sys/class/graphics/fbcon/rotate



# echo 1 | sudo tee /sys/class/graphics/fbcon/rotate_all



# sudo apt install network-manager



# chown -hvR ubuntu /home/ubuntu



Install xubuntu-core



# sudo apt install xubuntu-core^



# sudo apt install bluez blueman htop neofetch iio-sensor-proxy perl x11-xserver-utils



grate-driver 2D/3D GPU accelerate on launchpad.net

https://launchpad.net/~grate-driver/+archive/ubuntu/ppa/+packages?field.name_filter=&field.status_filter=published&field.series_filter=impish



# sudo add-apt-repository ppa:grate-driver/ppa



# sudo apt update



# sudo apt-get install alsa-ucm-conf libvdpau-tegra xserver-xorg-video-opentegra linux-firmware libd3dadapter9-mesa libegl-mesa0 libgbm1 libgl1-mesa-dri libglapi-mesa libglx-mesa0 libosmesa6 mesa-opencl-icd mesa-va-drivers mesa-vdpau-drivers mesa-vulkan-drivers



Rotate screen

https://gitlab.com/gullradriel/asus-grouper-nexus-7-sensor-daemon



Các phần mềm hỗ trợ để trong /opt



Image source là Ubuntu MATE 21.10 rpi armhf

https://releases.ubuntu-mate.org/impish/armhf/ubuntu-mate-21.10-beta1-desktop-armhf+raspi.img.xz



Image source là Raspberry Pi Generic (Hard-Float) preinstalled server image:

https://cdimage.ubuntu.com/ubuntu/releases/21.10/release/ubuntu-21.10-preinstalled-server-armhf+raspi.img.xz



Ubuntu MATE guide:

https://tinhte.vn/thread/ubuntu-mate-20-04-3-lts-nexus-7-2012-rev-e1565-kernel-5-15-0-rc4-next-20211011-postmarketos-grate.3198632/



Xem thêm hướng dẫn trong bài post này:

https://tinhte.vn/thread/ubuntu-21-04-1-hirsute-hippo-pre-image-cho-nexus-7-2012-wifi-rev-e1565-kernel-5-14-rc3-next-grate.3392201/



[MEDIA=youtube]XKZG655V5PQ[/MEDIA]
