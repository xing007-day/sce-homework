我就用BUUCTF上的**极客大挑战2019Havefun**的题目来直观解释

**一、解题思路**

 打开网页，F12 查看网页源码，注释中发现 PHP 代码，代码判断 GET 参数 cat 的值等于 dog 时输出 flag；构造 GET 请求  ？cat=dog，使用浏览器 Network 面板抓取这条 HTTP 请求

**二、Network面板解释**

1. 在浏览器打开靶机页面，按下 F12，调出开发者工具
2. 在开发者工具上方，切换到 Network 标签
3. 勾选面板上方的保留日志，防止请求刷新清空
4. 在浏览器地址栏，拼接参数访问：`http://xxx.buuoj.cn:81/?cat=dog`，按下回车
+ Request URL：`http://9dfa12275ff68c054bc6607d.http-ctf2.dasctf.com/?cat=dog`
+ Request Method：`GET`
+ Status Code：`200 OK`
+ Cookie：本次请求不需要身份凭证，请求头中不存在Cookie字段

**补充：BUUCTF主页请求**

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1793637897151-3bbf0e48-46c4-496a-b4fa-28016eba58eb.png)

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1793637740505-4ca6b14b-3a3b-4306-93ce-cfe357b6e0e7.png)

**<font style="color:#DF2A3F;">解释：</font>**

url： 请求的目标地址，浏览器向这个地址发送请求  

method： HTTP请求方法，GET代表把参数放在URL里传递  

cookie：浏览器携带的身份凭证，用来标识当前会话

 status：服务器返回状态码，200代表请求成功  

5、顺便切换到<font style="color:#DF2A3F;">元素</font>面板查看网页源码， 在源码注释中发现PHP代码：  

<!-- 这是一张图片，ocr 内容为： -->
![](https://cdn.nlark.com/yuque/0/2026/png/68387380/1793638232817-22055cdf-0aa2-40bc-8c9c-aae52eace3bb.png)

 需要传入 GET 参数 cat，值为 dog，才会输出 flag  （？是URL里“协议头”和“查询参数”的分隔符，用来告诉服务器，？后面的内容是用户提交的查询条件）



