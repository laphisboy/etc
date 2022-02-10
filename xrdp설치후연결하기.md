# xrdp 설치 및 연결 과정 (117 설치 과정 예시)

### 설치 1: 설치합니다

```jsx
sudo apt-get install xrdp
sudo apt-get install xfce4
```

### 설치 2: 설치 후 자동으로 실행되는데, status로 active (running) 인지 확인해줍니다.

```jsx
sudo systemctl status xrdp
```

![Untitled](xrdp%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%86%E1%85%B5%E1%86%BE%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20(117%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)%20d3ddcbf0db324721a5c33482032e4714/Untitled.png)

### 윈도우 10 에서 연결 1: 시작 메뉴에서 rdp 를 쳐서 나오는 “원격 데스크톱 연결” 에 서버 ip를 입력합니다 (3389 포트 번호는 입력 안 하셔도 됩니다)

![Untitled](xrdp%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%86%E1%85%B5%E1%86%BE%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20(117%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)%20d3ddcbf0db324721a5c33482032e4714/Untitled%201.png)

### 윈도우 10 에서 연결 2: 연결이 되면 로그인 화면이 나오는데 본인 계정 및 비밀번호를 입력합니다

![Untitled](xrdp%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%86%E1%85%B5%E1%86%BE%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20(117%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)%20d3ddcbf0db324721a5c33482032e4714/Untitled%202.png)

### 에러 1: “login failed for display 0” 가 뜨면 [startwm.sh](http://startwm.sh) 안에 내용을 아래 #!/bin/sh ~ 로 시작하는 내용으로 바꿔주고 xrdp restart해서 다시 로그인 시도합니다.

```jsx
sudo vi /etc/xrdp/startwm.sh
```

```jsx
#!/bin/sh
# xrdp X session start script (c) 2015, 2017 mirabilos
# published under The MirOS Licence

if test -r /etc/default/locale; then
        . /etc/default/locale
        test -z "${LANG+x}" || export LANG
        test -z "${LANGUAGE+x}" || export LANGUAGE
        test -z "${LC_ADDRESS+x}" || export LC_ADDRESS
        test -z "${LC_ALL+x}" || export LC_ALL
        test -z "${LC_COLLATE+x}" || export LC_COLLATE
        test -z "${LC_CTYPE+x}" || export LC_CTYPE
        test -z "${LC_IDENTIFICATION+x}" || export LC_IDENTIFICATION
        test -z "${LC_MEASUREMENT+x}" || export LC_MEASUREMENT
        test -z "${LC_MESSAGES+x}" || export LC_MESSAGES
        test -z "${LC_MONETARY+x}" || export LC_MONETARY
        test -z "${LC_NAME+x}" || export LC_NAME
        test -z "${LC_NUMERIC+x}" || export LC_NUMERIC
        test -z "${LC_PAPER+x}" || export LC_PAPER
        test -z "${LC_TELEPHONE+x}" || export LC_TELEPHONE
        test -z "${LC_TIME+x}" || export LC_TIME
        test -z "${LOCPATH+x}" || export LOCPATH
fi

#test -x /etc/X11/Xsession && exec /etc/X11/Xsession
#exec /bin/sh /etc/X11/Xsession
xfce4-session
```

```jsx
sudo service xrdp restart
```

### 에러 2: “login failed for display 0” 아래 패키지를 설치해주고 다시 xrdp restart해서 다시 로그인 시도합니다.

```jsx
sudo apt-get install xorgxrdp-hwe-18.04
sudo service xrdp restart
```

### 접속 화면

![Untitled](xrdp%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%86%E1%85%B5%E1%86%BE%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20(117%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)%20d3ddcbf0db324721a5c33482032e4714/Untitled%203.png)

### 추가 - 아래 터미널 아이콘이 작동 안 할 경우에는 alt+f2 로 application finder을 열고 xfce4-terminal을 실행시킵니다.

![Untitled](xrdp%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%86%E1%85%B5%E1%86%BE%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20(117%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)%20d3ddcbf0db324721a5c33482032e4714/Untitled%204.png)

### 이상입니다.

![Untitled](xrdp%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%86%E1%85%B5%E1%86%BE%20%E1%84%8B%E1%85%A7%E1%86%AB%E1%84%80%E1%85%A7%E1%86%AF%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20(117%20%E1%84%89%E1%85%A5%E1%86%AF%E1%84%8E%E1%85%B5%20%E1%84%80%E1%85%AA%E1%84%8C%E1%85%A5%E1%86%BC%20%E1%84%8B%E1%85%A8%E1%84%89%E1%85%B5)%20d3ddcbf0db324721a5c33482032e4714/Untitled%205.png)
