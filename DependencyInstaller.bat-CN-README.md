## 创建 DependencyInstaller.Bat

一般有使用第三方依赖的项目，如果想要放在GitHub上展示，往往面临着几个问题：

- 可能需要上传 `.lib` 或者 `.dll` 文件。如果不上传，其他用户可能无法顺利运行我的项目。
- 需要应用 `.h` 或者 二进制类文件， 比如 `../bin` 里的内容。

两者都不太理想。

为此，我会使用 `cmake` 及 [`vcpkg`](https://github.com/hchia93/hchia93/blob/main/vcpkg-README.md) 来处理这些第三方依赖, 生成新的 VisualStudio Solution。

在这个过程中，我用了 `.bat` 文件来安装 Windows 上的第三方依赖库安装。
每个项目都有不同的第三方依赖，我封装了项目特定的第三方依赖在 `vcpkg.json` 文件里。 这样，我就能够**规范脚本**，尽可能地**去除异化点**。

最后，结合我收集的资料，写了这份 `README` 以方便日后的更新。

## 流程
这个脚本的流程大致为：

1. 核对 `git`
2. 核对 & 安装 `vcpkg`
3. 安装 `vcpkg` 安装第三方依赖 （视项目而定)
4. 核对 `cmake`

> **⚠️ 注意事项**: 
> 此脚本会在项目根径生成 `vcpkg_installed/` 文件夹。
> 请将此目录登记在`.gitignore` 里.

### 脚本头
```cmd
@echo off
echo ========================================
echo Dependency Installer
echo ========================================
echo.
```

### 核对 git
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
### 核对及安装 vcpkg
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
### 核对项目 vcpkg.json
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

### 安装 vcpkg.json
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

### 显示 vcpkg.json 安装结果
```cmd
REM Display installed packages
echo [INFO] Installed packages:
"%VCPKG_ROOT%\vcpkg.exe" list
echo.
```

### 核对 CMake
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
### 脚本尾
```cmd
echo Dependency installation completed successfully!
echo.
pause 
```


