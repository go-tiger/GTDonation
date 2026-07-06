# 이벤트

GTDonation-Core는 치지직 채팅/후원 수신 시 Bukkit 이벤트를 발생시킵니다.

---

## DonationEvent

후원이 수신될 때 발생합니다.

**클래스:** `dev.gotiger.gTDonationCore.event.DonationEvent`

| 메서드 | 반환 타입 | 설명 |
|---|---|---|
| `getPlayer()` | `Player` | 후원을 받은 플레이어 |
| `getDonorName()` | `String` | 후원자 닉네임 |
| `getAmount()` | `int` | 후원 금액 |
| `getMessage()` | `String` | 후원 메시지 |
| `getPlatform()` | `Platform` | 플랫폼 (`CHZZK`, `SOOP`) |

### 예시

```java
@EventHandler
public void onDonation(DonationEvent event) {
    Player player = event.getPlayer();
    String donor = event.getDonorName();
    int amount = event.getAmount();
    String message = event.getMessage();

    player.sendMessage(donor + "님이 " + amount + "원 후원했습니다: " + message);
}
```

---

## ChatEvent

채팅 메시지가 수신될 때 발생합니다.

**클래스:** `dev.gotiger.gTDonationCore.event.ChatEvent`

| 메서드 | 반환 타입 | 설명 |
|---|---|---|
| `getPlayer()` | `Player` | 채팅 대상 플레이어 |
| `getChatterName()` | `String` | 채팅을 보낸 시청자 닉네임 |
| `getMessage()` | `String` | 채팅 내용 |
| `getPlatform()` | `Platform` | 플랫폼 (`CHZZK`, `SOOP`) |

### 예시

```java
@EventHandler
public void onChat(ChatEvent event) {
    Player player = event.getPlayer();
    String chatter = event.getChatterName();
    String message = event.getMessage();

    player.sendMessage("[채팅] " + chatter + ": " + message);
}
```

---

## Platform enum

| 값 | 설명 |
|---|---|
| `CHZZK` | 치지직 |
| `SOOP` | 숲 (SOOP) |

```java
if (event.getPlatform() == Platform.CHZZK) {
    // 치지직 전용 처리
}
```
