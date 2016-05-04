# Setting up Vivado on Linux

Start by downloading the lastest Linux version of Vivado from [Xilinx's website](http://www.xilinx.com/support/download.html). The current version at the time of writing this is Vivado 2016.1. Currently, Xilinx provides web installers, so the initial download is fairly small.

Once downloaded the file must be made executable and then installed.

```bash
cd ~/Downloads
chmod +x Xilinx_Vivado_SDK_2016.1_0409_1_Lin64.bin
sudo ./Xilinx_Vivado_SDK_2016.1_0409_1_Lin64.bin
```

Once the installation is started, make sure include the Software development kit and DocNav. Since, the Zybo is a Zynq-7000 you only need to select Zynq-7000 in the devices section.

![Installation tree](images/installer_1.png)

In Linux it is a good idea to install user applications inside the opt folder. Note, if you didn't run the installer with sudo, it will fail to write to the opt folder.

![Install directory](images/installer_2.png)

Click yes, if it asks you to create the folder. Continue with the installation until finished.

After installation is complete, the Vivado License Manager will pop up. To create a license go to Xilinx's [license managment page](http://www.xilinx.com/getlicense). Xilinx also offers free WebPack licenses. Once you fill out the licensing information, Xilinx will send you an email with the license. Download the license from the email and follow the instructions in the email to complete to load the license.

Next, you need to install the cable drivers for the Zybo.

```bash
cd /opt/Xilinx/Vivado/2016.1/data/xicom/cable_drivers/lin64/install_script/install_drivers
sudo ./install_drivers
```
You also need to source Vivado's settings.

```bash
source /opt/Xilinx/Vivado/2016.1/settings64.sh
```

Note, you should add the line ```source /opt/Xilinx/Vivado/2016.1/settings64.sh``` to your terminal's rc file (normally ~/.bashrc). So that the command is run everytime you use your terminal.

You might also need to change the ~/.Xilinx folders' group and owner for Vivado to start correctly. 

```bash
sudo chgrp -R <your-user-name> ~/.Xilinx
sudo chown -R <your-user-name> ~/.Xilinx
```

To start Vivado type ```vivado &``` in a terminal. Make sure to start Vivado in a directory you are able to write to, as Vivado creates log files in the directory you start it from.

If you want Vivado to start from the applications menu, you need to create a desktop file. The location for adding desktop entries is generally ```/usr/share/applications```

```bash
cd /usr/share/applications
sudo gedit vivado.desktop
```

Add the following text to the file.

```
[Desktop Entry]
Version=1.0
Type=Application
Name=Vivado
Icon=/opt/Xilinx/Vivado/2016.1/doc/images/vivado_logo.ico
Exec=/opt/Xilinx/Vivado/2016.1/bin/vivado
Categories=Development;IDE;
Terminal=false
```

This should allow you to start Vivado from the applications menu, without having to go through a terminal.

Next, you need to add Zybo board files to Vivado's boards directory. You can download the board files from [Digilent's github repo](https://github.com/Digilent/vivado-boards/). Click the download zip button to download a zip of the repo. Unzip the file and move it to ```/opt/Xilinx/Vivado/2016.1/data/boards/board_files```.

```bash
cd ~/Downloads
unzip vivado-boards-master.zip
sudo cp vivado-boards-master/new/board_files/zybo /opt/Xilinx/Vivado/2016.1/data/boards/board_files
```

You can delete the vivado-boards-master folder and zip now.
