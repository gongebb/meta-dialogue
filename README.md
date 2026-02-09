# Meta-Dialogue

AI와 메타인지 대화를 나누는 [Claude Code](https://docs.anthropic.com/en/docs/claude-code) 스킬입니다.

흩어진 생각을 구조화하고, 자기 이해를 심화하며, 글로 정제할 수 있는 인사이트를 도출합니다.

## 이런 상황에서 씁니다

- 글이나 인터뷰를 읽고 내 생각을 정리하고 싶을 때
- 아티클을 쓰려는데 소재가 안 잡힐 때
- 내가 뭘 원하는지 스스로 잘 모르겠을 때
- 커리어, 성장, 가치관에 대해 깊이 생각해보고 싶을 때

## 어떻게 다른가

일반적인 AI 대화는 질문하면 답을 줍니다. 이 스킬은 다릅니다.

- 질문할 때 가설을 함께 공유합니다. "이걸 물으면 이런 게 드러날 것 같아서"
- "왜?"에서 멈추지 않고, "그래서 뭘 알 수 있는데?"까지 갑니다
- 여러 생각 사이의 패턴과 연결을 발견하게 돕습니다
- 현재 상태 분석에서 끝나지 않고, 성장 방향을 엽니다

## 설치

### 1. npx degit (권장)

터미널에서 아래 명령어를 실행하면 설치됩니다.

```bash
npx -y degit gongebb/meta-dialogue/meta-dialogue ~/.claude/skills/meta-dialogue
```

> `npx`가 없다면 [Node.js](https://nodejs.org/)를 먼저 설치해주세요.

### 2. 직접 다운로드

이 레포지토리를 다운로드한 뒤, `meta-dialogue` 폴더를 `~/.claude/skills/`에 복사합니다.

```bash
git clone https://github.com/gongebb/meta-dialogue.git
cp -r meta-dialogue/meta-dialogue ~/.claude/skills/
```

## 사용법

Claude Code에서 `/meta-dialogue` 명령어로 호출합니다.

```
/meta-dialogue 요즘 이런 생각을 해...
/meta-dialogue [글 링크와 함께] 이 글로 대화하고 싶어
```

자연어로도 작동합니다:

```
최근 생각들을 정리하고 싶어
내가 뭘 원하는지 모르겠어
아티클 쓰려는데 소재가 안 잡혀
```

## 대화 흐름

```
출발점 파악 → 탐색적 대화 (3-5라운드) → 패턴 인식 → 성장 방향 탐색 → 결과물 제안
```

1. 최근 어떤 생각을 하고 있는지, 왜 이 대화를 시작했는지 파악
2. 가설 기반 질문으로 생각의 연결 고리를 발견
3. 여러 생각에서 반복되는 주제, 숨겨진 가치관을 인식
4. "여기서 어디로 갈 수 있는가"를 탐색
5. 아티클 소재, 자기 이해 요약, 다음 대화 주제 등을 제안

## 스킬 상세

질문 원칙, DO/DON'T 가이드, 대화 예시 등 상세 내용은 [SKILL.md](meta-dialogue/SKILL.md)를 참고하세요.

## 요구사항

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI 설치 필요
- Claude Pro 또는 API 키

## 라이선스

MIT
