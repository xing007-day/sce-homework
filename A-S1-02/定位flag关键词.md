<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1795191822252-f001c6ce-84ae-40fe-96a2-60ef172dbd05.png)

<font style="color:#DF2A3F;">文件内容过滤grep</font>：

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1795191934393-61db86f2-612b-4553-945d-e6edfb9ecbc6.png)

<font style="color:#DF2A3F;">find查找文件：</font>

+ find . -type f -exec grep "flag" {} ;
    - .从当前目录下开始找
    - -type f 只找普通文件，排除文件夹
    - -exec 把find找到的文件，传给grep执行

 

