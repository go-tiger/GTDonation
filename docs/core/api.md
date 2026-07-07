# GTDonationAPI

치지직 이벤트를 수동으로 발생시킬 때 사용합니다.

**클래스:** `dev.gotiger.gTDonationCore.api.GTDonationAPI`

---

## callDonationEvent

```java
GTDonationAPI.callDonationEvent(Player player, String donorName, int amount, String message, Platform platform)
```

| 파라미터 | 타입 | 설명 |
|---|---|---|
| `player` | `Player` | 후원을 받은 플레이어 |
| `donorName` | `String` | 후원자 닉네임 |
| `amount` | `int` | 후원 금액 |
| `message` | `String` | 후원 메시지 |
| `platform` | `Platform` | 플랫폼 (`CHZZK`, `SOOP`) |

---

## callChatEvent

```java
GTDonationAPI.callChatEvent(Player player, String chatterName, String message, Platform platform)
```

| 파라미터 | 타입 | 설명 |
|---|---|---|
| `player` | `Player` | 채팅 대상 플레이어 |
| `chatterName` | `String` | 채팅을 보낸 시청자 닉네임 |
| `message` | `String` | 채팅 내용 |
| `platform` | `Platform` | 플랫폼 (`CHZZK`, `SOOP`) |
