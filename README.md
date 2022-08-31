This repository is developed in Fish-IoT project

https://www.tequ.fi/en/project-bank/fish-iot/ 

------------------------------------------------------------------------------------

This repository is deprecated. 

Since newer Jetpack releases preferred way is to connect NVMe/SSD to NVIDIA Jetson NX Development Kit and flash directly to NVMe/SSD using NVIDIA SDK Manager from Linux host machine, for example, Ubuntu 20.04.

Please see following site:

https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html

------------------------------------------------------------------------------------

# tequ-jetson-nx-setup

Setup Jetson NX to boot from SSD drive. 

Tested with:
- NVIDIA Jetson NX Development Kit
- re_computer case - X86J4105
- Western Digital WDS500G3X0C - WD Black™ SN750 NVMe™ SSD M.2 500GB PCIe Gen3 8 GB/s 

## Actions

### 1. Download latest official Jetson NX image file
- https://developer.nvidia.com/jetson-nx-developer-kit-sd-card-image

### 2. Flash image to SD card
- Use for example Raspberry PI imager tool
- https://downloads.raspberrypi.org/imager/imager_latest.exe

### 3. Boot Jetson with SD card
- Plug SD card
- Connect mouse, keyboard and display for graphical setup
- Setup Micro-USB connection for terminal setup
- https://developer.nvidia.com/embedded/learn/get-started-jetson-xavier-nx-devkit#setup

### 4. Connect SSD drive

### 5. Prepare the SSD
Next we need to prepare the SSD for usage, so plug it in and follow the instructions.

1. Install GParted on the machine 

```
sudo apt-get update 
```

```
sudo apt install gparted
```

2. Open GParted 

```
gparted
```

3. Create new empty formatted partition (ext4) to NVMe 

Now the SSD is ready for use.

### 6. Copy Jetson OS to the SSD.

1. Clone project from jetsonhacks and move into the directory.

```
cd /home/
```
```
sudo git clone https://github.com/jetsonhacks/rootOnNVMe.git
```
```
cd /home/rootOnNVMe
```

2. Run copy script (SD => SSD)

```
./copy-rootfs-ssd.sh
```

3.  Enable booting on the SSD

```
./setup-service.sh
```
```
sudo reboot
```

4. Reboot

Now the Jetson will boot from the SSD. Remember that the Jetson Xavier NX still requires the SD card be plugged in. At the moment direct booting from NVMe is not supported.

### Sources
- https://developer.nvidia.com/embedded/learn/get-started-jetson-xavier-nx-devkit#intro
- https://www.seeedstudio.com/blog/2020/06/22/boot-jetson-xavier-from-m-2-ssd/
- https://www.jetsonhacks.com/2020/05/29/jetson-xavier-nx-run-from-ssd/
