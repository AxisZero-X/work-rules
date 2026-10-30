# WORKFLOW

## 시작

```bash
git status                                  # 저장소가 아니면 git init
git config user.email >/dev/null || git config user.email "me@local"
git config user.name  >/dev/null || git config user.name "me"
git add -A && git commit -m "받은 상태 기록"   # 변경이 있을 때만
git clone --depth 1 https://github.com/AxisZero-X/work-rules _rules
echo '_rules/' >> .git/info/exclude
[ -f AGENTS.md ] && cat _rules/AGENTS.md >> AGENTS.md   # 과제 AGENTS.md가 있으면 뒤에 이어 붙임
cp -n _rules/AGENTS.md _rules/PLAN.md _rules/DECISIONS.md _rules/VERIFICATION.md .
git add -A && git commit -m "작업 규칙과 문서 양식 추가"
```

## 순서

1. 요구사항을 읽고 필수 조건, 제약, 모호한 점을 정리한다.
2. 사용자에게 확인해서 PLAN.md의 문제와 합의를 채운다.
3. 단계마다 단계 제목, 완료 조건, 확인 명령, 금지 범위를 적어 PLAN.md를 확정하고 커밋한다.
4. 단계를 하나씩 진행하고, 결과를 직접 확인한 뒤 확인한 내용을 말하고 커밋한다.
5. 갈리는 판단은 DECISIONS.md에 남긴다.
6. 단계가 끝나면 PLAN.md의 현재 상태를 갱신하고 컨텍스트를 정리한다. 이어서 할 때는 AGENTS.md, PLAN.md, DECISIONS.md를 읽는다.
7. 막히면 원인을 정리하고 범위를 줄인다. 줄인 범위는 사용자에게 알리고 DECISIONS.md에 남긴다.
8. VERIFICATION.md를 채운다. 성공 기준, 실패·경계 케이스, 깨끗한 상태에서 재실행, 비밀값을 확인한다.
