
# 小雅同步元数据

高速异步爬虫从 https://emby.xiaoya.pro/ 同步小雅元数据
该版本修改了fetch_html、download函数，generate_localdb函数添加windows系统判断，exam_file函数添加了.replace('\\', '/')

---


## Prerequisite

Linux kernal "Max open files" need to be extended

Save it into /etc/profile.d/ to make it global avaiable after reboot

```bash
ulimit -n 4096
```
---
## Installation

#### Clone the project

```bash
  git clone https://github.com/Rik-F5/xiaoya_db
```

#### 跳转到项目文件夹

```bash
  cd xiaoya_db
```

#### 选择环境

```bash
  python3 -m venv .venv
  source .venv/bin/activate
```

#### 安装依赖

```bash
  python -m pip install -r requirements.txt
```
---
## Run Locally with venv activated

```bash
python solid.py --media <Xiaoya Folder>

```
---
## 调用示例

Download the metadata without replace the local NFOs
```bash
python solid.py --media <folder>
```

Download the metadata and replace the local NFOs if they are out of date or different

```bash
python solid.py --media <folder> --nfo true
```

Download the metadata and save the file list to a local DB (Python3.12+)

```bash
python solid.py --media <folder> --db true
```

Do not download any files. For testing or benchmark only.

```bash
python solid.py
```
---
## Parameters

```bash
-h, --help           show this help message and exit

--media <folder>     Path to store downloaded media files [Default: None]

--count [number]     Max concurrent HTTP Requests [Default: 100]

--debug, --no-debug  Verbose debug [Default: False]

--db, --no-db        <Python3.12+ required> Save into DB [Default: False]

--nfo, --no-nfo      Download NFO [Default: False]

--url [url]          Download path [Default: None]
···
