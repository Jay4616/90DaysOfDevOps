Day 13: LVM Lab Setup & Extension
Traditional static partitioning forces you to shut down services when a drive fills up. Logical Volume Management (LVM) creates a virtualized storage layer, allowing you to pool physical disks together and scale spaces dynamically on-the-fly without any downtime.

🛠️ Practical Lab Commands
1. Create a 1GB virtual disk image file filled with zeroes
  dd if=/dev/zero of=virt_disk.img bs=1M count=1024

2. Map the image file to the first available loop device
  sudo losetup -f --show virt_disk.img
(Note: Assume the output device returned is /dev/loop0)

3. Initialize the LVM architecture layers (PV, VG, and LV)
  sudo pvcreate /dev/loop0
  sudo vgcreate my_vg /dev/loop0
  sudo lvcreate -n my_lv -L 500M my_vg

4. Format the logical volume partition with Ext4 and mount it
  sudo mkfs.ext4 /dev/my_vg/my_lv
  sudo mkdir -p /mnt/my_storage
  sudo mount /dev/my_vg/my_lv /mnt/my_storage

5. Live storage dynamic extension (+200MB) and filesystem resizing
  sudo lvextend -L +200M /dev/my_vg/my_lv
  sudo resize2fs /dev/my_vg/my_lv

6. Verify the expanded space layout and confirm the new size
  df -h /mnt/my_storage
