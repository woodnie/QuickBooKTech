## apt &amp; yum {#apt-yum}

| **Task** | **Red Hat/Fedora** | **Ubuntu/Debian** |
| --- | --- | --- |
| **Adding, Removing and Upgrading Packages** |  |  |
| Refresh list of available packages | Yum refreshes each time it&amp;apos;s used | apt-get update |
| Install a package from a repository | yum install _package_name_ | apt-get install _package_name_ |
| Install a package file | yum install _package.rpm_ rpm -i _package.rpm_ | dpkg -install _package.deb_ |
| Remove a package | rpm -e _package_name_ | apt-get remove _package_name_ |
| Check for package upgrades | yum check-update | apt-get -s upgradeapt-get -s dist-upgrade |
| Upgrade packages | yum updaterpm -Uvh [args] | apt-get dist-upgrade |
| Upgrade the entire system | yum upgrade | apt-get dist-upgrade |
| **Package Information** |  |  |
| Get information about an available package | yum search _package_name_ | apt-cache search _package_name_ |
| Show available packages | yum list available | apt-cache dumpavail |
| List all installed packages | yum list installedrpm -qa | dpkg -list |
| Get information about a package | yum info _package_name_ | apt-cache show _package_name_ |
| Get information about an installed package | rpm -qi _package_name_ | dpkg -status _package_name_ |
| List files in an installed package | rpm -ql _package_name_ | dpkg -listfiles _package_name_ |
| List documentation files in an installed package | rpm -qd _package_name_ | - |
| List configuration files in an installed package | rpm -qc _package_name_ | - |
| Show the packages a given package depends on | rpm -qR _package_name_ | apt-cache depends |
| Show other packages that depend on agiven package (reverse dependency) | rpm -q -whatrequires [args] | apt-cache rdepends |
| **Package File Information** |  |  |
| Get information about a package file | rpm -qpi _package.rpm_ | dpkg -info _package.deb_ |
| List files in a package file | rpm -qpl _package.rpm_ | dpkg -contents _package.deb_ |
| List documentation files in a package file | rpm -qpd _package.rpm_ | - |
| List configuration files in a package file | rpm -qpc _package.rpm_ | - |
| Extract files in a package | rpm2cpio _package.rpm_ | cpio -vid | dpkg-deb -extract _package.deb_ dir-to-extract-to |
| Find package that installed a file | rpm -qf _filename_ | dpkg -search _filename_ |
| Find package that provides a particular file | yum provides _filename_ | apt-file search _filename_ |
| **Misc. Packaging System Tools** |  |  |
| Show stats about the package cache | - | apt-cache stats |
| Verify all installed packages | rpm -Va | debsums |
| Remove packages from the local cache directory | yum clean packages | apt-get clean |
| Remove only obsolete packages from the local cache directory | - | apt-get autoclean |
| Remove header files from the local cache directory(forcing a new download of same on next use) | yum clean headers | apt-file purge |
| **General Packaging System Information** |  |  |
| Package file extension | *.rpm | *.deb |
| Repository location configuration | /etc/yum.conf | /etc/apt/sources.list |