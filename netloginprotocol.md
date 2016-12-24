未认证用户访问外网网址服务器返回信息
B:
GET http://www.12306.cn/mormhweb/ HTTP/1.1
Host: www.12306.cn
Connection: keep-alive
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
Referer: http://www.12306.cn/
Accept-Encoding: gzip, deflate, sdch
Accept-Language: zh-CN,zh;q=0.8
Cookie: BIGipServerportal=3151233290.17183.0000; Hm_lvt_5d59452a2b1d03d9b7faab90c4809e85=1482323469; Hm_lpvt_5d59452a2b1d03d9b7faab90c4809e85=1482397762; Hm_lvt_78ea0ea66ad61026a21db437f2eff145=1482323469; Hm_lpvt_78ea0ea66ad61026a21db437f2eff145=1482397762


S:
HTTP/1.1 200 OK
Allow: GET,POST,HEAD
MIME-Version: 1.0
Server: NetEngine Server 1.0
Pragma: No-Cache
Content-Length: 180
Content-Type: text/html

<html><body><form name="CMCCWLANFORM" method="post" action="http://10.255.44.33/index_1.html"></form><script language='javascript'>    CMCCWLANFORM.submit();</script></body></html>


http://10.255.44.33/index_1.html内容
B：
POST http://10.255.44.33/index_1.html HTTP/1.1
Host: 10.255.44.33
Connection: keep-alive
Content-Length: 0
Cache-Control: max-age=0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Origin: http://www.12306.cn
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Referer: http://www.12306.cn/mormhweb/
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.8
Cookie: seachdown=2016-11-23; login=bQ0pOyR6IXU7PJaQQqRAcBPxGAvxAcroYylaKlmvDDGPdIp%252FBR3bb73S0Rk%252B9cgz9KC5ictxJLb5xID2ayZh0ZAnAaPrr4cSBevaxlY5jHqurZqdZA8vzqjyAAwPJ3n9b5fEAM0nM%252BER6M3G%252FZTcbJt45bfELuquYaDta2n2zxHArUqB54FFIw%253D%253D; Hm_lvt_78ea0ea66ad61026a21db437f2eff145=1482218285; Hm_lpvt_78ea0ea66ad61026a21db437f2eff145=1482458541; Hm_lvt_5d59452a2b1d03d9b7faab90c4809e85=1482218285; Hm_lpvt_5d59452a2b1d03d9b7faab90c4809e85=1482458541

S:
HTTP/1.1 200 OK
Server: nginx/1.8.0
Date: Fri, 23 Dec 2016 02:01:45 GMT
Content-Type: text/html
Content-Length: 591
Connection: close
Last-Modified: Tue, 29 Dec 2015 04:20:39 GMT
ETag: "24f-52801be7573c0"
Accept-Ranges: bytes

<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<meta http-equiv="expires" content="0">
<meta http-equiv="cache-control" content="no-store">
<meta http-equiv="pragma" content="no-cache">
<script language="javascript">
var p=/\/index_([\d]+).html/;
var arr=p.exec(document.location);
if(arr[1])
{
	location="ac_detect.php?"+"ac_id="+arr[1]+"&"+document.location.search.substring(1);
}
</script>
</head>
</body>
</html>

访问http://10.255.44.33/ac_detect.php?ac_id=1&网址
B:
GET http://10.255.44.33/ac_detect.php?ac_id=1& HTTP/1.1
Host: 10.255.44.33
Connection: keep-alive
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
Referer: http://10.255.44.33/index_1.html
Accept-Encoding: gzip, deflate, sdch
Accept-Language: zh-CN,zh;q=0.8
Cookie: seachdown=2016-11-23; login=bQ0pOyR6IXU7PJaQQqRAcBPxGAvxAcroYylaKlmvDDGPdIp%252FBR3bb73S0Rk%252B9cgz9KC5ictxJLb5xID2ayZh0ZAnAaPrr4cSBevaxlY5jHqurZqdZA8vzqjyAAwPJ3n9b5fEAM0nM%252BER6M3G%252FZTcbJt45bfELuquYaDta2n2zxHArUqB54FFIw%253D%253D; Hm_lvt_78ea0ea66ad61026a21db437f2eff145=1482218285; Hm_lpvt_78ea0ea66ad61026a21db437f2eff145=1482458541; Hm_lvt_5d59452a2b1d03d9b7faab90c4809e85=1482218285; Hm_lpvt_5d59452a2b1d03d9b7faab90c4809e85=1482458541

S:
HTTP/1.1 302 Found
Server: nginx/1.8.0
Date: Fri, 23 Dec 2016 02:01:45 GMT
Content-Type: text/html
Content-Length: 0
Connection: close
X-Powered-By: PHP/5.5.23
Location: http://10.255.44.33:801/srun_portal_pc.php?ac_id=1&

重定向至登录页面
B:
GET http://10.255.44.33:801/srun_portal_pc.php?ac_id=1& HTTP/1.1
Host: 10.255.44.33:801
Connection: keep-alive
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
Referer: http://10.255.44.33/index_1.html
Accept-Encoding: gzip, deflate, sdch
Accept-Language: zh-CN,zh;q=0.8
Cookie: seachdown=2016-11-23; login=bQ0pOyR6IXU7PJaQQqRAcBPxGAvxAcroYylaKlmvDDGPdIp%252FBR3bb73S0Rk%252B9cgz9KC5ictxJLb5xID2ayZh0ZAnAaPrr4cSBevaxlY5jHqurZqdZA8vzqjyAAwPJ3n9b5fEAM0nM%252BER6M3G%252FZTcbJt45bfELuquYaDta2n2zxHArUqB54FFIw%253D%253D; Hm_lvt_78ea0ea66ad61026a21db437f2eff145=1482218285; Hm_lpvt_78ea0ea66ad61026a21db437f2eff145=1482458541; Hm_lvt_5d59452a2b1d03d9b7faab90c4809e85=1482218285; Hm_lpvt_5d59452a2b1d03d9b7faab90c4809e85=1482458541

S:
HTTP/1.1 200 OK
Date: Fri, 23 Dec 2016 02:01:45 GMT
Server: Apache/2.4.12 (Unix) OpenSSL/1.0.1g-fips PHP/5.5.23
X-Powered-By: PHP/5.5.23
Keep-Alive: timeout=1, max=250
Connection: Keep-Alive
Transfer-Encoding: chunked
Content-Type: text/html; charset=utf-8

25bc
<html内容>
0

网络断开
B：
POST http://10.255.44.33:801/include/auth_action.php HTTP/1.1
Host: 10.255.44.33:801
Connection: keep-alive
Content-Length: 58
Accept: */*
Origin: http://10.255.44.33:801
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/50.0.2661.102 Safari/537.36
Content-Type: application/x-www-form-urlencoded
Referer: http://10.255.44.33:801/srun_portal_pc.php?ac_id=1&
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.8
Cookie: login=bQ0pOyR6IXU7PJaQQqRAcBPxGAvxAcroYylaKlmvDDGPdIp%252FBR3bb73S0Rk%252B9cgz9KC5ictxJLb5xID2ayZh0ZAnAaPrr4cSBevaxlY5jHqurZqdZA8vzqjyAAwPJ3n9b5fEAM0nM%252BER6M3G%252FZTcbJt45bfELuquYaDta2n2zxHArUqB54FFIw%253D%253D; seachdown=2016-11-23; login=bQ0pOyR6IXU7PJaQQqRAcBPxGAvxAcroYylaKlmvDDGPdIp%252FBR3bb73S0Rk%252B9cgz9KC5ictxJLb5xID2ayZh0ZAnAaPrr4cSBevaxlY5jHqurZqdZA8vzqjyAAwPJ3n9b5fEAM0nM%252BER6M3G%252FZTcbJt45bfELuquYaDta2n2zxHArUqB54FFIw%253D%253D; Hm_lvt_5d59452a2b1d03d9b7faab90c4809e85=1482218285; Hm_lpvt_5d59452a2b1d03d9b7faab90c4809e85=1482460049; Hm_lvt_78ea0ea66ad61026a21db437f2eff145=1482218285; Hm_lpvt_78ea0ea66ad61026a21db437f2eff145=1482460049

action=logout&username=1603321742&password=19860920&ajax=1

S:
HTTP/1.1 200 OK
Date: Fri, 23 Dec 2016 02:24:11 GMT
Server: Apache/2.4.12 (Unix) OpenSSL/1.0.1g-fips PHP/5.5.23
X-Powered-By: PHP/5.5.23
Content-Length: 15
Keep-Alive: timeout=1, max=250
Connection: Keep-Alive
Content-Type: text/html

网络已断开




PPPOE拨号认证
