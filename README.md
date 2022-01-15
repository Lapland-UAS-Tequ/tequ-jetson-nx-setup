This repository is developed in Fish-IoT project

https://www.tequ.fi/en/project-bank/fish-iot/ 

---

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

3. When in GParted, select the SSD from the dropdown in the top right corner.
4. When selected, go to Device and click on Create Partition Table (gpt) and follow the given instructions.
5. Now you can open the Disks app from the search menu.
6. Then find and select your SSD from the list and press: Ctrl+F and click on format.
7. You now should have the whole SSD as **Free Space**
8. Now click on the **+** icon and create a partition with at least 16GB of free space, click next.
9. Then give it a name and click **Create**

Now the SSD is ready for use.

### 6. Copy Jetson OS to the SSD.

1. Clone project from jetsonhacks and move into the directory.

```
cd /home/
sudo git clone https://github.com/jetsonhacks/rootOnNVMe.git
cd /home/rootOnNVMe
```

2. Run copy script (SD => SSD)

```
./copy-rootfs-ssd.sh
```

3.  Enable booting on the SSD

```
./setup-service.sh
sudo reboot
```

4. Reboot

Now the Jetson will boot from the SSD. Remember that the Jetson Xavier NX still requires the SD card be plugged in. At the moment direct booting from NVMe is not supported.

### Sources
- https://developer.nvidia.com/embedded/learn/get-started-jetson-xavier-nx-devkit#intro
- https://www.seeedstudio.com/blog/2020/06/22/boot-jetson-xavier-from-m-2-ssd/
- https://www.jetsonhacks.com/2020/05/29/jetson-xavier-nx-run-from-ssd/
