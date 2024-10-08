# TALCAR
**It is a corporate car rental service.**
1. 공휴일, 주말에 법인 차량을 사적 목적으로 대여 가능하도록 한다.
2. 서비스 내 가중치를 바탕으로 랜덤 추첨을 진행한다.

## Introduce

### Key-Point
- 가중치:
  - 선착순이 아닌 임직원의 가중치를 고려해서 랜덤 추첨
  - 가중치 랜덤 뽑기 알고리즘(Weighted Random Picker)을 바탕으로 추첨을 진행
- 패널티:
  - 불량 이용자에게 패널티를 부여
  - 패널티 종류: Black, 상, 중, 하, 최하
    - Black - 영구 정지
    - 상 / 중 / 하 - 52주 / 12주 / 4주 정지
    - 최하 - 2주 정지
- 재배정:
  - 취소 기간 동안 신청이 취소된 차량에 대해서 재배정을 진행
- 차량 관리:
  - 차량의 유류, 사고, 인수 반납 등의 사항에 대해서 체계적인 관리를 통해 차량을 관리
  - 관리자가 불량 이용자를 찾기에 더욱 용이
  - 차량 정보 DB 저장

### Expectation Effectiveness
- 기존보다 저렴한 비용으로 차량을 대여할 수 있다.
- 휴일에 사용하지 않는 법인 차량을 효율적으로 사용할 수 있다.
- 가중치를 포함한 랜덤 추첨을 통해 모두가 차량 대여 복지를 누릴 수 있도록 한다.

## Market Research
> **위드웹**
> 
> 주말, 공휴일 등 공식적인 업무를 하지 않는 날에, 법인차량 6대를 직원에게 무료로 대여한다.
>
> 장점:
> - 4인승~11인승까지 다양한 용도의 차량이 존재
> - 원하는 목적에 맞춰 차량 선택 가능
>   
> 단점:
> - 법인 차량 선착순 제공

> **LG전자**
>
> 유휴 법인 차량을 업무가 없는 주말에 직원에게 무료로 대여한다.
>
> 장점:
> - 고급 세단~승용차까지 다양한 종류의 존재
> - 원하는 목적에 맞춰 차량 선택 가능
>   
> 단점:
> - 공휴일 사용 불가능

### 개선이 필요한 부분
1. 선착순 / 단순 무작위 추첨
    → 사용자별 가중치를 설정하고, 가중치를 고려하여 추첨을 진행

2. 전용 플랫폼이 존재하지 않음
    → 모바일 기기, PC 등 다양한 환경에서 사용 가능한 플랫폼

3. 명확하지 않은 제재 기준 
    → 상황에 따른 제재 기준을 정하고, 관리자 페이지에서 쉽게 패널티를 적용

4. 차량 재배정의 간략화
    → 취소된 차량에 대해서 자동으로 사용자에게 재배정

## 사용자 DEMO
| <img src="https://github.com/user-attachments/assets/f2e0b107-4868-4d27-a69f-596832bfff23" height="300">                                                                                                             |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 로그인 페이지로 아이디의 권한에 따라서 라우팅이 된다.<br/><br/> **사용자** <br/>ID : hoan.c9907@gmail.com <br/>PW : password205<br/><br/> 만약 관리자 페이지도 보고싶다면 아래 정보를 입력하면 된다.<br/> **관리자**  <br/> ID : admin@kakaocorp.com<br/> PW : password205 |
<br/>

### 사용자 메인
| <img src="https://github.com/user-attachments/assets/d0534bfc-a895-4166-bfb8-ade04e035563" height="500"> |
|----------------------------------------------------------------------------------------------------------|
| 사용자 페이지의 로그인시 처음 화면이다.<br/> 다음 버튼을 눌러 차량 신청으로 이동 가능하다.                                                   |
<br/>

### 차량 신청
| <img src="https://github.com/user-attachments/assets/128978de-a506-4305-af3e-b489af544cac" height="400"> | <img src="https://github.com/user-attachments/assets/022ea57d-489e-4017-88c5-f2aafee496d6" height="400"> | <img src="https://github.com/user-attachments/assets/62661f86-bfe6-4a07-b398-cf3ef02ab337" height="400"> |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| 스케줄러로 생성한 이용 가능한 차량에 대한 신청을 선택할 수 있다.                                                                    | 신청시에 바로 신청 정보를 확인할 수 있다.                                                                                 | 신청 정보를 수정하거나 취소하는 작업을 할 수 있다.                                                                            |
<br/>

### 차량 대여


| <img src="https://github.com/user-attachments/assets/d0534bfc-a895-4166-bfb8-ade04e035563" height="400"> | <img src="https://github.com/user-attachments/assets/020707c8-b3c6-456f-891c-694b941ae42e" height="400"> | <img src="https://github.com/user-attachments/assets/3e29af13-d107-4e1a-ace6-d78ec01c139a" height="400"> |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|
| 신청에 당첨된 사용자는 화면 중앙 하단에 인수 버튼이 생기게 된다.<BR/> 버튼 클릭 시에 차량 인수 과정으로 넘어가게 된다.                                  | 차량 대여 시에 앞, 뒤, 좌, 우에 대해서 사진을 제출해야한다.                                                                     | 사진을 제출시에 하단의 이미지가 체크표시로 바뀐다.<BR/> 이때 이미지를 제출하지 않으면 다음 단계로 이동할 수 없다.                                      |
| <img src="https://github.com/user-attachments/assets/3d2ee153-630d-459a-8914-3ae7fdc96ab8">              | <img src="https://github.com/user-attachments/assets/332d1db6-cdfe-4d17-83c6-510d5c04991f">              | <img src="https://github.com/user-attachments/assets/251a79af-87bc-45fb-9fe2-a6eed48e59cc">              |
| 차량의 인수 전 유류상황을 확인합니다.                                                                                    | 차량 인수 시 특이사항을 작성합니다.<BR/> ex) 흠집, 담배 냄새, 쓰레기 등                                                           | 신청 완료 이후 내역을 확인 할 수 있다.                                                                                  |

| <img src="https://github.com/user-attachments/assets/21ef5dd6-4661-4092-b736-4119d38a3fe1" height="400"> | <img src="https://github.com/user-attachments/assets/01a4ab6c-9dd1-4dca-9f32-998bf37641ef" height="400"> | <img src="https://github.com/user-attachments/assets/b62073f2-8c26-4cd6-8a31-a990c4330a8f" height="400"> |
|----------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| 차량 반납 시에 앞, 뒤, 좌, 우에 대해서 사진을 제출해야한다.<BR/> 버튼 클릭 시에 차량 인수 과정으로 넘어가게 된다.                                   | 사진을 제출시에 하단의 이미지가 체크표시로 바뀐다.<BR/> 이때 이미지를 제출하지 않으면 다음 단계로 이동할 수 없다.                                      | 반납 시 특이사항을 제출한다. <br/> ex) 차량 사고, 반납 지연 사유 등                                                            |
| <img src="https://github.com/user-attachments/assets/3d2ee153-630d-459a-8914-3ae7fdc96ab8">              | <img src="https://github.com/user-attachments/assets/079b2e85-e2c3-489f-8ba4-24c2e813d116">              | <img src="https://github.com/user-attachments/assets/a241d6c9-7a3c-4f7a-bcb3-5831930ffd9a">             |
| 차량의 반납 전 유류상황을 확인합니다.                                                                                    | 차량 반납 시 주차 위치를 작성합니다.                                                       | 반납 이후에 내역을 확인 할 수 있다.                                                                                   |

    
## HOW TO USE
FE: [ReadME](https://github.com/KEA-ENTER/ENTER-FE/blob/develop/README.md)

BE: [ReadME](https://github.com/KEA-ENTER/ENTER-BE/blob/develop/README.md)

## Technology
**FE**
<img src="https://img.shields.io/badge/react-61DAFB?style=for-the-badge&logo=react&logoColor=black">
<img src="https://img.shields.io/badge/node.js-339933?style=for-the-badge&logo=Node.js&logoColor=white">
<img src="https://img.shields.io/badge/styledcomponents-DB7093?style=for-the-badge&logo=styledcomponents&logoColor=white">
<img src="https://img.shields.io/badge/nivo-231815?style=for-the-badge&logo=nivo&logoColor=white">

**BE**
<img src="https://img.shields.io/badge/springboot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white">
<img src="https://img.shields.io/badge/JPA-231815?style=for-the-badge&logo=JPA&logoColor=white">
<img src="https://img.shields.io/badge/java-007396?style=for-the-badge&logo=java&logoColor=white">
<img src="https://img.shields.io/badge/gradle-02303A?style=for-the-badge&logo=gradle&logoColor=white">
<img src="https://img.shields.io/badge/springsecurity-6DB33F?style=for-the-badge&logo=springsecurity&logoColor=white">
<img src="https://img.shields.io/badge/jwt-231815?style=for-the-badge&logo=jwt&logoColor=white">

**DB**
<img src="https://img.shields.io/badge/redis-FF4438?style=for-the-badge&logo=redis&logoColor=white">
<img src="https://img.shields.io/badge/mysql-4479A1?style=for-the-badge&logo=mysql&logoColor=white">
<img src="https://img.shields.io/badge/kc-objectstorage-231815?style=for-the-badge&logo=kc-objectstorage&logoColor=white">

**TEST**
<img src="https://img.shields.io/badge/junit5-25A162?style=for-the-badge&logo=junit5&logoColor=white">
<img src="https://img.shields.io/badge/mockito-231815?style=for-the-badge&logo=mockito&logoColor=white">
<img src="https://img.shields.io/badge/apachejmeter-D22128?style=for-the-badge&logo=apachejmeter&logoColor=white">

**INFRA**
<img src="https://img.shields.io/badge/jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white">
<img src="https://img.shields.io/badge/vault-FFEC6E?style=for-the-badge&logo=vault&logoColor=white">
<img src="https://img.shields.io/badge/loki-231815?style=for-the-badge&logo=loki&logoColor=white">
<img src="https://img.shields.io/badge/prometheus-E6522C?style=for-the-badge&logo=prometheus&logoColor=white">
<img src="https://img.shields.io/badge/kakaocloud-231815?style=for-the-badge&logo=kakaocloud&logoColor=white">
<img src="https://img.shields.io/badge/grafana-F46800?style=for-the-badge&logo=grafana&logoColor=white">
<img src="https://img.shields.io/badge/docker-2496ED?style=for-the-badge&logo=docker&logoColor=white">

***
### Member
![image](https://github.com/user-attachments/assets/cad77119-3e22-4a19-8c52-2191e09adf5d)


