---
name: czle-code-trace
description: GolfFix Android 코드의 호출 흐름, 데이터 분기, nullable/API 계약을 근거 중심으로 추적할 때 사용한다. 사용자가 "왜 이런 동작이 일어나는가", "데이터가 어떻게 분기되는가", "nullable 계약은 안전한가" 같은 질문을 하면 이 스킬로 코드를 읽으면서 흐름을 추적한다.
---

# GolfFix 코드 흐름 추적

## 목적

GolfFix Android 코드의 호출 흐름, 데이터 분기, nullable/API 계약을 근거 중심으로 추적한다. 사용자가 "왜 이런 동작이 일어나는가"를 묻거나 데이터 흐름 이해가 필요할 때 사용한다.

CLAUDE.md의 글쓰기 원칙을 따른다.

## 범위

- Android 클라이언트 저장소: `/Users/kimgideok/gf-client-android-kotlin`
- Kotlin, XML, manifest, API DTO/mapper, repository, ViewModel, Activity, Fragment, Compose, RecyclerView, 로컬 저장소 흐름
- 읽기 전용 분석. 사용자가 명시적으로 구현을 승인하기 전까지 파일을 수정하지 않는다.

## 워크플로우

1. 활성 브랜치를 확인한다. (필요할 경우)
2. 목표, 범위, 제외 사항을 한국어로 짧게 정리한다.
3. 사용자 가시 진입점에서 시작해 실제 호출 체인을 따라간다.
4. 정확한 기호, 파일 경로, 함수명, DTO 필드, 쿼리명, 예외 타입, nullable 계약을 우선한다.
5. 호출자 동작과 호출자 동작을 분리한다.
6. 로컬 데이터 동작과 서버/API 동작을 분리한다.
7. 사용자가 기존 호환성을 묻거나 "기존처럼"이라 하면 현재 동작과 비교한다.
8. 이전 가정이 코드로 모순되면 멈추고 추적을 수정한다.

## 추적 체크리스트

- 진입점: 화면, 클릭 핸들러, 이벤트 수집기, intent/deep link, 공개 메서드
- ViewModel과 상태/이벤트 경로
- UseCase/repository/API/DAO 경로
- DTO/mapper/nullability 계약
- Coroutine/Flow/lifecycle 경계
- Fallback 순서와 실패 동작
- 로컬 캐시 vs 서버 source of truth
- 기존 호환성이 필요한 동작

## 출력 형식

```markdown
## 결론

## 실제 호출 체인

## 데이터/상태 분기

## 기존 동작과 달라지는 지점

## 수정 필요 여부

## 검증 방법
```

불확실한 발견은 `확인 필요`로 표시하고 누락된 근거를 설명한다. 예외 정책, API 누락 의미, lifecycle 보장을 발명하지 않는다.

## 검증

- `./gradlew ...`는 실행하지 않는다.
- `rg`, `git diff --check`, 대상 파일 검사 같은 읽기 전용 확인을 사용한다.
- 런타임 검증이 필요하면 정확한 사용자 실행 명령이나 수동 QA 경로를 제시한다.
