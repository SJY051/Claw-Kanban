# 디시인사이드 게시글

## 제목
AI 코딩 에이전트 3개를 칸반보드에서 동시에 굴려봤다

## 본문

몰트봇 (OpenClaw) 사용 하면서

Claude Code, Codex, Gemini CLI 세 개 다 쓰는 사람 있음?

나는 셋 다 쓰는데 터미널 창 3개 열어놓고 번갈아가면서 쓰는게 너무 비효율적이라

그냥 칸반보드 하나 만들어서 태스크별로 AI를 자동 배정하게 만들었음

Claw-Kanban 이라는 건데


(telegram.png)

Telegram에서 앞글자에 #을 붙이고 할 일을 던지면 (DevOps/Backend/Frontend)이랑 태스크 유형(신규/수정/버그)에 따라 알아서 AI가 배정됨

- DevOps → Claude Code
- Backend → Codex CLI
- Frontend 신규 → Gemini CLI
- Frontend 수정/버그 → Claude Code


(dashboard.png)


(provider_setting.png)

설치된 CLI 도구를 자동으로 감지해서 인증 상태까지 보여줌
설치 안 된 도구는 드롭다운에서 비활성화 처리돼서 실수로 선택할 일 없음


(claude_code_tm.png)

실행 중인 에이전트의 터미널 출력을 웹에서 실시간으로 볼 수 있음

기존 openclaw에서는 일을 시키고 끝날때까지 뭐 하고있나 확인하기 힘들었는데

이젠 터미널 직접 까볼 수 있어서

시킨 일을 하염없이 기다릴 필요가 없다.


(telegram.png)

텔레그램에서 `# 버그 수정해줘` 이렇게 보내면 칸반에 카드가 자동 생성되고
에이전트가 알아서 실행한 다음 끝나면 결과까지 알려줌

출퇴근길에 폰으로 태스크 던지면 집에 도착할 때쯤 완료되어있는 느낌


동작 흐름:

태스크 생성 → AI 자동 배정 → 실행 → 자동 리뷰 → 완료

에이전트가 작업 끝내면 Claude가 자동으로 리뷰까지 해줌
리뷰 통과하면 Done, 문제 있으면 다시 돌려보냄


스택:
- React 19 + Express 5 + SQLite (node:sqlite)
- Node.js 22+ 필수
- 별도 DB 설치 필요 없음 (제로 디펜던시 SQLite)


GitHub: https://github.com/GreenSheep01201/Claw-Kanban
라이선스: Apache 2.0 (자유롭게 쓰면 됨)

피드백이나 버그 제보는 GitHub Issues로 부탁함
