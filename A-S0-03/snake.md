**一、题目分析**

  拿到附件`snake.jpg`，是一张图片。杂项图片隐写常规思路：先检测图片里面是否捆绑了其他文件。 题目名字是 snake（蛇），暗示后面会用到和蛇相关的密码学算法 Serpent。

**二、解题步骤**

1、 使用随波逐流检测图片内嵌文件， 使用 foremost 分离内嵌 zip 压缩包  

   分离完成后，进入输出目录`test1/zip`，得到文件：`00000543.zip`

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1793631688896-369b687b-0dab-42d6-b2a2-e2016e4c7c79.png)

  2、 打开压缩包，得到 key、cipher 两个文件 ** **

`key`：存放 Base64 编码的提示文本

`cipher`：加密后的密文文件，无法直接打开阅读

3、 随波逐流 Base64 解码 key  

用记事本打开`key`，复制里面的 Base64 字符串， Base64 解码出

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1793631809026-34b26055-c294-4961-86c2-f7c0b41129e3.png)

 翻译：Nicki Minaj 那首和蛇有关的歌叫什么名字？  

 搜索该问题，得到歌曲名称：`anaconda`

 `anaconda` 就是 Serpent 解密的密钥。  

 4、Serpent 解密 cipher  

模式选择：ECB；

密钥填入：`anaconda`；

载入密文文件`cipher`，解密； 解密成功，输出 flag：

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1793632080901-d5e37888-e680-4b6c-9f31-46eefa37d488.png)

**三、总结**

  binwalk：文件扫描工具，识别图片中嵌入的压缩包、固件；foremost：基于文件头签名，分离提取内嵌文件；Base64 编码：用来隐藏提示信息；Serpent：分组加密算法，名字含义为蛇，和题目 snake 形成呼应

