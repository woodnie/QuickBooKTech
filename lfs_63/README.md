# LFS 6.3 {#lfs-6-3}

Linux from scratch 6.3

/        10G

/boot        100MB

/home

/usr/

/opt        5-10GB

/tmp        2GB

/usr/src/

mkfs -v -t ext4 /dev/&lt;xxx&gt;

mkswap /dev/&lt;yyy&gt;

export LFS=/mnt/lfs

mkdir -pv $LFS

mount -v -t ext4 /dev/&lt;xxx&gt; $LFS

mkdir -pv $LFS

mount -v -t ext4 /dev/&lt;xxx&gt; $LFS

mkdir -v $LFS/usr

mount -v -t ext4 /dev/&lt;yyy&gt; $LFS/usr

/sbin/swapon -v /dev/&lt;zzz&gt;

mkdir -pv $LFS/sources

chmod -v a+wt $LFS/sources

wget  -c -i wget-list -P $LFS/sources