# robots.txt

[로봇 배제 표준](https://ko.wikipedia.org/wiki/%EB%A1%9C%EB%B4%87_%EB%B0%B0%EC%A0%9C_%ED%91%9C%EC%A4%80)  

로봇 배제 표준에 대하여 '웹 사이트에 로봇이 접근하는 것을 방지하는 규약'이 존재한다.  

위 위키피디아 링크에서 확인이 가능하다.  

### Example

**모든(*) 로봇(User-agent)에게 루트 디렉토리(/) 이하 모든 문서에 대한 접근을 허락한다.**  
~~~
User-agent: *
Allow: /
~~~
  
**모든(*) 로봇(User-agent)에게 루트 디렉토리(/) 이하 모든 문서에 대한 접근을 차단(불허, Disallow)한다.**  
~~~
User-agent: *
Disallow: /
~~~
  
**모든(*) 로봇에게 특정 디렉터리(/temp/)에 대한 접근을 차단한다.**  
~~~
User-agent: *
Disallow: /temp/
~~~
  
**특정 로봇(googlebot)에게 모든 문서에 대한 접근을 차단한다.**  
~~~
User-agent: googlebot
Disallow: /
~~~
  
**BadBot과 googlebot에게 특정 디렉터리(/private/)에 대한 접근을 차단한다.**  
~~~
User-agent: BadBot
User-agent: googlebot
Disallow: /private/
~~~
  
### 추가
  
대부분의 사이트들에서 웹 크롤링 로봇 접근 권한을 제어하고 있다.  

접근하기 전에 반드시 로봇 배제 표준을 확인하고 그 가이드라인을 따를 필요가 있다.  

또한, 로봇의 접근이 허용되더라도 웹 서버에 무리가 갈 만한 서비스 안정성을 해치는 행위는 삼가야한다.  

마지막으로, 크롤링으로 획득한 자료는 저작권이 있으니 임의로 배포하거나 변경해서는 안된다.  

### robots.txt 확인 방법

robots.txt파일은 루트 디렉토리에 위치하고 있다.  

웹 브라우저의 주소창에 입력하는 방식으로 그 내용을 확인할 수 있다.  

~~~
https://www.python.org/robots.txt
~~~

### python 코드를 통한 확인
~~~
import requests

urls = ["https://www.naver.com/", "https://www.python.org/"]
filename = "robots.txt"

for url in urls:
    file_path = url + filename
    print(file_path)
    
    resp = requests.get(file_path)
    print(resp.text)
    print('\n')
~~~

다음과 같은 코드로도 웹 사이트에 대한 robots.txt의 내용을 확인할 수 있다.  
