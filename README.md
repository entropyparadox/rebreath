# 리브레스 3D 뷰어 사용 가이드

## 목차
1. [소개](#소개)
2. [기능](#기능)
3. [설치 및 실행](#설치-및-실행)
4. [사용 방법](#사용-방법)
5. [키보드 단축키](#키보드-단축키)
6. [외부 연동](#외부-연동)

## 소개
리브레스 3D 뷰어는 의류 및 액세서리 제품의 3D 모델에 텍스처를 실시간으로 적용하고 확인할 수 있는 웹 기반 뷰어입니다.

## 기능
- 8가지 기본 3D 모델 제공 (가방, 모자 등)
- 실시간 텍스처 매핑
- 마우스 드래그로 모델 회전
- 이미지 크롭 및 편집 기능
- 투명 배경 지원

## 설치 및 실행
1. 프로젝트 파일을 웹 서버에 업로드
2. index.html 파일을 브라우저에서 실행

## 사용 방법

### 모델 선택

```javascript
// 모델 로드
iframe.contentWindow.postMessage({
type: 'loadModel',
path: 'models/p1-bag.obj' // p1~p8 중 선택
}, '')
```

## 지원 모델 목록
1. p1-bag: 기본 가방
2. p2-handybag: 핸드백
3. p3-pouch-tall: 세로형 파우치
4. p4-pouch: 가로형 파우치
5. p5-bag-string: 끈 달린 가방
6. p6-hat: 모자
7. p7-ecobag: 에코백
8. p8-cap: 캡 모자

### 텍스처 업로드
1. "텍스처 업로드" 버튼 클릭
2. 이미지 파일 선택
3. 크롭 영역 조정 (선택사항)
4. 자동으로 텍스처 적용

## 키보드 단축키
- `D`: 컨트롤 패널 표시/숨기기
- `1~8`: 모델 빠른 선택

## 외부 연동
iframe으로 뷰어를 외부에서 불러올 때 사용하는 메시지 통신 방법:

```javascript
// 모델 로드
iframe.contentWindow.postMessage({
type: 'loadModel',
path: 'models/p1-bag.obj' // p1~p8 중 선택
}, '');
// 텍스처 로드
iframe.contentWindow.postMessage({
type: 'loadTexture',
url: '이미지URL'
}, '');
```

## 기술 스택
- Three.js: 3D 렌더링
- WebGL: 하드웨어 가속 그래픽스
- HTML5 Canvas: 이미지 처리

## 브라우저 지원
- Chrome (권장)
- Firefox
- Safari
- Edge

## 참고사항
- 텍스처 이미지는 가급적 2048x2048 이하 크기 권장
- WebGL 지원 브라우저 필요
- 고해상도 디스플레이(Retina) 지원

## 라이선스
MIT License