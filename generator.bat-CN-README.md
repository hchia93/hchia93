# 依赖安装说明 (中文)

## 现代C++项目依赖管理

现在，我大多数C++项目都采用统一的依赖管理和解决方案生成方式，只需一个脚本：`generate.bat`。

此脚本将会：
1. 检查Git和vcpkg，如未安装`vcpkg`会自动安装到本地。
2. 根据项目中的`vcpkg.json`文件，自动安装所有依赖（本地`vcpkg_installed/`文件夹）。
3. 使用CMake生成Visual Studio解决方案，并自动配置所有依赖。

### 为什么用`generate.bat`？

- **无需上传`.lib`、`.dll`或头文件**：所有依赖都由vcpkg管理，并在`vcpkg.json`中声明。
- **无需手动配置**：脚本会自动安装vcpkg并完成所有依赖安装和配置。
- **统一工作流**：所有项目都采用相同的脚本和结构。
- **支持Git Action工作流**：项目可在Git上自动构建，简化CI/CD流程。

### 使用方法

1. 在项目根目录打开命令行。
2. 运行：

   ```cmd
   generate.bat
   ```

3. 用Visual Studio打开`generated-vs/`中的解决方案，正常编译运行即可。

> **注意：**  
> 第一次打开解决方案时，可能需要在Visual Studio中手动设置启动项目。

### 项目结构示例

```
Project/
├── CMakeLists.txt
├── vcpkg.json
├── generate.bat
├── src/
├── resource/
└── generated-vs/
```

### 其他说明

- 脚本会在本地生成`vcpkg_installed/`文件夹用于依赖管理，请将其加入`.gitignore`。
- 更多vcpkg信息请参考：[vcpkg官方文档](https://github.com/microsoft/vcpkg) 