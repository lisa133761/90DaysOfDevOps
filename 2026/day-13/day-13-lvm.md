day-13-lvm.md
 
## Commands Used: 
1. lsblk – View block devices
2. pvcreate – Create physical volume
3. vgcreate – Create volume group
4. lvcreate – Create logical volume
5. mkfs.ext4 – Format filesystem
6. mount – Mount filesystem
7. lvextend – Extend logical volume
8. resize2fs – Resize filesystem

What I Learned:

1. LVM allows flexible storage management by separating physical storage from logical volumes.
2. Logical volumes can be resized without unmounting the filesystem (in most cases).
3. Volume Groups combine multiple physical volumes into a single storage pool.
