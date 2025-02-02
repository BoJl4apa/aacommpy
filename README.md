AACommPy Package Documentation

AACommPy is a Python package that provides functionalities for working with the AAComm nuget package. AAComm is a nuget package used for communication with FPGA devices. AACommPy provides a Python wrapper for the AAComm nuget package, allowing you to use the nuget package's functionalities in your Python scripts.

1.Installation
To install AACommPy, follow these steps:
Download the Python package for AACommPy by executing the following command:

pip install aacommpy

Once the package is installed, you can access its functionalities from your Python scripts.

2. Usage
To use AACommPy, you can import the necessary modules and call the available functions. Here's an example of how to use the package:
---------python------------
from aacommpy.settings import AACOMM_SERVER_EXE_PATH
from aacommpy.AAComm import CommAPI, Services, Shared

api = CommAPI()

status = CommAPI.StartAACommServer(AACOMM_SERVER_EXE_PATH)

if status != "":
    print(status)
else:
    # Access the static variable IsAACommServerRunning
    is_running = CommAPI.IsAACommServerRunning
    print(f"AACommServer is running: {is_running}")

cData = Services.ConnectionData()
cData.ControllerType = Shared.ProductTypes.AGM800_ID
cData.CommChannelType = Shared.ChannelType.Ethernet
cData.ET_IP_1 = 172
cData.ET_IP_2 = 1
cData.ET_IP_3 = 1
cData.ET_IP_4 = 101
cData.ET_Port = 5000

res = api.Connect(cData)
print(res)-------------------------

3.Available Commands
AACommPy provides several commands that can be executed through the command line using the installed package. These commands include:

3.1.install: Downloads and installs the AAComm package. You can specify a version using the --version option.
    the version number is the same with the AAComm nuget package version you want to use with you python script.
3.2.version: Retrieves the installed version of AAComm.
3.3.update: Updates the installed AAComm package to the latest version.
3.4.dotnetfw: Sets the .NET framework version of AAComm library. You can choose from the available options: net40, net48, net6.0, net8.0. The default version is net48.

Example Usage
Here's an example of how to use the AACommPy package:

Install the package:

pip install aacommpy
#Run the command to download and install the AAComm package:

aacommpy install
#Check the installed version of AAComm:


aacommpy version
#Update the AAComm package to the latest version:

aacommpy update
#Set the .NET framework version to be used by AAComm to net4.8:

aacommpy dotnetfw --netfw net48
#Please note that the usage examples provided assume that you have the necessary permissions to install packages and run the commands.