# Dependency Installation (EN)

## Modern C++ Project Dependency Management

For most of my C++ projects, I now use a unified approach for dependency management and solution generation, based on a single script: `generate.bat`.

This script will:
1. Check for Git and vcpkg, and install `vcpkg` automatically if missing.
2. Use the `vcpkg.json` file in your project to install all required dependencies locally (in `vcpkg_installed/`).
3. Generate a Visual Studio solution using CMake, with all dependencies configured.

### Why use `generate.bat`?

- **No need to upload `.lib`, `.dll`, or header files**: All dependencies are managed by vcpkg and described in `vcpkg.json`.
- **No manual setup**: The script will install vcpkg if needed, and handle everything else automatically.
- **Consistent workflow**: All projects use the same script and structure.
- **Enable Git Action workflow**: Project can be built on Git, streamling CI/CD process.

### How to Use

1. Open a terminal in your project root.
2. Run:

   ```cmd
   generate.bat
   ```

3. Open the generated solution in `generated-vs/` with Visual Studio and build as usual.

> **Note:**  
> The first time you open the solution, you may need to set the correct startup project in Visual Studio.

### Project Structure Example

```
Project/
├── CMakeLists.txt
├── vcpkg.json
├── generate.bat
├── src/
├── resource/
└── generated-vs/
```

### Additional Notes

- The script will create a local `vcpkg_installed/` folder for dependencies. Add this to your `.gitignore`.
- For more details on vcpkg, see: [vcpkg Documentation](https://github.com/microsoft/vcpkg) 