# Python指令

## 一. 离线包安装

### 基本语法

```bash
pip install -f . -r requirements.txt --no-index
```

### 参数说明

| 参数                    | 说明                         |
|-----------------------|----------------------------|
| `-f .`                | 从当前目录查找包文件                 |
| `-r requirements.txt` | 从requirements.txt文件读取依赖包列表 |
| `--no-index`          | 不使用PyPI索引, 仅使用本地包          |

### 使用场景

* **离线环境安装**: 在没有网络连接的环境中安装Python包
* **批量安装**: 一次性安装多个依赖包
* **版本控制**: 确保安装指定版本的包

### 示例

```bash
# 在当前目录安装requirements.txt中列出的所有包
pip install -f . -r requirements.txt --no-index

# 指定其他目录
pip install -f /path/to/packages -r requirements.txt --no-index
```

## 二. .py文件打包为exe

### 使用PyInstaller打包

#### 基本语法

```bash
pyinstaller --onefile --noconsole <名称>.py
```

或

```bash
pyinstaller -F -w <名称>.py
```

### 参数说明

| 参数             | 短参数  | 说明                 |
|----------------|------|--------------------|
| `--onefile`    | `-F` | 打包成单个可执行文件         |
| `--noconsole`  | `-w` | 不显示控制台窗口(适用于GUI程序) |
| `--console`    | `-c` | 显示控制台窗口(默认)        |
| `--name`       | `-n` | 指定生成的可执行文件名称       |
| `--icon`       | `-i` | 指定程序图标             |
| `--add-data`   |      | 添加额外的数据文件          |
| `--add-binary` |      | 添加二进制文件            |

### 常用打包命令

#### 打包为单个文件(带控制台)

```bash
pyinstaller -F <文件名>.py
```

#### 打包为单个文件(不带控制台, GUI程序)

```bash
pyinstaller -F -w <文件名>.py
```

#### 打包为单个文件并指定图标

```bash
pyinstaller -F -w -i icon.ico <文件名>.py
```

#### 打包为单个文件并添加数据文件

```bash
pyinstaller -F --add-data "data/*;data" <文件名>.py
```

#### 打包为单个文件并添加二进制库

```bash
pyinstaller -F --add-binary "nle_library;nle_library" <文件名>.py
```

### 打包示例

```bash
# 打包main.py为单个可执行文件, 不显示控制台
pyinstaller -F -w main.py

# 打包为myapp.exe, 使用自定义图标
pyinstaller -F -w -i myicon.ico -n myapp main.py

# 打包包含额外资源
pyinstaller -F -w --add-data "images/*;images" --add-data "config/*;config" main.py
```

## 三. .ui文件转化为.py

### 使用pyuic5转换

#### 基本语法

```bash
pyuic5 <文件名.ui> -o <文件名>.py
```

### 参数说明

| 参数               | 说明                    |
|------------------|-----------------------|
| `<文件名.ui>`       | 输入的Qt Designer .ui文件  |
| `-o <文件名>.py`    | 指定输出的Python文件         |
| `-x`             | 生成可执行的代码框架            |
| `--from-imports` | 使用from PyQt5 import语法 |

### 常用转换命令

#### 基本转换

```bash
pyuic5 mainwindow.ui -o mainwindow.py
```

#### 生成可执行代码框架

```bash
pyuic5 mainwindow.ui -o mainwindow.py -x
```

#### 使用from导入语法

```bash
pyuic5 mainwindow.ui -o mainwindow.py --from-imports
```

#### 批量转换多个文件

```bash
# Windows
for %f in (*.ui) do pyuic5 "%f" -o "%~nf.py"

# Linux/Mac
for f in *.ui; do pyuic5 "$f" -o "${f%.ui}.py"; done
```

### 转换示例

```bash
# 转换单个文件
pyuic5 dialog.ui -o dialog.py

# 转换并生成可执行框架
pyuic5 mainwindow.ui -o mainwindow.py -x

# 转换并使用from导入
pyuic5 widget.ui -o widget.py --from-imports
```