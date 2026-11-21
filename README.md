# claude-session-panel

Claude Code(데스크톱 앱) 모드 **session-panel** 과 비서 스킬 **secretary** 입니다.

- **session-panel** (`mods/session-panel`): 진행 패널(목표·단계·진행도 %), 같은 PC의 세션끼리 메시지·인계(`/collab`, `/handoff`, `/pickup`), 모델 도구 `mcp__session-panel__progress / peers / send / handoff / pickup`
- **secretary** (`skills/secretary`): `/secretary` — 다른 세션들의 현황을 보고 다음에 시킬 일을 제안

세션끼리 주고받는 메시지는 각 PC의 `%USERPROFILE%\.claude\session-collab` 폴더를 거치므로, 같은 PC 안의 세션끼리만 연결됩니다.

## 다른 PC에 설치하기

그 PC에서 Claude Code 세션을 열고 아래 프롬프트를 붙여 넣으세요. 끝나면 Claude 앱을 완전히 껐다 켭니다.

```
세션 패널(session-panel) 모드와 비서(secretary) 스킬을 이 PC에 설치해 줘.

원본: https://github.com/airyanrip/claude-session-panel

할 일:
1. 저장소를 임시 폴더에 clone 하고 아래 위치로 복사해 줘 (이미 있으면 덮어쓰기 전에 나한테 물어봐).
   - mods/session-panel → %USERPROFILE%\.claude\mods\session-panel
   - skills/secretary → %USERPROFILE%\.claude\skills\secretary
2. %USERPROFILE%\.claude\settings.json 의 env 에 아래 두 값을 추가해 줘. 기존 설정은 건드리지 말고 합쳐 넣어. 경로는 이 PC의 실제 사용자 폴더 기준 절대경로로.
   - "CLAUDE_CODE_PLUGIN_DIRS": "C:\\Users\\<이 PC 사용자>\\.claude\\mods\\session-panel"
   - "CLAUDE_CODE_PLUGIN_DIR_WATCH": "1"
   (settings.json 수정이 권한 때문에 막히면, 넣을 JSON 조각을 보여주고 내가 직접 넣게 안내해 줘.)
3. %USERPROFILE%\.claude\session-collab 폴더가 없으면 만들어 줘 (세션끼리 메시지를 주고받는 폴더).
4. 가능하면 mods\session-panel 폴더에서 `claude plugin test .` 를 돌려서 모드가 정상 로드되는지 확인해 줘.
5. 끝나면 "Claude 앱을 완전히 껐다 켜면 새 세션부터 진행 패널이 뜬다"고 알려 주고, 확인 방법(새 세션에서 /panel 입력, 도구 목록에 mcp__session-panel__progress 가 보이는지)을 정리해 줘.
```

## 수동 설치

1. `mods/session-panel` → `%USERPROFILE%\.claude\mods\session-panel`, `skills/secretary` → `%USERPROFILE%\.claude\skills\secretary` 로 복사
2. `%USERPROFILE%\.claude\settings.json` 의 `env` 에 추가:
   ```json
   "CLAUDE_CODE_PLUGIN_DIRS": "C:\\Users\\<사용자>\\.claude\\mods\\session-panel",
   "CLAUDE_CODE_PLUGIN_DIR_WATCH": "1"
   ```
3. Claude 앱 재시작
