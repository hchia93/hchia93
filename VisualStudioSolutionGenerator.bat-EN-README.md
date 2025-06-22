## Creating VisualStudioSolutionGenerator.bat

After installing required dependencies from `vcpkg.json` located in each project root, it is time to generate the Visual Studio Solution to bind the external dependencies.

## Structure
```cmd
Project Root/
├── CMakeLists.txt              ← Found by cmake ..
├── vcpkg.json
├── src/
└── generated-vs/               ← Script runs from here
    └── (CMake generates files here)
```
> **Note:** `cmake .. -DCMAKE_TOOLCHAIN_FILE="%VCPKG_ROOT%/scripts/buildsystems/vcpkg.cmake" -G "Visual Studio 17 2022" -A x64` will look for the `CMakeLists.txt` and generate the solutions.

## Starting Up The Project
Open the generated solution located at:
```cmd
generated-vs/<project-name>
```
and **right-click** on your <project-name> and **set as start up project**. 

### Scrip Heading
```cmd
@echo off
echo ========================================
echo Visual Studio Solution Generator
echo ========================================
echo.
```
### Verify vcpkg
```cmd
REM Check if vcpkg is installed
if not exist "%VCPKG_ROOT%\vcpkg.exe" (
    echo [ERROR] vcpkg not found!
    echo Please run DependencyInstaller.bat first to install vcpkg and dependencies.
    echo.
    pause
    exit /b 1
)
```

### Verify Project's vcpkg.jason
```cmd
REM Check if vcpkg.json exists
if not exist "vcpkg.json" (
    echo [ERROR] vcpkg.json not found!
    echo This file is required to define project dependencies.
    echo.
    pause
    exit /b 1
)
```
### Verfiy Dependencies Installation
```cmd 
REM Verify dependencies are installed
echo [INFO] Verifying dependencies from vcpkg.json...
"%VCPKG_ROOT%\vcpkg.exe" install --triplet=x64-windows --dry-run >nul 2>&1
if errorlevel 1 (
    echo [WARNING] Some dependencies may not be installed.
    echo Running DependencyInstaller.bat first is recommended.
    echo.
)
```

### Generate Directory
```cmd
REM Check if build directory exists, if not create it
if not exist "generated-vs" (
    echo Creating generated-vs directory...
    mkdir generated-vs
)
```
### Copnfigure CMake
```cmd
REM Change to build directory
cd generated-vs
REM Configure the project with CMake using vcpkg toolchain
echo Configuring project with CMake and vcpkg...
echo Using vcpkg toolchain: %VCPKG_ROOT%\scripts\buildsystems\vcpkg.cmake
echo.
cmake .. -DCMAKE_TOOLCHAIN_FILE="%VCPKG_ROOT%/scripts/buildsystems/vcpkg.cmake" -G "Visual Studio 17 2022" -A x64

if errorlevel 1 (
    echo ERROR: CMake configuration failed!
    echo.
    echo Troubleshooting tips:
    echo 1. Make sure you have Visual Studio 2022 installed
    echo 2. Make sure vcpkg is properly installed and VCPKG_ROOT is set
    echo 3. Run DependencyInstaller.bat first to install dependencies
    echo 4. Check that all dependencies in vcpkg.json are available
    echo.
    pause
    exit /b 1
)
```

### Script Footer
```cmd
echo.
echo [SUCCESS] Solution generated successfully!
echo.

REM Go back to project root
cd ..

pause 
```



