## CentOS 7 첫 설치 후 네트워크 설정. 
> `CentOS 7 minimal 설치`

minimal 처음 설치 후에는 network 설정이 되어 있지 않다. 

### network service 확인 / 시작 / 재시작 명령어
~~~
systemctl status network
service network status
~~~

~~~
systemctl start network
service network start
~~~

~~~
systemctl restart network
service network restart
~~~

### network 설정
~~~
vi /etc/sysconfig/network-scripts/ifcfg-ens33
~~~
(ens33과 같은 이더넷 이름은 다를 수 있다.)   

ens33과 같은 이더넷 명을 변경을 하려면, 파일내의 `NAME`부분 변경 후, 파일명도 변경한 이더넷 이름으로 변경해주어야 한다.   
(ifcfg-xxxx)  

#### centOS 8

