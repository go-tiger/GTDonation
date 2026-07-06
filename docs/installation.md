# 설치하기

## 다운로드

> **릴리즈 준비 중입니다.** 현재는 직접 빌드해서 사용해야 합니다. → [직접 빌드하기](#직접-빌드하기)

출시 후에는 각 레포지토리의 GitHub Releases에서 JAR 파일을 다운로드할 수 있습니다.

| 플러그인 | GitHub |
|---|---|
| GTDonation-Core | [go-tiger/GTDonation-Core](https://github.com/go-tiger/GTDonation-Core) |
| GTDonation-Chzzk | [go-tiger/GTDonation-Chzzk](https://github.com/go-tiger/GTDonation-Chzzk) |
| GTDonation-Event | [go-tiger/GTDonation-Event](https://github.com/go-tiger/GTDonation-Event) |

---

## 설치 순서

플러그인 간 의존 관계가 있으므로 **반드시 아래 순서대로** `plugins/` 폴더에 넣어야 합니다.

1. `GTDonation-Core-0.1.0.jar`
2. `GTDonation-Chzzk-1.0.jar`
3. `GTDonation-Event-1.0.jar` *(선택)*

GTDonation-Chzzk는 GTDonation-Core에 의존합니다. Core 없이는 동작하지 않습니다.

---

## 직접 빌드하기

Gradle을 사용해 직접 빌드할 수 있습니다.

### GTDonation-Core

```bash
# Core는 먼저 Maven Local에 배포해야 합니다
cd GTDonation-Core
./gradlew publishToMavenLocal
```

### GTDonation-Chzzk

```bash
cd GTDonation-Chzzk
./gradlew shadowJar
# 결과물: build/libs/GTDonation-Chzzk-1.0.jar
```

### GTDonation-Event

```bash
cd GTDonation-Event
./gradlew jar
# 결과물: build/libs/GTDonation-Event-1.0.jar
```

---

## 서버 재시작

JAR 파일을 모두 `plugins/` 폴더에 넣은 뒤 서버를 재시작합니다. 최초 실행 시 각 플러그인의 설정 파일이 자동으로 생성됩니다.

> **다음 단계:** 치지직 OAuth를 설정하세요. → [시작하기](getting-started.md)
