#STM32 Command Line Builder Project
This project provides an automated method for building and flashing STM32 microcontrollers from the Linux command line. It leverages a Makefile to streamline the process. Follow the instructions below to set up and use the project.

🛠️ Prerequisites
🖥️ System Requirements:
Linux Operating System with sudo privileges.
STM32 microcontroller board connected to your system before flashing.
Internet connection for downloading tools and dependencies.
🔧 Tools You Need:
Make sure you have the following tools installed on your Linux system:
wget or curl
tar (for file extraction)
git (for cloning repositories)
make (to compile the project)
unzip (to extract files)
stlink-tools (for communication with STM32)
Install the missing tools with:
sudo apt update
sudo apt install wget tar git make unzip stlink-tools -y


1️⃣ Install ARM GCC Toolchain
To build STM32 firmware, you will need the ARM GCC toolchain.
📥 Download ARM GCC Toolchain
Visit the ARM GCC Toolchain Download Page.
Download the .tar.bz2 file appropriate for your system.
🛠️ Install the Toolchain
1.1 Download the Toolchain
Use wget or curl to download the file:
wget <download_link>


Replace <download_link> with the actual URL.
1.2 Extract the Toolchain
Extract the downloaded file to your working directory:

tar -xjf <downloaded_file> -C <working_directory>


1.3 Move Toolchain to Standard Location (Optional)

sudo mkdir -p /opt/arm-gcc
sudo mv <working_directory>/<extracted_directory> /opt/arm-gcc


1.4 Set Up Environment Variables
To add the ARM GCC toolchain to your PATH:

echo 'export PATH=/opt/arm-gcc/<toolchain_directory>/bin:$PATH' >> ~/.bashrc
source ~/.bashrc


1.5 Verify Installation
Run this command to confirm the toolchain is installed:

arm-none-eabi-gcc --version


2️⃣ Install stlink-tools
stlink-tools is required for flashing the STM32 microcontroller.
🛠️ Install stlink-tools

sudo apt-get update
sudo apt-get install stlink-tools


📝 Verify Installation
To confirm stlink-tools are installed correctly, run:

st-info --version


3️⃣ Clone the Project Repository
To get the project, clone it using git:

git clone https://github.com/abhishekweslee/STM32_Command_line_bulder.git


4️⃣ Extract Project Files
After cloning the repository, unzip the project archive:

cd STM32_Command_line_bulder/
unzip STM32_command_line.zip


5️⃣ Customize Project Directories
Since this is a generic template for STM32 microcontrollers, you'll need to replace the contents of the Core and Drivers directories with your files for the specific STM32 microcontroller you're using.
🔄 Replace Core and Drivers Directories
Core Directory: Replace the contents with your STM32-specific core files, such as:
Startup files
Linker scripts
System initialization code
An example structure for Core:



Core/
├── Inc/         # Header files
├── Src/         # Source files
└── Startup/     # Startup files

Drivers Directory: Replace with your specific STM32 microcontroller drivers:
CMSIS drivers
HAL drivers
An example structure for Drivers:



Drivers/
├── CMSIS/       # CMSIS drivers
└── STM32F4xx_HAL_Driver/   # STM32 HAL drivers


6️⃣ Build the Project
🚀 Navigate to the Project Directory
After replacing the files in the Core and Drivers directories, go to the project folder:

cd CLI_STM32_Project/


⚙️ Build the Project
To compile the firmware, run the following command:
make all


This may take a few minutes depending on your system and the project size.
7️⃣ Clean the Build (Optional)
If you need to clean the project (for example, after code changes), run:

make clean


This will remove all generated object and binary files.
8️⃣ Rebuild the Project (If Needed)
After cleaning or making changes, you can rebuild the project:

make all


9️⃣ Flash the STM32 Microcontroller
Before flashing, make sure the STM32 microcontroller is connected to your system.
🚨 Flash Firmware to STM32
Once the build is complete, you can flash the firmware to the STM32 using:

make flash


This will use stlink-tools to flash the firmware to the microcontroller.
📌 Conclusion
With this guide, you have:
Set up the ARM GCC toolchain.
Installed stlink-tools.
Customized the Core and Drivers directories for your STM32 microcontroller.
Built the project and flashed the STM32 firmware.
You're now ready to develop and debug your STM32 applications!
🎉 Additional Resources
For more information on STM32 development:
STM32CubeMX
STM32 HAL Documentation


