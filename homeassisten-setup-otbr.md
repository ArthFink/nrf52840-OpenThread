## Home Assistant Thread Setup Guide

Once the firmware is flashed to your nRF52840 dongle, follow these steps to set up OpenThread in Home Assistant.

### 1. Install OpenThread Border Router Add-on

Go to **Settings > Add-ons > Add-on Store**, and install the **OpenThread Border Router** add-on.

#### Configuration

- **Device**: /dev/serial/by-id/usb-Nordic_Semiconductor_nRF528xx_OpenThread_Device_XXXXXXXXXXXX-if00  
  *(Note: Device path may differ depending on your system)*
- **Baudrate**: 460800
- **Hardware flow control**: on
- **Automatically flash firmware**: off
- **Log level**: default:warn
- **OTBR firewall**: on
- **NAT64**: off

After starting the add-on, check the logs. You should see:

```
[20:57:37] INFO: Successfully sent discovery information to Home Assistant.
s6-rc: info: service otbr-agent-rest-discovery successfully started
s6-rc: info: service legacy-services: starting
s6-rc: info: service legacy-services successfully started 
```
### 2. Add Thread Integration

- Go to **Settings > Devices & Services**
- Click **"+ Add Integration"** and select **Thread**
- Click the gear icon ⚙️ next to the `ha-thread-xxxx` network
- Select **Preferred network**

### 3. Sync Thread Credentials to Mobile

In the **Home Assistant Companion App** (as described in [this guide](https://www.home-assistant.io/integrations/thread/#case-1-making-home-assistant-your-first-thread-network)):

- Go to **Settings > Companion App > Troubleshooting**
- Tap **Sync Thread credentials**

- If you skip this step, your phone won’t be aware of the Thread network and Border Router, which means it won’t be able to commission or control Thread devices—even if the network itself is working properly.

### 4. Add Matter Server and Pair Devices

- Add the **Matter Server** integration
- Pair your Matter-compatible device using the Companion App

### Resources

- [Thread Integration Documentation](https://www.home-assistant.io/integrations/thread/)
- [Making Home Assistant Your First Thread Network](https://www.home-assistant.io/integrations/thread/#case-1-making-home-assistant-your-first-thread-network)
