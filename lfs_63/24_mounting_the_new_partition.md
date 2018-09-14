## 2.4\. Mounting the New Partition {#2-4-mounting-the-new-partition}

2.4\. Mounting the New Partition

a chosen mount point. For the purposes of this book, it is assumed that the file system is mounted under /mnt/lfs, but the directory choice is up to you.

Choose a mount point and assign it to the LFS environment variable by running:

export LFS=/mnt/lfs

Next, create the mount point and mount the LFS file system by running:

mkdir -pv $LFS

mount -v -t ext4 /dev/&lt;xxx&gt; $LFS

Replace &lt;xxx&gt; with the designation of the LFS partition.

If using multiple partitions for LFS (e.g., one for / and another for /usr), mount them using:

mkdir -pv $LFS

mount -v -t ext4 /dev/&lt;xxx&gt; $LFS

mkdir -v $LFS/usr

mount -v -t ext4 /dev/&lt;yyy&gt; $LFS/usr