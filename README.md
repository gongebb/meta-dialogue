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

`.claude/skills/meta-dialogue/` 디렉토리를 Claude Code 프로젝트에 복사합니다.

```bash
# 프로젝트 루트에서
mkdir -p .claude/skills/meta-dialogue
cp skill.md .claude/skills/meta-dialogue/skill.md
```

또는 이 레포를 클론해서 직접 복사:

```bash
git clone https://github.com/gongebb/meta-dialogue.git
cp -r meta-dialogue/.claude/skills/meta-dialogue ~/.claude/skills/
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

## 실제 사용 예시

네이버피셜 리더 인터뷰를 읽고 대화를 시작했더니, 20분 만에 다음을 발견했습니다:

- "취향의 깊이가 부족하다"고 생각했는데, 진짜 걸리는 건 "나만의 목소리로 말하기를 미루고 있다"는 것
- 회사의 문제는 잘 정의하면서, 자신의 문제(뭘 말하고 싶은지)를 정의하는 건 계속 뒤로 미루고 있었다는 것
- "시작을 못 하겠다"의 원인이 능력 부족이 아니라 "첫 글이 나를 완벽하게 대변해야 한다"는 프레임이었다는 것

대화가 끝난 직후 첫 번째 글의 초안이 나왔습니다.

## 스킬 상세

질문 원칙, DO/DON'T 가이드, 대화 예시 등 상세 내용은 [skill.md](.claude/skills/meta-dialogue/skill.md)를 참고하세요.

## 요구사항

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI 설치 필요
- Claude Pro 또는 API 키

## 라이선스

MIT
