## Creating DependencyInstaller.bat

Whenever showcasing a project on GitHub that uses third-party dependencies, there are a few common challenges:

- You might need to upload `.lib` or `.dll` files. Others may not be able to run your project successfully without them.
- You may rely on `.h` files or binary class files, such as those located in `../bin`.

Both are not ideal.

To handle these third-party dependencies, I use `cmake` along with [`vcpkg`](https://github.com/hchia93/hchia93/blob/main/vcpkg-README.md) to handle project generation.

In this process, I use a `.bat` file to install third-party libraries on Windows. 
Since each project uses different dependencies, I encapsulated project specific dependencies in `vcpgk.json` and **standardized** the script across project with minimal deviation.

Lastly, I document what I gathered into this `README` and allow me to update accordingly in the future.

## Workflow Overview

The script roughly follows this flow:

1. Validate for `git`
2. Validate and install for `vcpkg`
3. Install third-party dependencies with `vcpkg` (project-specific)
4. Validate `cmake`

> **⚠️ Note:** 
> `vcpkg install --triplet=x64-windows` will generate a folder named `vcpkg_installed/` on your project root to store locally installed packages. This is different from vcpkg's global installation directory. Please remember to add it in `.gitignore`.

## Structure
```cmd
C:\vcpkg\                    ← vcpkg root (infrastructure)
├── scripts/buildsystems/vcpkg.cmake
├── ports/                   ← Package definitions
└── installed/               ← Global packages (unused)

Project1/
├── vcpkg.json
├── vcpkg_installed/         ← Project1's packages
└── src/

Project2/
├── vcpkg.json  
├── vcpkg_installed/         ← Project2's packages
└── src/
```

### Script Header
```cmd
@echo off
echo ========================================
echo Dependency Installer
echo ========================================
echo.
```
### Validate git
```cmd
REM Check if Git is installed
git --version >nul 2>&1
if errorlevel 1 (
    echo [ERROR] Git is not installed!
    echo Git is required to clone vcpkg and manage dependencies.
    echo.
    echo Please install Git from: https://git-scm.com/download/win
    echo After installing Git, run this script again.
    echo.
    pause
    exit /b 1
)
echo [OK] Git is available
```

### Validate & Install vcpkg
```cmd
REM Check if vcpkg is installed
if not exist "%VCPKG_ROOT%\vcpkg.exe" (
    echo [WARNING] vcpkg not found at %VCPKG_ROOT%
    echo.
    set /p choice="Do you want to git clone vcpkg to C:/? (Y/N): "
    if /i "%choice%"=="Y" (
        echo.
        echo [INFO] git clone vcpkg to C:/...
        if not exist "C:\vcpkg" (
            git clone https://github.com/microsoft/vcpkg.git C:\vcpkg
            if errorlevel 1 (
                echo [ERROR] Failed to clone vcpkg!
                echo Please check your internet connection and try again.
                echo.
                pause
                exit /b 1
            )
        ) else (
            echo [INFO] vcpkg directory already exists at C:\vcpkg
        )
        
        echo [INFO] Setting VCPKG_ROOT environment variable...
        set VCPKG_ROOT=C:\vcpkg
        echo [OK] vcpkg installed at: %VCPKG_ROOT%
    ) else (
        echo.
        echo Setup Environment Aborted.
        echo.
        pause
        exit /b 1
    )
) else (
    echo [OK] vcpkg at: %VCPKG_ROOT%
)
```

### Validate Project vcpkg.json
```cmd
REM Check if vcpkg.json exists
if not exist "vcpkg.json" (
    echo [ERROR] vcpkg.json not found!
    echo This file is required to define project dependencies.
    echo.
    pause
    exit /b 1
)
echo [OK] vcpkg.json found at project root
```

### Install Dependencies from vcpkg.json
```cmd
REM Install dependencies from vcpkg.json
echo [INFO] Installing dependencies from vcpkg.json...
echo.
"%VCPKG_ROOT%\vcpkg.exe" install --triplet=x64-windows

if errorlevel 1 (
    echo [ERROR] Failed to install dependencies!
    echo Please check your vcpkg installation and try again.
    echo.
    pause
    exit /b 1
)
echo [OK] Dependencies installed successfully
```

### Display Installed Dependencies
```cmd
REM Display installed packages
echo [INFO] Installed packages:
"%VCPKG_ROOT%\vcpkg.exe" list
echo.
```

### Validate CMake
```cmd
REM Check if CMake is available
cmake --version >nul 2>&1
if errorlevel 1 (
    echo [ERROR] CMake not found!
    echo Please install CMake and add it to your PATH.
    echo Visit: https://cmake.org/download/
    echo.
    pause
    exit /b 1
)
echo [OK] CMake: 
echo.
cmake --version
echo.
```

### Script Footer
```cmd
echo Dependency installation completed successfully!
echo.
pause 
```
