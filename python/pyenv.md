# 파이썬 가상 
> 라즈베리파이의 우분투20 환경에서 작업했습니다  

* * *
설치전에 업데이트를 해줍니다.  
~~~
sudo apt update
sudo apt upgrade
~~~

### pyenv 설치   
[참고 - pyenv 제작자의 Installer](https://github.com/pyenv/pyenv-installer)  
~~~
curl https://pyenv.run | bash
~~~

제작자가 만든 Installer로 기존 pyenv 깔던대로 깔면 환경변수 설정해주고 해야하는 부분이 
사라졌습니다.  
인스톨러가 다해주기때문.. 

#### pyenv 설치 (not installer) *(Ubuntu ver.)*
> 환경설정을 잘못 건드렸나... 자꾸 ~/.pyenv로 설치가 안되고 ~/HOME/.pyenv에 설치가됨;; 환경변수 잘못된거없었는데;; 그래서 재설치
~~~
git clone https://github.com/pyenv/pyenv.git ~/.pyenv  (git에서 직접 .pyenv 에 클론받고)
(환경변수 설정)
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
~~~

설치 후 Shell을 재실행해줍니다.  
~~~
exec $SHELL
~~~
  
잘 설치되어있는지 확인은 `pyenv`를 통해서 할 수 있습니다.  
~~~
pyenv
pyenv --version
~~~

`pyenv`가 제대로 설정이 되었다면, pyenv로 작업하기 전에 각 운영체제마다 필요로하는 패키지들이 있습니다.    
저는 우분투지만, 다른 운영체제를 쓰신다면 [[참고]](https://github.com/pyenv/pyenv/wiki/Common-build-problems)하시면 되겠습니다.  
아래 명령어로 필요한 패키지들을 설치해줍니다.  
~~~
sudo apt-get install -y build-essential libssl-dev zlib1g-dev libbz2-dev \
libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev \
xz-utils tk-dev libffi-dev liblzma-dev python-openssl git
~~~

vitualenv도 이어서 설치를하겠습니다. & 환경변수 설정 (선택사항)
~~~
git clone https://github.com/yyuu/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
echo 'eval "$(pyenv virtualenv-init -)"' >> ~/.bashrc
~~~

* * *

### pyenv 사용법  

##### pyenv 업데이트
~~~
pyenv update
~~~

##### pyenv 제거
~~~
(설치되어있는 곳)
rm -rf ~/.pyenv
~~~
(이후) 밑의 4줄을 `.bashrc`에서 제거.
~~~
export PYENV_ROOT="$HOME/.pyenv" 
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)" (선택)
~~~

##### pyenv로 관리되는 python 목록 확인  
~~~
pyenv version (현재 python 버젼 확인)
pyenv versions (깔려있는 python 버젼 리스트 확인)
system(서버/시스템에 깔려있는 python 버젼 쓴다는 뜻)
~~~

##### pyenv로 파이썬 설치 가능 목록 확인 & 원하는 버젼 설치 (저는 3.8.4)
~~~
pyenv install --list
pyenv install --list | grep "^\s*3\.8" (3.8버젼의 파이썬 목록 확인)
pyenv install 3.8.4
~~~

##### pyenv 목록 확인 및 시스템 전역에서 사용할 버젼으로 변경  
(명령어는 #)  
~~~
#pyenv versions
system
3.8.4
#pyenv global 3.8.4
~~~

##### pyenv 오류
`pyenv: shell integratoin not enabled. Run 'pyenv init' for instructions` 라는 오류로 pyenv init이 안되는 이유  
[참고-pyenv installation](https://github.com/pyenv/pyenv#installation)
~~~
echo -e 'if command -v pyenv 1>/dev/null 2>&1; then\n  eval "$(pyenv init -)"\nfi' >> ~/.bashrc
~~~
이후, 쉘 재시작. (제거할 경우 위 설정해준것도 제거해줘야겠죠)

### python 3.8.4 ...

##### pip 업그레이드
> 아마 최신일듯.. 
~~~
pip install --upgrade pip
~~~

##### virtualenv 설치
~~~
pip install virtualenv
~~~

##### 가상환경 만들기 
~~~
pip install virtualenv
~~~

##### 프로젝트 생성
~~~
mkdir project_name
cd project_name
pyenv local 3.8.4 (설치한버젼)
~~~
-> ls -al 시, .python-version 생성된 것을 확인할 수 있음. 

##### 가상환경 생성
`venv`라는 이름으로 가상환경(폴더) 생성
~~~
virtualenv venv
~~~

##### 가상환경 진입
~~~
source venv/bin/activate
~~~
-> (venv)~/project_name 이렇게 변경.  
~~~
(가상환경 진입 전)
#which python
...(경로)/.pyenv/shims/python
(가상환경 진입 후)
#which python 
...(경로)/project_name/venv/bin/python
~~~
