# WSL2 and ROS2 Humble Installation Guide for Windows 11
***

This guide will walk you through installing Windows Subsystem for Linux 2 (WSL2) on Windows 11 and then installing ROS2 Humble Hawksbill within the Ubuntu environment.

## Prerequisites

Before starting, ensure you have:
- **Windows 11** (any edition) with all updates installed
- **Administrator privileges** on your Windows machine
- **Virtualization enabled** in BIOS/UEFI (usually enabled by default on modern systems)
- **At least 4GB of RAM** (8GB+ recommended)
- **Active internet connection**

### Check Virtualization Status
1. Open **Task Manager** (`Ctrl + Shift + Esc`)
2. Navigate to the **Performance** tab
3. Look for "Virtualization: Enabled" status

If virtualization is disabled, you'll need to enable it in your BIOS/UEFI settings.

---

## Part 1: Installing WSL2 on Windows 11

### Step 1: Install WSL2 (Simple Method)

The easiest way to install WSL2 on Windows 11 is using a single command:

1. **Open PowerShell as Administrator**
   - Right-click the **Start** button
   - Select **"Windows PowerShell (Admin)"** or **"Terminal (Admin)"**

2. **Run the installation command**
   ```powershell
   wsl --install
   ```

3. **Restart your computer** when prompted

This command will:
- Enable the WSL feature
- Enable the Virtual Machine Platform
- Download and install the latest Linux kernel
- Install Ubuntu as the default Linux distribution

### Step 2: Initial Setup

After restarting:

1. **Launch Ubuntu** from the Start menu
2. **Wait for installation to complete** (first launch takes a few minutes)
3. **Create a user account**:
   - Enter a username (lowercase, no spaces)
   - Enter a password (you won't see characters as you type)
   - Confirm the password

### Step 3: Verify WSL2 Installation

Open PowerShell and run:
```powershell
wsl --list --verbose
```

You should see Ubuntu listed with version 2.

---

## Alternative Installation Method (Manual)

If the simple method doesn't work, use the manual approach:

### Step 1: Enable WSL Features

Open PowerShell as Administrator and run:

```powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
```

### Step 2: Restart Your Computer

### Step 3: Set WSL2 as Default

After restart, open PowerShell as Administrator:
```powershell
wsl --set-default-version 2
```

### Step 4: Install Ubuntu from Microsoft Store

1. Open **Microsoft Store**
2. Search for **"Ubuntu"**
3. Select **Ubuntu 22.04 LTS** (recommended for ROS2 Humble)
4. Click **"Get"** or **"Install"**
5. Launch Ubuntu from Start menu after installation

---

## Part 2: Installing ROS2 Humble in WSL2 Ubuntu

Now that you have Ubuntu running in WSL2, you'll install ROS2 Humble Hawksbill.

### Step 1: Set Up Locale

First, ensure your system supports UTF-8:

```bash
locale  # check for UTF-8
```

If UTF-8 is not present, set it up:

```bash
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
locale  # verify settings
```

### Step 2: Setup Sources

Enable the Ubuntu Universe repository:

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

Add the ROS2 GPG key:

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg
```

Add the ROS2 repository:

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

### Step 3: Install ROS2 Packages

Update your package list:

```bash
sudo apt update
```

**Important**: Upgrade your system first (especially critical for Ubuntu 22.04):

```bash
sudo apt upgrade
```

Now install ROS2. Choose one of the following options:

#### Option A: Desktop Install (Recommended)
Includes ROS2, RViz, demos, and tutorials:

```bash
sudo apt install ros-humble-desktop
```

#### Option B: ROS-Base Install (Minimal)
Communication libraries, message packages, and command line tools only:

```bash
sudo apt install ros-humble-ros-base
```

#### Option C: Development Tools (Optional)
If you plan to build ROS packages from source:

```bash
sudo apt install ros-dev-tools
```

### Step 4: Environment Setup

#### Source the Setup Script

You need to source the ROS2 setup script to use ROS2 commands:

```bash
source /opt/ros/humble/setup.bash
```

#### Automatic Sourcing (Recommended)

To avoid sourcing the setup script every time you open a terminal:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

### Step 5: Verify Installation

Test your ROS2 installation with the talker-listener demo:

#### Terminal 1 (C++ Talker):
```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_cpp talker
```

#### Terminal 2 (Python Listener):
Open a new terminal and run:
```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_py listener
```

You should see:
- **Talker** saying: `Publishing: 'Hello World: 1'`, `Publishing: 'Hello World: 2'`, etc.
- **Listener** saying: `I heard: [Hello World: 1]`, `I heard: [Hello World: 2]`, etc.

If both work correctly, your installation is successful! 🎉

---

## WSL2 Management Commands

Here are useful commands for managing your WSL2 installation:

### Basic WSL Commands

```powershell
# List installed distributions
wsl --list --verbose

# Shutdown all WSL instances
wsl --shutdown

# Start a specific distribution
wsl -d Ubuntu-22.04

# Set default distribution
wsl --set-default Ubuntu-22.04

# Check WSL version
wsl --version

# Update WSL
wsl --update
```

### File System Access

- **Access Windows files from Ubuntu**: `/mnt/c/` (for C: drive)
- **Access Ubuntu files from Windows**: `\\wsl$\Ubuntu-22.04\home\[username]\`

---

## Optional Enhancements

### Install Windows Terminal

For a better terminal experience:

1. Open **Microsoft Store**
2. Search for **"Windows Terminal"**
3. Install and set as default terminal

### Configure WSL2 Resource Limits

Create a `.wslconfig` file in your Windows user directory (`C:\Users\[YourUsername]\.wslconfig`):

```ini
[wsl2]
memory=4GB
processors=2
```

This limits WSL2 to use 4GB of RAM and 2 CPU cores.

---

## Troubleshooting

### Common Issues and Solutions

#### WSL Installation Fails
- Ensure virtualization is enabled in BIOS
- Run Windows Update to get the latest version
- Try the manual installation method

#### Ubuntu Won't Start
- Run `wsl --shutdown` then try again
- Check if virtualization is enabled
- Restart Windows and try again

#### ROS2 Commands Not Found
- Ensure you've sourced the setup script: `source /opt/ros/humble/setup.bash`
- Check if ROS2 was installed correctly: `ls /opt/ros/humble`

#### Network Issues in WSL2
- Restart WSL: `wsl --shutdown` (from PowerShell)
- Check Windows firewall settings
- Try updating WSL: `wsl --update`

#### Permission Issues
- Ensure you're using `sudo` for system-wide installations
- Check file permissions: `ls -la`

### Reset WSL2 (Last Resort)

If you encounter persistent issues:

```powershell
# Unregister the distribution (this will delete all data!)
wsl --unregister Ubuntu-22.04

# Reinstall from Microsoft Store
```

---

## Next Steps

Now that you have ROS2 Humble installed, you can:

1. **Follow ROS2 Tutorials**: Start with the [official ROS2 tutorials](https://docs.ros.org/en/humble/Tutorials.html)
2. **Create a Workspace**: Set up your development environment
3. **Install Additional Packages**: Add packages you need for your projects
4. **Set up VS Code**: Install the Remote-WSL extension for development

### Useful ROS2 Commands to Get Started

```bash
# Check ROS2 installation
ros2 --help

# List available packages
ros2 pkg list

# Run a node
ros2 run <package_name> <node_name>

# List running nodes
ros2 node list

# Show topics
ros2 topic list

# Create a workspace
mkdir -p ~/ros2_ws/src
cd ~/ros2_ws
colcon build
```

---

## Conclusion

You now have a fully functional ROS2 Humble installation running on Ubuntu 22.04 within WSL2 on Windows 11. This setup provides excellent performance and compatibility for ROS2 development while maintaining access to your Windows applications.

The combination of WSL2 and ROS2 offers:
- **Native Linux performance** for ROS2 applications
- **Seamless file sharing** between Windows and Linux
- **GPU support** for machine learning workloads (if needed)
- **Easy development workflow** with modern tools

Happy robotics development! 🤖

---
