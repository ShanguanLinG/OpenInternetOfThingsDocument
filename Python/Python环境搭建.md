# Python环境搭建

## 一. 准备工作

1. **打开Python环境包**: 03_新版_Python环境包

## 二. PyCharm安装

### 安装步骤

1. **运行安装程序**: 双击 `pycharm-community-2022.1.exe`
2. **开始安装**: 点击 `Next`
3. **选择安装路径**: 点击 `Next`(使用默认路径)
4. **安装选项**: 勾选所有选项, 点击 `Next`
5. **开始安装**: 点击 `Install`
6. **等待安装**: 等待安装完毕
7. **完成安装**:
    * 勾选 `I want to manually reboot later`
    * 点击 `Finish`

## 三. Python安装

### 安装步骤

1. **运行安装程序**: 双击 `python-3.6.8-amd64.exe`
2. **重要配置**: 选中 `Add Python 3.6 to PATH`, 点击 `Install Now`
3. **等待安装**: 等待安装完毕
4. **完成安装**: 点击 `Close`

## 四. Python离线包安装(一)

### 批量安装依赖包

1. **打开离线包目录**: 打开 `offline_packages` 文件夹
2. **安装第一个包**:
    * 打开第一个文件夹
    * 在文件目录下删除路径, 输入指令:
      ```bash
      pip install -r . -f requirements.txt --no-index
      ```
3. **等待安装**: 等待安装完毕, 安装完毕后会自动退出(很快)
4. **安装剩余包**: 打开第二个文件夹, 以此类推, 安装完所有的离线包

## 五. Python离线包安装(二)

### 安装自定义库

1. **创建临时文件夹**: 在桌面上新建一个文件夹
2. **打开公共工具包**: 打开 `公共工具包_全栈版`
3. **进入Python库目录**:
    * 打开 `调用库&使用说明`
    * 打开 `Python文件夹`
    * 打开 `nle_library_v3.6文件夹`

4. **解压nle_library**:
    * 选中 `nle_library_v3.6.rar`
    * 右键解压到当前文件夹
    * 将解压出来的 `nle_library` 复制到桌面的新建文件夹中

5. **解压tplink库**:
    * 返回上一级目录
    * 打开 `tp_camera_文件夹`
    * 选中 `tplink_v3.6.rar`
    * 右键解压到当前文件夹
    * 将解压出来的 `tplink` 文件夹复制到桌面的新建文件夹中

6. **查找Python安装路径**:
    * Win+R输入 `cmd` 并回车, 打开命令提示符
    * 输入 `where python`, 查找python安装的路径
    * 打开python所在的目录的上一级目录

7. **复制库文件**:
    * 找到 `Lib` 文件夹
    * 将桌面中新建文件夹中的两个文件夹(`nle_library` 和 `tplink`)移动到 `Lib` 文件夹中

## 六. PyCharm配置

### 初始设置

1. **打开PyCharm**
2. **选择设置导入**: 选择 `Do not import settings`, 点击 `OK`
3. **创建新项目**: 点击 `New Project` 创建项目
4. **配置解释器**:
    * 选择 `Previously configured interpreter`
    * 点击 `Interpreter` 右侧的三个点
5. **选择系统解释器**:
    * 选择 `System Interpreter`
    * 点击 `OK`
6. **完成创建**: 点击 `Create`, 设置完毕

## 七. 安装验证

### 验证步骤

1. **验证Python安装**:
   ```bash
   python --version
   ```
   应显示: `Python 3.6.8`

2. **验证pip安装**:
   ```bash
   pip --version
   ```

3. **验证库安装**:
   ```python
   python -c "import nle_library; import tplink; print('库导入成功')"
   ```

4. **验证PyCharm配置**:
    * 在PyCharm中创建测试文件
    * 运行简单的Python代码
    * 确认代码能正常执行

## 八. 常见问题

### 安装问题

| 问题         | 解决方案                        |
|------------|-----------------------------|
| Python安装失败 | 检查系统权限, 关闭杀毒软件              |
| pip命令不可用   | 重新安装Python, 确保勾选Add to PATH |
| 离线包安装失败    | 检查requirements.txt文件是否存在    |
| 库导入失败      | 检查库文件是否复制到正确的Lib目录          |

### 配置问题

| 问题                | 解决方案             |
|-------------------|------------------|
| PyCharm无法找到Python | 手动指定Python解释器路径  |
| 项目创建失败            | 检查项目路径权限         |
| 库在PyCharm中不可用     | 在PyCharm中重新配置解释器 |

### 环境变量问题

1. **PATH变量检查**:
   ```bash
   echo %PATH%
   ```
   检查是否包含Python安装路径

2. **环境变量设置**:
    * 系统属性 -> 高级 -> 环境变量
    * 在Path中添加Python安装路径和Scripts路径