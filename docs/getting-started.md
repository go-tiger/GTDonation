# 시작하기

플러그인 설치 후 치지직 후원 이벤트를 인게임에서 받기까지의 전체 흐름을 설명합니다.

---

## 1. 치지직 OpenAPI 앱 등록

[치지직 Developers](https://developers.chzzk.naver.com)에서 앱을 등록하고 **Client ID**와 **Client Secret**을 발급받으세요.

### API Scope 선택

앱 등록 시 아래 5개 스코프를 선택해야 합니다.

| Scope | 용도 |
|---|---|
| 유저 조회 | OAuth 로그인 후 채널 정보 확인 |
| 채널 정보 조회 | 채널 팔로워, 구독자 등 조회 |
| 채팅 메시지 조회 | 채팅 수신 (ChatEvent) |
| 후원 조회 | 후원 수신 (DonationEvent) |
| 구독 조회 | 구독 정보 조회 |

### Redirect URI 설정

Redirect URI는 다음 형식으로 설정합니다:

```
http://{서버 도메인 또는 IP}:{port}{callbackPath}
```

예시:
```
http://play.example.com:20154/callback
```

---

## 2. GTDonation-Chzzk 설정

서버를 한 번 실행하면 `plugins/GTDonationChzzk/config.json`이 생성됩니다.

```json
{
  "CLIENT_ID": "여기에 Client ID 입력",
  "CLIENT_SECRET": "여기에 Client Secret 입력",
  "displayHost": "play.example.com",
  "port": 20154,
  "https": false,
  "callbackPath": "/callback",
  "debug": false
}
```

설정 후 서버를 재시작합니다.

자세한 설정 옵션은 [config.json 설정 문서](chzzk/configuration.md)를 참고하세요.

---

## 3. 플레이어 계정 연동

플레이어가 서버에 접속하면 처음 한 번만 치지직 로그인 링크가 채팅창에 나타납니다.

```
[CHZZK] 로그인 링크를 클릭하세요: 여기를 클릭
```

링크를 클릭해 치지직 계정으로 로그인하면 연동이 완료됩니다.

```
[CHZZK] 인증이 완료되었습니다.
```

이후부터는 자동으로 토큰을 갱신하며 재접속 시 바로 연결됩니다.

---

## 4. 이벤트 수신 확인

연동 완료 후 치지직 채팅이나 후원을 보내면 GTDonation-Core의 이벤트가 발생합니다.

`debug: true`로 설정하면 서버 콘솔에서 수신 로그를 확인할 수 있습니다:

```
[CHZZK] 채팅 수신: 시청자닉네임 -> 안녕하세요!
[CHZZK] 후원 수신: 시청자닉네임 -> 1000
```

---

## 5. 인게임 액션 설정 (선택)

GTDonation-Event 플러그인을 설치하면 후원 금액별로 인게임 액션을 자동 실행할 수 있습니다.

자세한 내용은 [GTDonation-Event 설정](event/configuration.md)을 참고하세요.

Skript를 사용해 직접 이벤트를 처리하려면 [Skript 연동](event/skript.md)을 참고하세요.
