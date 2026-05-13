# Automated Java Installer & Verifier

A lightweight, robust Bash script designed for Debian-based Linux distributions. It automates system updates, installs the default Java Runtime Environment (JRE), parses command output to extract the version number, and validates the installation status.

## Prerequisites
* **Operating System**: Ubuntu, Debian, or any Debian-based Linux distribution.
* **Permissions**: Root or `sudo` privileges are required to install system packages.

## Getting Started

### 1. Clone the Repository
Clone this repository to your local Linux machine using git:
```bash
git clone github.com
cd YOUR_REPOSITORY_NAME
```

### 2. Make the Script Executable
By default, newly cloned scripts lack execution permissions. Grant the necessary permissions with `chmod`:
```bash
chmod +x install_java.sh
```

### 3. Run the Script
Execute the script using `sudo` to ensure the package manager has permission to install the software:
```bash
sudo ./install_java.sh
```

## How It Works
1. **System Sync**: Runs `apt update` to pull the latest package lists from repositories.
2. **Dependency Deployment**: Installs `default-jre` automatically without requiring manual user confirmation.
3. **Version Extraction**: Captures the output of `java -version`, redirects `stderr` to `stdout`, and processes the string using `awk` to grab the major version digits.
4. **Environment Check**: Runs a evaluation block:
   * Alerts if no Java binary is found.
   * Warns if an outdated legacy version (Java 8 or older) is present.
   * Confirms success if Java 11 or greater is securely installed.

