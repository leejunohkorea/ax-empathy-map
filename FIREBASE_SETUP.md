# AX 공감 나침반 Firebase 연결

아직 프로젝트 설정값을 받지 않아 실제 연결은 하지 않았습니다.

1. Firebase 프로젝트의 웹 앱 설정(firebaseConfig)을 firebase-config.js의 null 대신 넣습니다. 서비스 계정 비밀키는 사용하지 않습니다.
2. Cloud Firestore 기본 데이터베이스를 생성합니다.
3. Authentication에서 익명(참여자) 및 이메일/비밀번호(관리자) 로그인을 활성화합니다. 사이트 호스트를 승인된 도메인에 등록합니다.
4. Authentication에서 관리자 이메일 계정을 생성하고 UID를 복사합니다.
5. Firestore 콘솔에서 axAdmins/{관리자 UID} 문서를 만들고 enabled 필드를 boolean true로 설정합니다. 클라이언트에서는 관리자 권한을 만들 수 없습니다.
6. firestore.rules 규칙을 적용합니다. 기존 프로젝트를 쓴다면 기존 규칙을 덮어쓰지 말고 이 경로의 규칙을 병합하세요. 기존의 광범위한 허용 규칙이 이 경로까지 허용하지 않도록 점검합니다.
7. 사이트 관리자로 로그인 → 영문 회차 코드와 표시 이름 입력 → 새 회차 생성 → 참여 링크 복사.
8. 실제 응답 제출과 관리자 실시간 집계, 비관리자의 응답 목록 읽기 거부를 검증한 후 교육에 사용합니다.

응답 경로: axSessions/{회차}/responses/{Firebase 익명 UID}
각 응답은 원래 문항 순서의 boolean 30개와 서버 수정시간을 저장합니다. 화면은 유형을 교차 배치해 보여줍니다. 같은 브라우저/회차 재제출은 갱신되며 다른 기기나 브라우저 데이터 삭제 후에는 중복 참여가 가능합니다. 개인 식별 검증은 하지 않습니다.
관리자는 모든 회차의 원본 응답을 읽을 수 있으므로 신뢰하는 운영자에게만 권한을 줍니다. 집계는 관리자 화면에만 표시합니다. 5명 미만은 표시를 제한하지만 보안상 익명성 보장은 아닙니다.
회차 마감: Firestore 콘솔에서 axSessions/{회차}의 open을 false로 변경합니다.
GitHub Pages 배포 후 실제 사이트 호스트를 Firebase Authentication 승인된 도메인에 등록하세요.

공식 참고: https://firebase.google.com/docs/web/setup 및 https://firebase.google.com/docs/rules/rules-and-auth
