[根据一个数组元素，删除另一个数组中的对象](https://segmentfault.com/q/1010000008836875)
```js

var a = [{ id: 15 }, { id: -1 }, { id: 0 }, { id: 3 }, { id: 12.2 }];
var b = [15, 3];
for (let i = 0; i < b.length; i++) {
  for (let j in a) {
    if (a[j].id == b[i]) {
      a.splice(j,1);
    }
  }
}
console.log(a);
var a = [{ id: 15 }, { id: -1 }, { id: 0 }, { id: 3 }, { id: 12.2 }];
var b = [15, 3];
for(index in a){
    if(b.indexOf(a[index]["id"])>=0)
        a.splice(index,1);
}
console.log(a);
a.filter(item => { return b.indexOf(item.id) === -1; });
```
[PHP队列执行任务的时候,如何防止进程之间抢夺资源](https://segmentfault.com/q/1010000008732536)
[SQL语句 把每个用户的每个月的任务数 和实际完成数](https://segmentfault.com/q/1010000008797237)
select a.user_id,mission,a.cc count_order,date from (select user_id,count(1) cc,DATE_FORMAT(FROM_UNIXTIME(order_time),'%Y-%m') odr_mn from order group by user_id, odr_mn) a join task b on a.user_id=b.user_id and a.odr_mn=DATE_FORMAT(FROM_UNIXTIME(b.date),'%Y-%m');
select a.user_id,a.mission,a.date, (select count(*)  from order b where a.user_id=b.user_id and DATE_FORMAT(FROM_UNIXTIME(a.date),'%Y-%m-%d') = DATE_FORMAT(FROM_UNIXTIME(b.order_time),'%Y-%m-%d')) count_order from task a;

[数据库查询排序问题，如何按字符串中的数字排序](https://segmentfault.com/q/1010000008762633)
ORDER BY CONVERT(SUBSTR(column, 6), SIGNED INTEGER)

[一个列表当中有一个日期的值，我想求这个日期里面当天最大时间的那一条](https://segmentfault.com/q/1010000008822123)
```js
from collections import defaultdict
grouped = defaultdict(list)

for d in s:
    grouped[(d['create_time'].split()[0], d['level'])].append((d['create_time'], d['count']))
summed = {k : max(grouped[k]) for k in grouped}
s = [{'count': summed[k][1], 'create_time': summed[k][0], 'level': k[1]} for k in summed]

from itertools import groupby

data = [...]
fun_group = lambda x: x['level']
fun_max = lambda x: x['create_time']
lst = [max(list(g), key=fun_max) for k, g in groupby(sorted(data, key=fun_group), fun_group)]
print lst
```

[JavaScript数组系列问题：数组差集https://segmentfault.com/q/1010000008825206]()
```js
var a = generateRandomArray(5, 10);
var b = generateRandomArray(10, 10);

// 不去重
var result = {
    a: a.filter(el => !b.includes(el)),
    b: b.filter(el => !a.includes(el))
}

// 去重
var result2 = {
    a: [...new Set(a)].filter(el => !b.includes(el)),
    b: [...new Set(b)].filter(el => !a.includes(el))
}

// 合并一下
function diffSet(a, b, noDup) {
    if (noDup) {
        a = [...new Set(a)];
        b = [...new Set(b)];
    }
    return {
        a: a.filter(el => !b.includes(el)),
        b: b.filter(el => !a.includes(el))
    }
}
```

[php如何解决redis的存取乱码](https://segmentfault.com/q/1010000008827412)
在存储前，先把存储的字符串转码。

$string = iconv('UTF-8','GBK',$string);
这时候存储在redis中的中文就是GBK字符集的，读取的时候不是乱码了。原理是window大部分系统上支持GBK字符集
[php数字键名会被强转成整型的问题](https://segmentfault.com/q/1010000008822020)
如果你的这个数组的key全都是string类型的，可以考虑通过 stdClass 转换下
```js
$result = new stdClass();
$result->{'12w'} = '大扫除';
$result->{'3.3'} = ' 搜索 ';
$result->{'456'} = '333';
$result->{789} = 1266;

var_dump($result);
// 输出：(可以看到键全都是string类型的)
// object(stdClass)#1 (4) {
//   ["12w"]=>
//   string(9) "大扫除"
//   ["3.3"]=>
//   string(8) " 搜索 "
//   ["456"]=>
//   string(3) "333"
//   ["789"]=>
//   int(1266)
// }

// 转换为array：
var_dump((array)$result);
$arr1 = [1,4,2,6];
$arr2 = [
    ['field_name' => '这是场地1','field_id' => 'd9','create_time' => 1489734050],
    ['field_name' => '这是场地2','field_id' => 'd10','create_time' => 1489734050],
    ['field_name' => '这是场地3','field_id' => 'd11','create_time' => 1489734050],
    ['field_name' => '这是场地4','field_id' => 'd12','create_time' => 1489734050]
];

array_walk(
    $arr2,
    function (&$v, $k) use ($arr1) { $v['number'] = $arr1[$k]; }
);
```
[python 复杂表格合并excel](https://segmentfault.com/q/1010000008778429)
```js
# coding: utf-8
from __future__ import unicode_literals

import pandas as pd
lst = [
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色1", "数量": "1", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色2", "数量": "20", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色3", "数量": "3", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色4", "数量": "4", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色5", "数量": "5", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色6", "数量": "6", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色7", "数量": "30", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色8", "数量": "8", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色9", "数量": "9", },
    {"ID": "1", "订单号": "123456", "用户名": "路人甲", "产品": "XX用品", "颜色": "色10", "数量": "40", },
    {"ID": "2", "订单号": "456789", "用户名": "路人乙", "产品": "XXX用品", "颜色": "红色", "数量": "100", },
    {"ID": "3", "订单号": "123456789", "用户名": "路人丙", "产品": "XXXX用品", "颜色": "金色", "数量": "300", },
    {"ID": "3", "订单号": "987654321", "用户名": "路人丙", "产品": "XXXX用品", "颜色": "紫色", "数量": "100", }
]

df = pd.DataFrame(lst)
df["数量"] = df["数量"].apply(lambda x: int(x))
df["备注"] = ''
df1 = df.groupby(["ID","用户名","产品", '备注',"订单号","颜色"]).sum()

#导出到excel
df1.to_excel('test.xlsx')

#输出html
print df1.to_html()
```
[Python3安装selenium后下载chormdriver](https://segmentfault.com/q/1010000008831619)
https://chromedriver.storage.googleapis.com/index.html?path=2.28/  chromedriver 从来都没有win64的，不过win32的在64位下也可以跑

[php中用redis存储session，为什么第一次打印出来的session为空？](https://segmentfault.com/q/1010000008721376)
根据redis自带的monitor监控了一下redis的状态
$_session['test']=[1,23]
echo $redis->get('PHPREDIS_SESSION'.session_id());
[(转)22个免费的数据可视化和分析工具推荐](https://zhuanlan.zhihu.com/p/26002147)
[我为莆田系代言-把这款插件推广到五湖四海](https://zhuanlan.zhihu.com/p/25963120)
[在bilibili学科学数学视频课程](https://zhuanlan.zhihu.com/p/25990210)
[详解 Cookie 纪要](https://zhuanlan.zhihu.com/p/25793137)
[阿里的编码规范里面写超过三张表禁止join 这是为什么？这样的话那sql要怎么写](https://www.zhihu.com/question/56236190/answer/153450286)
[推荐给职场人士的实用网站](https://zhuanlan.zhihu.com/p/25990764?group_id=829290980518805504)
草料二维码是国内最大的二维码在线服务网
Ezgif是一款在线GIF动画转化工具
http://link.zhihu.com/?target=http%3A//TAGUL.com  Tagul是一款文字云制作工具
ProcessOn是一个在线协作绘图平台,为用户提供最强大
下载一个acrobat pro也可以pdf转word
[【神技】将文字隐藏到图片中 - 知乎专栏](https://zhuanlan.zhihu.com/p/25924908?group_id=827872454067240960)
新建文件夹，把图片命名为1.jpg，种子压缩为1.rar copy/b 1.jpg+1.rar =output.jpg
http://link.zhihu.com/?target=http%3A//www.shuidi.im/  
[一大波爬虫素材袭来！衣食住行工作学习招聘娱乐资讯一应俱全！](https://zhuanlan.zhihu.com/p/25911479?group_id=827586112770957312)
[试windows的一项功能，那就是任务计](https://zhuanlan.zhihu.com/p/25900491?group_id=827496543505502208)
[FastStone Capture—一款可以长截图的电脑软件](https://zhuanlan.zhihu.com/p/25971084?group_id=828583081584771072)
[Python爬虫学习系列教程](https://zhuanlan.zhihu.com/p/25949099?group_id=828237833503408128)
[爬虫入门到精通-网页的解析（xpath） - 知乎专栏](https://zhuanlan.zhihu.com/p/25887452)
豆瓣爬虫微博
https://github.com/kimg1234/pachong  https://github.com/GentlyGuitar/web-crawlers 
```js
session与cookie的区别：


1，session 在服务器端，cookie 在客户端（浏览器）

2，session 存在在服务器的一个文件里（默认），不是内存

3，session 的运行依赖 session id，而 session id 是存在 cookie 中的，也就是说，如果 浏览器禁用了 cookie ，同时 session 也会失效（当然也可以在 url 中传递）

4，session 可以放在 文件，数据库，或内存中都可以。

5，用户验证这种场合一般会用 session

因此，维持一个会话的核心就是客户端的唯一标识，即 session id
```
https://zhuanlan.zhihu.com/p/25887452

[全栈数据工程师养成攻略系列视频教程](https://github.com/Honlan/fullstack-data-engineer)
http://study.163.com/course/introduction.htm?courseId=1003520028#/courseDetail 
[cookie机制采用的是在客户端保持状态的方案，而session机制采用的是在服务器端保持状态的方案。 ](https://www.zhihu.com/question/57444302)
```js
生命周期

cookie如果没有设置过期时间，那么称为会话cookie， 生命期为浏览器会话期间，关闭浏览器窗口，cookie就消失。 

如果设置过期时间， 浏览器就会把cookie保存到硬盘上，关闭后再次打开浏览器，这些cookie仍然有效直到超过设定的过期时间。存储在硬盘上的cookie可以在不同的浏览器进程间共享，比如两个IE窗口。而对于保存在内存里的cookie，不同的浏览器有不同的处理方式 。生命周期为创建至设定的过期时间。


session 则是服务器使用一种类似于散列表的结构（也可能就是使用散列表）来保存信息。  当程序需要为某个客户端的请求创建一个session时，服务器首先检查这个客户端的请求里是否已包含了一个session标识（称为session id），如果已包含则说明以前已经为此客户端创建过session，服务器就按照session id把这个session检索出来使用（检索不到，会新建一个），如果客户端请求不包含session id，则为此客户端创建一个session并且生成一个与此session相关联的sessionid，session id的值应该是一个既不会重复，又不容易被找到规律以仿造的字符串，这个session id将被在本次响应中返回给客户端保存。保存这个session id的方式可以采用cookie，这样在交互过程中浏览器可以自动的按照规则把这个标识发送给服务器。一般这个cookie的名字都是类似于SEEESIONID。但cookie可以被人为的禁止，则必须有其他机制以便在cookie被禁止时仍然能够把session id传递回服务器。 


服务器共享

如上所示，可以看到每个session都会有一个对应的、唯一的session id，通过session id可以取到相应的session值，那么如何取到呢。首先我们要了解session是保存在什么地方的。


 SESSION 的数据保存在哪里呢？当然是在服务器端，但不是保存在内存中，而是保存在文件或数据库中。默认情况下，php.ini 中设置的 SESSION 保存方式是 files（session.save_handler = files），即使用读写文件的方式保存 SESSION 数据，而 SESSION 文件保存的目录由 session.save_path 指定，文件名以 sess_ 为前缀，后跟 SESSION ID，如：sess_c72665af28a8b14c0fe11afe3b59b51b。文件中的数据即是序列化之后的 SESSION 数据了。如果访问量大，可能产生的 SESSION 文件会比较多，这时可以设置分级目录进行 SESSION 文件的保存，效率会提高很多，设置方法为：session.save_path="N;/save_path"，N 为分级的级数，save_path 为开始目录。当写入 SESSION 数据的时候，PHP 会获取到客户端的 SESSION_ID，然后根据这个 SESSION ID 到指定的 SESSION 文件保存目录中找到相应的 SESSION 文件，不存在则创建之，最后将数据序列化之后写入文件。读取 SESSION 数据是也是类似的操作流程，对读出来的数据需要进行解序列化，生成相应的 SESSION 变量。 


因为是保存在文件而不是内存中，那么我们就可以在同服务器的不同进程和应用中使用。如果在不同服务器上使用那就需要session信息的保存需要多个服务器可以同时存取。同时因为服务器是根据客户端cookie中的 PHPSESSID 来读取对应的session信息，那么就需要不同服务器对同一客户端产生相同的cookie


第一个问题，可以通过mysql来保存session信息。主要依靠 session_set_save_handle() 函数，此函数有六个参数： session_set_save_handler ( string open, string close, string read, string write, string destroy, string gc )各个参数为各项操作的函数名，这些操作依次是：打开、关闭、读取、写入、销毁、垃圾回收。PHP 手册中有详细的例子，在这里我们使用 OO 的方式来实现这些操作，详细代码如下： 

<?php  
 session_module_name('user');   //设置按用户设定方式操作session
define('MY_SESS_TIME', 3600);   //SESSION 生存时长 
//类定义 
class My_Sess  
{  
function init()  
    {  
$domain = '.infor96.com';  
//不使用 GET/POST 变量方式 
ini_set('session.use_trans_sid',    0);  
//设置垃圾回收最大生存时间 
ini_set('session.gc_maxlifetime',   MY_SESS_TIME);  
//使用 COOKIE 保存 SESSION ID 的方式 
ini_set('session.use_cookies',      1);  
ini_set('session.cookie_path',      '/');  
//多主机共享保存 SESSION ID 的 COOKIE 
ini_set('session.cookie_domain',    $domain);  
//将 session.save_handler 设置为 user，而不是默认的 files 
        session_module_name('user');  
//定义 SESSION 各项操作所对应的方法名： 
        session_set_save_handler(  
array('My_Sess', 'open'),   //对应于静态方法 My_Sess::open()，下同。 
array('My_Sess', 'close'),  
array('My_Sess', 'read'),  
array('My_Sess', 'write'),  
array('My_Sess', 'destroy'),  
array('My_Sess', 'gc')  
        );  
    }   //end function 
function open($save_path, $session_name) {  
return true;  
    }   //end function 
function close() {  
global $MY_SESS_CONN;  
if ($MY_SESS_CONN) {    //关闭数据库连接 
$MY_SESS_CONN->Close();  
        }  
return true;  
    }   //end function 
function read($sesskey) {  
global $MY_SESS_CONN;  
$sql = 'SELECT data FROM sess WHERE sesskey=' . $MY_SESS_CONN->qstr($sesskey) . ' AND expiry>=' . time();  
$rs =& $MY_SESS_CONN->Execute($sql);  
if ($rs) {  
if ($rs->EOF) {  
return ";  
            } else {    //读取到对应于 SESSION ID 的 SESSION 数据 
$v = $rs->fields[0];  
$rs->Close();  
return $v;  
            }   //end if 
        }   //end if 
return ";  
    }   //end function 
function write($sesskey, $data) {  
global $MY_SESS_CONN;  
$qkey = $MY_SESS_CONN->qstr($sesskey);  
$expiry = time() + My_SESS_TIME;    //设置过期时间 
//写入 SESSION 
$arr = array(  
'sesskey' => $qkey,  
'expiry'  => $expiry,  
'data'    => $data);  
$MY_SESS_CONN->Replace('sess', $arr, 'sesskey', $autoQuote = true);  
return true;  
    }   //end function 
function destroy($sesskey) {  
global $MY_SESS_CONN;  
$sql = 'DELETE FROM sess WHERE sesskey=' . $MY_SESS_CONN->qstr($sesskey);  
$rs =& $MY_SESS_CONN->Execute($sql);  
return true;  
    }   //end function 
function gc($maxlifetime = null) {  
global $MY_SESS_CONN;  
$sql = 'DELETE FROM sess WHERE expiry<' . time();  
$MY_SESS_CONN->Execute($sql);  
//由于经常性的对表 sess 做删除操作，容易产生碎片， 
//所以在垃圾回收中对该表进行优化操作。 
$sql = 'OPTIMIZE TABLE sess';  
$MY_SESS_CONN->Execute($sql);  
return true;  
    }   //end function 
}   ///:~ 
//使用 ADOdb 作为数据库抽象层。 
require_once('adodb/adodb.inc.php');  
//数据库配置项，可放入配置文件中（如：config.inc.php）。 
$db_type = 'mysql';  
$db_host = '192.168.212.1';  
$db_user = 'sess_user';  
$db_pass = 'sess_pass';  
$db_name = 'sess_db';  
//创建数据库连接，这是一个全局变量。 
$GLOBALS['MY_SESS_CONN'] =& ADONewConnection($db_type);  
$GLOBALS['MY_SESS_CONN']->Connect( $db_host, $db_user, $db_pass, $db_name);  
//初始化 SESSION 设置，必须在 session_start() 之前运行！！ 
My_Sess::init();  
?>  

第二个问题，需要对cookie的域进行设置， 默认情况下，COOKIE 的域是当前服务器的域名/IP 地址，而域不同的话，各个服务器所设置的 COOKIE 是不能相互访问的，如 www.aaa.com 的服务器是不能读写 www.bbb.com 服务器设置的 COOKIE 的。这里我们所说的同一网站的服务器有其特殊性，那就是他们同属于同一个一级域。


<?php  
ini_set('session.cookie_domain', 'a.com');  
?>  
这样即可设置程序中的cookie域统一为http://a.com
```
[逆天的量化交易分析库-tushare](http://mp.weixin.qq.com/s?timestamp=1490513733&src=3&ver=1&signature=nJT*vnzBLuHO*WXF7liSKhDMPrRE2*GI8qjPL-WcMzGkC54wsfjYRn3s0Yo*mShbut1h-t5wZ6rObADXBxf0HLmWuyV85i14iEqKZb0s*0D*AcCZH7YjEDq0s0LbQIzi777ZM7Iq8oNUKXRMBRARiGq1lkUT0m6l265aDtLNp5I=)
 大邓 大邓带你玩python获取个股历史交易数据（包括均线数据）
import tushare as ts
#获得格力电器（000651）的历史交易数据
ts.get_hist_data('000651') #获取  格力电器  月k线图数据
ts.get_hist_data('000651',ktype='M')
[Python 编码为什么那么蛋疼](https://mp.weixin.qq.com/s?__biz=MjM5MzgyODQxMQ==&mid=2650366836&idx=1&sn=da43cd0208b6bb7b1c51c5ced3ac1027&chksm=be9cd82089eb5136830ba25a54ae57a5fc1ca105b68718fcf4d9f100ddb1ea18120990c47816&mpshare=1&scene=1&srcid=0322qLLgwIialacWUum1Na3P&pass_ticket=3YDDPMla3NLdWBObiZjW%2FWHyR8mvcOpq8zaEHFmLVa95m661cMsN7dyQ49FT96Du#rd)
```js
key 不存在时，get 默认返回 None
Python3 一共有33个关键字。
>>> import __hello__
Hello World...

>>> import keyword
>>> print(keyword.kwlist)
['False', 'None', 'True', 'and', 'as', 'assert', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
刘志军 Python之禅
用编辑器打开的文本，看到的一个个字符，最终保存在磁盘的时候都是以二进制字节序列形式存起来的。那么从字符到字节的转换过程就叫做编码（encode），反过来叫做解码（decode），两者是一个可逆的过程。编码是为了存储传输，解码是为了方便显示阅读。Python2 使用 ASCII 字符编码作为默认编码方式，而 ASCII 不能处理中文，
Python2 把字符串分为 unicode 和 str 两种类型。本质上 str 是一串二进制字节序列，下面的示例代码可以看出 str 类型的 “禅” 打印出来是十六进制的 \xec\xf8 ，对应的二进制字节序列就是 ‘11101100 11111000’。

>>> s = '禅'
>>> s
'\xec\xf8'
>>> type(s)
<type 'str'>
而 unicode 类型的 u”禅” 对应的 unicode 符号是 u’\u7985’

>>> u = u"禅"
>>> u
u'\u7985'
>>> type(u)
<type 'unicode'>
我们要把 unicode 符号保存到文件或者传输到网络就需要经过编码处理转换成 str 类型，于是 python 提供了 encode 方法，从 unicode 转换到 str，反之亦然。
str 本质上其实是一串二进制数据，而 unicode 是字符（符号），编码（encode）就是把字符（符号）转换为 二进制数据的过程，因此 unicode 到 str 的转换要用 encode 方法，反过来就是用 decode 方法。
# -*- coding:utf-8 -*-
def main():
    name = u'Python之禅'
    f = open("output.txt", "w")
    f.write(name)
>>> u"Python之禅".encode("ascii")

```

[Python 有哪些好玩的语法糖？](https://www.zhihu.com/question/57470958)
```js
 c = [b,a][a>b]   
 [P1, P2, P3, ...Pn].sort(key=lambda x: (x.grade, x.height))
把需要排序的属性拿出来作为一个 tuple，主要的放前面，次要的放后面。因为 Python 在比较 tuple 大小的时候正是按字典序进行的

lst = [1, -2, 10, -12, -4, -5, 9, 2]
还是排序，我们希望把正的放前面，负的放后面，并且分别按绝对值从小到大。即输出：[1, 2, 9, 10, -2, -4, -5, -12]
最简单的方法是：lst.sort(key=lambda x: (x < 0, abs(x)))
对于列表形如list_1 = [[1, 2], [3, 4, 5], [6, 7], [8], [9]]转化成列表list_2 = [1, 2, 3, 4, 5, 6, 7, 8, 9]的问题。一般方法list_1 = [[1, 2], [3, 4, 5], [6, 7], [8], [9]]
list_2 = []
for _ in list_1:
    list_2 += _
print(list_2)
list_1 = [[1, 2], [3, 4, 5], [6, 7], [8], [9]]
[i for k in list_1 for i in k]
 list_1 = [[1, 2], [3, 4, 5], [6, 7], [8], [9]]
sum(list_1, [])
 itertools.chain(*list_1)
 from numpy import array
array(list_1).flatten().tolist()
 
 去除小写字母

s=filter(lambda x:not str(x).islower(),"asdasfAsfBsdfC")
for ch in s:
    print(ch)
map函数接受的参数类型与filter类似，它用于把函数作用于可遍历对象的每一个元素。类似于数学中映射的概念。

例：

求y=2x+1（偷偷用了一下range函数生成定义域）

s=map(lambda x:2*x+1,range(6))
for x in s:
    print(x)
reduce函数对每个元素作累计操作，它接受的第一个参数必须是有两个参数的函数。

例：

求和

from functools import reduce
s=reduce(lambda x,y:x+y,range(1,6))
print(s)
求乘积（第三个可选参数表示累计变量的初值）

from functools import reduce
s=reduce(lambda x,y:x*y,range(1,6),1)
print(s)
柯里化(curry)函数
如果一个函数需要２个参数，而你只传入一个参数，那么你就可以得到一个柯里化的函数，这是函数式编程语言的重要特性之一，遗憾的是，python并不能在语法层面支持柯里化调用，但它在库中提供了接口。

例：

*3函数

f_mul=lambda x,y:x*y
from functools import partial
mul3=partial(f_mul,3)
print(mul3(1))
print(mul3(6))
打包与解包
有点类似于函数式中的模式匹配，略牵强。

t=(1,2,3)
x,y,z=t
列表生成式
这个也有点牵强，不知道严格意义上讲属不属于函数式风格。

例：生成奇数序列

l=[2*x+1 for x in range(10)]
for i in l:
    print(i)
最后来一个彩蛋（以前某答主提到的用调分函数来美颜的算法，忘了出处了，侵删）

from PIL import Image
from math import sqrt

im = Image.open("a.jpg")
ret= im.convert(mode="RGB")
ret = ret.point(lambda x:sqrt(x)*sqrt(255))
ret.save("b.jpg")
把点坐标拆成两个list，matpotlib有的时候画图很有用

例如(x1,y1),(x2,y2),...变成(x1,x2,x3....)和(y1,y2,y3,...)

x,y=zip(*original_list)
numbers = [1, 2, 3, 4, 5]
one, *_, five = numbers
if cond1:
    res = expr1
elif cond2:
    res = expr2
else:
    res = expr3
这样冗长的代码结构可以使用a if cond else b 加上 \ 续行化简得非常优雅。

res = \
    expr1 if cond1 else \
    expr2 if cond2 else \
    expr3
```
[苹果核 - 揭秘 Github 上那些开源项目的 star 数](http://pingguohe.net/2017/03/19/counting-stars-on-github.html?utm_source=tuicool&utm_medium=referral)
https://github.com/longerian/github_stat 
如何向开源项目提交无法解答的问题 https://zhuanlan.zhihu.com/p/25795393 我为莆田系代言-把这款插件推广到五湖四海https://zhuanlan.zhihu.com/p/25963120  http://link.zhihu.com/?target=https%3A//chrome.google.com/webstore/detail/%25E8%258E%2586%25E7%2594%25B0%25E7%25B3%25BB%25E5%258C%25BB%25E9%2599%25A2%25E7%25BD%2591%25E7%25AB%2599%25E6%258F%2590%25E9%2586%2592/pihadmdiehanenijehoohjnpiaofmmng  http://link.zhihu.com/?target=http%3A//open-power-workgroup.github.io/Hospital/data/draft1/html/hospitals.html  
LAMP兄弟连视频下载地址：免费PHP视频教程下载-LAMP兄弟连PHP培训教程学习网；

传智播客视频下载地址：免费php视频教程下载；

后盾网视频下载地址：后盾网论坛-php培训-php教程；

自学it网下载地址：PHP视频教程 自学it网
[10行Python代码的词云](https://mp.weixin.qq.com/s?src=3&timestamp=1490443479&ver=1&signature=lhZ*wr*weZ9H-AfJ8rGBjnr2vX5sf3CjTNRB3tsnZy1B4eblmctUb6dOzThK56vllCncngSLMbNnDwoMpKFdAAsH4Q8uc61emzAvBsgfqf6qNoOrPhqlegYQ3Fa8Pxh0TZbq6X4WToGETo4tSLoKwzP5r0gwbQinfBjtujmfxu8=)
老曹 喔家ArchiSelf
```js
import matplotlib.pyplot as plt
from wordcloud import WordCloud
import jieba

text_from_file_with_apath = open('/Users/hecom/23tips.txt').read()

wordlist_after_jieba = jieba.cut(text_from_file_with_apath, cut_all = True)
wl_space_split = " ".join(wordlist_after_jieba)

my_wordcloud = WordCloud().generate(wl_space_split)

plt.imshow(my_wordcloud)
plt.axis("off")
plt.show()

直接进入wordcloud.py 的源码，找字体库相关的代码

FONT_PATH = os.environ.get("FONT_PATH", os.path.join(os.path.dirname(__file__), "DroidSansMono.ttf"))
wordcloud 默认使用了DroidSansMono.ttf 字体库，改一下换成一个支持中文的ttf 字库

from PIL import Image
import numpy as np
abel_mask = np.array(Image.open("/Users/hecom/chw.png"))
在构造函数的时候，将mask传递进去即可：

background_color="black", mask=abel_mask
```
[Python批量判断IP地址所属地区]()
```js
from random import randrange
from netaddr import IPRange

def ipRangeTest(ipAddr, ipRange):
    # 遍历IP地址与地区分布对应关系字典
    # 如果ipAddr在某个地区的IP段内
    # 返回该地区名称
    for key, value in ipRange.items():
        if ipAddr in value:
            return key
    return 'unknown'

# 可以根据实际情况替换这个字典的内容
# 或从IP地址库中读入信息
ipRange = {'area1':IPRange('10.2.1.0', '10.2.1.255'),
           'area2':IPRange('10.2.2.0', '10.2.2.255'),
           'area3':IPRange('10.3.0.0', '10.3.255.50'),
           'area4':IPRange('11.1.0.0', '11.1.0.255')}

# 测试
for _ in range(10):
    a = randrange(9,12)
    b = randrange(1,4)
    c = randrange(4)
    d = randrange(256)
    ipAddr = '.'.join(map(str, (a,b,c,d)))
    print(ipAddr, ipRangeTest(ipAddr,ipRange))

部分运行结果：
9.2.3.40 unknown
10.1.3.67 unknown
11.1.1.54 unknown
9.1.2.243 unknown
9.3.2.182 unknown
10.3.0.30 area3
9.1.1.58 unknown
11.1.2.205 unknown
10.3.2.179 area3
11.3.1.240 unknown
```
浮点数 
>>>from decimal import *
# 设置精度为 7 位
>>>getcontext().prec = 7
>>>Decimal(1) / Decimal(7)
Decimal('0.1428571')
[爬虫神器-selenium](https://zhuanlan.zhihu.com/p/25981552)
```js
from selenium import webdriver

from bs4 import BeautifulSoup

初始化浏览器

driver = webdriver.Firefox()

打开某个网址

driver.get(url)

如果网站需要输入登录账号密码

这里用到firepath找到目标位置的xpath

找到输入账号框，清除框内信息，再输入你的账号

driver.find_element_by_xpath(xpath).clear()

driver.find_element_by_xpath(xpath).send_keys("你的账号")

找到输入密码框，清除框内信息，再输入你的密码

driver.find_element_by_xpath(xpath).clear()

driver.find_element_by_xpath(xpath).send_keys("你的密码")

定位“点击登录”框的位置的xpath，执行登录

driver.find_element_by_xpath(xpath).click()

访问你想爬的网页的网址

driver.get(url)

获取该网页的源码

html = driver.page_source

BeautifulSoup定位标签  视频地址http://v.qq.com/vplus/bd8acb3d0418431a6f356522325b0902
bsObj = BeautifulSoup（html，‘html.parser’）
```
[Python爬虫—破解JS加密的Cookie](https://zhuanlan.zhihu.com/p/25957793)
```js
首次请求没有Cookie，服务端回返回一段生成Cookie并自动刷新的JS代码。浏览器拿到代码能够成功执行，带着新的Cookie再次请求获取数据。而Python拿到这段代码就只能停留在第一步。
作者：Jerry
链接：https://zhuanlan.zhihu.com/p/25957793
来源：知乎
著作权归作者所有，转载请联系作者获得授权。

import re
import PyV8
import requests

TARGET_URL = "http://www.kuaidaili.com/proxylist/1/"

def getHtml(url, cookie=None):
    header = {
        "Host": "www.kuaidaili.com",
        'Connection': 'keep-alive',
        'Cache-Control': 'max-age=0',
        'Upgrade-Insecure-Requests': '1',
        'User-Agent': 'Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/49.0.2623.87 Safari/537.36',
        'Accept': 'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8',
        'Accept-Encoding': 'gzip, deflate, sdch',
        'Accept-Language': 'zh-CN,zh;q=0.8',
    }
    html = requests.get(url=url, headers=header, timeout=30, cookies=cookie).content
    return html

def executeJS(js_func_string, arg):
    ctxt = PyV8.JSContext()
    ctxt.enter()
    func = ctxt.eval("({js})".format(js=js_func_string))
    return func(arg)

def parseCookie(string):
    string = string.replace("document.cookie='", "")
    clearance = string.split(';')[0]
    return {clearance.split('=')[0]: clearance.split('=')[1]}

# 第一次访问获取动态加密的JS
first_html = getHtml(TARGET_URL)

# first_html = """
# <html><body><script language="javascript"> window.onload=setTimeout("lu(158)", 200); function lu(OE) {var qo, mo="", no="", oo = [0x64,0xaa,0x98,0x3d,0x56,0x64,0x8b,0xb0,0x88,0xe1,0x0d,0xf4,0x99,0x31,0xd8,0xb6,0x5d,0x73,0x98,0xc3,0xc4,0x7a,0x1e,0x38,0x9d,0xe8,0x8d,0xe4,0x0a,0x2e,0x6c,0x45,0x69,0x41,0xe5,0xd0,0xe5,0x11,0x0b,0x35,0x7b,0xe4,0x09,0xb1,0x2b,0x6d,0x82,0x7c,0x25,0xdd,0x70,0x5a,0xc4,0xaa,0xd3,0x74,0x98,0x42,0x3c,0x60,0x2d,0x42,0x66,0xe0,0x0a,0x2e,0x96,0xbb,0xe2,0x1d,0x38,0xdc,0xb1,0xd6,0x0e,0x0d,0x76,0xae,0xc3,0xa9,0x3b,0x62,0x47,0x40,0x15,0x93,0xb7,0xee,0xc3,0x3e,0xfd,0xd3,0x0d,0xf6,0x61,0xdc,0xf1,0x2c,0x54,0x8c,0x90,0xfa,0x24,0x5b,0x83,0x0c,0x75,0xaf,0x18,0x01,0x7e,0x68,0xe0,0x0a,0x72,0x1e,0x88,0x33,0xa7,0xcc,0x31,0x9b,0xf3,0x1a,0xf2,0x9a,0xbf,0x58,0x83,0xe4,0x87,0xed,0x07,0x7e,0xe2,0x00,0xe9,0x92,0xc9,0xe8,0x59,0x7d,0x56,0x8d,0xb5,0xb2,0x6c,0xe0,0x49,0x73,0xfc,0xe7,0x20,0x49,0x34,0x09,0x71,0xeb,0x60,0xfd,0x8e,0xad,0x0f,0xb9,0x2e,0x77,0xdc,0x74,0x9b,0xbf,0x8f,0xa5,0x8d,0xb8,0xb0,0x06,0xac,0xc5,0xe9,0x10,0x12,0x77,0x9b,0xb1,0x19,0x4e,0x64,0x5c,0x00,0x98,0xc6,0xed,0x98,0x0d,0x65,0x11,0x35,0x9e,0xf4,0x30,0x93,0x4b,0x00,0xab,0x20,0x8f,0x29,0x4f,0x27,0x8c,0xc2,0x6a,0x04,0xfb,0x51,0xa3,0x4b,0xef,0x09,0x30,0x28,0x4d,0x25,0x8e,0x76,0x58,0xbf,0x57,0xfb,0x20,0x78,0xd1,0xf7,0x9f,0x77,0x0f,0x3a,0x9f,0x37,0xdb,0xd3,0xfc,0x14,0x39,0x11,0x3b,0x94,0x8c,0xad,0x8e,0x5c,0xd3,0x3b];qo = "qo=251; do{oo[qo]=(-oo[qo])&0xff; oo[qo]=(((oo[qo]>>4)|((oo[qo]<<4)&0xff))-0)&0xff;} while(--qo>=2);"; eval(qo);qo = 250; do { oo[qo] = (oo[qo] - oo[qo - 1]) & 0xff; } while (-- qo >= 3 );qo = 1; for (;;) { if (qo > 250) break; oo[qo] = ((((((oo[qo] + 200) & 0xff) + 121) & 0xff) << 6) & 0xff) | (((((oo[qo] + 200) & 0xff) + 121) & 0xff) >> 2); qo++;}po = ""; for (qo = 1; qo < oo.length - 1; qo++) if (qo % 5) po += String.fromCharCode(oo[qo] ^ OE);eval("qo=eval;qo(po);");} </script> </body></html>
# """

# 提取其中的JS加密函数
js_func = ''.join(re.findall(r'(function .*?)</script>', first_html))

print 'get js func:\n', js_func

# 提取其中执行JS函数的参数
js_arg = ''.join(re.findall(r'setTimeout\(\"\D+\((\d+)\)\"', first_html))

print 'get ja arg:\n', js_arg

# 修改JS函数，使其返回Cookie内容
js_func = js_func.replace('eval("qo=eval;qo(po);")', 'return po')

# 执行JS获取Cookie
cookie_str = executeJS(js_func, js_arg)

# 将Cookie转换为字典格式
cookie = parseCookie(cookie_str)

print cookie

# 带上Cookie再次访问url,获取正确数据
print getHtml(TARGET_URL, cookie)[0:500]


```
[想知道大家都用python写过哪些有趣的脚本?](https://www.zhihu.com/question/28661987/answer/152739366)
https://link.zhihu.com/?target=https%3A//github.com/lzjun567/crawler_html2pdf/blob/master/pdf/crawler.py
[23家互联网名企的300多篇精华笔经面经，免费领取](https://zhuanlan.zhihu.com/p/25863996)
[35岁HR告诉你，如何正确的写简历（附12款精美模板）](https://zhuanlan.zhihu.com/p/25953536)
[国内有没有适合青少年观看的性教育视频？](https://www.zhihu.com/question/47016153/answer/104716432)
[提问的智慧 - 中文版](https://link.zhihu.com/?target=http%3A//doc.zengrong.net/smart-questions/cn.html)
https://link.zhihu.com/?target=https%3A//ryancao.gitbooks.io/php-developer-prepares/content/assets/smart-questions-cn.jpg
https://link.zhihu.com/?target=http%3A//study.163.com/topics/sexuality-education/
[10分钟python图表绘制 | seaborn入门（四）：回归模型lmplot](https://zhuanlan.zhihu.com/p/25909753)
pip install seaborn 
```js

import seaborn as sns
sns.set_style("whitegrid")
tips = sns.load_dataset("tips") #载入自带数据集
#研究小费tips与总消费金额total_bill在吸烟与不吸烟人之间的关系

g = sns.lmplot(x="total_bill", y="tip", hue="smoker", data=tips,palette="Set1")

#继续研究pokemon数据集
import pandas as pd
import seaborn as sns
pokemon=pd.read_csv('H:/zhihu/Pokemon.csv')
pokemon.head()
```

[奇舞学院 推出的视频](https://link.zhihu.com/?target=http%3A//t.75team.com/video)
[知乎看片-指日可待 ： 如何优雅的“轮带逛”初级篇——获取单张图片](https://zhuanlan.zhihu.com/p/25936300)
[Python 程序如何高效地调试？](https://www.zhihu.com/question/21572891/answer/153088414)
```js
有两种不同的方法启动Python调试器，一种直接在命令行参数指定使用pdb模块启动Python文件，如下所示：

python -m pdb test_pdb.py 
另一种方法是在Python代码中，调用pdb模块的set_trace方法设置一个断点，当程序运行自此时，将会暂停执行并打开pdb调试器。

#/usr/bin/python
from __future__ import print_function
import pdb

def sum_nums(n):
    s=0
    for i in range(n):
        pdb.set_trace()
        s += i
        print(s)

if __name__ == '__main__':
    sum_nums(5)
```
[深度学习方面的学术交流平台？](https://link.zhihu.com/?target=https%3A//jizhi.im/community)
今天上线了新功能，社区帖子中也可以插入在线Python运行环境，这样在交流PY的时候，不仅可以show me the code，还可以run the code, see the output https://www.zhihu.com/question/54749093/answer/153175713  
[快来get新技能--抓包+cookie,爬微博不再是梦](https://mp.weixin.qq.com/s?__biz=MzI1MTE2ODg4MA==&mid=2650068076&idx=1&sn=9306af74c6fc6edc98906101c3d8c1ee&chksm=f1f76573c680ec652e4a3a313535e1e16c28b6b4484a9b35bc55e8bcb132f8194893d28170da&scene=21#wechat_redirect)
r  = requests.get(url,cookiess = Cookie)
[记忆转换工具](https://faded12.github.io/conversion/)
https://zhuanlan.zhihu.com/p/25865945 
[有哪些好看的婚礼请柬？](https://www.zhihu.com/question/22406901/answer/152969274)

[求职必胜，提升面试成功率靠谱攻略](https://zhuanlan.zhihu.com/p/25975370)
[新媒体运营工具盘点](https://zhuanlan.zhihu.com/p/25477198)

[用python实现简单的文本情感分析](https://mp.weixin.qq.com/s?__biz=MzI1MTE2ODg4MA==&mid=2650067952&idx=1&sn=4dc4b061db10b68f9154eadc4fe24e51&chksm=f1f762efc680ebf9ba3c92b731bbe56272a3513c0608d83bc4c2350f6f3abadd894bc2fc7ce6&scene=21#wechat_redirect)

[计算中文混合字符串长度（二）](http://blog.csdn.net/zhouzme/article/details/18909553)
```js
将字符串转换为 一个中文为 1，一个英文、数字 为 0.5 ，取最大整数长度值，类似腾讯微博计算字数长度方式
function asGbkLength($str, $fromEncode = 'utf-8')  
{  
    return ceil(strlen(mb_convert_encoding($str, 'gbk', $fromEncode))/2);  
}  
$str = 'abcd计算字符串长度12345';  
echo $str;  
echo '<br>';  
echo asGbkLength($str); // 12  
/** 
 * 计算字符串的字符长度，默认为 utf-8 编码, 一个中文算 3个字符长度, gbk 则是 2个字符长度 
 * @param string str 检测的字符串 
 * @param integer step 字符编码长度, utf-8 为3 , gbk 为 2 
 * @return integer 
 */  
function myStrlen(str, step) {   
    var len = str.length;   
    var reLen = 0;  
    step = step ? step : 3;  
    for (var i = 0; i < len; i++) {          
        if (str.charCodeAt(i) < 27 || str.charCodeAt(i) > 126) {   
            reLen += step; // 全角  
        } else {   
            reLen++;   
        }   
    }   
    return reLen;  
}  
function asGbkLength(str)  
{  
    return Math.ceil(myStrlen(str, 2)/2);  
}  
计算包含中文的混合字符串长度，一个中文、英文、数字 均为 1
function resolveContainCn($string, $charset = 'utf-8')  
{  
    if ($string == '') {  
        return '';  
    }  
           
    if ($charset == 'utf-8') {  
        $pa = "/[\x01-\x7f]|[\xc2-\xdf][\x80-\xbf]|\xe0[\xa0-\xbf][\x80-\xbf]|[\xe1-\xef][\x80-\xbf][\x80-\xbf]|\xf0[\x90-\xbf][\x80-\xbf][\x80-\xbf]|[\xf1-\xf7][\x80-\xbf][\x80-\xbf][\x80-\xbf]/";  
    }  
    else {  
        $pa = "/[\x01-\x7f]|[\xa1-\xff][\xa1-\xff]/";  
    }  
    $matches = array();  
    preg_match_all($pa, $string, $matches);  
    return $matches[0];  
}  
function strlenCn($string, $charset = 'utf-8')  
{  
    if (function_exists('mb_strlen')) {  
        return mb_strlen($string, $charset);  
    }  
    return count(resolveContainCn($string, $charset));  
}  
$str = 'abcd计算字符串长度12345';  
echo $str;  
echo '<br>';  
echo strlenCn($str); // 16 
```
[PHP高效获取远程图片尺寸和大小](http://blog.csdn.net/zhouzme/article/details/18902113)
```js
function myGetImageSize($url, $type = 'curl', $isGetFilesize = false)   
{  
    // 若需要获取图片体积大小则默认使用 fread 方式  
    $type = $isGetFilesize ? 'fread' : $type;  
   
     if ($type == 'fread') {  
        // 或者使用 socket 二进制方式读取, 需要获取图片体积大小最好使用此方法  
        $handle = fopen($url, 'rb');  
   
        if (! $handle) return false;  
   
        // 只取头部固定长度168字节数据  
        $dataBlock = fread($handle, 168);  
    }  
    else {  
        // 据说 CURL 能缓存DNS 效率比 socket 高  
        $ch = curl_init($url);  
        // 超时设置  
        curl_setopt($ch, CURLOPT_TIMEOUT, 5);  
        // 取前面 168 个字符 通过四张测试图读取宽高结果都没有问题,若获取不到数据可适当加大数值  
        curl_setopt($ch, CURLOPT_RANGE, '0-167');  
        // 跟踪301跳转  
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, 1);  
        // 返回结果  
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);  
   
        $dataBlock = curl_exec($ch);  
   
        curl_close($ch);  
   
        if (! $dataBlock) return false;  
    }  
   
    // 将读取的图片信息转化为图片路径并获取图片信息,经测试,这里的转化设置 jpeg 对获取png,gif的信息没有影响,无须分别设置  
    // 有些图片虽然可以在浏览器查看但实际已被损坏可能无法解析信息   
    $size = getimagesize('data://image/jpeg;base64,'. base64_encode($dataBlock));  
    if (empty($size)) {  
        return false;  
    }  
   
    $result['width'] = $size[0];  
    $result['height'] = $size[1];  
   
    // 是否获取图片体积大小  
    if ($isGetFilesize) {  
        // 获取文件数据流信息  
        $meta = stream_get_meta_data($handle);  
        // nginx 的信息保存在 headers 里，apache 则直接在 wrapper_data   
        $dataInfo = isset($meta['wrapper_data']['headers']) ? $meta['wrapper_data']['headers'] : $meta['wrapper_data'];  
   
        foreach ($dataInfo as $va) {  
            if ( preg_match('/length/iU', $va)) {  
                $ts = explode(':', $va);  
                $result['size'] = trim(array_pop($ts));  
                break;  
            }  
        }  
    }  
   
    if ($type == 'fread') fclose($handle);  
   
    return $result;  
}  
   
// 测试的图片链接  
echo '<pre>';  
$result = myGetImageSize('http://s6.mogujie.cn/b7/bao/120630/2kpa6_kqywusdel5bfqrlwgfjeg5sckzsew_345x483.jpg_225x999.jpg', 'curl');  
print_r($result); 
```
[MySQL字段自增自减的SQL语句](http://blog.csdn.net/zhouzme/article/details/18909469)
通常情况下是可以类似上面自增的方法 把 +号 改成 -号 就行了，但问题是如果当前 comments 统计数值为 0 时 再做减法将会变成该字段类型的最大数值 65535
update `info` set `comments` = IF(`comments`< 1,0,`comments`-1) WHERE `id` = 32  
update `info` set `comments` = IF(`comments`<1, 0, `comments`-1) WHERE `id` = 32  
[给 phper 出一道基本的面试题](https://www.v2ex.com/t/349774)
```js
echo '6+5' . 9+7; 13 实际 计算为 6+7 
和 “ 123abc ” +1 输出结果为 int 124 一个性质  // ‘ 6+59 ’+7=6+7=13
例子里的 ((int)'6+1') == intval('6+1') == 6 。从其他语言的叫都上来看完全属于设计不合理，因为会导致混乱。 

试想如果你想严格判断整数输入的话，只能在 intval 转换前再加上一些格式判断，否则甚至可能就会导致安全问题（比如 var_dump('0e1' == '0e2') => true ）。
class A{ 
public $bar = 1; 
public $c = 2; 
} 
$a = new A(); 
$bar = ['baz'=>'c']; 
echo $a->$bar['baz']; 

@moult 
js 嘛，坑多了去了 
比如这个 
if([]){alert(0);}; 
if([]==false){alert(1);}; 
if(![]==false){alert(2);};
1. 126 

php -r 'echo '6+5' . 9 + 7;' 

相当于 intval('11' . '9') + 7 


2. 13 

php -r "echo '6+5' . 9 + 7;" 

相当于 '6+59' + 7 = 6 + 7 ，运行会报警 Notice: A non well formed numeric value encountered ，说明有碰到这种非预期的数值转化，可能有 bug 。 


3. syntax error 

php -r "echo '6+5'.9 + 7;" 

报错 PHP Parse error: syntax error, unexpected '.9' (T_DNUMBER), expecting ',' or ';' in Command line code on line 1 
『.9 』 被当成符号了， echo 后面只支持 『,』和『;』


```
[ 将int，bigint整型数值可逆转换字符串](http://blog.csdn.net/zhouzme/article/details/51098101)
如： 9223372036854775807 => aZl8N0y58M7
```js
class Convert
{
    /**
     * 默认密钥字符串
     * @var string
     */
    const KEY = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';

    /**
     * 将 Int 类型十进制数值转换为指定进制编码
     * @param int|string $num 取值范围 0 ~ 2147483647 之间
     * @return string
     */
    public static function encodeInt($num) {
        $str = '';
        if ($num <= 0)
            $str = substr(self::KEY, 0, 1);
        while ($num > 0) {
            $val = intval($num / 62);
            $mod = $num % 62;
            $str = substr(self::KEY, $mod, 1) . $str;
            $num = $val;
        }
        return $str;
    }

    /**
     * 将编码字符串转换为 Int 类整型数值
     * @param string $code
     * @return int
     */
    public static function decodeInt($code){
        $result = null;
        $len = strlen($code);
        for ($i = 1; $i <= $len; $i++) {
            $char = substr($code, $i - 1, 1);
            $result += intval(strpos(self::KEY, $char)) * pow(62, $len - $i);
        }
        return $result;
    }

    /**
     * 支持15位长度的整型，超过则精度大幅降低
     * @param int $num
     * @return string
     */
    public static function encodeInt2($num) {
        $out = '';
        for ($t = floor(log10($num)/log10(62)); $t >= 0; $t--) {
            $a = floor($num/bcpow(62, $t));
            $out = $out . substr(self::KEY, $a, 1);
            $num = $num - $a * pow(62, $t);
        }
        return $out;
    }

    /**
     * 支持最大15位整型字符串的解码
     * @param string $num
     * @return string
     */
    public static function decodeInt2($num) {
        $out = 0;
        $len = strlen($num) - 1;
        for ($t = 0; $t <= $len; $t++) {
            $out = $out + strpos(self::KEY, substr( $num, $t, 1 )) * pow(62, $len - $t);
        }
        return $out;
    }

    /**
     * 将 BigInt 类型的数值转换为指定进制值
     * @param int|string $num
     * @return string
     */
    public static function encodeBigInt($num) {
        bcscale(0);
        $str = '';
        if ($num <= 0)
            $str = substr(self::KEY, 0, 1);
        while ($num > 0) {
            $div = bcdiv($num, 62);
            $mod = bcmod($num, 62);
            $str = substr(self::KEY, $mod, 1) . $str;
            $num = $div;
        }
        return $str;
    }

    /**
     * 将编码字符串转换为 BigInt 类整型数值
     * @param string $code
     * @return string
     */
    public static function decodeBigInt($code) {
        bcscale(0);
        $result = '';
        $len = strlen($code);
        for ($i = 1; $i <= $len; $i++) {
            $char = substr($code, $i - 1, 1);
            $result = bcadd(bcmul(strpos(self::KEY, $char), bcpow(62, $len - $i)), $result);
        }
        return $result;
    }
}
```

[PHP不使用递归的无限级分类](http://blog.csdn.net/zhouzme/article/details/50097669)
```js

$list = array(
    array('id'=>1, 'pid'=>0, 'deep'=>0, 'name'=>'test1'),
    array('id'=>2, 'pid'=>1, 'deep'=>1, 'name'=>'test2'),
    array('id'=>3, 'pid'=>0, 'deep'=>0, 'name'=>'test3'),
    array('id'=>4, 'pid'=>2, 'deep'=>2, 'name'=>'test4'),
    array('id'=>5, 'pid'=>2, 'deep'=>2, 'name'=>'test5'),
    array('id'=>6, 'pid'=>0, 'deep'=>0, 'name'=>'test6'),
    array('id'=>7, 'pid'=>2, 'deep'=>2, 'name'=>'test7'),
    array('id'=>8, 'pid'=>5, 'deep'=>3, 'name'=>'test8'),
    array('id'=>9, 'pid'=>3, 'deep'=>2, 'name'=>'test9'),
);
function resolve($list) {
    $newList = $manages = $deeps = $inDeeps = array();
    foreach ($list as $row) {
        $newList[$row['id']] = $row;
    }
    $list = null;
    foreach ($newList as $row) {
        if (! isset($manages[$row['pid']]) || ! isset($manages[$row['pid']]['children'][$row['id']])) {
            if ($row['pid'] > 0 && ! isset($manages[$row['pid']]['children'])) $manages[$row['pid']] = $newList[$row['pid']];
            $manages[$row['pid']]['children'][$row['id']] = $row;
        }
        if (! isset($inDeeps[$row['deep']]) || ! in_array($row['id'], $inDeeps[$row['deep']])) {
            $inDeeps[$row['deep']][] = array($row['pid'], $row['id']);
        }
    }
    krsort($inDeeps);
    array_shift($inDeeps);
    foreach ($inDeeps as $deep => $ids) {
        foreach ($ids as $m) {
            // 存在子栏目的进行转移
            if (isset($manages[$m[1]])) {
                $manages[$m[0]]['children'][$m[1]] = $manages[$m[1]];
                $manages[$m[1]] = null;
                unset($manages[$m[1]]);
            }
        }
    }
    return $manages[0]['children'];
}
function resolve2(& $list, $pid = 0) {
    $manages = array();
    foreach ($list as $row) {
        if ($row['pid'] == $pid) {
            $manages[$row['id']] = $row;
            $children = resolve2($list, $row['id']);
            $children && $manages[$row['id']]['children'] = $children;
        }
    }
    return $manages;
}
Array
(
    [1] => Array
        (
            [id] => 1
            [pid] => 0
            [deep] => 0
            [name] => test1
            [children] => Array
                (
                    [2] => Array
                        (
                            [id] => 2
                            [pid] => 1
                            [deep] => 1
                            [name] => test2
                            [children] => Array
                                (
                                    [4] => Array
                                        (
                                            [id] => 4
                                            [pid] => 2
                                            [deep] => 2
                                            [name] => test4
                                        )

                                    [5] => Array
```
[PHP5.6通过CURL上传图片@符无效的兼容问题](http://blog.csdn.net/zhouzme/article/details/51050980)
```js
CURL 的一个配置参数 CURLOPT_SAFE_UPLOAD 
CURLOPT_SAFE_UPLOAD 在 PHP5.5中默认值是 false 
而在 PHP5.6中已经默认为 true 了。 
所以只需要增加一行强制设置为 false 就行，如下： 
注意：该参数的设置顺序，必须在设置 CURLOPT_POSTFIELDS 参数之前才有效哦
$url = 'http://127.0.0.1/test3.php';
$file = __DIR__ .'/0634134726bc5b8b.jpg';
$data = array('mypic'=>new CURLFile($file));
$curl = curl_init();
curl_setopt($curl, CURLOPT_URL, $url);
curl_setopt($curl, CURLOPT_RETURNTRANSFER, true);
curl_setopt($curl, CURLOPT_POST, true);
curl_setopt($curl, CURLOPT_POSTFIELDS, $data);
$content = curl_exec($curl);
curl_close($curl);
print_r($content);
```
[PhpMyAdmin+Opcache出现无响应，500错误](http://blog.csdn.net/zhouzme/article/details/54345932)

设置 opcache 黑名单打开 php.ini 
搜索 blacklist_filename，设置为你的文件绝对路径就可以了，若没有则添加一条
[opcache]
opcache.blacklist_filename="C:/ProgramFiles(x86)/php_opcache_blacklist"
[ Windows RunHiddenConsole 后台运行 nginx，php，redis](http://blog.csdn.net/zhouzme/article/details/53613594)
start-redis.bat
C:\RunHiddenConsole\RunHiddenConsole redis-server.exe redis-union.conf --loglevel verbose 
[ PHP5.5在windows 安装使用 memcached 服务端的方法以及 php_memcache.dll 下载](http://blog.csdn.net/zhouzme/article/details/22231931)
[ phpDocumentor2安装配置和使用](http://blog.csdn.net/zhouzme/article/details/25816753)
[PHP截取含中文的混合字符串长度的函数](http://blog.csdn.net/zhouzme/article/details/18909537)
```js
/** 
 * 截取中文混合字符串指定长度 
 *  
 * @param string $string 
 * @param integer $length 
 * @param string $etc 超过长度时的省略符 
 * @param string $charset 字符编码 utf-8 或者 gbk 
 * @return string 
 */  
public function truncateCn($string, $length = 80, $etc = '...', $charset = 'utf-8')  
{  
    if ($length == 0) {  
        return '';  
    }  
         
    if (function_exists('mb_substr')) {  
        $etc = mb_strlen($string, $charset) > $length ? $etc : '';  
        return mb_substr($string, 0, $length, $charset) . $etc;  
    }  
         
    if ($charset == 'utf-8') {  
        $pa = "/[\x01-\x7f]|[\xc2-\xdf][\x80-\xbf]|\xe0[\xa0-\xbf][\x80-\xbf]|[\xe1-\xef][\x80-\xbf][\x80-\xbf]|\xf0[\x90-\xbf][\x80-\xbf][\x80-\xbf]|[\xf1-\xf7][\x80-\xbf][\x80-\xbf][\x80-\xbf]/";  
    }  
    else {  
        $pa = "/[\x01-\x7f]|[\xa1-\xff][\xa1-\xff]/";  
    }  
    preg_match_all($pa, $string, $t_string);  
    if (count($t_string[0]) > $length) {  
        return join('', array_slice($t_string[0], 0, $length)) . $etc;  
    }  
         
    return join('', array_slice($t_string[0], 0, $length));  
}  
```
[PHP全角半角转换函数](http://blog.csdn.net/zhouzme/article/details/18909523)
```js
/** 
  * 全角字符转换为半角 
  *  
  * @param string $str 
  * @return string 
  */  
 public function Sbc2Dbc($str)  
 {  
     $arr = array(  
             '０'=>'0', '１'=>'1', '２'=>'2', '３'=>'3', '４'=>'4','５'=>'5', '６'=>'6', '７'=>'7', '８'=>'8', '９'=>'9',   
             'Ａ'=>'A', 'Ｂ'=>'B', 'Ｃ'=>'C', 'Ｄ'=>'D', 'Ｅ'=>'E','Ｆ'=>'F', 'Ｇ'=>'G', 'Ｈ'=>'H', 'Ｉ'=>'I', 'Ｊ'=>'J',   
             'Ｋ'=>'K', 'Ｌ'=>'L', 'Ｍ'=>'M', 'Ｎ'=>'N', 'Ｏ'=>'O','Ｐ'=>'P', 'Ｑ'=>'Q', 'Ｒ'=>'R', 'Ｓ'=>'S', 'Ｔ'=>'T',   
             'Ｕ'=>'U', 'Ｖ'=>'V', 'Ｗ'=>'W', 'Ｘ'=>'X', 'Ｙ'=>'Y','Ｚ'=>'Z', 'ａ'=>'a', 'ｂ'=>'b', 'ｃ'=>'c', 'ｄ'=>'d',   
             'ｅ'=>'e', 'ｆ'=>'f', 'ｇ'=>'g', 'ｈ'=>'h', 'ｉ'=>'i','ｊ'=>'j', 'ｋ'=>'k', 'ｌ'=>'l', 'ｍ'=>'m', 'ｎ'=>'n',   
             'ｏ'=>'o', 'ｐ'=>'p', 'ｑ'=>'q', 'ｒ'=>'r', 'ｓ'=>'s', 'ｔ'=>'t', 'ｕ'=>'u', 'ｖ'=>'v', 'ｗ'=>'w', 'ｘ'=>'x',   
             'ｙ'=>'y', 'ｚ'=>'z',  
             '（'=>'(', '）'=>')', '〔'=>'(', '〕'=>')', '【'=>'[','】'=>']', '〖'=>'[', '〗'=>']', '“'=>'"', '”'=>'"',   
             '‘'=>'\'', '’'=>'\'', '｛'=>'{', '｝'=>'}', '《'=>'<','》'=>'>','％'=>'%', '＋'=>'+', '—'=>'-', '－'=>'-',   
             '～'=>'~','：'=>':', '。'=>'.', '、'=>',', '，'=>',', '、'=>',',  '；'=>';', '？'=>'?', '！'=>'!', '…'=>'-',   
             '‖'=>'|', '”'=>'"', '’'=>'`', '‘'=>'`', '｜'=>'|', '〃'=>'"','　'=>' ', '×'=>'*', '￣'=>'~', '．'=>'.', '＊'=>'*',  
             '＆'=>'&','＜'=>'<', '＞'=>'>', '＄'=>'$', '＠'=>'@', '＾'=>'^', '＿'=>'_', '＂'=>'"', '￥'=>'$', '＝'=>'=',  
             '＼'=>'\\', '／'=>'/'  
         );  
     return strtr($str, $arr);  
 }  
```
[PHP 获取指定日期对应的星座名称](http://blog.csdn.net/zhouzme/article/details/18909505)
```js
public function getConstellation($month, $day)  
    {  
        $day   = intval($day);  
        $month = intval($month);  
        if ($month < 1 || $month > 12 || $day < 1 || $day > 31) return false;  
        $signs = array(  
                array('20'=>'宝瓶座'),  
                array('19'=>'双鱼座'),  
                array('21'=>'白羊座'),  
                array('20'=>'金牛座'),  
                array('21'=>'双子座'),  
                array('22'=>'巨蟹座'),  
                array('23'=>'狮子座'),  
                array('23'=>'处女座'),  
                array('23'=>'天秤座'),  
                array('24'=>'天蝎座'),  
                array('22'=>'射手座'),  
                array('22'=>'摩羯座')  
        );  
        list($start, $name) = each($signs[$month-1]);  
        if ($day < $start)  
            list($start, $name) = each($signs[($month-2 < 0) ? 11 : $month-2]);  
        return $name;  
    }  
```
[ mysql连接失败或出现“Too many connections”错误](http://blog.csdn.net/zhouzme/article/details/20015887)
修改为：max_connections = 1000


默认值：100

最大值：16384

即该参数最大值不能超过16384，即使超过也以16384为准
[PHP的ip2long和long2ip函数的实现原理](http://blog.csdn.net/zhouzme/article/details/35285831)
```js
$ip = '12.34.56.78';  
$ips = explode('.', $ip);  
$result = 0;  
$result += $ips[0]<<24;  
$result += $ips[1]<<16;  
$result += $ips[2]<<8;  
$result += $ips[3];  
echo bindec(decbin($result));  
echo '<br>';  
echo bindec(decbin(ip2long($ip)));  
echo '<br>';  
  
$str = '';  
$str .= intval($result/intval(pow(2, 24))) .'.';  
$str .= intval(($result&0x00FFFFFF)/intval(pow(2, 16))) .'.';  
$str .= intval(($result&0x0000FFFF)/intval(pow(2, 8))) .'.';  
$str .= intval($result&0x000000FF);  
  
echo $str;  
echo '<br>';  
echo long2ip($result); 
```
[Redis 数据序列化方法 serialize, msgpack, json, hprose 比较](http://blog.csdn.net/zhouzme/article/details/46863709)
```js
 Msgpack 都是非常牛逼的，只不过需要自己单独安装 Msgpack 的扩展，不过安装也很简单的。

服务器上可以直接 pecl install msgpack 
如果不行的话，就手动下载 tgz 包: 
在这里下载最新版本 https://pecl.php.net/package/msgpack 
然后 pecl install msgpack-0.5.6.tgz 即可


```
