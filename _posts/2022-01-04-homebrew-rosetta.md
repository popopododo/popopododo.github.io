---
title:  "Error : Cannot install on Intel processor in ARM default prefix (/opt/homebrew)!"
excerpt: "brew install 이 안 됨"

categories:
  - Blog
tags:
  - "Homebrew"
last_modified_at: 2022-01-04T08:06:00-05:00
---



M1 맥북을 사고나서 개발환경 세팅, github.io 를 로컬로 구성하던 중 homebrew, ruby, jekyll 을 설치하는데 꽤나 애를 먹었다..

위 포스팅에는 Rosetta로 homebrew 를 깔아서 환경설정이 뒤죽박죽된것에 대한 해결책을 정리해놓는다.

원인 
- brew를 사용하여 install을 진행하던 중 나타났던 에러


brew config 로 경로확인 

- HOMEBREW_PREFIX: 부분이 /usr/local 로 되어 있음

해결방법 

- *초기 설정 때 터미널을 Rosetta를 사용하여 열기를 사용하여 설치해서 생긴 에러
우선 homebrew 를 re-install 하였다.*



<u>Rosetta를 사용하여 열고 끄기 설정</u>

Finder -> 응용프로그램 -> 사용하는 터미널 프로그램 오른쪽 클릭 -> 정보 가져오기에 가면 이런 창이 나타나는데,

<img src="https://user-images.githubusercontent.com/76838814/148074692-25e54b47-716f-49db-a0e2-532e496be5c0.png" width='300'>

위 그림에서 Rosetta를 사용하여 열기를 체크하면 된다.

### Homebrew Re-install


Uninstall

```/bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh))"```

Install

```/bin/bash -c "$(curl -fsSL [https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh](https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh))”```


위 과정 후 PATH 등록을 해준다.

```sudo vi ~/.zshrc```

로 접속 후 i(insert) 로 하단 코드 추가

혹은

기존에 있는 환경설정 코드에 추가

```export PATH=/opt/homerew/bin:$PATH```

<img src="https://user-images.githubusercontent.com/76838814/148076625-8176f4da-3cad-4b81-bdb8-1fc56e68be0a.png">



HOMEBREW_PREFIX가 정상적으로 /opt/homebrew 로 잘 설정되었다.

