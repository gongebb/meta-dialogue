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

## 스킬 구성

이 레포에는 두 가지 스킬이 있습니다.

| 스킬 | 설명 | 추천 대상 |
|------|------|----------|
| **meta-dialogue** (v1) | 단일 세션 대화. 가설 기반 질문으로 생각을 구조화 | 처음 써보는 사람 |
| **meta-dialogue-v2** | v1 + 세션 간 축적, 패턴 깨짐 감지, 프레임 건강도 안전장치 | 반복 사용자 |

v2는 세션을 거듭할수록 메타 프로필이 쌓여서 대화가 깊어집니다.

## 폴더 구조

```
meta-dialogue/
├── README.md
├── LICENSE
├── meta-dialogue/              # v1 스킬
│   └── SKILL.md                #   질문 원칙, DO/DON'T, 대화 예시
└── .claude/skills/
    └── meta-dialogue-v2/       # v2 스킬
        ├── skill.md            #   v1 원칙 + 축적/안전장치/추론 가이드
        └── references/         #   시작할 때 참고할 템플릿
            ├── meta-profile-template.md    # 메타 프로필 초기 구조
            └── session-record-template.md  # 세션 기록 형식
```

### v2 사용 시 생성되는 파일

v2를 사용하면 프로젝트 내에 다음 구조가 자동으로 만들어집니다.

```
{프로젝트}/context/me/
├── meta-dialogue-sessions/
│   ├── _meta-profile.md        # 가설, 패턴, 사각지대 (세션마다 업데이트)
│   ├── 2026-02-08-topic-a.md   # 세션 기록
│   └── 2026-02-09-topic-b.md
└── about-me.md                 # (선택) 사고 원칙, 커리어 맥락
```

## 설치

### 1. npx skills (권장)

```bash
# v1만 설치
npx skills add https://github.com/gongebb/meta-dialogue --skill meta-dialogue -g -a claude-code -y

# v2 설치
npx skills add https://github.com/gongebb/meta-dialogue --skill meta-dialogue-v2 -g -a claude-code -y
```

> `npx`가 없다면 [Node.js](https://nodejs.org/)를 먼저 설치해주세요.

### 2. 직접 다운로드

```bash
git clone https://github.com/gongebb/meta-dialogue.git

# v1
cp -r meta-dialogue/meta-dialogue ~/.claude/skills/

# v2
mkdir -p ~/.claude/skills/meta-dialogue-v2
cp -r meta-dialogue/.claude/skills/meta-dialogue-v2/* ~/.claude/skills/meta-dialogue-v2/
```

## 사용법

### v1

```
/meta-dialogue 요즘 이런 생각을 해...
/meta-dialogue [글 링크와 함께] 이 글로 대화하고 싶어
```

### v2

```
/meta-dialogue-v2 최근 팀 회고에서 느낀 건데...
/meta-dialogue-v2 나에 대해 더 알고 싶어
```

자연어로도 작동합니다:

```
최근 생각들을 정리하고 싶어
내가 뭘 원하는지 모르겠어
아티클 쓰려는데 소재가 안 잡혀
```

## 대화 흐름

### v1

```
출발점 파악 → 탐색적 대화 → 패턴 인식 → 성장 방향 탐색 → 결과물 제안
```

### v2

```
메타 프로필 로드 → 가설 기반 진입 → 탐색 → 패턴 확인/깨짐 감지 → 결과물 + 프로필 업데이트
```

v2는 이전 세션의 가설을 바탕으로 시작하되, 기존 패턴에 끼워맞추지 않습니다. 패턴이 깨지는 순간이 가장 가치 있는 발견입니다.

## 스킬 상세

- v1 원칙, 대화 예시: [meta-dialogue/SKILL.md](meta-dialogue/SKILL.md)
- v2 축적 구조, 안전장치: [.claude/skills/meta-dialogue-v2/skill.md](.claude/skills/meta-dialogue-v2/skill.md)
- 메타 프로필 템플릿: [references/meta-profile-template.md](.claude/skills/meta-dialogue-v2/references/meta-profile-template.md)
- 세션 기록 템플릿: [references/session-record-template.md](.claude/skills/meta-dialogue-v2/references/session-record-template.md)

## 요구사항

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI 설치 필요
- Claude Pro 또는 API 키

## 라이선스

MIT
