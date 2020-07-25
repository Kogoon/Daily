# Flask 시작하기 
[Flask_document](https://flask.palletsprojects.com/en/1.1.x/)

### Flask 설치
~~~
pip install Flask
~~~

### 기본 Flask Application 모습
`hello.py`
~~~
from flask import Flask 
app = Flask(__name__)

@app.route('/')
def hello_world():
    return "Hello World!"
    
if __name__ == '__main__':
    app.run()
~~~

#### 외부 접속 허용
네트워크상 다른 장비에서 접속하고 싶으면,
~~~
if __name__ == '__main__':
    app.run(host='0.0.0.0')
~~~
위 설정은 public IP 접근을 OS에게 허용한다는 뜻. 

#### Flask 서비스 실행
기본 포트는 `5000`
~~~
python hello.py
~~~

#### debugging 활성화
~~~
if __name__ == '__main__':
    app.run(debug=True)
~~~
또는
~~~
if __name__ == '__main__':
    app.debug = True
    app.run()
~~~


### ERROR
아래와 같은 에러 발생시
~~~
WARNING: This is a development server. Do not use it in a production deployment.
~~~

FLASK_ENV 환경변수를 추가해준다.
~~~
export FLASK_ENV=development
~~~


