제돈햄칼 (제육돈까스햄버거칼국수)
==================================
목차
1. 프로젝트 소개
   - 프로젝트 설명
   - 팀원 소개
 
2. 전체 파이프라인
3. 기술 스택
4. 주요 기능
   
  - 모델
       - 데이터셋
       - 후보 모델
       - 최종 선정 모델
  - 디코봇
       - 정상 돌렸을 때
       - 악성 돌렸을 때
   
5. 시연 장면
6. 개선 사항
<br>
<br>
1. 프로젝트 소개
<br>
- 프로젝트 설명
<br>
KISIA에서 주최한 AI보안 기술 개발 네트워크반 교육에서 진행하는 프로젝트입니다.
<br>
최근 악성 URL로 인한 피해가 커지고 있어 이를 악성 URL 탐지를 주제로 선정하였습니다.
<br>
AI 모델은 문자열 기반으로 악성 URL 여부를 탐지하며, 악성일 경우 어떤 종류인지 분류합니다.
<br>
세계적으로 많은 사용자를 보유한 '디스코드'속 편의 기능을 도와주는 '디스코드 봇'과 학습한 AI 모델을 연동하였습니다.
<br>
채팅 속 URL이 올라오는 즉시 이를 탐지하여 악성 여부 및 WHOIS API를 통한 도메인 정보를 제공합니다.
<br>
<br>
<br>
<br>
- 팀원 소개
<br>

| PL<br>남정운                                                                                                                                | TL<br>정민성                                                                                                                                | 팀원<br>김용범                                                                                                                              | 팀원<br>강승구                                                                                                                              | 팀원<br>한승헌                                                                                                                              |
|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| <p align="center"><img src="https://github.com/user-attachments/assets/17984ec1-4d16-427e-89ed-ca4e42478b62" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/020342da-9da4-45cf-a756-44d3f102d723" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/9fe7ca3b-eeb5-4984-b063-34545cdf2456" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/a5e88cbb-4696-461f-978f-edf95d58d054" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/0588dae5-edca-45d4-a85f-e4c8428e640c" width="140" height="200"/></p> |
| `Feature Engineering`<br>`SVM 학습`<br>`디스코드 봇 구현`                                                                             | `Feature Engineering`<br>`XGB 학습`<br>`기술적 피드백`                                                                                | `Feature Engineering`<br>`Random Forest 학습`<br>`데이터셋 분류&연구`                                                                 | `Feature Engineering`<br>`LGBM 학습`                                                                                                    | `Decision Tree 학습`<br>`학습 모델 분류`<br>`데이터셋 관리`                                                                           |



<br>
<br>
2. 전체 파이프라인
<br>
<img src="https://github.com/user-attachments/assets/7a25dca1-cace-4b46-bd9f-c58d62428ce3"/>
<br>
<br>
3. 기술 스택
<br>
<img src="https://github.com/user-attachments/assets/7c54e3c0-afd0-4a6d-a892-d87f937b2046" width="500" height="400"/>
<br>
<br>
4. 주요 기능
<br>
- 모델
<br>
* 학습 모델 후보



- 디스코드
<br>
사용자가 채팅에 URL을 올림 -> URL은 디스코드 봇과 연동된 모델이 분류 -> 정상/악성 분류 -> 악성이면 다시 4가지로 분류 -> 기타 정보까지 함께 결과 채팅에 올려줌
<br>
<br>
5. 시연 장면
<br>
[![유튜브 썸네일]("https://github.com/user-attachments/assets/5f7ec61a-e1d5-484a-a71b-b133a3333c98")]("https://youtu.be/gLWFPLfxF_w")
<br>
<br>
6. 개선 사항
