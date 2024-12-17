# 리브레스 3D 뷰어 사용 가이드

## 목차
1. [소개](#소개)
2. [기능](#기능)
3. [설치 및 실행](#설치-및-실행)
4. [API 사용법](#api-사용법)
5. [외부 연동](#외부-연동)
6. [개발자 참고사항](#개발자-참고사항)

## 소개
리브레스 3D 뷰어는 의류 및 액세서리 제품의 3D 모델에 텍스처를 실시간으로 적용하고 확인할 수 있는 웹 기반 뷰어입니다.

## 기능
- 8가지 기본 3D 모델 제공 (가방, 모자 등)
- 실시간 텍스처 매핑
- REST API 지원
- 디버그 모드 제공

## 설치 및 실행

### 요구사항
```txt
fastapi==0.104.1
python-multipart==0.0.6
uvicorn==0.24.0
opencv-python==4.8.1.78
numpy==1.26.2 
```

## API 사용법

### 이미지 처리 API 호출 예시
```python
url = "http://localhost:8000/process-image/"
files = {
    'clothing_image': ('texture.jpg', open('path/to/texture.jpg', 'rb'), 'image/jpeg')
}
data = {
    'product_name': 'sample_product'
}

response = requests.post(url, files=files, data=data)

if response.status_code == 200:
    with open('result.png', 'wb') as f:
        f.write(response.content)
```

## 외부 연동
iframe으로 뷰어를 외부에서 불러올 때 사용하는 메시지 통신 방법:

```javascript
// 모델 로드
iframe.contentWindow.postMessage({
    type: 'loadModel',
    path: 'models/p1-bag.obj'  // p1~p8 중 선택
}, '*');

// 텍스처 로드
iframe.contentWindow.postMessage({
    type: 'loadTexture',
    url: '이미지URL'
}, '*');
```

## 개발자 참고사항

### 디버그 모드
- 활성화 시 각 처리 단계별 중간 이미지 저장
- 텍스처 추출 과정 시각화
- 매핑 결과 확인 가능

### 성능 최적화
- 텍스처 추출은 이미지 중앙 50% 영역에서 수행
- PNG 압축 레벨 9 적용
- 메모리 효율적 처리를 위한 임시 파일 관리

### 오류 처리
- 잘못된 이미지 형식에 대한 검증
- 파일 저장/로드 실패 시 명확한 에러 메시지
- 처리 과정 중 예외 발생 시 자동 정리

## 라이선스
MIT License