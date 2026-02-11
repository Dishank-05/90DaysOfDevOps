# Day 13 – Linux LVM

## Note
yum install lvm2
Install lvm first to run below commands 

lsblk
To check attached external disk

### 1. Physical Volume
pvcreate /dev/xvdb
pvs

### 2. Volume Group
vgcreate devops-vg /dev/xvdb
vgs

### 3. Logical Volume
lvcreate -L 500M -n app-data devops-vg
lvs

### 4. Format & Mount
mkfs.ext4 /dev/devops-vg/app-data
mount /dev/devops-vg/app-data /mnt/app-data

### 5. Extend LV
lvextend -L +200M /dev/devops-vg/app-data
resize2fs /dev/devops-vg/app-data

## What I Learned
1. LVM provides flexible storage management
2. We can extend the logical volume 
3. Flow: PV → VG → LV → Mount

