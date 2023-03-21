This repository is developed in Fish-IoT project

https://www.tequ.fi/en/project-bank/fish-iot/ 

------------------------------------------------------------------------------------

Since newer Jetpack releases preferred way is to connect NVMe/SSD to NVIDIA Jetson NX Development Kit and flash directly to NVMe/SSD using NVIDIA SDK Manager from Linux host machine, for example, Ubuntu 20.04.

Please see following site:

https://docs.nvidia.com/sdk-manager/install-with-sdkm-jetson/index.html

------------------------------------------------------------------------------------

# tequ-jetson-nx-setup

Setup Jetson NX to boot from SSD drive. 

Tested with following setups:

From SD-card to NVMe:
- NVIDIA Jetson NX Development Kit
- re_computer case - X86J4105
- WesternDigital WDS500G3X0C - WD Black™ SN750 NVMe™ SSD M.2 500GB PCIe Gen3 8 GB/s 

From EMMC to NVMe:
- A203 Carrier board
- Jetson Xavier NX 8 GB module, 16 GB EMMC
- Greenliant 64 GB NVMe GLS88DQ064G3-I-BZ300


## Actions

### 1. Download latest official Jetson NX image file
- https://developer.nvidia.com/jetson-nx-developer-kit-sd-card-image

### 2. Flash image to SD card / EMMC
- Use for example Raspberry PI imager tool or NVIDIA SDK Manager

### 3. Connect display, mouse and keyboard
- You can also use remote control eg. [NoMachine](https://www.nomachine.com) if you dont have peripherals.

### 4. Connect external drive

### 5. Boot Jetson 

### 6. Prepare the SSD
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

### 7. Copy Jetson OS to the SSD.

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

2. Run copy script (SD/EMMC => SSD)

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

Now the Jetson will boot from the SSD. Remember that the Jetson Xavier NX still requires the SD/EMMC be plugged in when using this approach.

### Sources
- https://developer.nvidia.com/embedded/learn/get-started-jetson-xavier-nx-devkit#intro
- https://www.seeedstudio.com/blog/2020/06/22/boot-jetson-xavier-from-m-2-ssd/
- https://www.jetsonhacks.com/2020/05/29/jetson-xavier-nx-run-from-ssd/
