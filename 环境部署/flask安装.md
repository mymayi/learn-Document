#### 在线环境：
1. **创建虚拟环境**:
    ```bash
    python -m venv online-env
    source online-env/bin/activate  # 在 Windows 上使用 `online-env\Scripts\activate`
    ```

2. **下载包**:
    ```bash
    pip download flask pillow opencv-python flask-cors
    ```

3. **将下载的包复制到 USB 驱动器或其他存储设备**:
    ```bash
    cp *.whl *.tar.gz /path/to/usb/drive/
    ```

#### 离线环境：
1. **将下载的包从 USB 驱动器复制到离线环境中的某个目录**:
    ```bash
    cp /path/to/usb/drive/*.whl /path/to/offline/directory/
    cp /path/to/usb/drive/*.tar.gz /path/to/offline/directory/
    cd /path/to/offline/directory/
    ```

2. **创建虚拟环境**:
    ```bash
    python -m venv offline-env
    source offline-env/bin/activate  # 在 Windows 上使用 `offline-env\Scripts\activate`
    ```

3. **安装包**:
    ```bash
    pip install --no-index --find-links=. flask pillow opencv-python flask-cors
    ```

### 验证安装

确保所有包都已正确安装。你可以通过以下命令列出已安装的包：

```bash
pip list
```

你应该能看到 Flask、Pillow、OpenCV 和 Flask-CORS 列表中。

### 运行 Flask 应用

最后，运行你的 Flask 应用以确保一切正常：

```bash
python app.py
```

这样，你就可以在离线环境中成功安装并运行 Flask 应用了。