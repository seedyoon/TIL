# 삽질 정리

## apt-get update 문제, Official 라이브러리 이외의 패키지 업데이트

### mono lib 종속성 문제

* mono upgrade 시 문제가 되어 제거 후 재 설치를 진행 중에 문제 발생
* 종속성을 연결하여서 강제 업데이트로 처리
* 자꾸 install 뒤에 프로젝트를 넣어서 전체가 처리 되지 않음, 아래 처럼 하면 종속성 관련된 것들이 다 강제 처리 됨

```bash
sudo apt-get -f install
```

### GPG Error NODATA' (does the network require authentication?)

* 회사 자체 방화벽에서 키를 막아서 제대로 받지 못하는 경우
  * 프록시 설정이 필요
  * 설정 후 몇차례 시도하면 됨(이전에는 진행 자체가 안되었음)

```bash

vi /etc/apt/apt.conf.d/99HttpProxy
acquire::http::Proxy "http://172.20.9.235:3128";

```

* 데비안 http proxy 설정
  * <https://codepoets.co.uk/2014/debian-http_proxy-setting/>


### 엉켜버린 hash sum 문제

* 해쉬가 맞지 않고 저장소가 깨졌다, 연결이 안된다 등 문제 발생

```bash

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ftp.uk.debian.org wheezy Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://ftp.uk.debian.org wheezy-updates Release: The following signatures were invalid: NODATA 1 NODATA 2

W: Failed to fetch http://security.debian.org/dists/wheezy/updates/contrib/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://security.debian.org/dists/wheezy/updates/main/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://security.debian.org/dists/wheezy/updates/non-free/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/trusty/main/source/Sources  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/trusty/main/binary-amd64/Packages  Hash Sum mismatch

W: Failed to fetch http://ppa.launchpad.net/webupd8team/java/ubuntu/dists/trusty/main/i18n/Translation-en  Hash Sum mismatch

W: Failed to fetch http://ftp.uk.debian.org/debian/dists/wheezy/Release

W: Failed to fetch http://ftp.uk.debian.org/debian/dists/wheezy-updates/Release
```

### 현상에 따른 여러 방법들

* Debian - Apg-get : NO_PUBKEY / ERROR ( 퍼블릭 키 재 인증)
  * 해당 방법은 저장소 문제로 실패 
  * <http://www.commentcamarche.net/faq/4445-debian-apt-get-no-pubkey-gpg-error>


* DEB으로 설치 중 의존성 에러가 나면?
  * 강제 설치 명령어 (sudo apt-get -f install) 설명이 나옴 
  * <http://moordev.tistory.com/110>

* 깔끔한 처리를 위한 저장소 정리
  * 참조 <http://stackoverflow.com/questions/15505775/debian-apt-packages-hash-sum-mismatch>
 ```bash
sudo apt-get clean
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

# 또는
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean sudo apt-get update
```

### wheezy 저장소 찾기

* wheezy 자체가 oldstable..
* 소스관리가 안되어서 expire 나는 경우 - Updates for this repository will not be applied.
  * 다른 저장소로 바꾸어 주면 됨
  * <http://vhrms.tistory.com/m/378>
  * <http://www.potatogim.net/wiki/%EC%9C%84%ED%82%A4%EB%A1%9C%EA%B7%B8:2014/08/26_apt-get_%ED%98%B9%EC%9D%80_apttitude_%EC%A0%80%EC%9E%A5%EC%86%8C%EC%9D%98_%EA%B8%B0%EA%B0%84_%EB%A7%8C%EB%A3%8C>

* 영국 저장소 - Cannot update Debian Wheezy due to GPG error (NODATA)
  * 그나마 관리가 좀 되어 있음
  * <http://serverfault.com/questions/713299/cannot-update-debian-wheezy-due-to-gpg-error-nodata>

* Debian worldwide mirror sites
  * /etc/apt/source.list 목록 만들어 주는 곳
    * <https://debgen.simplylinux.ch/#>
    * <https://www.debian.org/mirror/list>





