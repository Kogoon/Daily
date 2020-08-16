# python requests

 인터넷 브라우저(크롬, 등)에 웹 주소를 입력하면 웹페이지 정보를 요청(request)하게 된다.  
   
 이때, 웹 서버가 브라우저에서 요청에 대한 응답(response)를 하게 된다.  
 
### requests 모듈 설치

 웹 서버를 요청하고 응답하는 과정을 처리하는 파이썬 라이브러리 `requests`가 있다.   
 
 ~~~
 pip install requests
 ~~~
 의 명령으로 쉽게 설치가 가능하다.   
 
### requests 동작 확인 

아래 실습 코드로 동작이 잘 되는지 확인하자.   
~~~
import requests

url  = "https://www.python.org/"
resp = requests.get(url)
print(resp)

url2  = "https://www.python.org/1"
resp2 = requests.get(url2)
print(resp2)
~~~
`requests` 모듈의 get함수를 이용해서 url에 대한 웹서버에 GET요청을 하게 된다.  

웹서버가 응답한 내용(상태코드)를 resp에 저장하여 출력한다.  

결과로는, 
~~~
<Response [200]>
<Response [404]>
~~~

200은 정상을, 404는 Not Found를 의미한다. [(참고)http status code](https://en.wikipedia.org/wiki/List_of_HTTP_status_codes)

### HTML 소스 확인

일반 GET 함수로는 상태를 응답받을 수 있다.  
   
html 소스코드는 text 속성에 저장되어 있는데 이를 확인하려면,  
 
~~~
import requests

url = "https://www.python.org/"
resp = requests.get(url)

html = resp.text
print(html)
~~~

text 함수를 이용해서 html 소스코드를 확인할 수 있다.  

웹 서버의 응답 객체는 headers, cookies, text 등 여러 가지 속성을 갖는다.  

정상적인 응답코드를 받았다면, 실행결과로 html에 저장된 HTML 소스코드가 출력된다.  
