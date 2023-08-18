# Docker

* Docker 는 SM으로 KT 업무 당시 사수에게 어깨너머로 들어는 보았으나 자세히 개념을 몰라 정리하고자함.

## Docker 개념

* Docker 란 어플리케이션을 패키징 할 수 있는 툴. 
* 컨테이너(container)라고 불리는 하나의 작은 소프트웨어 유닛안에 어플리케이션, 환경설정, 디펜던시를 배포할 수 있도록 도와주는 툴

즉, 어플리케이션을 구동하기위한 모든 것들을 Docker Container안에 담아 놓음.

> Docker VS Virtual Machine

### Virtual Machine
* Virtual Machine 은 하이퍼 바이저를 이용해 여러 개의 운영체제를 하나의 호스트에서 생성해서 사용했음.
* 시스템 자원을 가상화하고 독립된 공간을 생성하는 작업이 HyperVisor를 거치고, OS를 사용하기위한 라이브러리, 커널 등을 포함하므로
* 성능 손실이 크고, 배포할 때 용량이 크므로 요즘은 Docker를 사용함.

### Docker
* Docker는 컨테이너에 필요한 커널을 공유해서 사용하고, 어플리케이션을 구동하는데 필요한 라이브러리 및 실행 파일만 존재하므로 용량이 줄어듬.
* 가상화된 공간을 생성할 때 리눅스 자체 기능을 사용하여 프로세스 단위의 격리 환경을 만드므로 성능 손실이 없음.
* 가상머신과 달리 커널을 공유해서 사용하고, 컨테이너에는 라이브러리와 실행파일만 존재하므로 용량이 작음.  

![image](https://github.com/wltnthss/Skils/assets/60785586/495dfc53-94c1-4dba-aa72-836de6c00a3e)

Container Engine 중에 가장 많이 사용하는 것이 Docker 라는 것임.

Container Engine이 Host OS 접근해서 필요한 것들을 처리해줌.

### Docker 구성요소

Docker의 큰 그림은 컨테이너를 만들고 구성하고 배포함.

![image](https://github.com/wltnthss/Skils/assets/60785586/ccb86bf3-b272-4064-9dcd-c7a796dea6cd)

* Dockerfile 은 컨테이너를 어떻게 만드는지 설명서와 같음.
  * 필요한 파일, 어떤 라이브러리, 필요한 환경변수, 스크립트 등
  * docker build 명령어를 통해 도커 이미지를 만들 수 있음.
* Image 는 어풀리케이션을 실행하는데 필요한 코드, 런타임환경, 시스템툴 등 세팅이 포함됨
  * 실행되고 있는 어플리케이션 상태를 이미지화 (불변의 상태) 함
  * docker run 명렁어를 실행하면 Docker Container 를 만들 수 있음.
  * [저장소 이름]/[이미지 이름]:[태그] 기본적인 형태로 구성됨.
* Container 는 어플리케이션의 이미지를 고립된 환경에서 실행수 있음.
  * 컨테이너안에서 어플리케이션이 동작된다 라고 볼 수 있음.
  * 준비한 Image를 활용해서 어플리케이션을 구성함.
  * Image는 class와 같다고 봄.
  * 각각의 컨테이너는 인스턴스와 같다고 봄.

### Docker 실행 흐름

1. Local Machine, Servcer 에 Docker를 설치함
2. Dockerfile 을 작성한 다음 어플리케이션을 스냅샷할 Image를 Build 함.
3. 이미지를 Container Registry 에 올림
4. Server에서 Image를 다운(Pull)해서 컨테이너를 실행(Run)함.
