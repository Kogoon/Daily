## yum 명령어
> `centOS`  
RPM(Redhat Package Manager), YUM(Yellodog Updater Modified)은 리눅스의 패키지 인스톨 프로그램이다.(패키지 설치 프로그램)  

### 패키지 검색
~~~
yum search 검색어
~~~

### 패키지 설치
~~~
yum install 패키지명
~~~

### 패키지 삭제
~~~
yum remove 패키지명
rpm -e 패키지명
~~~

### 여러 패키지 삭제
~~~
yum remove *php*
~~~
> 패키지 명에 php가 들어간 패키지 전체 삭제

### 패키지 업데이트
~~~
yum update 패키지명
~~~

### 패키지 정보 확인
~~~
yum info 패키지명
~~~

### 설치된 패키지 목록 확인
~~~
yum list installed
rpm -qa
~~~
