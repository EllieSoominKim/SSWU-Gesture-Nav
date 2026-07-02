# SSWU Gesture Nav 🖐️💻

[English](README.md) | [한국어](README.ko.md)

웹캠으로 동작(제스처)을 인식해서 정해진 사이트를 새 탭으로 열어주는 브라우저 기반 도구입니다. Google의 Teachable Machine으로 학습한 이미지 분류 모델과 TensorFlow.js를 사용합니다.

## 📺 데모

[▶️ 데모 영상 보기](https://drive.google.com/file/d/1MbhxkCxRtlWEpIQS9_mOURxL9ogOnunT/view?usp=sharing)

## 📌 개요

이 프로젝트는 특정 동작(예: 손 흔들기, 특정 포즈 등)을 웹캠으로 인식하여, 미리 지정한 사이트(학교 포털, LMS, 도서관 등)를 자동으로 열어주는 개인용 단축키 도구입니다. 별도의 설치 없이 브라우저에서 바로 실행할 수 있습니다.

## ✨ 동작 방식

1. "시스템 시작하기" 버튼을 누르면 Teachable Machine 모델을 불러오고 웹캠을 활성화합니다.
2. 웹캠 화면을 실시간으로 분석하여 등록된 동작 클래스 중 하나와 **95% 이상 일치**하면 해당 동작을 인식합니다.
3. 인식된 동작에 매칭된 URL을 새 탭으로 엽니다.
4. 같은 동작이 반복 인식되어도 **5초 이내에는 중복으로 창이 열리지 않도록 방지**합니다.

## 🛠️ 사용 기술

| 기술 | 역할 |
| --- | --- |
| [TensorFlow.js](https://www.tensorflow.org/js) | 브라우저에서 머신러닝 모델 실행 |
| [Teachable Machine](https://teachablemachine.withgoogle.com/) | 이미지 분류 모델 학습 |

## 🚀 사용 방법

### 1. 모델 학습하기
[Teachable Machine](https://teachablemachine.withgoogle.com/train/image)에서 원하는 동작(클래스)을 학습시키고 모델을 게시(Export)하여 모델 주소를 얻습니다.

### 2. 모델 주소 설정하기
`index.html` 파일의 `URL` 변수를 본인의 모델 주소로 교체합니다.

```javascript
// index.html
const URL = "본인의_모델_주소";
```

### 3. 동작과 사이트 매칭하기
`SITES` 객체에 클래스 이름과 열고 싶은 사이트 주소를 매칭합니다. 클래스 이름은 Teachable Machine에서 설정한 이름과 정확히 일치해야 합니다.

```javascript
// index.html
const SITES = {
    "클래스이름1": "https://example.com/",
    "클래스이름2": "https://example2.com/"
};
```

### 4. 실행하기
`index.html` 파일을 브라우저에서 열고 "시스템 시작하기" 버튼을 누른 뒤, 웹캠 접근 권한을 허용하면 사용할 수 있습니다.

## ⚙️ 커스터마이징

이 저장소의 예시 코드에는 특정 학교(성신여자대학교)의 포털, LMS, 도서관 주소가 예시로 들어 있습니다. 본인의 용도에 맞게 `SITES` 객체의 이름과 주소를 자유롭게 수정해서 사용하시면 됩니다.

## 🔒 주의 사항

- 이 도구는 웹캠 영상을 실시간으로 처리하지만, 영상이나 예측 결과를 별도로 저장하거나 외부로 전송하지 않습니다. 모든 처리는 브라우저 내에서만 이루어집니다.
- 인식 정확도는 학습에 사용한 이미지의 품질과 다양성에 따라 달라질 수 있습니다.
- 개인 학습 목적의 프로젝트입니다.
