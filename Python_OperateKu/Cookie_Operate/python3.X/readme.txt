python3中使用Cookiejar库来处理cookie

CookieJar()的使用方法
      import http.cookiejar
      #使用http.cookiejar.CookieJar() 创建CookieJar对象
      cjar = http.cookiejar.Cookiejar()
      #使用HTTPCOokieProcessor创建cookie处理器，并以其为参数构建opener对象
      opener = urllib.request.build_opener(urllib.request.HTTPCookieProcessor(cjar))
      #将opener安装为全局
      urllib.request.install_opener(opener)
      #接下来为正常的打开指定的URL过程
      file = opener.open(url)


什么是Cookie？
概括来说，就是保存会话信息，帮助维持会话状态的一种方式
与HTTP协议有关。我们访问的每一个互联网页面，都是通过HTTP协议进行，而HTTP协议是一个无状态协议，无法维持会话之间的状态
为了避免登陆一个网站，每次新打开这个网站新的页面而进行重复登陆的繁琐过程，就引入了Cookie与Session这两种方式保存会话信息。
通过Cookie保存会话信息，
会将对应的会话信息保存到客户端，当我们访问同一个网站其他页面时，会从Cookie中读取对应的会话信息，从而判断目前的会话状态，比如可以判断是否已经登陆等。
通过Session保存会话信息，
会将对应的会话信息保存到服务端，但是服务器端会给客户端发SessionID等信息，这些信息一般存储在客户端的Cookie中，当然，如果客户端紧张了Cookie，也会通过其他方式存储。目前，大部分情况还是会将这一部分的信息存到Cookie中。然后，用户在访问该网站其他网页时，会从Cookie中读取这一部分信息，然后从服务器中的Session中根据这一部分Cookie信息检索出该客户端的所有会话信息，然后进行会话控制。显然，使用Seesion方式来保存会话信息，还是会用到Cookie。
