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

## 버전 통합 (v2.0)

> **2026-03-01**: v1과 v2를 하나의 `meta-dialogue` 스킬로 통합했습니다.

이전에는 v1(단일 세션)과 v2(축적형)가 별도 스킬이었습니다. 이제 하나의 스킬이 두 가지 모드를 지원합니다.

| 모드 | 설명 | 저장 경로 설정 |
|------|------|---------------|
| **기본** (축적형) | 메타 프로필 기반, 세션 간 누적. 대화가 깊어짐 | 필요 |
| **lightweight** | 단발 대화. 저장 없이 바로 시작 | 불필요 |

저장 경로를 설정하면 축적형, 설정하지 않으면 lightweight로 동작합니다. "가볍게 하자"고 말해도 lightweight로 전환됩니다.

**기존 사용자**: v1, v2 폴더를 삭제하고 새 `meta-dialogue` 폴더로 교체하세요. 기존 메타 프로필과 세션 기록은 그대로 호환됩니다.

## 폴더 구조

```
meta-dialogue/
├── README.md
├── LICENSE
└── skills/
    └── meta-dialogue/
        ├── SKILL.md              # 스킬 본체 (대화 원칙, 축적 구조, 안전장치)
        └── references/
            ├── meta-profile-template.md    # 메타 프로필 초기 구조
            ├── session-record-template.md  # 세션 기록 형식
            ├── session-protocol.md         # 세션 종료/저장 프로토콜
            └── safety-guards.md            # 프레임 건강도 안전장치
```

### 축적형 모드 사용 시 생성되는 파일

```
{저장 경로}/
├── meta-profile.md             # 가설, 패턴, 사각지대 (세션마다 업데이트)
├── about-me.md                 # (선택) 사고 원칙, 커리어 맥락
└── sessions/
    ├── _raw/                   # 대화 원문
    ├── 2026-02-08-topic-a.md   # 세션 기록
    └── 2026-02-09-topic-b.md
```

## 설치

### 1. npx skills (권장)

```bash
npx skills add https://github.com/gongebb/meta-dialogue -g -a claude-code -y
```

> `npx`가 없다면 [Node.js](https://nodejs.org/)를 먼저 설치해주세요.

### 2. 직접 다운로드

```bash
git clone https://github.com/gongebb/meta-dialogue.git
cp -r meta-dialogue/skills/meta-dialogue ~/.claude/skills/
```

## 설정

### 축적형 모드 (저장 경로 설정)

세션 기록과 메타 프로필을 파일로 저장하려면 CLAUDE.md에 저장 경로를 설정하세요:

```markdown
# ~/.claude/CLAUDE.md 또는 프로젝트 CLAUDE.md에 추가
meta-dialogue 저장 경로: /your/path/here
```

Obsidian 볼트나 원하는 디렉토리를 지정하면 됩니다.

### Lightweight 모드

저장 경로 설정 없이 바로 사용하면 됩니다. 세션 기록이나 메타 프로필 업데이트 없이 단발 대화만 진행합니다.

## 사용법

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

### Lightweight 모드

```
출발점 파악 → 탐색적 대화 → 패턴 인식 → 성장 방향 탐색 → 결과물 제안
```

### 축적형 모드

```
메타 프로필 로드 → 가설 기반 진입 → 탐색 → 패턴 확인/깨짐 감지 → 결과물 + 프로필 업데이트
```

축적형 모드는 이전 세션의 가설을 바탕으로 시작하되, 기존 패턴에 끼워맞추지 않습니다. 패턴이 깨지는 순간이 가장 가치 있는 발견입니다.

## 스킬 상세

- 스킬 본체: [skills/meta-dialogue/SKILL.md](skills/meta-dialogue/SKILL.md)
- 메타 프로필 템플릿: [references/meta-profile-template.md](skills/meta-dialogue/references/meta-profile-template.md)
- 세션 기록 템플릿: [references/session-record-template.md](skills/meta-dialogue/references/session-record-template.md)

## 요구사항

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI 설치 필요
- Claude Pro 또는 API 키

## 라이선스

MIT
