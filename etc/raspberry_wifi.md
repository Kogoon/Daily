# 라즈베리파이3 무선랜 설정하기   
## RaspberryPi3 Wifi config  

> `Raspberry3` `ubuntu` `wifi`  


### 라즈베리파이 와이파이 설정법..  
서버 업데이트 진행해주고..  
~~~
sudo apt update
sudo apt upgrade
~~~

네트워크 정보를 확인해준다.   
~~~
ifconfig
~~~

는 이미지 깔고난 바로 다음이라 안깔려있어서 `net-tools` 설치.   
~~~
sudo apt install net-tools
~~~

다시 한번 네트워크 확인해주고 사용가능한 와이파이를 확인해준다.   
~~~
ifconfig or iwconfig
sudo iwlist wlan0 scan
(설치안되어있으면) sudo apt install wireless-tools
~~~

#### Rasbian...  
무선랜 설정을 위해  
~~~
wpa_passphrase <Wifi_name/SSID> <PASSWORD>
ex) #wpa_passphrase iptime 12345678
~~~

위의 명령어를 치고나면 뜨는 정보들을 복사해준뒤에, (vi/nano 편한거)  
`wpa_supplicant` 창을 열고 복사한 내용을 붙여넣기해서 넣어준다.
~~~
sudo vi /etc/wpa_supplicant/wpa_supplicant.conf
~~~

그다음 재부팅
~~~
sudo reboot
~~~


### 라즈베리파이 Ubuntu에서의 Wifi 설정법...
> 우분투를 깔았더니 라즈비안 설정법이 먹히지가 않는다.. 검색해서 다른 방법 가져옴..

시스템의 사용가능한 네트워크 어댑터를 확인해준다. (혹시 다를 수 있으니)
~~~
ls /sys/class/net
~~~

wlan0(무선랜)을 확인해준후, 아래 명령어로 네트워크 설정을 해준다.
~~~
sudo vi /etc/netplan/50-cloud-init.yaml
~~~

초기모습. 
~~~
network:
  ethernets:
    eth0:
      dhcp4: true
      optional: true
  version: 2
~~~

아래와 같이 `ethernets`을 `wifis`의 내용으로 바꾸어준다.  
> 난 와이파이 적용이 안되었는데 혹시나 랜선 연결까지 안될까봐 두개다 놔두었음.. 
~~~
network:
  wifis:
    wlan0:
      dhcp4: true
      access-point:
        "<Wifi_name/SSID>":
        password: "<PASSWORD>"
  version: 2
~~~

혹시라도 `ethernets`부분을 제거하고 `apply`를 하게되면 랜선연결이 안될 수 있으니  
미리 `ifconfig` 쳐서 wlan0의 IP를 파악해놓자..   
  
위의 설정을 마쳤으면 적용&재부팅을 해준다.   
~~~
sudo netplan apply
sudo reboot
~~~

다음 ssh 연결을 wlan0 IP로 접근해주면 끝.  
> Ubuntu 방법이 뭐 설치할 필요도 없이 쉬운듯?  

* * *  
[도움된 글]  
[eelu172 블로그-rasbian](https://eelu175.tistory.com/29)  
[vkein 블로그-ubuntu](https://vkein.tistory.com/entry/%EB%9D%BC%EC%A6%88-%EB%B2%A0%EB%A6%AC%ED%8C%8C%EC%9D%B4-%EC%B4%88%EA%B8%B0-%EC%84%A4%EC%A0%95)  
