---
publish: true
tags: 
aliases: 
finished: true
title: anki
created: 2024-11-18 13:40
updated: 2024-11-18 13:40
TARGET DECK: 刷题::25计网-王道::第 6 章 应用层::6.5 万维网(WWW)::anki
---
## HTTP 协议

Q: HTTP 协议的作用是什么？
A: HTTP 协议定义了浏览器 (万维网客户进程) 怎样向万维网服务器请求万维网文档, 以及服务器怎样把文档传送给浏览器。

Q: 从层次的角度看，HTTP 属于哪一层协议？
A: 从层次的角度看, HTTP 是面向事务 (Transaction-oriented) 的应用层协议, 它规定了在浏览器和服务器之间的请求和响应的格式与规则, 是万维网上能够可靠地交换文件（包括文本、声音、图像等各种多媒体文件）的重要基础。

Q: HTTP 协议的特点是什么？
A: HTTP 协议的特点是**无连接**和**无状态**。

Q: HTTP 协议使用什么传输层协议保证可靠传输？
A: HTTP 使用 **TCP** 作为传输层协议, 保证了数据的可靠传输。

Q: 为什么说 HTTP 是无连接的？
A: HTTP 是**无连接**的，也就是说，虽然 HTTP 使用了 TCP 连接，但通信的双方在交换 HTTP 报文之前不需要先建立 HTTP 连接。
**解释：**
- HTTP 的无连接特性简化了服务器的设计, 使之更易支持大量并发的请求。
- 可以类比打电话，TCP 连接相当于拨通电话并保持通话，而 HTTP 报文相当于通话的内容。每次通话结束后，不需要一直保持电话连接，只需要在下次通话时再拨号即可。

Q: 为什么说 HTTP 是无状态的？
A: HTTP 是无状态的，也就是说，同一个客户第二次访问同一个服务器上的页面时，服务器的响应与第一次被访问时的相同，因为服务器并不记得曾经服务过的这个客户。
**解释：**
- HTTP 的无状态特性简化了服务器的设计, 使之更易支持大量并发的请求。
- 可以类比超市收银员，每个顾客结账时，收银员只关心当前顾客的商品，并不关心顾客之前是否来过或买过什么。

Q: HTTP/1.0 支持什么连接方式？
A: HTTP/1.0 只可以使用非持续连接。
**解释：**
- 对于非持续连接, 每个网页元素对象 (如 JPEG 图形、Flash 等) 的传输都需要**单独建立**一个 TCP 连接。

Q: HTTP/1.1 支持什么连接方式？
A: HTTP/1.1 既可以使用非持续连接，也可以使用持续连接。
**解释：**
- HTTP/1.1 默认使用持续连接。
- 所谓持续连接, 是指万维网服务器在发送响应后仍然保持这条连接, 使同一个客户和该服务器可以继续在这条 TCP 连接上传送后续的 HTTP 请求报文和响应报文。

Q: 持续连接的两种工作方式是什么？
A: 持续连接又分为非**流水线**和**流水线**两种工作方式。
**解释：**
- 对于非流水线方式, 客户在收到前一个响应后才能发出下一个请求, 服务器在发送完一个对象后, 其 TCP 连接就处于空闲状态, 浪费了服务器资源。
- 对于流水线方式, 客户可以连续发出对各个对象的请求, 服务器就可连续响应这些请求。若所有的请求和响应都是连续发送的, 则引用所有对象**共计经历 1 个 RTT** 延迟, 而不是像非流水线方式那样, 每个对象都**必须**有 1 个 RTT 延迟。这种方式减少了 TCP 连接中的空闲时间, 提高了效率。

Q: 非持续连接请求一个万维网文档所需的时间如何计算？
A: 非持续连接请求一个万维网文档所需的时间是：该文档的传输时间 (与文档大小成正比) 加上两倍往返时间 RTT (一个 RTT 用于 TCP 连接，另一个 RTT 用于请求和接收文档)。

Q: 流水线方式相对于非流水线方式有什么优势？
A: 流水线方式相对于非流水线方式的优势在于：引用所有对象共计经历 1 个 RTT 延迟，而不是像非流水线方式那样，每个对象都必须有 1 个 RTT 延迟。这种方式减少了 TCP 连接中的空闲时间，提高了效率。

Q: HTTP 报文有哪两类？
A: HTTP 报文有两类：请求报文和响应报文。

### HTTP 报文结构

Q: HTTP 报文由哪三个部分组成？
A: HTTP 报文都由三个部分组成：开始行、首部行、实体主体。

Q: HTTP 请求报文的请求行包含哪三个内容？
A: HTTP 请求报文的“请求行”有三个内容: 方法、请求资源的 URL 及 HTTP 的版本。

Q: HTTP 响应报文的状态行包含哪三个内容？
A: HTTP 响应报文的第 1 行是状态行, 它包含三个内容: HTTP 的版本、状态码、解释状态码的短语。

Q: HTTP 请求报文中常用的方法有哪些？
A: HTTP 请求报文中常用的方法有：
| 方法（操作） | 意义                                  |
|--------------|---------------------------------------|
| GET          | 请求读取由 URL 标识的信息                |
| HEAD         | 请求读取由 URL 标识的信息的首部            |
| POST         | 给服务器添加信息（如注释）               |
| PUT          | 将文件上传到服务器                        |
| DELETE       | 删除服务器上的文件                        |
| CONNECT      | 用于代理服务器                          |
| OPTIONS      | 询问服务器支持哪些方法                   |
| TRACE        | 追踪请求的路径                           |
| PATCH        | 对服务器上的资源进行部分修改             |

Q: GET 方法的意义是什么？
A: GET 方法的意义是请求读取由 URL 标识的信息。
**示例：**
- 在浏览器地址栏输入网址访问网页。
- 从网站下载文件。

Q: HEAD 方法的意义是什么？
A: HEAD 方法的意义是请求读取由 URL 标识的信息的首部。
**示例：**
- 检查网页是否更新。
- 获取文件的元数据，例如文件大小、修改时间等。

Q: POST 方法的意义是什么？
A: POST 方法的意义是给服务器添加信息（如注释）。
**示例：**
- 提交表单数据。
- 上传文件。

Q: CONNECT 方法的意义是什么？
A: CONNECT 方法用于代理服务器。
**示例：**
- 建立到 HTTPS 网站的安全连接。

Q: HTTP 持续连接的默认端口号是多少？
A: HTTP 持续连接的默认端口号是 80。

### HTTPS 协议

Q: HTTPS 的工作原理是什么？
A: HTTPS 的工作原理如下：
1. 浏览器向服务器发送 HTTPS 请求。
2. 服务器向浏览器发送其 SSL 证书。
3. 浏览器验证证书的有效性。
4. 浏览器和服务器建立加密连接。
5. 浏览器发送加密的 HTTP 请求。
6. 服务器接收加密的 HTTP 请求，并进行解密。
7. 服务器发送加密的 HTTP 响应。
8. 浏览器接收加密的 HTTP 响应，并进行解密。

Q: HTTPS 使用的加密算法有哪些？
A: HTTPS 使用的加密算法主要包括：
- **对称加密算法**: 例如 AES、DES 等。用于加密和解密数据。
- **非对称加密算法**: 例如 RSA、ECC 等。用于交换密钥和数字签名。
- **哈希算法**: 例如 SHA-256、MD5 等。用于验证数据的完整性。
