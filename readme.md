# Windows User Steps
________________________________________________________________________________

First and foremost, virtualization *must* be enabled on your computer. You can
check if this is currently enabled on your machine by opening up your
Task Manager and navigating to the Performance tab. It will be listed under your
CPU as shown in the following picture.

![hypervisor enabled](/img/windows-3.png)

***IF HYPERVISOR IS DISABLED*** you will need to see if your CPU is compatible 
with Virtualization. (If you have an AMD Ryzen processor you are compatible)
If you have an Intel processor it gets complicated, however you can check on the
[product specification site](https://ark.intel.com).

If your CPU is incompatible with `Intel VT-x` and `AMD SVM` stop here, this
solution will not work on your machine.

If your CPU *is* compatible with these virtualization technologies but is 
currently disabled, you will need to enabled virtualization in your BIOS/EFI.
This step varies from motherboard to motherboard, but is typically listed as an
advanced feature under your CPU settings in your BIOS/EFI.

To get into your BIOS/EFI a user will need to hold a specific key during system 
boot. This varies from system to system, for mine it is holding the `delete` key
on system startup. Once you are in your BIOS it may look something like the 
following image(s). Your BIOS/EFI is not guaranteed to look like mine, it will 
very likely look different. You may need to consult your motherboard's manual or
a helpful search on YouTube might have a nice video showing you how to enable 
virtualization for your specific motherboard.

![bios step 0](/img/bios-0.jpg)

![bios step 1](/img/bios-1.jpg)

![bios step 2](/img/bios-2.jpg)

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


# Running our container
Once we have installed Docker Desktop, let's install two extensions in 
Visual Studio Code. To install an extension, click on the extensions icon on the 
left side of your Visual Studio Code window. In the search bar type in 
`ms-azuretools.vscode-docker` and click the install button on it. After that 
search for the extension `ms-vscode-remote.remote-containers` and install it.

These two extensions will allow us to run our docker container!

1. Download this repository to your machine as a `.zip` file by clicking on the 
green `Code` button above the file list.
2. Unzip the folder anywhere on your machine, preferably somewhere that you will
recognize to come back to. (e.g. on your Desktop or in your Documents folder)
3. Open the folder that you have unzipped in Visual Studio Code.
4. A pop up should appear in the bottom right corner asking you to re-open the 
current folder in a container. Select `Reopen in Container`
5. Wait for a little while and let VSCode run for a while

Once this process has finished, click on the `New Terminal` button in VSCode as 
shown in the following pictures. If yours looks like the final picture, 
congratulations! You did it, you now have a fully fledged development
environment for the rest of the cohort!

![final step](/img/final-0.png)

![final step](/img/final-1.png)
