제돈햄칼 bot
==================================
## 목차

> 1. [프로젝트 소개](#프로젝트-소개)
>    
>      * 팀원 소개
>
> 2. [전체 파이프라인](#전체-파이프라인)
> 
> 3. [기술 스택](#기술-스택)
> 
> 4. [모델](#모델)
>
>      * Feature Engineering
>      * 정확도 분석
>  
> 5. [주요 기능](#주요-기능)
>
>      * 정상 URL 탐지 시
>      * 악성 URL 탐지 시
>
> 6. [시연 영상](#시연-영상)
> 
> 7. [개선 사항](#개선-사항)
<br>
<br>

# 프로젝트 소개

>KISIA에서 주최한 AI보안 기술 개발 네트워크반 교육에서 진행하는 프로젝트입니다.
>
>최근 악성 URL로 인한 피해가 커지고 있어 이를 악성 URL 탐지를 주제로 선정하였습니다.
>
>AI 모델은 문자열 기반으로 악성 URL 여부를 탐지하며, 악성일 경우 어떤 종류인지 분류합니다.
>
>세계적으로 많은 사용자를 보유한 '디스코드'속 편의 기능을 도와주는 '디스코드 봇'과 학습한 AI 모델을 연동하였습니다.
>
>채팅 속 URL이 올라오는 즉시 이를 탐지하여 악성 여부 및 WHOIS API를 통한 도메인 정보를 제공합니다.
>
>discord.py 모듈을 사용하여 디스코드 봇 기능을 구현하였습니다.
>
>디스코드 봇과의 연계성 및 기능 수행 최적화를 위해 Heroku 를 이용해 배포하였습니다.
<br>

### 팀원 소개

<br>

| PL<br>남정운                                                                                                                                | TL<br>정민성                                                                                                                                | 팀원<br>김용범                                                                                                                              | 팀원<br>강승구                                                                                                                              | 팀원<br>한승헌                                                                                                                              |
|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| <p align="center"><img src="https://github.com/user-attachments/assets/17984ec1-4d16-427e-89ed-ca4e42478b62" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/020342da-9da4-45cf-a756-44d3f102d723" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/9fe7ca3b-eeb5-4984-b063-34545cdf2456" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/a5e88cbb-4696-461f-978f-edf95d58d054" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/0588dae5-edca-45d4-a85f-e4c8428e640c" width="140" height="200"/></p> |
| `Feature Engineering`<br>`SVM 학습`<br>`디스코드 봇 구현 및 배포`                                                                             | `Feature Engineering`<br>`XGB 학습`<br>`기술적 피드백`                                                                                | `Feature Engineering`<br>`Random Forest 학습`<br>`데이터셋 분류&연구`                                                                 | `Feature Engineering`<br>`LGBM 학습`                                                                                                    | `Decision Tree 학습`<br>`학습 모델 분류`<br>`데이터셋 관리`                                                                           |



<br>
<br>

# 전체 파이프라인

>
><img src="https://github.com/user-attachments/assets/7a25dca1-cace-4b46-bd9f-c58d62428ce3"/>
>
> 1. Heroku 및 Github를 이용하여 **제돈햄칼 봇**을 배포하였습니다.
> 2. **제돈햄칼 봇**은 디스코드 사용자들의 채팅 속 URL의 유무를 탐지합니다.
> 3. URL을 탐지한 경우, 해당 URL의 정상/악성 여부를 분류합니다.
> 4. 분류 결과와 WHOIS API를 이용한 기타 정보를 사용자에게 제공합니다.
<br>
<br>

# 기술 스택
   
>
><img src="https://github.com/user-attachments/assets/7c54e3c0-afd0-4a6d-a892-d87f937b2046" width="500" height="400"/>

<br>
<br>

# 모델
>
>
### Feature Engineering
>
><img src="https://github.com/user-attachments/assets/da7ce42a-4605-49af-9d5e-1a78a554e30d" width="200" height="200"/>
><img src="https://github.com/user-attachments/assets/94e40381-8369-4d8b-b794-ed5ecc70ed9d" width="200" height="200"/>
>
> 프로젝트의 시작부터 끝까지 다양한 Feature를 추출하였습니다.
>
> Feature 간 상관관계 및 SHAP value를 비교하여 아래 최종 Feature를 추출하였습니다.
>
<br>
<br>

|         **count '-'**         |         **count '?'**         |         **count '/'**         |         **count '='**         |         **count '.'**         |
|:-----------------------------:|:-----------------------------:|:-----------------------------:|:-----------------------------:|:-----------------------------:|
| `URL 속`<br>`- 개수 추출` | `URL 속`<br>`? 개수 추출` | `URL 속`<br>`/ 개수 추출` | `URL 속`<br>`= 개수 추출` | `URL 속`<br>`. 개수 추출` |
|         **URL_length**        |        **PATH_length**        |                               |                               |                               |
|         `URL 길이 추출`         |      `URL PATH 길이 추출`       |                               |                               |                               |
|        **URL_has_file**       |         **use_of_IP**         |          **entropy**          |       **dom_ALEXA_rank**      |                               |
|  `URL 속 파일 확장자`<br>`포함 여부` | `도메인 속 IP`<br>`포함 여부` |   `URL 문자열의`<br>`엔트로피 값 추출`   |    `도메인의 ALEXA`<br>`순위 유무`   |                               |


### 정확도 분석
>
>
|      학습 모델      | 정확도<br>Accuracy |
|:-------------------:|:----------------------:|
|         LGBM        |         88.47%         |
|         XGB         |         90.11%         |
|         SVM         |         89.63%         |
|    Decision Tree    |         90.23%         |
| **_Random Forest_** |      **_91.63%_**      |
>
> 위 Feature를 사용하여 모델들을 학습시키고, 각 모델들의 정확도를 비교한 결과 **Random Forest**가 가장 높은 정확도를 보여 해당 모델로 최종 선택하였습니다.
>
<br>
<br>


# 주요 기능
>
### 정상 URL 탐지 시
><img src="https://github.com/user-attachments/assets/cd60b71c-fde4-4af5-82bc-5e602bfcd428"/>
>
> 탐지한 URL이 정상 URL일 경우 결과 및 WHOIS API를 이용한 URL 정보를 제공합니다.
### 악성 URL 탐지 시
><img src="https://github.com/user-attachments/assets/859c2c59-df89-450d-834d-72c604e8cc27"/>
>
> 탐지한 URL이 악성 URL일 경우 해당 URL을 **스팸, 위/변조, 피싱, 악성코드 포함** 사이트로 분류하여 결과 및  WHOIS API를 이용한 URL 정보를 제공합니다.  
<br>
<br>

# 시연 영상
>
><img src="https://github.com/user-attachments/assets/25d2460a-c5cd-4b45-b7c9-8a44eaeaea84"/>
<br>
<br>

# 개선 사항
>
>    * 정확도 개선을 위해 다양한 데이터셋 탐색
> 
>    * 오탐, 미탐을 줄이기 위한 Feature 추출
> 
>    * WHOIS 외 더 많은 정보 획득 가능한 API 탐색
>
>    * 추가적인 보안 기능 방안 연구
>
<br>
<br>

### 데이터셋 출처
>
> ***한국인터넷진흥원 (KISA)*** <br>
> https://www.kisa.or.kr/
>
> ***URLHaus*** <br>
> https://urlhaus.abuse.ch/
>
> ***Kaggle "Malicious URLs dataset"*** <br>
> https://www.kaggle.com/datasets/sid321axn/malicious-urls-dataset
>
> ***Phishtank*** <br>
> https://phishtank.org/
>
> ***University if New Brunswick (2016). "ISCX-2016 dataset"*** <br>
> https://www.unb.ca/cic/datasets/url-2016.html
