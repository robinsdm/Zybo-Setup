# Setting up Vivado on Linux

Start by downloading the lastest Linux version of Vivado from [Xilinx's website](http://www.xilinx.com/support/download.html). The current version at the time of writing this is Vivado 2016.1. Currently, Xilinx provides web installers, so the initial download is fairly small.

Once downloaded the file must be made executable and then installed.

```bash
cd ~/Downloads
chmod +x Xilinx_Vivado_SDK_2016.1_0409_1_Lin64.bin
sudo ./Xilinx_Vivado_SDK_2016.1_0409_1_Lin64.bin
```

Once the installation is started, make sure include the Software development kit and DocNav. Since, the Zybo is a Zynq-7000 you only need to select Zynq-7000 in the devices section.

![Installation tree][images/installer_1.png]

In Linux it is a good idea to install user applications inside the opt folder. Note, if you didn't run the installer with sudo, it will fail to write to the opt folder.

![Install directory][images/installer_2.png]

Click yes, if it asks you to create the folder. Continue with the installation until finished.
