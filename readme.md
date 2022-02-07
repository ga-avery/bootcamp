# Windows User Steps
________________________________________________________________________________

As a pre-requisite of Docker Desktop for Windows one must have the Windows 
features "Virtual Machine Platform" and "Windows Subsystem for Linux" installed.
These are both freely available on all Windows 10+ machines, even on Home
Edition!

Below I have divided the steps to install these two features on your machine
 now.

First, we search for "Windows features" in our windows menu. 

![windows features](/img/windows-0.png)

Second, we scroll to the bottom of the Windows Features window and find the two
features that we're wishing to install. Once they are checked we can select `OK`
!!IMPORTANT!! this may require a system restart to take effect.

![windows features 2](/img/windows-1.png)

________________________________________________________________________________

Once this is done let's install 
[Docker Desktop for Windows](https://www.docker.com/products/docker-desktop).
Once installed (may require a restart) make sure that your settings has "Use the
 WSL 2 based engine" is selected.

![docker settings](/img/windows-2.png)
