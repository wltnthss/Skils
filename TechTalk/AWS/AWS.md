# AWS

## 개요

*  AWS 아마존의 웹 서비스라고 알고있으며 대부분의 회사가 AWS를 사용한다해 개념 및 사용방법을 정리하고자함.
*  AWS 개념을 알기에 앞서 AWS도 클라우드 서비스이므로 클라우드 서비스를 먼저 정리하고자함.

## 클라우드

* 클라우드는 인터넷 상의 가상화된 서버에 프로그램을 두고 필요할때마다 자유롭게 쓰는 것을 말함.
* 그 중에서 AWS같은 경우는 IaaS(Infrastructure as a service)로 가상의 하드웨어를 제공받아 그 위에 올라가는 운영체제나 프로그램등을 모두 자유롭게 서비스로 이용하는 것임.

## 클라우드 서비스 장점

* 확장성
  * 직접 데이터센터를 구축할 필요가 없으므로 빠르게 원하는 만큼의 서비스 확장이 가능함.
* 탄력성
  * 서비스가 트래픽이 몰리는 경우에만 리소스를 많이 썻다가 빠지면 다시 되돌릴 수 있음.
* 접근성
  * 언제 어디서나 클라우드에 접근하거나 제공하는 서비스를 사용할 수 있음.
* 장애 허용성
  * 여러 공간에 나누어 저장함으로써 장애가 발생해도 데이터를 안전하게 막음.
  
## AWS 개념

AWS (Amazon Web Services) 로 아마존닷컴의 클라우드 컴퓨팅 사업부임.

![image](https://github.com/wltnthss/Skils/assets/60785586/b78cd729-d059-420a-bd15-df5bc69f6bf0)

* 유저가 서비스에 들어오면 AWS에 있는 데이터센터 중에서 구입한 만큼의 기능을 가진 서비스에 접근함.
* 구입한 부분을 모아둔 것을 VPC라고함.
  * VPC는(Virtual private Cloud)의 약자로 페이스북 내에서 내 포스트를 등록하듯이 VPC안에서 등록하는 가상 컴퓨터중 대표적인 것임.
* EC2(Elastic Cloud Compute)의 약자로 컴퓨터라고 생각하면됨.
  * 컴퓨터에 cpu, os, ram 등 가상의 공간에 나만의 컴퓨터를 등록하는 것임.
  * 웹사이트를 개발하기위한 코드를 만들면 코드를 넣어주고 동작하게 하는 컴퓨터로 사용함.
  * 대표적인 AWS 서비스로 RDS와 S3 가 있음.

## AWS 사용팁

* IAM내에서 100명 이상의 사용자를 등록하는 경우
* 쉘 커맨드를 이용해 AWS CLI 사용

```
// iam 은 사용하려는 서비스, create-user는 내리고 싶은 명령
ex)aws iam create-user --user-name example@example.com

while IFS= read -r email
do
   aws iam create-user --user-name $email  // 유저 생성
   aws iam add-user-to-group --group-name "crew" --user-name $email  // 그룹에 등록

done < "crew.txt"     
```
