在当今信息时代，写作已成为许多人不可或缺的一项技能。无论是写博客、撰写文章，还是做笔记和整理思路，一个高效的写作工具都能极大地提升工作效率和创作质量。[StackEdit](https://zhida.zhihu.com/search?content_id=230303528&content_type=Article&match_order=1&q=StackEdit&zhida_source=entity)作为一款强大的在线[Markdown](https://zhida.zhihu.com/search?content_id=230303528&content_type=Article&match_order=1&q=Markdown&zhida_source=entity)编辑器，不仅具备卓越的写作功能，还支持[实时预览](https://zhida.zhihu.com/search?content_id=230303528&content_type=Article&match_order=1&q=%E5%AE%9E%E6%97%B6%E9%A2%84%E8%A7%88&zhida_source=entity)、[多设备同步](https://zhida.zhihu.com/search?content_id=230303528&content_type=Article&match_order=1&q=%E5%A4%9A%E8%AE%BE%E5%A4%87%E5%90%8C%E6%AD%A5&zhida_source=entity)等特性，备受写作者们的青睐。

然而，由于一些隐私和安全的考虑，有些人可能更倾向于在私有环境中部署StackEdit。本文将介绍如何使用[Docker](https://zhida.zhihu.com/search?content_id=230303528&content_type=Article&match_order=1&q=Docker&zhida_source=entity)进行私有部署StackEdit，让你可以在自己的服务器上拥有一个安全可控的写作环境。

### **介绍**

StackEdit 是非常出色的在线 markdown 编辑器.

官网 [https://stackedit.io/](https://link.zhihu.com/?target=https%3A//stackedit.io/)

源码 [https://github.com/benweet/stackedit/](https://link.zhihu.com/?target=https%3A//github.com/benweet/stackedit/)

### **docker 启动**

首先，我们需要准备一台具备Docker环境的服务器。如果你还没有安装Docker，请参考Docker官方文档完成安装。

接下来，我们需要获取StackEdit的Docker镜像。StackEdit的官方仓库提供了Docker镜像的下载。使用以下命令获取最新版本的StackEdit镜像：

docker pull benweet/stackedit

下载完成后，我们可以使用以下命令启动StackEdit容器：

docker run -d -p 8080:8080 benweet/stackedit

这将在容器中启动StackEdit，并将容器的8080端口映射到服务器的8080端口。你可以根据需要修改端口映射。

现在，你可以在浏览器中输入服务器的IP地址和端口号（例如：[http://your_server_ip:8080](https://link.zhihu.com/?target=http%3A//your_server_ip%3A8080)）来访问StackEdit。初始页面将展示一个干净简洁的Markdown编辑器，你可以开始尽情写作了！

StackEdit还提供了许多高级功能，例如实时预览、多文档管理、云端同步等。你可以通过在启动容器时添加各种配置参数来定制StackEdit的行为。例如，你可以通过添加`-e`参数来设置StackEdit的主题：

docker run -d -p 8080:8080 -e STACKEDIT_THEME="dark" benweet/stackedit

上述命令将使用暗色主题启动StackEdit容器。

此外，如果你希望数据在容器重启后仍然保留，你可以将数据目录挂载到宿主机。例如：

docker run -d -p 8080:8080 -v /path/to/data:/data benweet/stackedit

上述命令将容器中的`/data`目录挂载到宿主机的`/path/to/data`目录，确保数据的持久性和安全性。

通过使用Docker进行私有部署，

### **[docker-compose](https://zhida.zhihu.com/search?content_id=230303528&content_type=Article&match_order=1&q=docker-compose&zhida_source=entity) 部署**

docker-compose.yml

version: '3.3'  
services:  
  stackedi:  
    image: benweet/stackedit:latest  
    restart: always  
    ports:  
      - 8080:8080  
    volumes:  
      - ./data:/data  
docker-compose up -d 

上述命令将启动StackEdit容器。

### **使用效果**

特点：

-   实时预览: StackEdit提供了实时预览功能，即在你编辑Markdown文档的同时，可以即时看到渲染后的效果，方便你实时调整和查看文章的样式和格式。
    
-   离线编辑: StackEdit支持离线编辑，你可以在没有网络连接的情况下继续写作。这对于旅途中、无网络环境下或者网络不稳定的情况下都非常有用。
    
-   多平台同步: StackEdit支持多设备同步，你可以在不同的设备上安装StackEdit，并通过云同步功能将你的文档同步到所有设备上。这样，你可以随时随地继续写作，无需担心数据丢失或不同步的问题。
    
-   云端存储: StackEdit将你的Markdown文档存储在云端，确保你的数据安全和可靠性。即使你更换设备或者重新安装StackEdit，你的文档也可以轻松恢复。
    
-   丰富的编辑功能: StackEdit提供了丰富的Markdown编辑功能，包括标题、列表、引用、代码块、表格等，使得你可以以更加直观和简洁的方式撰写文章。
    
-   **导入和导出:** StackEdit支持从本地文件、Google Drive、Dropbox等多种来源导入Markdown文档，并且可以将文档导出为HTML、PDF、Markdown等格式，方便你在不同场景下的使用和分享。
    
-   自定义主题: StackEdit允许你自定义编辑器的主题，包括字体、颜色、背景等，以满足个性化的需求和喜好。
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQxNzM5MDgyMiw0NDA5MDU2MTldfQ==
-->