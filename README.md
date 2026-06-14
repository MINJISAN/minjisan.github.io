# Min Jisan Portfolio Draft

정적 포트폴리오 사이트 초안입니다. 로컬 서버를 켠 뒤 브라우저에서 확인하면 됩니다.

```bash
python3 -m http.server 4173
```

브라우저에서 `http://localhost:4173/index.html`을 열어주세요.

## 공개 페이지와 에디터 페이지

공개용 페이지는 `index.html`입니다. 이 페이지에는 에디터 버튼이나 수정 UI가 없습니다.

편집용 페이지는 `editor.html`입니다.

```txt
http://localhost:4173/index.html   공개 포트폴리오
http://localhost:4173/editor.html  편집용 페이지
```

중요: 정적 사이트에 `editor.html`을 그대로 같이 업로드하면 주소를 아는 사람은 접근할 수 있습니다. 진짜로 나만 쓰려면 아래 중 하나를 선택해야 합니다.

- `editor.html`은 배포하지 않고 로컬에서만 사용하기
- Netlify/Vercel/Cloudflare 같은 호스팅에서 비밀번호 또는 Access 인증 걸기
- 나중에 Sanity, Notion, Google Sheet, Supabase 같은 별도 CMS/DB와 로그인 붙이기

## 에디터에서 작품 추가/수정하기

`editor.html`을 열면 작품 편집 패널이 보입니다.

1. 제목, 장르, 연도, 타입을 입력합니다.
2. 카드 이미지는 `Thumbnail`에서 선택합니다.
3. 상세에서 재생하거나 열 파일은 `Media File`에서 선택합니다.
4. 큰 영상/음악 파일은 브라우저 저장 공간을 많이 쓰므로, 파일을 `Resource` 폴더에 넣고 `Media Path`에 `Resource/videos/work.mp4`처럼 경로를 적는 방식을 권장합니다.
5. `Save`를 누르면 카드와 상세 페이지에 바로 반영됩니다.

수정 내용은 현재 브라우저에 자동 저장됩니다. 다른 브라우저나 다른 컴퓨터로 옮기려면 `Export JSON`으로 내보낸 뒤, 새 브라우저에서 `Import JSON`으로 가져오면 됩니다.

## 코드로 직접 작품 추가하기

기본 작품 목록은 `script.js`의 `defaultWorks` 배열에서 관리합니다.

- `title`: 카드와 상세 화면에 보이는 제목
- `genre`: 필터와 장르 텍스트
- `year`: 연도
- `type`: `image`, `video`, `audio`, `pdf` 중 하나
- `thumb`: 카드 썸네일 이미지 경로
- `src`: 상세 화면에서 열거나 재생할 파일 경로
- `description`: 상세 설명

영상, 음악, 이미지는 `Resource` 폴더나 `assets` 폴더에 넣고 `src`만 연결하면 상세 화면에서 재생/표시됩니다.
