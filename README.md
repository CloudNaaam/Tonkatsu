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
<img src="https://github.com/user-attachments/assets/ff0693ba-bdd3-46e6-bfe6-dadd5933b7a0" width="500" height="400"/>
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
ㅁㄴㅇㅁㄴㅇ
<br>
<br>
6. 개선 사항
