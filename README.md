제돈햄칼 bot
==================================
## 목차

> 1. [Introduction](#introduction)
>    
>   - 팀원 소개
>
> 2. [Pipeline](#pipeline)
> 
> 3. [Skill](#skill)
> 
> 4. [Model](#model)
>
>   - Feature Engineering
>   - 정확도 분석
>  
> 5. [Function](#function)
>  - 디코봇
>       - 정상 돌렸을 때
>       - 악성 돌렸을 때
>
> 6. [Preview](#preview)
> 
> 7. [Improvement](#improvement)
<br>
<br>

# Introduction

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
<br>
<br>

### 팀원 소개

<br>

| PL<br>남정운                                                                                                                                | TL<br>정민성                                                                                                                                | 팀원<br>김용범                                                                                                                              | 팀원<br>강승구                                                                                                                              | 팀원<br>한승헌                                                                                                                              |
|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| <p align="center"><img src="https://github.com/user-attachments/assets/17984ec1-4d16-427e-89ed-ca4e42478b62" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/020342da-9da4-45cf-a756-44d3f102d723" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/9fe7ca3b-eeb5-4984-b063-34545cdf2456" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/a5e88cbb-4696-461f-978f-edf95d58d054" width="140" height="200"/></p> | <p align="center"><img src="https://github.com/user-attachments/assets/0588dae5-edca-45d4-a85f-e4c8428e640c" width="140" height="200"/></p> |
| `Feature Engineering`<br>`SVM 학습`<br>`디스코드 봇 구현`                                                                             | `Feature Engineering`<br>`XGB 학습`<br>`기술적 피드백`                                                                                | `Feature Engineering`<br>`Random Forest 학습`<br>`데이터셋 분류&연구`                                                                 | `Feature Engineering`<br>`LGBM 학습`                                                                                                    | `Decision Tree 학습`<br>`학습 모델 분류`<br>`데이터셋 관리`                                                                           |



<br>
<br>

# Pipeline

<br>
<img src="https://github.com/user-attachments/assets/7a25dca1-cace-4b46-bd9f-c58d62428ce3"/>
<br>
<br>
<br>

# Skill
   
<br>
<img src="https://github.com/user-attachments/assets/7c54e3c0-afd0-4a6d-a892-d87f937b2046" width="500" height="400"/>
<br>
<br>
<br>

# Model

<br>
- Feature Engineering
<img src="https://github.com/user-attachments/assets/da7ce42a-4605-49af-9d5e-1a78a554e30d" width="200" height="200"/>
<img src="https://github.com/user-attachments/assets/94e40381-8369-4d8b-b794-ed5ecc70ed9d" width="200" height="200"/>
<br>
<br>

|         **count '-'**         |         **count '?'**         |         **count '/'**         |         **count '='**         |         **count '.'**         |
|:-----------------------------:|:-----------------------------:|:-----------------------------:|:-----------------------------:|:-----------------------------:|
| `URL 속`<br>`- 개수 추출` | `URL 속`<br>`? 개수 추출` | `URL 속`<br>`/ 개수 추출` | `URL 속`<br>`= 개수 추출` | `URL 속`<br>`. 개수 추출` |
|         **URL_length**        |        **PATH_length**        |                               |                               |                               |
|         `URL 길이 추출`         |      `URL PATH 길이 추출`       |                               |                               |                               |
|        **URL_has_file**       |         **use_of_IP**         |          **entropy**          |       **dom_ALEXA_rank**      |                               |
|  `URL 속 파일 확장자`<br>`포함 여부` | `도메인 속 IP`<br>`포함 여부` |   `URL 문자열의`<br>`엔트로피 값 추출`   |    `도메인의 ALEXA`<br>`순위 유무`   |                               |

<br>
<br>
<br>

# Function

<br>
- 모델
<br>
* 학습 모델 후보
<br>

|      학습 모델      | 정확도<br>Accuracy |
|:-------------------:|:----------------------:|
|         LGBM        |         88.47%         |
|         XGB         |         90.11%         |
|         SVM         |         89.63%         |
|    Decision Tree    |         90.23%         |
| **_Random Forest_** |      **_91.63%_**      |

<br>
<br>
- 디스코드
<br>
사용자가 채팅에 URL을 올림 -> URL은 디스코드 봇과 연동된 모델이 분류 -> 정상/악성 분류 -> 악성이면 다시 4가지로 분류 -> 기타 정보까지 함께 결과 채팅에 올려줌
<br>
<br>
<br>

# Preview

<br>
<img src="https://github.com/user-attachments/assets/25d2460a-c5cd-4b45-b7c9-8a44eaeaea84"/>
<br>
<br>
<br>

# Improvement

- 정확도 개선을 위해 다양한 데이터셋 탐색
- 오탐, 미탐을 줄이기 위한 Feature 추출
- WHOIS 외 더 많은 정보 획득 가능한 API 탐색
- 추가적인 보안 기능 방안 연구

