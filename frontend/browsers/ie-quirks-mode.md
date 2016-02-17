参考[msdn描述](https://msdn.microsoft.com/en-us/library/ff405803(v=vs.85).aspx)
参考[嗷嗷博客](http://www.aoao.org.cn/blog/2007/01/browser-mode/)

浏览器的模式问题 Quirks Mode vs Standards Mode
Posted on 2007-01-12 by aoao
当微软开始产生与标准兼容的浏览器时，他们希望确保向后兼容性。为了实现这一点，他们IE6.0以后的版本在浏览器内嵌了两种表现模式： Standards Mode（标准模式或Strict Mode）和Quirks mode（怪异模式或兼容模式Compatibility Mode）。在标准模式中，浏览器根据W3C所定的规范来显示页面；而在怪异模式中，页面将以IE5，甚至IE4的显示页面的方式来表现，以保持以前的网 页能正常显示。
对于这两种模式引起最大的问题就是盒模式的问题，或者现在大家已经忽视了IE5的存在，但是，IE在怪异模式运行的盒模式依然在最新版本的IE7保留着，一旦应用不得当，IE7将变成跟IE5一样愚蠢。
当然，不只IE浏览器存在两种模式。
Opera 浏览器 (Opera 7~8) 支持与 IE 相同的两种呈现模式：Quirks Mode和 Standards Mode（有关详细信息，请参阅 http://www.opera.com/docs/specs/doctype/），但是Opera9的Quirks Mode又不与之前的Quirks Mode呈现不一样，比如不再兼容IE5那种盒模式。
Mozilla Firefox 1+ 支持三种呈现模式：Quirks Mode、Almost Standards Mode（几乎标准的模式）和 Standards Mode。Firefox 的 Almost Standards 模式对应于 IE 和 Opera 的 Standards 模式。其中的Almost Standards Mode，除了在处理表格的方式方面有一些细微的差异之外，这种模式与标准模式基本相同。对于进入Quirks Mode的可参考http://www.mozilla.org/docs/web-developer/quirks/doctypes.html）
说了这样多可能你还不知道是到底Mode是怎样。现在试一下html 4的。
为什么要选择html4 呢？因为太多人认为只有xhtml才是符合标准的，又有多少人真的在使用xhtml呢？
可以先打开前两个看代码比较一下．
http://labs.aoao.org.cn/test/doctype/html4strict/
http://labs.aoao.org.cn/test/doctype/html4/
http://labs.aoao.org.cn/test/doctype/ishtml4strict/
当没有使用DTD声明或者使用HTML4以下（不包括HTML4）的DTD声明时，基本所有的浏览器都是使用Quirks Mode呈现。
也就是前两个code是一样，可是为什么运行结果不一样呢？因为第一个使用了DTD 声明html是 html4 strict的文档，IE6+的IE会开启标准模式来处理网页，第三个属于一个垃圾的方式把IE引入 quirks mode ^_^ 我常常用这招哦
我只是列出两个比较典型的问题，不同模式还会引起一大堆问题。有兴趣的朋友可以再找一下资料。
其实关于浏览器的模式问题我还写了很多，因为其他问题暂时没发出来，只是最近看到无忧上又在闹Web标准的事，突然发现某方连IE都不了解，哎！
document.compatMode可参考
This entry was posted in Web开发 and tagged 浏览器. Bookmark the permalink.
