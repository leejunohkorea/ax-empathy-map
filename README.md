# AI 시대, 우리 조직의 속마음

## GitHub 업로드
ZIP 압축을 풀고 안의 파일을 저장소 최상위에 업로드하세요. ZIP 자체를 올리는 것이 아닙니다.
index.html과 firebase-config.js는 같은 폴더에 두세요.
GitHub Pages는 저장소 루트의 index.html을 시작 페이지로 사용하도록 설정합니다.

## 포함 파일
- index.html: 설문, 개인 결과, 관리자 조직 결과 화면
- firebase-config.js: Firebase 웹 앱 설정 입력 위치
- firestore.rules: Firestore 보안 규칙
- FIREBASE_SETUP.md: 연결 및 관리자 계정 등록 안내

## 현재 상태
문항 선택 중에는 카테고리를 숨기고 최종 결과에서만 표시합니다.
Firebase 설정값은 비어 있습니다. 연결 전에는 개인 결과만 확인할 수 있으며 서버 저장은 되지 않습니다.
관리자 비밀번호는 코드에 넣지 않았습니다. Firebase에서 관리자 계정을 만들어 사용합니다.
