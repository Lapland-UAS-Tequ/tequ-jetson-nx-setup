# tequ-jetson-nx-setup

## Actions

If you already have a working Jetson-NX, you can skip step 1.

### 1. First download the [Jetson-NX .img file](https://developer.nvidia.com/jetson-nx-developer-kit-sd-card-image).
- When you have downloaded it, flash it to an SD card using any imager you want.
- When flashed, plug it in to the Jetson and complete first time setup.

### 2. Preparing the SSD.
Next we need to prepare the SSD for usage, so plug it in and follow the instructions.
1. Install GParted on the machine
```
sudo apt install gparted
```
2. Next, open GParted using:
```
gparted
```
3. When in GParted, select the SSD from the dropdown in the top right corner.
4. When selected, go to Device and click on Create Partition Table and follow the given instructions.
5. Now you can open the Disks app from the search menu.
6. Then find and select your SSD from the list and press: Ctrl+F and click on format.
7. You now should have the whole SSD as **Free Space**
8. Now click on the **+** icon and create a partition with 16GB of free space, click next.
9. Then give it a name and click **Create**

Now the SSD is prepared.

### 3. Copying the Jetson OS to the SSD.
Now that the SSD is prepared, we need to transfer the OS to it.

1. First, clone the project and move into the directory.
```
git clone https://github.com/jetsonhacks/rootOnNVMe.git
cd rootOnNVMe
```
2. Then copy the OS to the SSD
```
./copy-rootfs-ssd.sh
```
3. Now you need to enable booting on the SSD and reboot, so the changes take effect.
```
./setup-service.sh
sudo reboot
```

And that's it! Now the Jetson will boot from the SSD. Remember that the Jetson Xavier NX still requires the SD card be plugged in.

### Sources
- https://www.seeedstudio.com/blog/2020/06/22/boot-jetson-xavier-from-m-2-ssd/
- https://www.jetsonhacks.com/2020/05/29/jetson-xavier-nx-run-from-ssd/
