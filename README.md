# Dialingo — AI 기반 실시간 음성 방언-외국어 통역 서비스

> 2023 제1회 K-디지털 플랫폼 AI 경진대회 **우수상** · 4인 팀 · 2일 (2023.12.12~13)

한국어 방언 사용자와 외국인의 소통을 위해, 방언 음성을 인식해 외국어로 통역하는 서비스입니다.

![image](https://github.com/user-attachments/assets/92edddd9-ab41-464b-91b8-f784c14ca08f)
![image](https://github.com/user-attachments/assets/fa8ea35f-46ac-4d7b-b69e-1b76f0bc6bd5)

## 구조

```
방언 음성 → Azure STT → 방언-표준어 번역 모델(Transformer) → Azure Translator → 외국어
```

- **번역 모델** — AI Hub 지역별 방언 발화 데이터(충청·경상·전라·제주)로 학습.
  구현은 [dltkddn0525/kr-dialect-machine-translation](https://github.com/dltkddn0525/kr-dialect-machine-translation)을 기반으로 했습니다.
- **학습된 모델** — `myproject/translator/results/model.pth`, 토크나이저 `myproject/translator/dataset/bpe_4000.model`
- **웹** — Django. 데모 음성은 `myproject/media/recordings/`
- **배포** — Azure 웹앱 CI/CD (대회 계정 지원 종료로 현재 중단)

## 담당 (PM & Data Scientist)

- 프로젝트 기획, 방언 데이터 수집·전처리
- 방언-표준어 번역 모델 학습
- Azure Speech·Translator 리소스 구성
- 대회 3일 전 팀 구성 → 24시간 내 MVP 완성

## 한계와 다음 과제

Azure 음성 인식이 방언을 표준어만큼 잡아내지 못해 실사용 정확도가 아쉬웠습니다.
방언 음성으로 직접 학습한 인식 모델로 교체하는 것이 다음 과제입니다.

TTS를 붙이면 양방향 음성 대화가 되고, 데이터가 확보되면 외국어 쪽 방언으로도 확장할 수 있습니다.
