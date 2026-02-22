# Scaling Up: Managing Multiple RTMs with Home Assistant

If you have multiple Resin Temperature Masters (RTMs) running on a print farm, or if you simply want to keep long-term logs of your temperature data, **Home Assistant (HA)** is the perfect tool. Home Assistant is a free, smart-home hub that runs locally on your own computer.

Because the RTM is built to integrate instantly and seamlessly with Home Assistant. This guide will show you how to set up Home Assistant using Docker Compose on Windows (via WSL2) or Linux, and how to connect your RTMs.

## Installing Docker (Windows & Linux)
## 1. Install Docker

Before setting up Home Assistant, you need Docker installed on your computer.

### Option A: Windows (Using WSL2 & Docker Desktop)
Windows Subsystem for Linux (WSL2) allows you to run a genuine Linux environment directly inside Windows.
1. Click the Windows Start button, type `PowerShell`, right-click it, and select **Run as administrator**.
2. Type `wsl --install Ubuntu-24.04` and press Enter. *(For deeper troubleshooting, refer to the [official Microsoft WSL installation guide](https://learn.microsoft.com/en-us/windows/wsl/install)).*
3. Wait for the installation to finish, and **restart your computer**. 
4. Download and install **Docker Desktop for Windows** from the [official Docker website](https://www.docker.com/products/docker-desktop/).
5. During installation, ensure the option **"Use WSL 2 instead of Hyper-V"** is checked. 
6. **Ensure automatic startup:** To guarantee Home Assistant turns back on after you restart your PC, Docker Desktop needs to launch automatically. Open Docker Desktop, click the **Settings** (gear) icon in the top right, go to the **General** tab, and check the box for **"Start Docker Desktop when you log in"**. 

### Option B: Linux
If you have a dedicated Linux machine or server, open your terminal and run the official Docker installation script:
```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```


## Set Up Home Assistant with Docker Compose

Docker Compose uses a simple text file to configure and run your smart home hub. For the best performance and stability on Windows, we will set this up directly inside the WSL2 Linux file system rather than your standard Windows drive.

1. Open your Linux terminal:
    * Windows users: Open your Start Menu, search for WSL (or Ubuntu, if you installed that specific distribution), and open the terminal.
    * Linux users: Simply open your standard terminal.
1. Create a new folder for Home Assistant in your Linux home directory and move into it by running this command:
    ```bash
    mkdir ~/homeassistant && cd ~/homeassistant
    ```
1. Create the configuration file using the built-in nano text editor:
    ```bash
    nano docker-compose.yml
    ```
1. Save and exit: Press Ctrl + O to save, press Enter to confirm the file name, and then press Ctrl + X to exit the editor.
1. Paste the configuration: Copy the text below and paste it into the terminal (in Windows WSL, you can usually paste by simply right-clicking inside the terminal window), the code can be found [here](docker-compose.yaml)
1. Start Home Assistant by running the following command fomr the directory where the `docker-compose.yaml` exists:
    ```bash
    docker compose up -d
    ```
    > Because our configuration includes restart: unless-stopped, this container will now automatically start up anytime Docker loads.
1. Access the dashboard: Home Assistant is now running in the background! Open your normal web browser and go to http://localhost:8123 (or the IP address of your Linux machine) to create your administrator account.

## Adding Your RTMs to Home Assistant
Now that Home Assistant is running, let's link your controllers!

1. Log in to your Home Assistant dashboard.
1. In the left sidebar, click Settings, then click Devices & Services.
1. If you are using Linux: Home Assistant should automatically pop up an alert saying it has "Discovered" a new ESPHome device. Click Configure and follow the prompts.
1. If auto-discovery doesn't trigger (common on Windows):
    1. Click the Add Integration button in the bottom right.
    1. Search for ESPHome and click it.
    1. Enter the IP Address of your RTM (you can find this on the RTM's OLED screen) and click Submit.

Repeat this process for each RTM you own.
You can now click on your RTM in Home Assistant to see historic temperature graphs, change the target temperature, and even set up automations!