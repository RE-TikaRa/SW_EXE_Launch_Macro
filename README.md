# SolidWorks VBA 程序启动器（EXE）

面向 SolidWorks 的 VBA 宏程序启动器：从配置文件读取应用列表，在窗体中选择后直接启动。

## 功能
- 从 `SolidWorksAppList.txt` 加载程序列表并显示在窗体列表框
- 双击列表项或按回车键启动选中的程序
- 状态栏显示程序数量
- 配置文件不存在时自动生成默认示例（计算器、记事本）

## 运行环境
- Windows
- SolidWorks（VBA 宏环境）

## 使用方式
1. 将  `EXE_Ver2.0.swp` 与 `SolidWorksAppList.txt` 放在同一目录
2. 在 SolidWorks 中执行宏
3. 在弹出的窗体中选择程序，双击或按回车启动

## 配置文件说明（SolidWorksAppList.txt）
### 位置规则
- **优先**：宏文件所在目录
- **回退**：`%USERPROFILE%\Documents\SolidWorksAppList.txt`

### 编码建议
该文件由 `FileSystemObject.CreateTextFile` 创建，默认使用系统 ANSI 编码。  
**建议使用 ANSI/GBK 保存**，以避免中文显示异常。

### 格式
```
显示名称|完整路径
```

示例（默认生成内容）：
```
计算器|C:\Windows\System32\calc.exe
记事本|C:\Windows\System32\notepad.exe
```

### 兼容旧格式
仅写路径也可被识别：
```
C:\Path\To\App.exe
```
此时显示名称会自动取文件名。

## 目录结构（当前目录）
- `EXE_Ver2.0.swp`：宏文件本体
- `frmAppLauncher.bas`：窗体代码
- `main.bas`：入口模块
- `mdlAPI.bas`：API 声明模块
- `mdlAppList.bas`：应用列表管理模块
- `mdlTypes.bas`：公共类型定义模块
- `Microsoft Visual Basic for Applications.pdf`：源码/说明导出
- `README.md`：项目说明
- `SolidWorksAppList.txt`：应用列表配置
- `LICENSE`：MIT 许可文本
- `.codemap/`：辅助索引文件

## 常见问题
- **初始化错误 / 配置路径为空**：宏可能不是从文件运行，系统会回退到文档目录；检查 `Documents` 下是否生成配置文件。
- **启动失败 / 文件不存在**：配置路径错误或程序已被移动；修正 `SolidWorksAppList.txt` 的路径后重试。
- **列表为空**：配置文件为空或格式不正确；按“显示名称|完整路径”填写。

## 作者
Made By Tika

## 许可
MIT License。详见 `LICENSE`。
