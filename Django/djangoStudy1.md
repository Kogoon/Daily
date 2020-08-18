# Django 공부 - 1  
>anaconda 환경에서 실행.   
  
### Update  
~~~
conda update <환경이름>
~~~
<환경이름>에서 conda가 관리하는 패키지 버젼 등을 업데이트한다.   
  
### Activate  
~~~
conda activate <환경이름> / conda deactivate <환경이름>
~~~
<환경이름>으로 된 가상환경 접속/해제  

### Install  
~~~
pip install django
~~~
장고 설치  

### Create Project  
~~~
django-admin startproject <프로젝트명>
~~~
현재 directory에서 <프로젝트명>으로 된 directory가 생성된다.   

### Intro  
* manage.py : django 프로젝트와 상호작용하는 파일.   

#### <프로젝트명>project의 <프로젝트명>  
* settings.py : django 프로젝트의 설정을 구성하는 파일.  
* urls.py : django 프로젝트의 url들을 관리하는 파일.  

### Run Server
~~~
python manage.py runserver
~~~
웹브라우저에서 `127.0.0.1:8000`를 주소창에 치면 로켓 화면이 나온다. (장고 기본 첫 화면)

### Hello World
역시 첫 시작은 Hello World.  
`manage.py`파일이 있는 위치에서 아래 명령어로 `app`을 만들 수 있다.  
`app`은 프로젝트의 구성단위. ( apps -> project)
~~~
python manage.py startapp <앱이름>
~~~

### apps.py
생성한 `app`의 directory로 들어가면,  `apps.py`와 그안에 `class`가 생성이 되어 있다. 

### 적용
`app`을 만들었으면 django 내에서 설정을 해 줄 필요가 있다. 
1. settings.py
2. templates
3. views.py
4. urls.py

#### 1
settings.py의
~~~
INSTALLED_APPS = [
    'hello.apps.HelloConfig',
    ...(중략)
]
~~~
INSTALLED_APPS에 `app`의 클래스를 설정해준다.  

#### 2
tesplates에는 html의 파일들이 들어간다.  
만든 `app` directory 내의 `template`라는 폴더를 생성해주고  
그 안에 index.html 생성한다.  
~~~
<h1>Hello World!</h1>
~~~

#### 3
`views.py` 파일 안의 주석 부분 밑에 코드를 추가해준다.  
~~~
from django.shortcuts import render

# Create your views here.
def index(request):
    return render(request, 'index.html')
~~~

#### 4
`project`의 `urls.py`에서 `app`의 templates 폴더 내의 html 파일과 연결해준다. 
urls.py
~~~
from django.contrib import admin
from django.urls import path
import hello.views

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', hello.views.index, name="index")
]
~~~
hello `app`안의 `views.py`를 읽어와야하니 `import hello.views` 추가해주고,  
`path('', hello.views.index, name="index")` 부분을 추가해준다.  

### Runserver
~~~
python manage.py runserver
~~~
Hello World의 출력을 확인한다. 
