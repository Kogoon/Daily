# CSS Selector 사용하기. 

CSS(Cascading Style Sheets)는 HTML과 같은 마크업 언어의 디자인을 꾸미기 위해 사용하는 스타일 지정 도구이다.  
최근의 웹 문서들은 CSS 스타일시트를 즐겨 사용하므로, CSS 속성을 이요하여 HTML 요소에 접근하는 것이 유용할 때가 많다.
BeautifulSoup에서는 select() 메소드에 CSS 선택자(CSS Selector)를 매개변수로 전달하는 방법을 사용한다.  
select() 메소드는 해당하는 태그를 모두 찾아서 리스트로 리턴한다.   
  
크롬(Chrome) 개발자 도구를 이용하면, CSS Selector를 쉽게 복사할 수 있다. 
[서울 지하철 위키](https://en.wikipedia.org/wiki/Seoul_Metropolitan_Subway)에서의 지하철 이미지를 선택하고  
우클릭해서 Copy - Copy Selector 하면 '#mw-content-text > div.mw-parser-output > table:nth-child(3) > tbody > tr:nth-child(2) > td > a > img'의
내용을 얻을 수 있다.  

이 내용을 select() 매소드의 매개변수로 전달하여 태그 요소를 찾는다. 

### Code
~~~
import requests
from bs4 import BeautifulSoup

url = "https://en.wikipedia.org/wiki/Seoul_Metropolitan_Subway"
resp = requests.get(url)
html_src = resp.text
soup = BeautifulSoup(html_src, 'html.parser')

subway_image = soup.select('#mw-content-text > div > table:nth-child(3) > \
                    tbody > tr:nth-child(2) > td > a > img')
print(subway_image)
print("\n")
print(subway_image[0])
print("\n")

subway_image2 = soup.select('tr > td > a > img')
print(subway_image2[1])
~~~
* selector에서 `>`는 자식 선택자를 나타낸다.  
