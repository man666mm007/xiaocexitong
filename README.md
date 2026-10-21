# 概率论小测查询系统

一个基于 Flask、SQLite 和 Jinja 的课程小测应用，支持学生答题、成绩查询与统计、预约签到、错题回顾和教师管理。

## Windows 一键安装

将完整的 Windows 首次安装 ZIP 解压到一个你有写入权限的本地文件夹，然后双击 start_windows.bat。安装程序不需要预装 Python 或管理员权限；缺少 Python 时会将官方 Python 3.13.15 x64 安装到包目录内的 python-runtime 子文件夹。

应用、数据库、上传文件、更新助手、缓存、备份和日志都留在解压目录中。安装后不要移动或改名目录。教师安装步骤和故障排查见 docs/TEACHER_FIRST_INSTALL_WINDOWS.md。

首次安装 ZIP 仅包含运行所需的公开应用文件、发布公钥和更新助手，不包含签名私钥、数据库、上传资料、备份、secret_key.txt、演示数据或虚拟环境。不要把实际数据或本地运行目录放进公开源代码包。

## 源码开发

源码开发需要 Python 3.11 或 3.12。创建虚拟环境并安装依赖：

    py -3.12 -m venv .venv
    .venv\Scripts\python.exe -m pip install -r requirements.txt

生成本地密钥并初始化教师账号。请通过安全渠道提供真实账号信息，不使用默认账号或固定密码：

    $env:QUIZ_SECRET_KEY = (& python -c "import secrets; print(secrets.token_hex(32))")
    .venv\Scripts\python.exe scripts\init_project.py --teacher-id "teacher-login-id" --teacher-name "Teacher Name"

启动本地服务：

    .venv\Scripts\python.exe scripts\start_server.py

Linux 和 macOS 用户可使用对应平台的 Python、虚拟环境和环境变量。Windows 首次安装脚本仅用于 Windows 包内安装，并会在本地生成 secret_key.txt。

## 测试

    .venv\Scripts\python.exe -m unittest discover -s tests -v

## 发布内容

公开源代码包不应包含数据库、上传资料、备份、签名私钥、服务器配置、固定演示凭据、演示数据、虚拟环境、日志或 QA 截图。发布前请检查 ZIP 内容和签名。
