# CI/CD

- CI/CD를 Jenkins 를 통해서 사용해본적이 있으나 자세한 개념과 관리는 해본 적이 없어 알아보기위함.
- 어플리케이션 개발 단계부터 배포 때까지 자동화를 통해서 효율적으로 배포할 수 있도록 만드는 것

![image](https://github.com/wltnthss/Skils/assets/60785586/03f57d77-395d-4d61-a609-c4f59408ce87)

## CI/CD의 필요성

![image](https://github.com/wltnthss/Skils/assets/60785586/79a40ac5-a95c-4252-80de-ac56945246ca)

* 처음부터 CI/CD (Jenkins)를 사용해와서 CI/CD가 없을 떄 어떻게 하는지 알아보기위함.
* 직접 jar파일을 빌드한 후, FTP를 사용하여 서버에 올린 후 java -jar로 직접 실행시켜야함. 자잘한 변경사항이 생기면 또 다시 빌드 - 전송 - 직접 실행 후 서버에 올라가면 테스트까지 진행해야했음.

## CI(Continuous Integration)

* 지속적인 통합이라고 부름.
* main repository 에 주기적으로 빌드하고 테스트하고 머지.
* 코드 변경사항을 주기적으로 빈번하게 머지해야함.
* 주기적으로 머지된 것을 자동으로 빌드되어야하고 자동으로 테스트까지 되어야함.
  * ex) Main Branch에서 하루에 코드를 변경한 것을 머지함 -> CI Script를 통해 Build 후 Test함.
* Merge 충돌을 피함으로써 개발 생산성이 향상되고 버그 수정에 용이하며 코드의 퀄리티가 향상됨.

## CD(Continuous Deployment OR Continuous Delivery)

* 지속적 제공 및 배포라고 부름.
  * ex) CI를 통해서 주기적으로 Merge하고 Build하고 Test 후 검증팀이 검증 후 사용자에게 배포할 것이 결정되면 수동적으로 배포하는 것이 CD(Continuous Delivery)
    라고 함. 또는 release 준비가 되자마자 자동으로 배포하는 것을 CD(Continuous Deployment) 라고 부름.
    즉, 최종적으로 자동적으로 모든 배포를 설정하는 것을 Continuous Deployment 라 부름.

## CI/CD 과정

![image](https://github.com/wltnthss/Skils/assets/60785586/e7a3c9dd-df87-419a-8fc7-97bea83f2e5c)

전반적인 CI/CD의 흐름은 위와 같음.

