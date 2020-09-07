## Suricata
> `CentOS 7`


### Suricata 설치 
[Suricata CentOS installation](https://redmine.openinfosecfoundation.org/projects/suricata/wiki/CentOS_Installation)의 설명서대로 진행했다. 

### 요구사항
  
> `CentOS 6` Only
~~~
yum install epel-release
~~~

> `CentOS 7`
~~~
sudo yum -y install gcc libpcap-devel pcre-devel libyaml-devel file-devel \
  zlib-devel jansson-devel nss-devel libcap-ng-devel libnet-devel tar make \
  libnetfilter_queue-devel lua-devel PyYAML libmaxminddb-devel rustc cargo \
  lz4-devel
~~~

> `CentOS 7 minimal` 
CentOS 7 minimal에는 wget이 깔려있지 않아서 추가로 설치해주었다. 
~~~
yum install -y wget
~~~

### Suricata 설치 
~~~
http://www.openinfosecfoundation.org/download/suricata-3.1.tar.gz
tar -xczf suricata-3.1.tar.gz
cd suricata-3.1
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-nfqueue --enable-lua
~~~
위와 같이 진행 후
~~~
make
sudo make install 
sudo ldconfig
~~~

### Auto Setup
~~~
make install-conf
make install-rules
make install-full
~~~
