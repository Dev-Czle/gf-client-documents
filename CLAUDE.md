# CLAUDE.md

이 파일은 Claude Code가 이 저장소에서 작업할 때 따라야 할 규칙을 정의합니다.

## 역할

**크로스-플랫폼 모바일 문서화 저장소**

- Android와 iOS 설계 결정, 아키텍처 비교, 공유 요구사항을 한국어로 기록
- Markdown 중심 (가끔 HTML)
- 각 플랫폼 레포에서 작업할 때 다른 플랫폼의 관점을 빠르게 찾을 수 있게 함

## 참고 레포

- Android: `/Users/kimgideok/gf-client-android-kotlin`
- iOS: `/Users/kimgideok/AndroidProjects/gf-client-ios-swift`

두 플랫폼의 코드를 동시에 참고한 상태에서 문서를 작성합니다.

## 문서 종류

1. **Architecture-*.md** — 아키텍처 설계 패턴 비교 (레이어 구조, 의존성 등)
2. **Decision-*.md** — 크로스-플랫폼 설계 결정 기록 (왜 Android는 A, iOS는 B를 했는지)
3. **Shared-*.md** — 공유 요구사항 (API 계약, 데이터 스키마 등)
4. **Migration-*.md** — 한쪽 개선사항을 다른 쪽에도 적용할 지 판단하는 가이드

## 네이밍

주제별 (이슈 번호 아님):
- `Architecture-Networking.md`
- `Decision-Camera-Recording.md`
- `Shared-User-Data-Model.md`

## 작업 방식

1. 두 레포를 동시에 참고합니다.
2. 코드 경로는 구체적으로 명시합니다 (`android/app/src/.../`, `golffix/...`).
3. 예시 코드는 인라인으로 작성합니다.
4. 불확실한 부분은 `{확인 필요}`로 표시합니다.
5. 어투와 문서 형식은 점진적으로 발전시킵니다.

## 기록 대상

- 두 플랫폼이 다르게 푼 문제와 이유
- API/데이터 계약 변경
- 공통 컴포넌트/패턴
- 마이그레이션 판단 기준

