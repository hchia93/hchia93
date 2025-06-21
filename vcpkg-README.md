# Installation Guide: `vcpkg` 

This guide outlines the steps to install `vcpkg`, a C++ package manager, which is essential for building C++ projects that use external dependencies.

## Prerequisites

- **Git**: Ensure you have Git installed. If the `git` command isn't recognized, please install it first from [git-scm.com](https://git-scm.com/).
- **Administrator Access**: Some steps require running Command Prompt or PowerShell as Administrator.

## Installation Steps

### 1. Clone `vcpkg`

Open Command Prompt or PowerShell as Administrator and clone the Vcpkg repository:

```bash
git clone https://github.com/Microsoft/vcpkg.git C:\vcpkg
```

> **Note**: This guide assumes installation to `C:\vcpkg` for consistency. You can choose any directory that suits your needs, but remember to update the paths in project batch files accordingly.

### 2. Bootstrap `vcpkg`

Navigate into the cloned `vcpkg` directory and run the bootstrap script:

```bash
cd C:\vcpkg
bootstrap-vcpkg.bat
```

### 3. Set Environment Variable

Set the `VCPKG_ROOT` environment variable to point to your `vcpkg` installation:

```bash
setx VCPKG_ROOT "C:\vcpkg"
```

> **Important**: You may need to restart your Command Prompt, PowerShell, or IDE for the environment variable to take effect.

### 4. Verify Installation

To confirm `vcpkg` is working correctly, run:

```bash
C:\vcpkg\vcpkg.exe version
```

You should see the Vcpkg version information displayed.

## Usage

After installation, you can use `vcpkg` to install C++ libraries:

```bash
# Install a library
C:\vcpkg\vcpkg.exe install <package-name>:x64-windows

# List installed packages
C:\vcpkg\vcpkg.exe list

# Integrate with Visual Studio
C:\vcpkg\vcpkg.exe integrate install
```

## Related Projects

This `vcpkg` installation is used by:
- [The Basketball](https://github.com/yourusername/the-basketball-sfml) - SFML + Box2D physics game
- [Vulkan Tutorial](https://github.com/yourusername/vulkan-tutorial-triangle) - Vulkan graphics tutorial 
