Download Link: https://assignmentchef.com/product/solved-cloud-computing-homework-2
<br>
This assignment will be done using KVM, a popular type-2 hypervisor. KVM is built on the Linux kernel to reuse its existing functions to support virtualization. As a part of this assignment, you will be experimenting with KVM and gaining familiarity with the development environment and add new features to it. KVM can run on many different architectures, but the specific platform we will be targeting is the x86_64 CPU family.

We will use <a href="https://www.vmware.com/products/workstation-pro.html">VMware Workstation/Fusion</a> in this assignment so your custom hypervisor can be isolated from the rest of your system. VMware

Workstation/Fusion supports nested virtualization, allowing you to install, run and develop hypervisors in a virtual machine. You will first install a Linux/KVM host on VMware, and then create virtual machines on the host. Note that this is different from deployment in production platforms which the hypervisor runs directly on bare metal.

<strong>Q: Create a Virtual Machine on KVM.</strong>

The first thing you need to do is install Linux/KVM in a VMware VM, then install another VM running Linux on top of the VMware VM. Running a VM inside of a VM is referred to as nested virtualization. The VM running inside of a VM is sometimes referred to as a nested VM. We are asking you to configure your own VMs instead of giving you a preconfigured system so you can learn how to do this on your own. The following steps have been tested on VMware Workstation 12 PRO, though they should also work with other recent versions of VMware Workstation or Fusion.

<ol>

 <li>Create a New Virtual Machine.</li>

 <li>Select “Custom (advanced) and click Next”.</li>

 <li>Click next until you reach the page “Guest Operating System Installation”</li>

 <li>Download the iso image for Ubuntu-XX.XX.X from <a href="https://www.ubuntu.com/download/desktop">here</a>.</li>

 <li>Continue to setup your VM spec.</li>

 <li>We then need to expose the hardware <em>virtualization</em> feature to the KVM running in the VM. On VMware Workstation, go to <em>Processors</em> of your VM configuration, then select both “<em>Virtualize Intel VT-x/EPT and AMD-V/RVI</em>” and “<em>Virtualize CPU performance counters</em>“.</li>

</ol>

NOTE: The exact location to the virtualization hardware to the VM might be different depending on the VMware version.

NOTE: You may need to enable hardware virtualization (Intel VT) features for your computer in the BIOS. You can get more information from <a href="https://www.intel.com/content/www/us/en/support/articles/000007139/server-products.html">here</a>.

<ol start="7">

 <li>Click “Finish” and Install Ubuntu-XX.XX.X on your VM.</li>

</ol>

Once your VM is set up, you can use the terminal directly or ssh into the VM to run commands.

Recommended VM Spec: At least 4 VCPU, 2GB RAM, NAT network, 50GB virtual disk.

In “Processors”, set “Preferred mode” as “Automatic” to leverage hardware features to accelerate the VM.

Once you finish installing Ubuntu, it’s time to configure the environment for KVM.

NOTE: us.archive.ubuntu.com may not be fast enough, you need to figure our local image site in China

<strong>BONUS</strong>: in your report, if you can figure out ‘console=ttyS0,115200n8 serial’ and write it down, you will get BONUS points.

You can then log in to the VM after virt-install finishes. Next, modify <em>/etc/default/grub</em> in your VM as below using your favorite editor:

Finally, shutdown and restart the VM.

The following libvirst commands are useful for managing your VM. You can check the status of your VM using: