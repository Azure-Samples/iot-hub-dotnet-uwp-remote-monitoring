---
services: iot-hub, iot-suite
platforms: uwp, csharp, windows10
author: olivierbloch
---

# iot-hub-dotnet-uwp-remote-monitoring
This sample shows how to run and connect a Universal Windows Platform application to an Azure IoT Suite Remote Monitoring Preconfigured Solution.
This sample is usefull to try or demonstrate Azure IoT Suite. Here are some links to learn more on [Azure IoT Suite](https://azure.microsoft.com/en-us/documentation/suites/iot-suite/) and [Azure IoT Suite preconfigured solutions](https://azure.microsoft.com/en-us/documentation/articles/iot-suite-what-are-preconfigured-solutions/).

## Running this sample
### Hardware prerequisites
In order to run this sample you will need the following hardware:
  - A PC running Windows 10
  - [optional] A Windows 10 mobile device if you want to deploy the application on such a device.

### Software prerequisites
[Visual Studio 2015](https://www.visualstudio.com/) with [Windows 10 SDK](https://dev.windows.com/en-US/downloads/windows-10-sdk)

### Settings prerequisites
You will need to setup your Windows 10 OS to developer mode.
  - On Windows 10 PC:
    - Click on the Windows Icon, 
    - Type `For Developers Settings` and press enter.
    - In the **Developers Settings** section, select the option **Developer Mode**
  - On Windows 10 Mobile (if you plan to deploy to a phone running Windows 10 mobile)
    - Touch the search button
    - Type `Settings` and touch the **Settings** icon to enter the settings panel
    - Scroll down to **Update & Security**, then Developers and select the **Developer mode** option

## Deploy an Azure IoT Suite Remote Monitoring preconfigured solution
In order to deploy an Azure IoT Suite precongigured solution, you need an Azure subscription. If you don't have one, you can easily create a [free trial subscription](https://azure.microsoft.com/en-us/free/).
This [article](https://azure.microsoft.com/en-us/documentation/articles/iot-suite-getstarted-preconfigured-solutions/) describes in details how to get started with Azure IoT Suite Remote Monitoring preconfigured solutions, but if you want the short version, see below.
Once you have an Azure subscription, browse to [http://www.azureiotsuite.com](http://www.azureiotsuite.com)
Once logged in using your Azure subscription credentials:
  - Click on **Create a new solution**.
  - Select **Remote Monitoring**
  - Enter a solution name
  - Select a region for your solution to be hosted in
  - Select your subscription (if you have several subscription for the account your logged in with)
  - Click on **Create solution** at the bottom

It will take several minutes to deploy all the services of the solution, in the meantime, you can get device application ready.

## Run the device application on Windows 10 PC and mobile
In order to run the device application on your PC, here are the few steps:

1. Clone or download the github repository (see links on top)

1. Open the solution AzureIoTSuiteUWPDevice\AzureIoTSuiteUWPDevice.sln in Visual Studio

1. Build and deploy:
   - For Windows 10 PC:
      - Ensure the target platform for the project is set to **X86**
      - Click on the **Build** menu then on **Build Solution**
      - Select **Local Machine** as your target device
      - Press F5
   - For Windows 10 Mobile:
      - Connect your Windows 10 Mobile phone to your PC using a USB cable and ensure the phone is unlocked
      - Ensure the target platform for the project is set to **ARM**
      - Click on the **Build** menu then on **Build Solution**
      - Select **Device** as your target device
      - Press F5

## Create a device ID for your UWP device application in Azure IoT Suite Remote Monitoring preconfigured solution
At this point the Remote Monitoring solution should be deployed (if not, go get a coffee).

```
Important: we are not using the simulated devices that are automatically deployed as part of the remote monitoring solution. It is recommended to deactivate all the simulated devices from the Devices tab in the dashboard to prevent unecessary traffic and cost to the Azure subscription.
```

In order to connect your UWP application to your Azure IoT Suite instance (which by now should be deployed), you will need to create a unique ID for it in the Suite dashboard.
Navigating the Remote Monitoring dahboard and creating a device ID is extensively described in the [Getting Started with Azure IoT Suite preconfigured solutions article](https://azure.microsoft.com/en-us/documentation/articles/iot-suite-getstarted-preconfigured-solutions/).
Once you have created a new device ID, copy the Device ID, Host Name and Device Key from the IoT Suite into the UWP application.

## Use the application
The UWP device application is dead simple.
  - Connecting to IoT Suite:
    - Enter the credentials generated in previous steps in the corresponding fields of the app.
    - Press the "Press to Connect To IoT Suite" button.
    - At this point you should see the device metadata appear in the IoT Suite dashboard under the **devices** tab.
  - Sending telemetry data
    - Press the **Press to send data to IoT Suite** button.
    - Data will start showing up in the IoT Suite dashboard. You can play with the sliders to change the values
  - Receiving messages from IoT Suite on the device
    - In the IoT Suite dashboard, go to the **Devices** tab
    - Select your device
    - In the right menu, press on **Commands**
    - In the Commands combo, select the command you want to send to the device, type your text and press **send**
    - The device should display the message.

