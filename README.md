# 🌱 쓰버리 (SSbry) - AI 기반 스마트 분리배출 가이드

**Team**: [팀명 입력]

AI 기반 쓰레기 분류 시스템 - YOLOv8n 모델로 쓰레기를 자동 인식하고, 올바른 분리배출 방법을 안내하며, 에너지 절약 효과를 시각화하는 모바일 애플리케이션

---

## ⚠️ 배포 상태

현재 **Android APK 버전**이 배포되어 있습니다.

- **다운로드**: [Google Drive 링크](https://drive.google.com/drive/folders/13n6XdaZlxzuWlXpKfPHqG-SxXi9Pc5KS?usp=sharing)
- **플랫폼**: Android 전용

---

## 📖 프로젝트 소개

### 개발 배경

일상적인 쓰레기 분류를 넘어, **개인의 작은 실천이 어떻게 재생에너지 생산으로 이어지고, 탄소중립 사회를 만드는지** 정량적 데이터로 연결하는 프로젝트입니다.

단순히 쓰레기를 분류하는 것이 아니라, 분리배출된 쓰레기가 **재생에너지원으로 직간접적으로 사용**된다는 것을 알리고, 올바른 분리배출 습관을 유도합니다.

### 주요 특징

- **AI 자동 인식**: YOLOv8n 커스텀 모델로 갤러리 사진 속 쓰레기 자동 분류
- **6개 카테고리 분류**: 플라스틱, 종이, 유리, 캔류, 비닐류, 일반쓰레기
- **즉시 배출 가이드**: 올바른 분리배출 방법과 주의사항 안내
- **에너지 효과 시각화**: 절약액, 재생에너지 생산량(kWh), CO₂ 감축량 계산
- **게임화 요소**: 연못 생태계로 참여 유도
- **쓰레기 백과사전**: 카테고리별 상세 가이드 및 FAQ

### 시스템 흐름도

```
[사용자]
    ↓ (갤러리에서 쓰레기 사진 업로드)
[Flutter 앱]
    ↓
[ONNX Runtime]
    ↓ (이미지 전처리)
[YOLOv8n 모델]
    ├─→ 객체 탐지 (Bounding Box)
    ├─→ 분류 (6개 카테고리)
    └─→ 신뢰도 점수 계산
        ↓
[분류 결과]
    ├─→ 분리배출 방법 안내
    ├─→ 에너지 정보 제공
    │   ├─ 경제적 절약액
    │   ├─ 재생에너지 생산량 (kWh)
    │   └─ CO₂ 감축량 (소나무 그루 수)
    └─→ 연못 생태계 업데이트
        ↓
[사용자 대시보드]
    ├─→ 누적 통계 확인
    └─→ 환경 기여도 시각화
```

---

## 📸 프로젝트 스크린샷

### 모바일 인터페이스

#### 홈 화면

<img src="screenshots/home.png" width="300">

#### AI 분류 화면

<img src="screenshots/ai.png" width="300">

#### 통계 및 백과사전

<img src="screenshots/stats.png" width="300">

#### 연못 생태계

<img src="screenshots/pond.png" width="300">

---

## 📁 프로젝트 구조

```
SSbry/
├── lib/                          # Flutter 앱 소스코드
│   ├── main.dart                 # 앱 엔트리 포인트
│   ├── screens/                  # 화면 위젯
│   │   ├── home_screen.dart      # 홈 화면
│   │   ├── ai_classification_screen.dart  # AI 분류
│   │   ├── encyclopedia_screen.dart       # 쓰레기 백과사전
│   │   ├── pond_screen.dart      # 에너지 연못
│   │   └── statistics_screen.dart # 통계
│   ├── services/                 # 비즈니스 로직
│   │   ├── ml_service.dart       # ONNX 모델 추론
│   │   ├── image_service.dart    # 이미지 처리
│   │   └── energy_calculator.dart # 에너지 효과 계산
│   ├── models/                   # 데이터 모델
│   │   ├── trash_item.dart
│   │   └── classification_result.dart
│   └── widgets/                  # 재사용 컴포넌트
│       ├── category_card.dart
│       └── energy_info_widget.dart
│
├── assets/                       # 리소스 파일
│   ├── models/
│   │   └── yolov8n_trash.onnx    # YOLOv8n ONNX 모델
│   ├── images/                   # UI 이미지
│   └── data/
│       └── trash_guide.json      # 분리배출 가이드 데이터
│
├── ml/                           # 머신러닝 모델 개발
│   ├── dataset/                  # TrashNet 데이터셋
│   ├── train.py                  # 모델 학습 스크립트
│   ├── export_onnx.py            # ONNX 변환
│   └── config.yaml               # 학습 설정
│
├── screenshots/                  # README 이미지
├── android/                      # Android 설정
├── pubspec.yaml                  # Flutter 의존성
└── README.md
```

---

## 🎯 기술 스택

### 📱 Mobile

[![Flutter](https://img.shields.io/badge/Flutter-3.x-02569B?style=flat&logo=flutter&logoColor=white)](https://flutter.dev/)
[![Dart](https://img.shields.io/badge/Dart-0175C2?style=flat&logo=dart&logoColor=white)](https://dart.dev/)
[![Android Studio](https://img.shields.io/badge/Android_Studio-3DDC84?style=flat&logo=android-studio&logoColor=white)](https://developer.android.com/studio)

### 🤖 Machine Learning

[![YOLOv8](https://img.shields.io/badge/YOLOv8n-Custom_Model-00FFFF?style=flat)](https://github.com/ultralytics/ultralytics)
[![ONNX Runtime](https://img.shields.io/badge/ONNX_Runtime-005CED?style=flat&logo=onnx&logoColor=white)](https://onnxruntime.ai/)
[![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=flat&logo=pytorch&logoColor=white)](https://pytorch.org/)

### 🎨 Design & Data

[![Figma](https://img.shields.io/badge/Figma-F24E1E?style=flat&logo=figma&logoColor=white)](https://www.figma.com/)
[![환경부](https://img.shields.io/badge/환경부-Official_Data-green?style=flat)](https://www.me.go.kr/)

### ☁️ Deployment

[![Google Drive](https://img.shields.io/badge/Google_Drive-APK_Distribution-4285F4?style=flat&logo=google-drive&logoColor=white)](https://drive.google.com/)

---

## 🚀 주요 기능

### 1. AI 기반 쓰레기 자동 분류

- **위치**: `lib/services/ml_service.dart`
- **기능**:
  - 갤러리에서 사진 선택 또는 카메라 촬영
  - YOLOv8n 모델을 통한 실시간 객체 탐지
  - 6개 카테고리 분류 (플라스틱, 종이, 유리, 캔류, 비닐류, 일반쓰레기)
  - 다중 객체 동시 인식 지원
  - 신뢰도 점수 기반 결과 필터링
- **모델**: YOLOv8n (ONNX 포맷, Opset 17)

### 2. 올바른 분리배출 가이드

- **위치**: `lib/screens/ai_classification_screen.dart`
- **기능**:
  - 카테고리별 배출 방법 즉시 안내
  - 오분류 방지 주의사항 알림
  - 버튼 하나로 상세 정보 접근
  - 140자 이내 핵심 정보 전달

### 3. 에너지 절약 효과 시각화

- **위치**: `lib/services/energy_calculator.dart`
- **제공 정보**:
  - **경제적 절약액** (원 단위)
  - **재생에너지 생산량** (kWh)
  - **CO₂ 감축량** → 소나무 그루 수 변환
  - 개인/가정/국가 단위 환경 효과
- **데이터 출처**: 환경부, 한국에너지공단, IRENA

### 4. 에너지 연못 (게임화)

- **위치**: `lib/screens/pond_screen.dart`
- **기능**:
  - 분리배출 실천 → 연못 생태계 청결도 증가
  - 누적 통계에 따른 시각적 피드백
  - 랜덤 에너지 지식 제공
  - 장기적 참여 유도

### 5. 쓰레기 백과사전

- **위치**: `lib/screens/encyclopedia_screen.dart`
- **제공 내용**:
  - 카테고리별 상세 분리배출 가이드
  - 재생에너지 전환 과정 설명
  - 자주 묻는 질문 (FAQ)
  - 환경부·지자체 분리배출 정보

### 6. 통계 대시보드

- **위치**: `lib/screens/statistics_screen.dart`
- **기능**:
  - 누적 분류 횟수 및 정확도
  - 총 에너지 절약량
  - 카테고리별 분류 비율
  - 월별/주별 사용 트렌드

---

## 💻 로컬 실행 가이드

### 1️⃣ 개발 환경 설정

```bash
# Flutter SDK 설치 확인
flutter --version

# 프로젝트 클론
git clone [프로젝트 GitHub URL]
cd SSbry

# 의존성 설치
flutter pub get
```

### 2️⃣ ONNX 모델 준비

```bash
# ML 디렉토리로 이동
cd ml

# Python 가상환경 설정
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 의존성 설치
pip install -r requirements.txt

# 모델 학습 (선택사항)
python train.py --data dataset/trash.yaml --epochs 30

# ONNX 변환
python export_onnx.py --weights best.pt --opset 17
```

**모델 파일 배치**:

- `assets/models/yolov8n_trash.onnx`에 모델 파일 저장
- `pubspec.yaml`에 assets 경로 등록 확인

### 3️⃣ 앱 실행

```bash
# Android 에뮬레이터 실행 또는 실제 기기 연결

# 앱 실행
flutter run

# 릴리즈 APK 빌드
flutter build apk --release
```

**빌드 결과**: `build/app/outputs/flutter-apk/app-release.apk`

### 4️⃣ 환경 설정

**Android 최소 요구사항**:

- minSdkVersion: 21
- targetSdkVersion: 33

**권한 설정** (`android/app/src/main/AndroidManifest.xml`):

```xml
<uses-permission android:name="android.permission.CAMERA" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
```

---

## 🛠️ 개발 과정 및 트러블슈팅

### 주요 기술적 도전 과제

#### 1. 카메라 촬영 불가능 문제

**문제**: Flutter Web에서 카메라 지원이 불안정하고 ONNX 모델이 Web을 지원하지 않음

**시도한 해결 방법**:

```
✗ Flutter Web + WebAssembly 시도
✗ TensorFlow.js 변환 시도
✗ 카메라 플러그인 교체
```

**최종 해결**:

```dart
// Web 배포 포기, 네이티브 앱 개발에 집중
// 카메라 대신 갤러리 업로드 방식 채택
import 'package:image_picker/image_picker.dart';

final ImagePicker _picker = ImagePicker();
final XFile? image = await _picker.pickImage(
  source: ImageSource.gallery
);
```

**결과**:

- 더 안정적인 성능과 사용자 경험 확보
- ONNX Runtime의 완벽한 호환성
- Android APK 성공적 배포

#### 2. ONNX Opset 버전 불일치

**문제**: 앱 실행 시마다 모델이 제대로 연동되지 않는 오류 발생

**원인 분석**:

```python
# Python에서 모델 export 시
torch.onnx.export(model, dummy_input, "model.onnx")
# 기본 opset_version = 18

# Flutter ONNX Runtime
# max_opset_version = 17
```

**해결 방법**:

```python
# 모델 재export
import torch

torch.onnx.export(
    model,
    dummy_input,
    "yolov8n_trash.onnx",
    opset_version=17,  # ✓ 17로 변경
    do_constant_folding=True,
    input_names=['images'],
    output_names=['output']
)
```

**결과**:

- 모델이 정상적으로 연동되어 안정적인 추론 가능
- 앱 실행 시 모델 로드 성공률 100% 달성

#### 3. image_gallery_saver 패키지 충돌

**문제**: Gradle 버전 충돌로 빌드 실패

```gradle
FAILURE: Build failed with an exception.
* What went wrong:
Could not determine the dependencies of task ':app:compileDebugJavaWithJavac'.
> Could not resolve all task dependencies for configuration ':app:debugCompileClasspath'.
```

**시도한 해결 방법**:

```yaml
# pubspec.yaml
✗ image_gallery_saver: ^1.7.1
✗ image_gallery_saver: ^2.0.1
✗ image_gallery_saver: ^2.0.3
# Gradle 버전 업데이트 시도
# 의존성 순서 변경 시도
```

**최종 해결**:

```yaml
dependencies:
  # image_gallery_saver: ^2.0.3  # ✗ 제거
  gal: ^2.1.4 # ✓ 최신 패키지로 변경
```

**결과**:

- 더 최신이고 안정적인 `gal` 패키지 사용
- Android 13+ 권한 처리 개선
- 정상 빌드 및 작동 확인

#### 4. 데이터 증강 기법 적용

**문제**: 실제 사용 환경의 다양한 조명과 각도에서 인식률 저하

**해결**: 학습 시 데이터 증강 기법 적용

```python
# YOLOv8 학습 설정
augmentation:
  hsv_h: 0.015      # 색조 변화
  hsv_s: 0.7        # 채도 변화
  hsv_v: 0.4        # 명도 변화
  degrees: 15.0     # 회전 각도
  translate: 0.1    # 이동
  scale: 0.5        # 스케일 변화
  fliplr: 0.5       # 좌우 반전
  mosaic: 1.0       # 모자이크 증강
```

**결과**:

- 다양한 조명 환경에서 정확도 향상
- 실제 사용자 환경에 강건한 모델 구축

---

## 🏆 성과 및 배운 점

### 프로젝트 성과

- ✅ **AI 객체 인식**: 6개 카테고리 높은 정확도 달성
- ✅ **다중 객체 동시 인식**: 한 장의 사진에서 여러 쓰레기 분류
- ✅ **모바일 최적화**: YOLOv8n으로 경량화, 빠른 추론 속도
- ✅ **사용자 경험**: 직관적 UI/UX 설계

### 사회적 임팩트 (1,000명 사용 시 예상)

- **505,000 kWh** 에너지 생산 기여
- **233톤 CO₂** 감축 (소나무 3.5만 그루 효과)
- **7,575만원** 경제적 효과

### 배운 점

- Flutter 네이티브 앱 개발 및 상태 관리
- ONNX Runtime을 활용한 모바일 ML 모델 배포
- YOLOv8 모델 커스터마이징 및 데이터셋 구축
- 사용자 중심 UI/UX 설계 및 게임화 요소 적용
- 공공 데이터 활용 및 환경 문제 해결 접근법

---

## 👥 팀원 구성

|               | **오왕경**                                                                                                                           | **윤태훈**                                                                                                                    | **최하연**                                                                                                                           |
| :-----------: | ------------------------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
|   **역할**    | 팀장 / 앱 개발                                                                                                                       | ML Engineer                                                                                                                   | 기획 / 데이터                                                                                                                        |
| **담당 업무** | Flutter 앱 개발<br/>UI/UX 디자인<br/>모델 연동<br/>통합 테스트                                                                       | 데이터 수집/전처리<br/>YOLOv8 모델 훈련<br/>ONNX 변환<br/>성능 최적화                                                         | 일정 관리<br/>자료 수집/검증<br/>AI 부분 서포트<br/>발표 자료 작성                                                                   |
|  **GitHub**   | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/[깃허브_아이디])   | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/taehun96)   | [![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat&logo=github&logoColor=white)](https://github.com/[깃허브_아이디])   |
|   **Email**   | [이메일 주소]                                                                                                                        | [이메일 주소]                                                                                                                 | [이메일 주소]                                                                                                                        |
|   **Blog**    | [![Velog](https://img.shields.io/badge/Velog-20C997?style=flat&logo=velog&logoColor=white)](https://velog.io/@[블로그_아이디]/posts) | [![Velog](https://img.shields.io/badge/Velog-20C997?style=flat&logo=velog&logoColor=white)](https://velog.io/@taehun96/posts) | [![Velog](https://img.shields.io/badge/Velog-20C997?style=flat&logo=velog&logoColor=white)](https://velog.io/@[블로그_아이디]/posts) |

---

## 📊 데이터 출처

본 프로젝트는 다음 공개 데이터 및 자료를 활용하여 개발되었습니다.

### 정부 및 공공기관

- **환경부**: 재활용품 분리배출 가이드라인
- **한국환경공단**: 폐기물 처리 및 재활용 통계
- **한국에너지공단**: 신재생에너지 생산량 데이터
- **서울시 및 각 지자체**: 공식 분리배출 안내

### 국제기구

- **IRENA** (국제재생에너지기구): 재생에너지 통계
- **IEA** (국제에너지기구): 에너지 효율 데이터
- **IPCC**: 탄소 배출 계수
- **그린피스**: 환경 영향 평가 자료

### 데이터셋

- **TrashNet Dataset** (Kaggle): YOLOv8 모델 학습 기반 데이터
  - 6개 카테고리, 2,500+ 이미지
  - 자체 라벨링 및 증강 데이터 추가

---

## 📦 다운로드

### Android APK

**[Google Drive에서 다운로드](https://drive.google.com/drive/folders/13n6XdaZlxzuWlXpKfPHqG-SxXi9Pc5KS?usp=sharing)**

### QR 코드

<img width="200" height="200" alt="QR Code" src="https://github.com/user-attachments/assets/5b80b801-61ee-4256-bece-e465c2ea6f21" />

### 설치 방법

1. 위 링크 또는 QR 코드로 접속하여 APK 파일 다운로드
2. Android 기기에서 APK 파일 실행
3. "알 수 없는 출처" 앱 설치 허용 (설정에서 활성화)
4. 설치 완료 후 앱 실행

**최소 요구사항**: Android 5.0 (API 21) 이상

---

## 🔗 관련 링크

- **AI 모델 저장소**: [SSbry Model Repository](https://github.com/Q5dis/SSbry.git)
- **프로젝트 발표 자료**: [링크 추가 예정]
- **데모 영상**: [링크 추가 예정]

---

## 📝 라이센스

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🤝 기여하기

프로젝트에 기여하고 싶으신가요?

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 💬 문의

프로젝트에 대한 문의사항이 있으시면 Issues를 통해 연락 주세요.

**이메일**: [프로젝트 대표 이메일]

---

<div align="center">

**분리배출에서 재생에너지까지, 에너지 순환의 여정** 🌍♻️

Made with ❤️ by [팀명]

</div>
