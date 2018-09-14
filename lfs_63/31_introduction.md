## 3.1\. Introduction {#3-1-introduction}

export LFS=/mnt/lfs

$LFS/sources can be used both as the place to store the tarballs and patches and as a working directory.

chmod -v a+wt $LFS/sources

pushd $LFS/sources

md5sum -c md5sums

popd