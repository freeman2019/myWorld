[TOC]

# Linux下的OCR软件

## 软件

### ABBYY FineReader
- 软件可能比较大，只能识别文件

### OCRFeeder
- 只能识别文件

### gimageReader:yum:
- 开源、简洁、能部分识别

### tesseract
- 开源、谷歌维护、可训练、只能识别文件（可以用于以后的手写字）中文识别率差?


## 安装

### 添加ppa
PPA 的一般形式是： ppa:user/ppa-name
```bash
sudo add-apt-repository ppa:user/ppa-name
sudo apt-get update
```
安装gimageReader
```bash
sudo add-apt-repository ppa:sandromani/gimagereader
sudo apt-get update
sudo apt-get install gimagereader tesseract-ocr tesseract-ocr-chi-sim  # 安装需要的语言(Chinese simplify)
```
### 移除ppa
```bash
sudo add-apt-repository -r ppa:user/ppa-name
sudo apt-get update
```