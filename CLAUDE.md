# ble-sync-test — 배지 싱크 실험 페이지

안드로이드 Chrome에서 BLE(Web Bluetooth)로 배지(BADGE-DEMO)에 재생 위치를 보내는 실험 페이지.
Web Bluetooth는 HTTPS에서만 동작하므로 GitHub Pages로 공개한다.

## 규칙
- 설명은 한국어. 사용자 Eddie는 임베디드 SW 비전공.
- 공개 저장소에는 `index.html`, `CLAUDE.md`만 올린다. **음원(.ogg, .m4a 등)은 저작권 때문에 절대 올리지 않는다** (.gitignore로 막음).
- `.env` 등 민감 파일은 열지 않는다.

## 반복 작업: 처음 올리기 (Eddie가 "Pages로 올려줘"라고 할 때)
1. `gh auth status`로 로그인 확인. 로그인한 **개인 계정** 아래에 만든다(조직 InfraBlockchain 아님).
2. 실행:
   ```
   git init -b main
   git add index.html CLAUDE.md .gitignore
   git status        # .ogg 등 음원이 없는지 확인
   git commit -m "배지 싱크 실험 페이지"
   gh repo create ble-sync-test --public --source . --remote origin --push
   gh api -X POST repos/{owner}/ble-sync-test/pages -f "source[branch]=main" -f "source[path]=/"
   ```
   `{owner}`는 `gh api user --jq .login` 결과.
3. 1~2분 뒤 주소 `https://<owner>.github.io/ble-sync-test/` 를 Eddie에게 알려 준다 (`gh api repos/{owner}/ble-sync-test/pages --jq .html_url`).

## 반복 작업: 수정본 올리기 ("페이지 갱신해줘")
`git add index.html && git commit -m "<요약>" && git push` → 1~2분 뒤 반영.
