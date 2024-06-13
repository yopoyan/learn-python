
# 如何用 Python 获取网络数据

```scheme

import requests
resp = requests.get('https://ip.renfei.net')
if resp.status_code == 200:
    print(resp.text)



```


实际上，上述服务的服务器返回的 Content-Type 值为 application/json，这种格式意味着返回的 Response 对象的 text 的数据格式是一个 JSON 编码的字符串，我们完全可以通过反序列化的方式将它映射到 Python 的字典中，从而获取到我们的 IP 地址，并用在后续的业务中。解析代码如下：


```scheme
import requests
import json
resp = requests.get('https://ip.renfei.net')
if resp.status_code == 200:
    print(resp.text)
if resp != None:
  ip_info = json.loads(resp.text)
  print(f'我的出口 IP 地址是：{ip_info["clientIP"]}')

```