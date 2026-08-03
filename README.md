# TEXBAT 元数据云端下载工具

该工作流会在 GitHub Actions 的 Ubuntu 云服务器上尝试下载 TEXBAT 官方元数据，并打包为 `texbat_metadata.zip`。

## 包含的文件

- `cleanStatic.md5`
- `cleanStatic.xml`
- `cleanDynamic.md5`
- `cleanDynamic.xml`
- `ds1.md5`–`ds6.md5`
- `ds1.xml`–`ds6.xml`
- `ds7.md5`
- `ds8.md5`

官方目录没有 `ds7.xml` 和 `ds8.xml`。

## 使用方法

1. 新建一个 GitHub 私有仓库。
2. 解压本工具包，将 `.github` 文件夹上传到仓库根目录。
3. 打开仓库的 **Actions** 页面。
4. 选择 **Fetch TEXBAT metadata**。
5. 点击 **Run workflow**。
6. 运行完成后，在页面底部下载名为 **TEXBAT-metadata** 的 Artifact。
7. Artifact 中包含 `texbat_metadata.zip`。
8. 查看压缩包内是否有 `FAILED_FILES.txt`。如果没有，说明全部文件下载成功。

## 说明

该工具会依次尝试：

- `rnl-data` HTTPS
- `rnl-data` HTTP
- `radionavlab` HTTPS
- `radionavlab` HTTP

它会拒绝空文件、HTML错误页、无32位哈希的MD5文件以及不符合XML基本格式的响应。

如果 GitHub Actions 也显示全部失败，说明官方数据服务器当前对多个公共云出口均不可达，只能等待服务器恢复或联系TEXBAT维护方。
