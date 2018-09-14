## VCA Exam {#vca-exam}

VMware 2V0-620 vSphere 6 Foundations Beta Exam

Q1\. By default, each ESXi 6.x host is provisioned with a certificate from which root certificate authority?

A. RedHat Certificate Authority

B. VMware Certificate Authority

C. DigiCert Certificate Authority

D. Verisign Certificate Authority

Answer: B

Q2\. Which vSphere 6 Enterprise Edition feature will allow an organization to ensure that critical multi- threaded applications have

the maximum possible uptime?

A. Fault Tolerance

B. High Availability

C. Distributed Resource Scheduler

D. App HA

Answer: A

Q3\. Which vSphere 6 Standard Edition feature will allow an organization to ensure that critical multi- threaded applications have

the maximum possible uptime?

A. Fault Tolerance

B. High Availability

C. Distributed Resource Scheduler

D. App HA

Answer: B

Q4\. Which vSphere 6.x feature will allow an organization to utilize native snapshots?

A. Virtual Volumes

B. Virtual SAN

C. VMFS3

D. VMFS5

Answer: A

Q5\. Which two components can be used when configuring Enhanced Linked Mode? (Choose two.)

A. vCenter Server Appliance

B. vRealize Operations Manager

C. vSphere Management Appliance

D. vCenter Server for Windows

Answer: A,D

Q6\. What is the effective vSphere licensing level during the 60 day evaluation period?

A. vSphere Foundation Essentials Plus

B. vSphere Standard

C. vSphere Enterprise

D. vSphere Enterprise Plus

Answer: D

Q7\.

What component must be installed prior to deploying a vCenter Server in vSphere 6.x?

A. vCenter Identity Services

B. Platform Services Controller

C. vCenter Single Sign-On

D. Client Integration Plug-In

Answer: B

Q8\. An administrator deploys vCenter Server using the embedded Platform Services Controller. After testing the deployment for a

couple of months, it is determined that the environment would be better served with an external Platform Services Controller.

What should the administrator do to meet this new requirement?

A. Deploy a fresh instance of vCenter Server with an external Platform Services Controller.

B. Perform a fresh install of an external Platform Services Controller.

C. Migrate the embedded Platform Services Controller to an external Platform Services Controller.

D. Upgrade the embedded Platform Services Controller to an external Platform Services Controller.

Answer: A

Q9\. An administrator is installing vCenter Server for an environment that has 40 ESXi 6.x Hosts and 150 virtual machines.

Which database would meet the minimal requirements needed for this task?

A. vFabric Postgres

B. Microsoft SQL Express 2008

C. Microsoft SQL Server 2014

D. Oracle 11g

Answer: A

Q10\. What information is required as part of an interactive ESXi 6.x installation?

A. Keyboard layout

B. IP Address

C. Root password

D. DNS information

Answer: A

Q11\. After installation of a host in your test environment, you need to move it to production. The only major change that needs to

be made is that the hostname of the server needs to change.

What are two ways that an administrator can change the host name without editing configuration files on the host directly?

(Choose two.)

A. Login to the Direct Console User Interface and change it from here.

B. Edit the Default TCP/IP Configuration from the vSphere Web Client.

C. Use the Ruby vSphere Client to send a script to the ESXi host that updates the hostname.

D. Update the information in DNS and the ESXi host will automatically update with these changes.

Answer: A,B

Q12\. You are editing the management network configuration of an ESXi 6.x Host from the vSphere Web Client. You mistakenly

put the incorrect VLAN in place for the management network.

What action do you need to take to correct this?

A. You need to manually edit the configuration on the host with command line utilities.

B. No action is required. By default ESXi rolls back configuration changes that disconnect the host.

C. The ESXi host system configuration will need to be restored to the factory configuration to fix the issue.

D. The change can be reverted in the vSphere Web Client by simply editing the switch again.

Answer: B

Q13\. You have just installed an ESXi 6.x Host. As part of your company security regulations, a security banner must be presented

on the console of the host.

How can this action be accomplished?

A. Configure the Advanced Settings &gt; Annotations screen of the ESXi host.

B. This is configured from the Direct Console User Interface configuration menu.

C. It is not possible to configure a security banner for the ESXi host.

D. From vCenter Server, this setting is configured globally in the vCenter Server configuration.

Answer: A

https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&amp;cmd=displayKC&amp;externalId=2046347

Q14\. In order for a company to meet regulatory requirements, all ESXi 6.x Hosts must be configured to direct logs to a syslog

server.

What are two ways ESXi hosts can configured for this action? (Choose two)

A. Use the esxcli system syslog command.

B. Edit them in the ESXi host Advanced System Settings.

C. From the Syslog collector user interface of the Web Client.

D. Syslog logging is notavailablefor ESXi Hosts.

Answer: A,B

Q15\. An administrator is performing an interactive installation of ESXi 6.x.

Which three options are available for installation? (Choose three.)

A. DVD

B. USB

C. PXE

D. Scripted

E. Auto Deploy

Answer: A,B,C

Q16\. An administrator is performing a scripted installation of ESXi 6.x.

In which three locations does the script need to be? (Choose three.)

A. PXE Server

B. HTTPS

C. FTP

D. NFS

E. VVOLs Datastore

Answer: B,C,D

Q17\. Which three items should be validated prior to installing ESXi 6.x? (Choose three.)

A. Remote Storage has been disconnected.

B. Installation media is available.

C. Server hardware clock is set to UTC.

D. Storage has been partitioned with a VMFS volume.

E. Network cards have been setup to use Jumbo Frames.

Answer: A,B,C

Q18\. An administrator has just completed performing an interactive installation of ESXi 6.x and is booting the host.

How is the network initially configured?

A. The network is configured by Automatic Private IP Addressing (APIPA).

B. The network is configured based on the settings detected in DNS.

C. The network is configured with the address as specified in the installer.

D. The network is automatically configured by DHCP.

Answer: D

Q19\. An administrator has just completed installing an ESXi 6.x host, but doesn&amp;apos;t know what address has been configured.

Where is the ESXi host IP address configured?

A. RVC console

B. Direct Console User Interface

C. vSphere Web Client

D. vSphere Client

Answer: B

Q20\. An administrator has just configured the IP address on an ESXi host from the Direct Console User Interface.

How can the configuration be validated as correct without any additional tools?

A. Add the host to vCenter Server and if it works, then all networking settings are ok.

B. Select the Test Management Network option from the DCUI.

C. Connect to the host with the vSphere Client and click the Test Network option.

D. Use PowerCLI to connect to the host and initiate a network test.

Answer: B

Q21\. An administrator has recently installed a new ESXi 6.x Host, and during the configuration notices sporadic network problems.

To check whether the issue occurred sometime during the configuration, the administrator would like to reset the system.

How can this be accomplished in the shortest amount of time?

A. Run the ESXi installer again and reinstall the host.

B. Select the Reset System Configuration option from the vSphere Client when connected directly to the host.

C. From the Direct Console User Interface, select Reset System Configuration.

D. Use a host profile to reset the configuration to a default state.

Answer: C

Q22\. Your manager has given you a bash script that retrieves data for ESXi 6.x host configurations. This data needs to be

collected right after the installation of a host and must be run directly on the host.

Which two actions can be used to run this script on an ESXi host? (Choose two.)

A. Connect to the host with Ruby vSphere Console and run the script from there.

B. Enable SSH access from the Direct Console User Interface.

C. Enable the ESXi Shell from the Direct Console User Interface.

D. Run the script directly from the vSphere Web Client.

Answer: B,C

Q23\. What is the default load balancing policy for a newly created VMkernel port on a vSphere Distributed Switch?

A. Route based on orginating virtual port ID

B. Route based on IP Hash

C. Route based on source mac address

D. Route based on physical NIC load

Answer: A

Q24\. How are ports scaled on vSphere Standard Switches (vSS)?

A. Ports on a vSS can be dynamically scaled up and down.

B. Ports on a vSS can only be statically scaled up or down.

C. Ports on a vSS can only be dynamically scaled down.

D. Ports on a vSS can only be dynamically scaled up.

Answer: A

Q25\. Which three connection types are available when configuring a vSwitch in the vSphere Web Client? (Choose three.)

A. VMkernel Network Adapter

B. Physical Network Adapter

C. Virtual Machine Port Group for a Standard Switch

D. vMotion Network Adapter

E. vSAN Network Adapter

Answer: A,B,C

Q26\. How many Link Aggregation Groups (LAGs) can be configured on a vSphere 6.x Distributed Switch?

A. 64

B. 96

C. 128

D. 256

Answer: A

Q27\. An administrator is configuring the Failover Order option on a vSphere Distributed Switch.

Which two options should be used with IP-hash load balancing? (Choose two.)

A. Active Uplinks

B. Standby Uplinks

C. Unused Uplinks

D. Override Failover Order

Answer: A,C

Q28\. An administrator is creating a new vSphere Distributed Switch that will be utilized with a specific vSphere Cluster. The cluster

itself contains a mix of ESXi 5.x and 6.x Hosts.

Which Distributed Switch version should be created to support this configuration?

A. Distributed Switch: 6.0.0

B. Distributed Switch: 5.0.0

C. Distributed Switch: 5.1.0

D. Distributed Switch: 5.5.0

Answer: B

Q29\. During a new vSphere Distributed Switch configuration, where does the Maximum Transmission Unit (MTU) value get

modified?

A. Uplink Settings

B. Switch Settings

C. Portgroup Settings

D. NIC Teaming Settings

Answer: B

Q30\.

Which two actions are prerequisites to adding ESXi 6.x hosts to a vSphere Distributed Switch? (Choose two.)

A. Verify that there is at least one Distributed Port Group on the Distributed Switch.

B. Verify that the Distributed Port Group have active uplinks configured in its teaming and failover policy.

C. Verify that the Distributed Switch has been configured with a Network Profile.

D. Verify that Network I/O control for Management Traffic is configured for the highest share value.

Answer: A,B

Q31\. Which load balancing policy, previously limited to vSphere Distributed Switches, is now available on vSphere Standard

Switches with vSphere 6.x?

A. Route based on physical NIC workload

B. Route based on IP Hash

C. Route based on the originating virtual port

D. Route based on Source MAC Hash

Answer: A

Q32\. Which three VLAN Tagging modes are available in vSphere 6.x? (Choose three.)

A. External Switch Tagging

B. Private VLAN Tagging

C. Virtual Switch Tagging

D. VXLAN Tagging

E. Virtual Guest Tagging

Answer: A,C,E

Q33\. Which three traffic types are available services options when configuring a vmkernel port? (Choose three.)

A. Provisioning Traffic

B. Virtual Volumes Traffic

C. vSphere Replication NFC Traffic

D. Virtual SAN Traffic

E. FCoE Traffic

Answer: A,C,D

Q34\. Which two networking connection types can be configured on a virtual switch? (Choose two.)

A. Virtual machine portgroups

B. VMkernel services (such as NFS, iSCSI, or vMotion) to the physical network

C. Web services over the Management Network

D. NFS and FCoE storage services

Answer: A,B

Q35\. An administrator is configuring the Maximum Transmission Unit value on a vSphere Distributed Switch.

Which two options are typical values for ESXi networking? (Choose two.)

A. 1492

B. 1500

C. 9000

D. 9089

Answer: B,D

Q36\. An administrator needs to monitor traffic on vSwitches in a vSphere 6.x environment.

Which option, if configured, would accomplish this task?

A. Forged Transmits

B. MAC Address Changes

C. Promiscuous Mode

D. Notify Switches

Answer: C

Q37\. Which two allow for the disabling of Network Rollback operations? (Choose two.)

A. Modifying the vpxd advanded configuration options and adding the config.vpxd.network.rollback key

B. Modifying the C:\ProgramData\VMware\CIS\cfg\vmware-vpx\vpxd.cfg file and adjusting the&lt;rollback&gt; xml tag

C. Modifying the C:\ProgramData\VMware\CIS\cfg\vmware-vpx\vpxd.cfg file and adjusting the &lt;networkrollback&gt; xml tag

D. Modifying the C:\ProgramData\VMware\CIS\cfg\vmware-vpx\firstboot\vpxd-service-spec.prop file and adjusting the &lt;rollback&gt;

xml tag

Answer: A,B

Q38\. What are two ways to identify TCP/IP stack information? (Choose two.)

A. Using the vSphere Web Client

B. Using esxcli network ip netstack

C. Using esxcfg-netstack

D. Using the vSphere Client

Answer: A,B

Q39\. Which two Fibre Channel zoning options are supported with vSphere 6.x? (Choose two.)

A. Single-Initiator

B. Single-Initiator-Single-Target

C. Multiple-Initiators-Single-Target

D. Multiple-Initiators-Multiple-Targets

Answer: A,B

Q40\. Which two parameters are required when adding an iSCSI target to an iSCSI Software Adapter using Dynamic Discovery?

(Choose two.)

A. The iSCSI device&amp;apos;s IP Address or Fully Qualified Domain Name

B. The Port Number

C. The iSCSI device&amp;apos;s iSCSI Qualified Name (IQN)

D. The Default Gateway IP Address

Answer: A,B

Q41\. What is true regarding datastores on ESXi 6.x?

A. NFS 4.1 datastore does not support Fault Tolerance (FT)

B. VMFS3 and VMFS5 datastores can be newly created

C. NFS datastore can be concurrently mounted using NFS 4.1 on one host and NFS on another

D. NFS 3.0 datastore does not support Fault Tolerance (FT)

Answer: A

Q42\. Which type of Adapter does not require vmkernel networking?

A. Independent Hardware iSCSI Adapter

B. Dependent Hardware iSCSI Adapter

C. Software iSCSI Adapter

D. Software FCoE Adapter

Answer: A

Q43\. What are two benefits of using NFS 4.1 with vSphere 6.x as compared to NFS 3? (Choose two.)

A. NFS 4.1 supports Kerberos Authentication

B. NFS 4.1 supports multipathing

C. NFS 4.1 supports IPv6

D. NFS 4.1 supports hardware acceleration

Answer: A,B

Q44\. Which two storage controller configurations can be used with Virtual SAN? (Choose two.)

A. SAS controllers in Passthrough mode

B. SAS controllers in RAID0 mode

C. SAS controllers in RAID1 mode

D. SAS controllers in RAID10 mode

Answer: A,B

Q45\. A company has decided to implement Virtual SAN within their vSphere 6.x environment. The Virtual SAN cluster will be

composed of three ESXi 6.x hosts that are on the Virtual SAN Ready Node list.

Each ESXi host includes:

- Two SAS Controllers that support Passthrough Mode

- Four Solid State Drives (SSDs) 1TB in size each

- 20 SAS Magnetic Disks (MDs) 1TB in size each

- The SSDs and MDs are evenly split between the two SAS controllers

The company will pilot a Virtual SAN cluster utilizing VMware best practices while maximizing storage capacity. The Virtual SAN

cluster will use Manual Mode.

Which two Disk Group configurations would meet the stated configuration requirements? (Choose two.)

A. 4 disk groups with 1 SSD and 5 MDs each

B. 2 disk groups with 1 SSD and 7 MDs each

C. 2 disk groups with 2 SSDs and 7 MDs each

D. 2 disk groups with 1 SSD and 10 MDs each

Answer: A,B

Q46\. An administrator is creating a new Virtual SAN cluster on a Layer 2 network. There is an existing Virtual SAN cluster on the

same Layer 2 network.

Which two actions would allow the new Virtual SAN cluster to coexist with the older cluster? (Choose two.)

A. Change the default Multicast Address on the new Virtual SAN cluster.

B. Change the default Unicast Address on the new Virtual SAN Cluster.

C. Create a separate VLAN for each cluster.

D. Create an ARP Alias for the Virtual SAN VMkernel Network Adapter.

Answer: A,C

Q47\. Which two Virtual SAN related actions might start resynchronization of virtual machine objects? (Choose two.)

A. Editing a virtual machine storage policy to increase the number of replicas.

B. Editing a virtual machine storage policy to reduce the number of replicas.

C. Editing a virtual machine storage policy to increase the number of disk stripes.

D. Editing a virtual machine storage policy to reduce the number of disk stripes.

Answer: A,C

Q48\. Which two NFS Protocol versions does vSphere 6 support? (Choose two.)

A. Version 3

B. Version 3.1

C. Version 4

D. Version 4.1

Answer: A,D

Q49\.

An administrator attempts to create a Thick Provisioned Virtual Disk (VMDK) on an NFS datastore; but it fails.

Which two reasons would explain the failure? (Choose two.)

A. Datastore is on an NFS 3 storage server that does not support Hardware Acceleration

B. Datastore is on an NFS 4.1 storage server

C. Only VMFS datastores support &quot;Thick Provisioned&quot; VMDK

D. The NFS datastore was not created on a &quot;Thick Provisioned&quot; device

Answer: A,B

Q50\. What condition would prevent an administrator from creating a new VMFS3 datastore on an ESXi 6.x host using the vSphere

Web Client?

A. A VMFS3 datastore cannot be created on an ESXi 6.x host.

B. The VMFS3 kernel module is not loaded.

C. A VMFS3 datastore cannot be mounted on an ESXi 6.x host.

D. VMFS3 datastores are not compatible with virtual machines created on an ESXi 6.x host.

Answer: A

Q51\. Which two statements are true about VMFS5 datastores on ESXi 6.x? (Choose two.)

A. Virtual Disk (VMDK) size can be larger than 2TB.

B. Datastore extent size can be larger than 2TB.

C. Only Physical Mode Raw Device Map (Passthrough-RDM) can be larger than 2TB.

D. 2MB block size is required to support larger than 2TB file size.

Answer: A,B

Q52\. Which three conditions would prevent Storage I/O Control from being enabled on a group of datastores? (Choose three.)

A. The datastores planned for the solution are used by different vSphere clusters.

B. A datastore planned for the solution is configured as a Raw Device Mapping file.

C. A datastore planned for the solution has three extents.

D. A datastore planned for the solution is configured as NFS.

E. The organization has an Enterprise license.

Answer: B,C,E

Q53\. When is it possible to place a VMFS5 datastore in maintenance mode?

A. When it is a member of a Storage DRS cluster

B. When it is a member of Virtual SAN cluster

C. When it is a member of a multi-extent datastore

D. When it is a member of a Virtual Volume

Answer: A

Q54\. Refer to the Exhibit.

A vSphere 6.x Standard Switch is configured with 4 virtual machine portgroups, as shown in the exhibit.

Which portgroup would be utilized by default when creating a new virtual machine?

A. Access Network

B. DMZ Network

C. VM Network

D. Virtual Machine Network

Answer: A

Q55\. You are creating a virtual machine in the Web Client using the New Virtual Machine wizard.

Which two steps are required? (Choose two.)

A. Select a valid name.

B. Select a cluster for the compute resource.

C. Select a network adapter.

D. Select the virtual machine compatibility.

Answer: A,D

Q56\. From which two locations in the inventory hierarchy can you deploy a virtual machine using a template? (Choose two.)

A. Directly from the template.

B. From a compute resource.

C. From an existing virtual machine.

D. From a Datastore.

Answer: A,B

Q57\. An administrator is deploying multiple Windows 2003 Virtual Machines from the same template.

What two steps should be taken to avoid network conflicts? (Choose two.)

A. Customize the guest operating system.

B. Install VMware Tools into the new virtual machines.

C. Copy the Microsoft Sysprep tools onto the vCenter Server system.

D. Ensure the e1000 vmnic is selected for each new virtual machine.

Answer: A,C

Q58\. An ESXi 6.x host consists of 24 logical cores. Hyperthreading is enabled on the host.

What is the maximum number of vCPUs that can be assigned to a virtual machine on this host?

A. 24

B. 48

C. 64

D. 128

Answer: A

Q59\. An administrator has an application that requires connection directly to PCI devices through a virtual machine.

What is a limitation of this configuration?

A. Devices must be reserved for PCI passthrough on at least one host on which the virtual machine will run.

B. Snapshots are not supported with DirectPath I/O passthrough devices.

C. A maximum of 18 PCI vSphere DirectPath devices can be added to a virtual machine.

D. Only one PCI controller can be presented to the virtual machine.

Answer: B

Q60\. What is the optimal configuration when building a virtual machine for a single-threaded Windows application?

A. Deploy single-threaded applications on uniprocessor virtual machines.

B. Deploy single-threaded applications on symmetric multi-processor virtual machines.

C. Tune single-threaded applications to take advantage of symmetric multi-processor resources.

D. Tune Single-threaded applications at the hypervisor level.

Answer: A

Q61\. A mission-critical virtual machine built on vSphere 4.1 needs to be moved to an ESXi 6.x host.

Which virtual hardware version is needed to move the virtual machine without upgrading?

A. 6

B. 7

C. 10

D. 11

Answer: B

Q62\. Which two configurable options apply to both virtual machine CPU and memory allocation? (Choose two.)

A. Reservation

B. Shares

C. Resource Pool

D. Reserve All

Answer: A,B

Q63\. A new vApp was built and tested in the corporate headquarters datacenter running vSphere 6.x.

What condition would explain why the virtual machine is failing to boot in an offsite datacenter running on vSphere 5.5?

A. The virtual machine was built with the default hardware version.

B. The VMFS 5 datastore is not compatible with virtual machines configured with vSphere 6.x.

C. A DRS 5.5 cluster cannot run virtual machines configured with vSphere 6.x.

D. The VMDK file is locked.

Answer: A

Q64\. When modifying a vApp, which two vSphere entities can be added? (Choose two.)

A. A resource pool

B. A network pool

C. A vApp

D. A folder

Answer: A,C

Q65\. You need to add an object to an existing vApp using the vSphere Web Client. How is this accomplished?

A. Create an Object Inside the vApp.

B. Add an Object to a vApp.

C. Add an Object to the Datastore the vApp is located in.

D. Move all Objects to a new Datastore folder.

Answer: A,B

Q66\. A virtual machine template is accidently removed from the vCenter Server Inventory.

Which method would be used to recover the template back into the environment?

A. Use the datastore browser to locate the template, then right click and add the .vmtx file to inventory.

B. Use the datastore browser to locate the template, then right click and add the .vmx file to inventory.

C. Using the Managed Object Browser and adding the template from the ManagedObjectReference:GuestFileManager object.

D. Using the Managed Object Browser and adding the template from the ManagedObjectReference:VirtualDiskManager object.

Answer: A

Q67\. A vApp named Sales has a Memory Limit of 32 GB and a CPU Limit of 12,000 MHz. There are three virtual machines within

the vApp:

- Sales-DB -- Has a memory reservation of 20 GB.

- Sales-DC -- Has a memory reservation of 8 GB.

- Sales-Web -- Has a memory reservation of 8 GB.

Which statement is correct?

A. All three virtual machines can power on, but will have memory contention.

B. All three virtual machines can power on without memory contention.

C. Only two of the three virtual machines can power on.

D. Only one of the virtual machines can power on.

Answer: C

Q68\. An administrator is cloning and configuring five new web server virtual machines.

What would be the benefit of configuring resource shares for the new VMs?

A. To prioritize access to a resource during contention.

B. To guarantee access to a resource during contention.

C. To prioritize access to a resource before contention occurs.

D. To guarantee access to a resource before contention occurs.

Answer: A

Q69\. An administrator is virtualizing a physical application server and adding it to an existing multi-tiered vApp. The application

license is currently tied to the physical NIC&amp;apos;s MAC address, so the administrator needs to ensure the license will function properly

in the virtual machine.

Which two actions can the administrator take to satisfy this task? (Choose two.)

A. Set the MAC address for the vNIC in the guest operating system.

B. Install the physical server&amp;apos;s NIC into the ESXi host.

C. Configure the MAC address for the vNIC using the vSphere Web Client.

D. Assign the physical server NIC&amp;apos;s MAC address in the vSphere Distributed Switch.

Answer: A,C

Q70\. A virtual machine has been renamed and an administrator is unable to find files with the new virtual machine name in the

datastore.

What is the reason for this?

A. The names of the files on the datastore do not change.

B. The names of the files on the datastore have been corrupted.

C. The virtual machine needs to be re-added to the inventory.

D. The Distributed Resource Scheduler moved the virtual machine to another host.

Answer: A

Q71\. What is required when changing a virtual machine name using the vSphere Web Client?

A. Verify connectivity to the ESXi host where the virtual machine is running and its inventory list is accessible.

B. Verify in which datastore the virtual machine resides and that you have access and its inventory list is accessible.

C. Verify that virtual machine files are stored in the same datastore and can be accessed in the datastore browser list.

D. Verify the virtual machine is not running in Fault Tolerant mode and that it is not in a Distributed Resource Scheduler cluster.

Answer: A

Q72\. Which two options would allow a database administrator, with no access to the vSphere infrastructure, to connect to a virtual

machine? (Choose two.)

A. Use the Virtual Machine Remote Console (VMRC).

B. Use Remote Desktop Protocol (RDP) to connect.

C. Ask the vSphere administrator to grant permission to access the console through vCenter Server.

D. Ask the vSphere administrator to grant permission to access with the Horizon View Direct Connect Client.

Answer: B,C

Q73\. An administrator has a virtual machine that requires four times the compute resources than other virtual machines on the

same ESXi 6.x host.

How should the administrator configure the virtual machine settings, in order to be prepared for any resource contention?

A. Set the shares of the priority virtual machine to High and the rest to Low.

B. Set the shares of the priority virtual machine to High.

C. Set the shares of the priority virtual machine to High and the rest to Normal.

D. Set the shares of the priority virtual machine to Normal and the rest to Low.

Answer: A

Q74\. A vApp is running out of compute resources when overall activity is high within the resource pool.

At other times, everything is fine.

What should be done to resolve this issue?

A. Increase the size of the resource pool Shares.

B. Set the vApp&amp;apos;s CPU and Memory Reservation Type to Expandable.

C. Set the vApp&amp;apos;s CPU and Memory Limit to Unlimited.

D. Create a new resource pool with the existing hardware configuration.

Answer: B

Q75\. You want to deploy a vApp and dynamically assign IP addresses without a DHCP server on the network.

Which action would you take to accomplish this task?

A. Enable IP pools.

B. Configure a local DHCP server in the vApp.

C. Enable NAT on the vApp router.

D. Configure the guest OS for workgroup and WINS.

Answer: A

Q76\. A vApp template recently added to a Content Library is not displayed.

Which two actions could correct this problem? (Choose two.)

A. Manually synchronize the library

B. Select the Download all library content immediately option

C. Select the Sync subscribed library option

D. Manually download the vApp template

Answer: A,B

Q77\. When you add an ESXi 6.x host to a new Cluster, which vSphere object owns the CPU and Memory resources of the hosts?

A. vCenter Server

B. Datacenter

C. Cluster

D. Host

Answer: C

Q78\. An administrator creates a DRS cluster of eight ESXi 6.x hosts. There are 10 virtual machines balanced across the hosts. An

attempt to place the first host into maintenance mode fails.

What are two reasons that the host failed to enter maintenance mode? (Choose two.)

A. The DRS cluster Automation Level is set to Partially Automated mode.

B. One of the virtual machines on the ESXi Host entering maintenance mode is configured with a DRS Host affinity rule Should run

on hosts in group.

C. One of the virtual machines on the ESXi Host entering maintenance mode is configured with a DRS Host affinity rule Must run

on hosts in group.

D. One of the virtual machines on the ESXi Host entering maintenance mode is configured with an individual Automation Level set

to Partially Automated.

Answer: A,D

Q79\. Which two statements are correct when turning off a Distributed Resource Scheduler (DRS) Cluster? (Choose two.)

A. The resource pool hierarchy of the DRS cluster is maintained.

B. The resource pool hierarchy of the DRS cluster is removed.

C. The affinity settings of the DRS cluster are removed and not maintained when DRS is re- enabled.

D. The affinity settings of the DRS cluster are maintained when DRS is re-enabled.

Answer: B,C

Q80\. An administrator enables High Availability (HA) on a Virtual SAN cluster.

Which network is used for HA Network Heatbeat configuration?

A. The Management network.

B. The vMotion network.

C. The Virtual SAN network.

D. The Provisioning Traffic network.

Answer: C

Q81\. What are three goals of resource management within a cluster? (Choose three.)

A. To prevent virtual machines from monopolizing resources and to guarantee predictable service rates.

B. To exploit undercommitted resources and overcommit with graceful degradation.

C. To provide solutions to potential problems that you might encounter when using vCenter Server.

D. To control the relative importance of virtual machines and provide flexible dynamic partitioning.

E. To provide additional network administration capabilities.

Answer: A,B,D

Q82\. Which three features can be enabled for a new host cluster? (Choose three.)

A. Storage Distributed Resource Scheduling

B. High Availability

C. Fault Tolerance

D. Distributed Resource Scheduling

E. Virtual SAN

Answer: B,D,E

Q83\. An organization has an ESXi 6.x host that contains two resource pools. The host is being relocated to a DRS cluster.

What two actions can be taken to integrate the host into the cluster, and what would happen to the existing ESXi resource pool

hierarchy as a result? (Choose two.)

A. Place all of the host&amp;apos;s virtual machines into the DRS cluster root resource pool. The resource pools present on the host will be

deleted.

B. Create a resource pool for the ESXi host&amp;apos;s virtual machines and resource pools. The resource pools present on the host will be

deleted.

C. Place all of the host&amp;apos;s virtual machines into the DRS cluster root resource pool. The resource pools present on the host will be

preserved.

D. Create a resource pool for the ESXi host&amp;apos;s virtual machines and resource pools. The resource pools present on the host will be

preserved.

Answer: A,D

Q84\. Which two events happen when Distributed Resource Scheduler (DRS) is disabled? (Choose two.)

A. The cluster&amp;apos;s resource pool heirarchy and affinity rules are re-established when DRS is turned back on.

B. The cluster&amp;apos;s resource pool hierarchy and affinity rules are not re-established when DRS is turned back on.

C. The cluster&amp;apos;s resource pools are removed from the cluster.

D. The cluster&amp;apos;s resource pools are removed from the cluster and assigned to the hosts.

Answer: B,C

Q85\. A High Availability (HA) cluster is configured to respond to a given number of host failures. The cluster contains virtual

machines configured with these settings:

- VM1 has a 1GHz CPU reservation and no Memory reservation

- VM2 has a 2GHz CPU reservation and no Memory reservation

- VM3 has no CPU reservation and no Memory reservation

Given this information, what is the correct slot size for the cluster?

A. The CPU Reservation should be set to 32MHz and the memory reservation should be set to 32MB plus memory overhead.

B. The CPU reservation should be set to 1 GHz and the memory reservation should be set to 0MB

plus memory overhead.

C. The CPU reservation should be set to 2 GHz, and the memory reservation should be set to 0MB plus the virtual machine

memory overhead.

D. The CPU reservation should be set to 2 GHz, and the memory reservation should be set to 32MB, plus the virtual machine

memory overhead.

Answer: C

Q86\. Which two High Availability (HA) Cluster admission control policies can help avoid resource fragmentation? (Choose two.)

A. Define failover capacity by static number of hosts

B. Define failover capacity by reserving a percentage of the cluster resources

C. Use dedicated failover hosts

D. Use Virtual Machine Monitoring

Answer: A,C

Q87\. What is a requirement when enabling a Virtual SAN cluster in an existing High Availability (HA) and Distributed Resource

Scheduler (DRS) Cluster?

A. Disable DRS and HA before enabling Virtual SAN

B. Enable DRS before enabling Virtual SAN

C. Disable HA before enabling Virtual SAN

D. Enable Storage DRS before enabling Virtual SAN

Answer: C

Q88\. What must be enabled to ensure that VM Component Protection (VMCP) works in a High Availability cluster?

A. VMware Tools Virtual Machine Communication Interface (VMCI)

B. Fault Tolerance

C. Atomic Test and Set (ATS)

D. All Paths Down (APD) Timeout

Answer: D

Q89\. An organization has a number of virtual machines that would benefit from Fault Tolerance. These include:

- A single vCPU Apache Server

- A dual vCPU vCenter Server

- A quad vCPU SQL Server

- An eight vCPU Hadoop Server

Which two virtual machines can be configured to use VMware Fault Tolerance? (Choose two.)

A. Apache Server

B. vCenter Server

C. SQL Server

D. Hadoop Server

Answer: A,C

Q90\. Which three statements are true regarding Fault Tolerance? (Choose three.)

A. Applications need to be continuously available to users.

B. Applications without native clustering capabilities can be protected.

C. Custom clustering solutions are complicated to configure and maintain.

D. Applications that have 16 vCPUs are supported.

E. Prevents application crashes by analyzing the workload and correcting problems.

Answer: A,B,C

Q91\. Which three features are not supported when using Fault Tolerance in vSphere 6.x? (Choose three.)

A. Virtual Volumes (VVOLS)

B. Storage vMotion

C. Virtual Machine Component Protection

D. vMotion

E. vSphere Distributed Switches

Answer: A,B,C

Q92\. What is true about resource pools created on a Distributed Resource Scheduler (DRS) cluster?

A. A root resource pool is created with the specified values.

B. A root resource pool is automatically created using the aggregate total of the ESXi host resources in the cluster.

C. A root resource pool is automatically created using the aggregate total of all resources in the datacenter.

D. A root resource pool is not needed when creating resource pools on a DRS cluster.

Answer: B

Q93\. Refer to the Exhibit.

-- Exhibit --

-- Exhibit --

An administrator has created the resource pool configuration shown in the Exhibit.

Based on the exhibit, which virtual machine(s) can be successfully powered on?

A. VM-M1 only

B. VM-K1 only

C. VM-K1 and VM-K2 only

D. VM-K1, VM-K2, and VM-M1

Answer: D

Q94\. An administrator is moving a virtual machine into a resource pool. The VM and resource pool are configured as shown:

VM configuration:

- 2GHz CPU reservation

- 1GB Memory limit

Resource Pool configuration:

- 6GHz CPU reservation

- 1GB Memory reservation

- No limit to memory

What happens to the virtual machine&amp;apos;s resource settings when it is moved into the pool?

A. The VM inherits the resource settings of the resource pool if expandable reservations is enabled.

B. The VM&amp;apos;s reservations and limits are ignored and removed.

C. The VM keeps the 2GHz CPU reservation but receives the 1GB memory reservation.

D. The VM keeps the 2GHz CPU reservation and the 1GB Memory limit.

Answer: D

Q95\. Which two statements are true regarding VMware vSphere Flash Read Cache (vFRC)? (Choose two.)

A. Cache fills and cache evictions happen in the granularity of a cache block size.

B. vFRC caches data from both read and write I/Os, but write I/Os are always serviced by the underlying storage.

C. vFRC caches data from both read and write I/Os, but write I/Os are always serviced by the underlying cache data.

D. Cache fills and cache evictions happen in the granularity of the disk block size.

Answer: A,B

Q96\. An administrator is tasked with performing a vMotion migration of a virtual machine. The virtual machine is configured as

follows:

- vSphere Flash Read Cache (vFRC) enabled

- Ispart of a Distributed Resource Cluster (DRS) Cluster

Which two statements are true? (Choose two.)

A. Each ESXi host in the cluster supports multiple virtual flash resources.

B. Each ESXi host in the cluster supports one virtual flash resource.

C. DRS treats powered-on virtual machines with Flash Read Cache as having a preferred affinity to their current host and moves

them only for mandatory reasons.

D. DRS treats powered-on virtual machines with Flash Read Cache as having a required affinity to their current host and does not

move them.

Answer: B,C

Q97\. Which two actions are required when enabling vFlash Read Cache for a virtual machine&amp;apos;s virtual disk? (Choose two.)

A. A value in the Virtual Flash Read Cache text box must be entered.

B. A Flash Resource Pool for Cache size reservation must be entered.

C. The Device backing and the block size must be configured.

D. The Enable virtual flash host swap cache check box must be selected.

Answer: A,D

Q98\. vMotion can be performed between which three physical boundaries? (Choose three.)

A. Between two vCenter Server Systems

B. Between two vSphere Distributed Virtual Switches

C. Between two vCenter Server Datacenter objects

D. Between two VMware NSX Layer 4 segments

E. Between two NFS datastores

Answer: A,B,C

Q99\. Which three operations occur during a cold migration of a virtual machine? (Choose three.)

A. The virtual machine disks are moved if the datastore is being changed.

B. The virtual machine is registered with the destination server.

C. The source virtual machine is removed from the old hosts.

D. The virtual machine hardware is upgraded.

E. The virtual machine files are quiesced prior to the migration.

Answer: A,B,C

Q100\. An administrator needs to verify that vMotion operations can be performed in a vSphere data center.

What round trip time (RTT) latency is the maximum value that will allow vMotion operations to succeed?

A. 50ms RTT

B. 100ms RTT

C. 150ms RTT

D. 200ms RTT

Answer: B

Q101\. Which three are requirements when using vMotion to move a virtual machine across vCenter Server systems? (Choose

three.)

A. Both vCenter Servers must be using Enhanced Linked Mode.

B. Both vCenter Servers must be in the same Single Sign-On Domain.

C. Time must be synchronized.

D. Duplicate VM MAC addresses must be configured.

E. Both vCenter Servers must have High Availability enabled on source and destination clusters.

Answer: A,B,C

Q102\. An administrator is migrating a virtual machine from a Test cluster to a Production cluster. The two environments do not

have any shared storage.

What is the easiest way to accomplish this task?

A. Perform a Storage vMotion.

B. Perform a regular vMotion.

C. Perform a Virtual to Virtual migration.

D. Perform a backup and restore using VMware Data Protection.

Answer: B

Q103\. What is a benefit of using Enhanced vMotion Compatibility for an environment?

A. EVC masks CPU features to allow compatibility between hosts that are dissimilar.

B. EVC allows for cross platform vMotion to occur.

C. EVC enables Long Distance vMotion.

D. EVC enables Storage vMotion functionality.

Answer: A

Q104\. Refer to the Exhibit.

-- Exhibit --

An administrator attempts to enable Enhanced vMotion Compatibility (EVC) on a cluster. The operation results in a compatibility

error, as shown in the exhibit.

What is the likely cause of this error?

A. The CPUs in the ESXi host are not AMD CPUs.

B. The CPUs in the ESXi host do not support hardware virtualization capabilities.

C. The XD/NX CPU features have not been enabled in the BIOS of the server.

D. There is no shared storage between the hosts in the cluster.

Answer: A

Q105\. An administrator is attempting to migrate a large Hadoop virtual machine using vMotion. The administrator notices a delay

when the machine is quiesced. The Hadoop virtual machine is processing many transactions a second to an in-memory database.

Which two actions would help reduce the amount of time needed to perform a vMotion on this virtual machine? (Choose two.)

A. Use multiple NICs for the vMotion vmkernel port.

B. Use a 10Gbps Network card for the vMotion vmkernel port.

C. Add an additional management network to help transmit the data quicker.

D. Disable Fault Tolerance before performing the vMotion.

Answer: A,B

Q106\. An administrator attempts to migrate a suspended virtual machine to a newly deployed vSphere 6.x cluster. The

compatibility check fails.

What condition could cause this behavior?

A. The new vSphere 6.x cluster is running Intel CPUs instead of AMD CPUs.

B. A suspended virtual machine cannot be migrated.

C. The hardware virtualization feature of the CPU is not enabled on the new hosts.

D. A vSphere Distributed Switch is required to migrate a suspended virtual machine.

Answer: A

Q107\. An administrator must determine an appropriate backup solution, given these conditions:

- 50 of the virtual machines are in a resource pool named Finance.

- 50 of the virtual machines are in a resource pool named QA.

Which solution allows an administrator the ability to backup 100 virtual machines?

A. Use Snapshot Manager on the vCenter Server to backup the virtual machines.

B. Use the VMware Consolidated Backup (vcb) tool on the ESXi Host to backup the virtual machines.

C. Use the VMware Data Recovery (VDR) Appliance on the vCenter Server to backup the virtual machines.

D. Use the VMware Data Protection (VDP) Appliance on one of the ESXi Hosts to backup the virtual machines.

Answer: D

Q108\. A vSphere administrator needs to backup a virtual machine that has a Microsoft SQL Server Database installed.

Which solution allows for an application quiesce to occur during backup?

A. VMware vCenter Converter

B. VMware vCenter Site Recovery Manager

C. VMware vSphere Replication

D. VMware vSphere Data Protection Advanced

Answer: D

Q109\. Which two statements are true about deploying and using vSphere Replication? (Choose two.)

A. ESXi hosts managed by a single vCenter Server instance require a connection between the two vSphere Replication

appliances.

B. Sites managed by different vCenter Server instances require a connection between the two vSphere Replication appliances.

C. Sites managed by different vCenter Server instances require the use of Site Recovery Manager and a connection between the

two vSphere Replication appliances.

D. ESXi hosts managed by a single vCenter Server instance require a single vSphere Replication appliance.

Answer: B,D

Q110\. An administrator is attempting to restore a number of files in a directory within the Operating System of a virtual machine.

How can the administrator restore the files from a previous backup?

A. Use the File Level Restore option from the selected backup of the virtual machine in the vSphere Web Client.

B. Connect to the File Level Restore tool from a web browser in the virtual machine.

C. Connect to the File Level Restore tool from the VMware Data Protection appliance.

D. Use the File Level Restore option from the selected backup of the virtual machine in the vSphere Client.

Answer: B

Q111\. What are three valid disk configurations for the vSphere Data Protection 6.x Appliance? (Choose three.)

A. 500GB

B. 1TB

C. 1.5TB

D. 2TB

E. 4TB

Answer: A,B,C

Q112\. What is a benefit of using VMware Data Protection (VDP)?

A. Provides support for guest-level backups and restores of Microsoft SQL Servers, Exchange Servers, and Share Point Servers.

B. Provides support for advanced storage services including replication, encryption, deduplication, and compression.

C. Provides direct access to VDP configuration integrated into the vSphere Client.

D. Reduces disk space consumed by virtual machine data using deduplication.

Answer: D

Q113\. When configuring vSphere Replication for a virtual machine, what is the lowest Recovery Point Objective (RPO) that can be

selected?

A. 1 min

B. 5 min

C. 10 min

D. 15min

Answer: B

Q114\. An administrator configures vSphere Replication for a virtual machine and enables multiple point in time (PIT) instances

under the recovery settings in the Configure Replication wizard.

Which two statements are correct for vSphere Replication with multiple point in time instances enabled? (Choose two.)

A. vSphere Replication retains a number of snapshot instances of the virtual machine on the target site based on the retention

policy that you specify.

B. vSphere Replication uses the virtual machine&amp;apos;s snapshot instances to define the target site

Point in Time instance based on the retention policy that you specify.

C. vSphere Replication does not support virtual machines with snapshots.

D. vSphere Replication supports virtual machines with snapshots.

Answer: A,C

Q115\. Which three actions can be taken as a result of executing the vSphere Update Manager 6.x scan and remediation wizards?

(Choose three.)

A. Install and upgrade software in virtual machines.

B. Upgrade the firmware on ESXi host devices.

C. Upgrade and Patch ESXi hosts.

D. Install and update third-party software on hosts.

E. Upgrade virtual machine hardware.

Answer: C,D,E

Q116\. Which three steps must be taken to use vSphere Update Manager 6.x to upgrade an ESXi 5.5 host to vSphere 6.x?

(Choose three.)

A. Download an ESXi Image.

B. Configure the vSphere Update Manager Download Service.

C. Create a baseline and attach it to the ESXi Host.

D. Scan the vCenter Content Library for the ESXi Image.

E. Remediate the ESXi Host.

Answer: A,C,E

Q117\. vSphere Update Manager allows which two virtual machine attributes to be upgraded? (Choose two.)

A. Virtual machine firewall policies for NSX.

B. Software Packages in the virtual machine.

C. Virtual machine Hardware Version.

D. VMware Tools Upgrade.

Answer: C,D

Q118\. An administrator enables vSphere High Availability (HA) on an existing cluster with a large number of hosts and virtual

machines. The administrator notices that the setup of vSphere HA on some of the hosts is failing.

What step, if taken, might resolve this issue?

A. Increase the value of the config.vpxd.das.electionWaitTimeSec setting.

B. Set the value of vpxd.das.aamMemoryLimit to 256\.

C. Set the value of the das.useDefaultIsolationAddress setting to False.

D. Increase the value of the das.iostatsinterval setting.

Answer: A

Q119\. An attempt to enable vSphere Fault Tolerance for a powered-on virtual machine fails.

Which two scenarios would result in this failure? (Choose two.)

A. The virtual machine has three vCPUs configured.

B. The host on which the virtual machine is running has insufficient memory resources.

C. The virtual machine has insufficient resources to accommodate full reservation plus the overhead memory.

D. VMware High Availability is enabled on the cluster of which this host is a member.

Answer: B,C

Q120\. An administrator is unable to remove an ESXi 6.x host from a vSphere Distributed Switch.

What are two likely reasons for this issue? (Choose two.)

A. Vmkernel interfaces on the switch are still in use.

B. VM Network port group adapters are connected to different switch.

C. Physical NICs are migrated to different switch.

D. VM Network adapters are connected to this switch.

Answer: A,D

Q121\. An administrator is attempting to enable Storage I/O Control on a datastore, but it is failing.

What is the likely reason for this failure?

A. The host is connected to a datastore is running on ESX 4.0\.

B. The host is connected to a Fibre Channel storage array.

C. The datastore has multiple extents.

D. The datastore is managed by a single vCenter Server.

Answer: A

Q122\. Which scenario shows a reason for VMware Tools failing to install?

A. Virtual machine has a CD-ROM configured.

B. Guest OS Antivirus is blocking the VMware Tools installation.

C. Guest OS has 64-bit ldd (list dynamic dependencies) utility installed.

D. Virtual machine is powered on.

Answer: B

Q123\. What are two possible causes of Storage Distributed Resource Scheduler (SDRS) being disabled on one or more virtual

machine disks in a datastore cluster? (Choose two.)

A. The virtual machine has vSphere Fault Tolerance disabled.

B. The virtual machine is a template.

C. The virtual machine swap file is on a shared datastore.

D. The disk is a CD-ROM/ISO file.

Answer: B,D

Q124\. What may be a cause for failure to unmount an NFS datastore?

A. It has active snapshot files.

B. It is being used for High Availability (HA) heartbeat.

C. It is part of a Cluster.

D. It is managed by Distributed Resource Scheduler (DRS).

Answer: A

Q125\. An administrator is troubleshooting basic network connectivity issues.

Which two scenarios are potential issues that this administrator might face? (Choose two.)

A. The vSwitch is not attached to the correct physical network.

B. The portgroup is not configured to use correct VLAN.

C. Traffic shaping is configured incorrectly.

D. Jumbo frames is configured incorrectly.

Answer: A,B

Q126\. Why are some virtual machines orphaned after rebooting a High Availability (HA) enabled host?

A. The Orphaned virtual machines have HA restart disabled.

B. The Orphaned virtual machines moved recently and the change did not persist.

C. The host is attached to failed storage.

D. The host just came out of maintenance mode.

Answer: A

Q127\. An administrator is attempting to power on a virtual machine, but is unable to do so.

Which two reasons are probable causes of the failure? (Choose two.)

A. Storage access to the virtual machine swap file has been lost.

B. One of the virtual machine VMDK files is locked.

C. Virtual machine is running CentOS 7.0 64-bit.

D. Virtual machine has Hyper-Threading enabled.

Answer: A,B

Q128\. Refer to the Exhibit.

-- Exhibit --

A 4 GB Memory virtual machine is experiencing extended memory issues, as shown in the Exhibit.

What potential issues could be attributed to this memory pressure?

A. A limit is imposed on the virtual memory of this virtual machine.

B. The Balloon driver has been uninstalled.

C. A limit has been imposed on the Virtual CPU of the virtual machine.

D. Storage IO control has been enabled for the virtual machine causing the swapped memory.

Answer: A,B

Q129\. An administrator has unsuccessfully attempted several times to install an Operating System inside a virtual machine. The

administrator finds that the installation fails at random intervals.

Which two actions can be taken to resolve this issue? (Choose two.)

A. Verify the md5sum and if invalid, download the installation files again.

B. Attempt the installation an additional time.

C. Attempt to use a different installation media or installation method.

D. Create a new virtual machine and attempt the installation with the existing media.

Answer: A,C

Q130\. A Fault Tolerance (FT) virtual machine with four vCPUs is experiencing high latency when performing ICMP and Application

tests.

What are three potential causes that may be attributing to this latency? (Choose three.)

A. The FT network has insufficient bandwidth and is running on a 1GB Link.

B. The FT network is on a particularly high latency link.

C. The FT network has been configured with Network I/O Control.

D. The FT virtual machine is running an e1000 network adapter.

E. The FT virtual machine is running on poor performing network-based storage.

Answer: A,B,C

Q131\. VMware tools is failing to install on a Microsoft Windows virtual machine.

What are two possible situations that would prevent the installation? (Choose two.)

A. The VMware tools installation media is corrupt.

B. The incorrect Operating System was selected in the virtual machine options.

C. The software prerequisites have not been installed.

D. The prerequisite services have not been started.

Answer: A,B

Q132\. An administrator is attempting to power on a virtual machine, but the task is hanging at 95%.

What three scenarios best explain why this problem is happening? (Choose three.)

A. A virtual machine question is currently being posed to the administrator.

B. Another task for the virtual machine or other component is already in progress.

C. The VMware High Availability cluster has insufficient resources to guarantee failover.

D. The host has lost access to the storage device containing the virtual machine files.

E. The host is under resource contention and unable to power on the virtual machine.

Answer: A,B,C

Q133\. An application running in a virtual machine is experiencing performance issues. When utilizing performance monitoring

utilities, it is noted that the CPU Utilization of the application is at 100%.

Which two scenarios are probable causes of the CPU contention for the application? (Choose two.)

A. There is a network I/O constraint.

B. There is a storage I/O constraint.

C. There is insufficient disk space assigned to the virtual machine.

D. The application is not virtualization aware.

Answer: A,B

Q134\. A user is trying to retrieve objects from a SharePoint server and finds the request is taking an excessive amount of time. An

administrator tries to isolate the issue and notes the following:

- Application performance is poor when compared to virtual machines on other hosts.

- Performance improves when the virtual machine is moved to another host.

- The virtual machine encounters higher than expected CPU %Ready times.

What conclusion can be reached regarding the performance issues for this virtual machine?

A. Host Power Management is directly impacting virtual machine performance.

B. The virtual machine has a large number of snapshots.

C. The Path Selection Policy for the storage device is set differently on the affected host.

D. Network I/O control is configured for the portgroup.

Answer: A

Q135\. When attempting to access a virtual machine, an administrator is unable to login using the vSphere credentials.

What two options are probable causes of the authentication failure? (Choose two.)

A. The vSphere credentials have not been granted permissions.

B. The vSphere credentials are granted read-only permissions.

C. The vSphere credentials are granted no-access permissions.

D. The vSphere credentials are not a member of the local administrator group.

Answer: A,B

Q136\. A physical Windows 2008 R2 Server is converted to a virtual machine using VMware vCenter Converter. Upon completion

of the conversion and subsequent power on operation, the virtual machine fails to boot and the message below is observed in the

Console of the virtual machine:

STOP 0x0000007B INACCESSIBLE_BOOT_DEVICE

Which two potential issues may be causing this boot failure? (Choose two.)

A. An incorrect SCSI controller was selected during conversion.

B. Incompatible software drivers were migrated into the virtual machine from the source machine.

C. The vmdk file backing the virtual machine was thick provisioned.

D. A snapshot was taken immediately after the conversion completed.

Answer: A,B

Q137\. When attempting to power on a Virtual Machine you observe the following error:

Cannot open the disk &amp;apos;/vmfs/volumes/volume/vm/vm-000002.vmdk&amp;apos; or one of the snapshot disks it depends on.

Which three actions will be the best solutions to address this problem? (Choose three.)

A. Verify that the virtual machine&amp;apos;s disk files are present.

B. Investigate the host and virtual machine log files.

C. Verify the vmdk descriptor files and if required, recreate them.

D. Delete the disk file preventing the power on operation.

E. Migrate or register the virtual machine to a different host.

Answer: A,B,C

Q138\. Refer to the Exhibit.

-- Exhibit --

An administrator has been given requirements to configure vMotion for a new virtual machine. The configuration should:

- Provide Network Redundancy

- Use VLAN 550

- Be secured against anyone trying to spoof communication

The vSwitch1 configuration is shown in the Exhibit.

Which three changes should be made to meet the stated requirements? (Choose three.)

A. The VLAN ID must be set appropriately.

B. The default values for MAC Address Changes and Forged Transmits must be altered.

C. The teaming and failover adapters must be set appropriately.

D. The Traffic Shaping configuration must be altered.

E. The Load Balancing Policy must be set appropriately.

Answer: A,B,C

Q139\. Refer to the Exhibit.

A storage administrator is not seeing full utilization of all bandwidth from an ESXi host. The vSphere administrator observes the

adapter details, as shown in the Exhibit.

What is the probable cause of this issue?

A. Another path needs to be used to allow full utilization of the bandwidth.

B. The array is not setup to use the correct multipathing policy.

C. There are no virtual machines on the host.

D. No traffic is being sent across it because a path failed.

Answer: D

Q140\. An administrator is monitoring a High Availability (HA) and Distributed Resource Scheduler (DRS) enabled cluster and has

noticed that virtual machines in the cluster are being migrated without user intervention.

Why is this happening?

A. The DRS Automation level is set to Fully Automated.

B. The Automation level is set to Automatic.

C. The DPM Threshold is set to Aggressive.

D. The Power Management feature is configured.

Answer: A

Q141\. An administrator is installing a new network card in an ESXi 6.x host that is part of a vSphere cluster. When the host is

placed into maintenance mode, the vSphere Web Client displays the progress bar at 2% for over 30 minutes.

Which two are likely reasons for this occurrence? (Choose two.)

A. Maintenance mode is unable to migrate all virtual machines from the host.

B. There is a large number of virtual machines that must be migrated from the host.

C. VMware High Availability is in the process of reconfiguring the cluster.

D. Each virtual machine on the ESXi host must be reconfigured to recognize the new adapter.

Answer: A,B

Q142\. An administrator is using the Host Failures to Tolerate Admission Control Policy for a vSphere High Availability (HA) cluster.

When configuring this setting on the cluster, the administrator sees this error message:

Insufficient resources to satisfy HA failover level on cluster

What are two likely causes for the error? (Choose two.)

A. The hosts in the cluster are disconnected.

B. A host in the cluster is displaying an HA error.

C. Distributed Resource Scheduler has not been configured on the cluster.

D. Virtual Machine Component Protection has not been turned on.

Answer: A,B

Q143\. An administrator has been tasked with enabling High Availability (HA) on a cluster in a vSphere 6.x environment with default

settings. The cluster configures properly and there are no errors. The next day when powering on a virtual machine, an error is

presented:

Not Enough Failover Resources

Which three scenarios are likely causes of this error message? (Choose three.)

A. The default VM Monitoring Sensitivity is set too high.

B. There are not enough datastore heartbeat datastores configured by default.

C. The default slot size in the cluster is set too high.

D. There are virtual machines with large CPU reservations.

E. A host is in maintenance mode for a replacement of a failed Hard Drive.

Answer: C,D,E

Q144\. An administrator is attempting to remove an ESXi 6.x host from a vSphere Distributed Switch (vDS). When the administrator

attempts to remove the host, the following error is observed:

The resource &amp;apos;16&amp;apos; is still in use.

What three steps are needed to successfully remove the host from the switch? (Choose three.)

A. Select Manage Ports on the vDS for the host.

B. Locate all ports currently in use on the vDS for the host.

C. Migrate or delete any vmkernel or virtual machine adapters associated with the switch.

D. Remove all network cards from the switch before trying to remove the host.

E. Create a standard switch for everything to be automatically be migrated to.

Answer: A,B,C

Q145\. An administrator logs into the vSphere Web Client, but is unable to see any hosts and clusters.

Which two options could fix the problem? (Choose two.)

A. Verify that the client web browser and vCenter Server are in the same broadcast domain.

B. Verify that the vCenter Server system is registered with the same Platform Services Controller as the vSphere Web Client.

C. Log in to the vCenter Server as a user within the Active Directory domain.

D. Log in to the vSphere Web Client as a user with permissions on the vCenter Server system.

Answer: B,D

Q146\. Users of an application are reporting performance issues. The following performance values are observed in the vSphere

Web Client:

- Host CPU utilization is 90%

- Virtual Machine memory utilization is consistently greater than 90%

- CPU Ready values are higher than 20%

What could be the cause of the application performance issue?

A. The host is lacking the CPU resources required to meet the demand.

B. The host is lacking the memory resources required to meet the demand.

C. The virtual machine is lacking the CPU resources required to meet the demand.

D. The virtual machine is lacking the memory resources required to meet the demand.

Answer: A

Q147\. An administrator reports that the System Event log data is only available for 24 hours when reviewing the Hardware Status

tab.

Which condition could be responsible for the loss of data?

A. A Reset event log was executed.

B. The statistical collection level was set to a value of 1\.

C. The boot disk of the host is corrupt.

D. Syslog has been configured at the vCenter Server level.

Answer: A

Q148\. An administrator receives a report that no real time statistics are available for a virtual machine in the vCenter Server

inventory.

Which two statements indicate likely causes of the problem? (Choose two.)

A. The virtual machine is powered off.

B. The host containing the virtual machine is disconnected from vCenter Server.

C. There is insufficient real time data to display the information.

D. The vCenter Server service is not running.

Answer: A,B

Q149\. A virtual machine is experiencing performance issues. The following performance metrics are observed:

- CPU usage value for the virtual machine is above 90%

- CPU ready value for the virtual machine is above 20%

Which two activities will likely resolve the performance issues? (Choose two.)

A. Set a CPU reservation for the virtual machine.

B. Increase the CPU limit on the virtual machine.

C. Decrease CPU shares equally for all virtual machines on the host.

D. Increase CPU shares equally for all virtual machines on the host.

Answer: A,B

Q150\. - An administrator wants to add a web server to an existing multi-tier application consisting of three virtual machines:

- A web server

- A database server

- An application server

The web server should be added to the application when the primary web server reaches:

- 70% vCPU utilization

- 55% active memory

Which option will achieve this result?

A. Create a virtual machine alarm with an action to run a script that starts a new instance of the web server.

B. Create a host cpu and memory alarm with an action to run a script that starts a new instance of the webserver.

C. Configure HA application monitoring for the web server and set it to trigger deployment of a new instance of the web server.

D. Configure Fault Tolerance on the virtual machine and leave the secondary machine disabled until needed.

Answer: A

Q151\. An administrator has configured an alarm to be notified when a virtual machine meets two conditions:

- high virtual CPU

- high active memory consumption

The alarm is malfunctioning and triggering when either condition is met instead of both.

What can be done to correct the issue?

A. Edit the alarm and select Trigger if ALL of the following conditions are satisfied.

B. Edit the alarm and select Trigger if ANY of the following conditions are satisfied.

C. Create two separate alarms, one for CPU and one for memory.

D. Delete the existing alarm and create a new event based alarm.

Answer: A

Q152\. An administrator has configured an alarm to be notified when a virtual machine meets either of these conditions:

- High virtual CPU

- High active memory consumption.

The alarm is only triggering when both of the conditions are met.

What can be done to correct the alarm behavior?

A. Edit the alarm and select Trigger if ANY of the following conditions are satisfied.

B. Edit the alarm and select Trigger if ALL of the following conditions are satisfied.

C. Create two separate alarms, one for CPU and one for memory and link them together with ESXCLI.

D. Delete the existing alarm and create a new event based alarm.

Answer: A

Q153\. An organization has configured Distributed Power Management (DPM) on a vSphere 6 cluster. The organization wants to

be alerted when an ESXi host has been powered down by DPM.

Which two options represent the type and name of the alarm that would accomplish this? (Choose two.)

A. DrsEnteringStandbyModeEvent

B. DrsEnteredStandbyModeEvent

C. Event-based

D. Condition-based

Answer: B,C

Q154\. Which three actions can be executed when an alarm is triggered? (Choose three.)

A. Send an email.

B. Send an SNMP trap.

C. Run a script or command.

D. Run an Orchestrator workflow.

E. Send a trigger to syslog.

Answer: A,B,C

Q155\.

Which two SMTP Notification Event Details are specific to alarms triggered by events? (Choose two.)

A. User Name

B. Summary

C. Old Status

D. Target

Answer: A,B

Q156\. An administrator deploys vRealize Operations into a vSphere 6.x environment. After the deployment, the administrator

notices that badges are not appearing.

What is a likely cause of this behavior?

A. Badges do not appear until you register vRealize Operations with vCenter Server.

B. Badges do not appear until you register a vCenter Server in vRealize Operations.

C. The vRealize Operations appliance needs to be redeployed.

D. The vCenter Server appliance needs to be redeployed.

Answer: A

Q157\. An administrator is unable to create the first group in a new vRealize Operations environment.

What is the likely cause of the problem?

A. There are no group types defined.

B. The group is not defined in SSO.

C. There are more than 32 group types defined.

D. The description for the group is not provided.

Answer: A

Q158\. An administrator is only able to see the Health Badge when using the vRealize Operations user interface.

What is the likely cause of this behavior?

A. The vRealize Operations Foundation License is in use.

B. The vmware-sps service failed to start.

C. The vRealize Operations Standard License is in use.

D. The vmware-rbd-watchdog service failed to start.

Answer: A

Q159\. Which two are true about the Risk badge in vRealize Operations? (Choose two.)

A. The Risk badge indicates potential future problems that may degrade the performance of the system.

B. Risks may require attention in the near future.

C. The Risk badge indicates problems that are degrading performance of the system.

D. Risks require attention now to correct system performance problems.

Answer: A,B

Q160\. Which three are architecture components of vRealize Operations? (Choose three.)

A. Identity Server

B. Administrative Server

C. Analytics Server

D. Database Server

E. Connection Broker

Answer: B,C,D

Q161\. A vCenter Operations Manager 5.7 environment is upgraded to vRealize Operations. After the upgrade, the analytics

services fail to start.

Which three steps must be taken to resolve the problem? (Choose three.)

A. Take the vRealize Operations cluster offline.

B. Delete the activity persistence files.

C. Bring the cluster back online.

D. Remove any unresponsive nodes.

E. Stop the CaSA service.

Answer: A,B,C

Q162\. Which two badges are major badges in vRealize Operations? (Choose two.)

A. Risk

B. Efficency

C. Workload

D. Faults

Answer: A,B

Q163\. A user wants to monitor a business-critical virtual machine to ensure that it doesn&amp;apos;t run out of

resources.

What metric could be monitored in vRealize Operations to address this concern?

A. Time Remaining badge

B. Compliance badge

C. Reclaimable Waste badge

D. Density badge

Answer: A

Q164\. After selecting an object in vRealize Operations, how can a user compare the badge values of related child objects?

A. Use the Scoreboard tab

B. Use the Relationship tab

C. Use the Members tab

D. Use the Overview tab

Answer: A

Q165\. Refer to the Exhibit.

An administrator logs into the vSphere Web Client and sees the warning shown in the Exhibit.

During a change control window, the warning was addressed.

What should be done to verify that the host is no longer showing the warning?

A. Run a Remediate host operation.

B. Recheck the compliance of the host.

C. Restart the host to get rid of the warning.

D. Install VMware tools to clear the warning.

Answer: B

Q166\. Refer to the Exhibit.

A storage administrator has reported that full utilization of all bandwidth from an ESXi 6.x host is not being seen. In troubleshooting

the issue, the Adapter details are shown in the Exhibit.

Based on the exhibit, what is cause of the issue?

A. The array is not setup to use the correct multipathing policy.

B. There are no virtual machines on the ESXi host.

C. Not all links are used because a path is disabled.

D. Another path needs to be configured.

Answer: C

Q167\. Refer to the Exhibit.

An administrator is configuring an ESXi 6.x host to use multiple NICs to resolve a management network redundancy error. After

configuring a second NIC, the server is not able to communicate when the primary connection is taken down. The administrator

analyzes the Exhibit shown here.

Based on the exhibit, what is the likely cause of the issue?

A. vmnic4 is not attached to a vSwitch.

B. vmnic2 is not connected to a physical switch.

C. E1000 is the incorrect NIC Driver for this card.

D. There is a MAC address conflict on the network.

Answer: B

Q168\. Refer to the Exhibit.

An administrator has configured a host profile so that ESXi 6.x hosts will point to the corporate NTP server for time synchronization.

The NTP server is located at 10.0.30.213, but time has not been synchronized properly across the ESXi hosts.

The administrator reviews Host Profile settings as shown in the Exhibit.

Which two steps are required to resolve the issue? (Choose two.)

A. Correct the NTP server IP address.

B. Check the host for host profile compliance.

C. Remediate the host based on the updated host profile.

D. Change the NTP server to the FQDN as IP Addresses are not supported.

Answer: A,C

Q169\. Refer to the Exhibit.

-- Exhibit --

-- Exhibit --

An administrator has configured network connectivity for a new virtual machine, as shown in the Exhibit.

What will occur with the network traffic of this virtual machine when communicating externally from vSwitch1?

A. The virtual machine will communicate on both uplinks

B. The virtual machine will only communicate on vmnic1

C. The virtual machine will only communicate on vmnic2

D. The virtual machine will fail to communicate externally

Answer: D

Q170\. Refer to the Exhibit.

An administrator is migrating a powered-on virtual machine, as shown in the exhibit.

Which option should be selected to perform a Storage vMotion of the VM?

A. Change storage only

B. Change VM compute resource only

C. Change both compute resource and storage, changing the compute resource first.

D. Change both compute resource and storage, changing the storage resource first.

Answer: A

Q171\. Refer to the Exhibit.

An administrator is installing Windows into a virtual machine. The DVD has been mounted on the Host and configured for the

virtual machine as shown in the Exhibit.

Based on the exhibit, when the virtual machine is booted, why would it attempt to search for a PXE server?

A. The CD/DVD device is not connected.

B. The ISO is in the incorrect storage location.

C. The OS minimum requirements have not been met.

D. The CD/DVD device is not set to Client Device.

Answer: A

Q172\. Refer to the Exhibit.

-- Exhibit --

An administrator is analyzing a virtual machine as shown in the Exhibit.

What is the current long term risk for this virtual machine?

A. The virtual machine may run out of memory before April 27\.

B. The virtual machine may continue to function after April 27\.

C. The virtual machine has adequate memory configured for operation for the next 120 days.

D. The virtual machine has adequate memory reservation configured for operation for the next 120 days.

Answer: A

Q173\. Refer to the Exhibit.

An administrator is adding an NFS datastore as shown in the Exhibit.

What is the purpose of the Servers to be added list?

A. It contains the IP addresses of the NFS Storage Server to provide multipathing capability.

B. It contains the IP addresses of the ESXi hosts that mount the datastore.

C. It contains the IP addresses used for Dynamic Discovery of targets.

D. It contains the IP addresses used for Static Discovery of targets.

Answer: A