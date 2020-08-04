

### install 
~~~
pip install django
~~~

### start project
~~~
django-admin startproject mysite .
(django-admin start project (dir name) .)
~~~

~~~
tree
mysite
├───manage.py
└───mysite
        settings.py
        urls.py
        wsgi.py
        __init__.py
~~~

### settings.py 설정
`mysite/settings.py` 수정해야할부분. 
~~~
TIME_ZONE = 'Asia/Seoul'
~~~


### runserver
~~~
python manage.py runserver
~~~

외부 접근 허용을 하고 싶을 경우에는, 
`settings.py`의 `ALLOWED_HOSTS`에 내부서버의 ip 및 도메인을 추가해주도록한다.
그리고 아래와 같이 명령어를 사용한다. 
~~~
python manage.py runserver 0.0.0.0:8000
~~~
포트는 변경이 가능하다. 
