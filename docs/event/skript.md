# Skript 연동

GTDonation-Event를 Skript에서 직접 제어할 수 있습니다.

**필요 플러그인:** [Skript](https://github.com/SkriptLang/Skript), [skript-reflect](https://github.com/SkriptLang/skript-reflect)

`config.yml`에서 `script-mode: true`(기본값)로 설정하면 config.yml의 액션은 무시되고, Skript에서 이벤트를 직접 처리합니다.

---

## 기본 구조

파일 상단에 필요한 클래스를 모두 `import:` 합니다. `DonationScriptAPI`는 이벤트 핸들러 내에서 `Bukkit`을 통해 가져옵니다.

```sk
import:
    dev.gotiger.gTDonationCore.event.ChatEvent
    dev.gotiger.gTDonationCore.event.DonationEvent
    dev.gotiger.gTDonationEvent.GTDonationEvent
    dev.gotiger.gTDonationEvent.config.DonationTarget
    org.bukkit.Bukkit

on ChatEvent:
    set {_player} to event.getPlayer()
    set {_chatterName} to event.getChatterName()
    set {_message} to event.getMessage()
    set {_platform} to event.getPlatform()

    send "&b[%{_platform}% - 채팅]&f %{_chatterName}%님이 %{_player}%님의 채널에서: %{_message}%" to console

on DonationEvent:
    set {_api} to Bukkit.getPluginManager().getPlugin("GTDonationEvent").getScriptAPI()
    set {_player} to event.getPlayer()
    set {_donorName} to event.getDonorName()
    set {_amount} to event.getAmount()
    set {_message} to event.getMessage()
    set {_platform} to event.getPlatform()

    if {_amount} = 1000:
        {_api}.getRandomBuff({_player}, {_donorName}, DonationTarget.PLAYER)
```

---

## API 메서드

### 빵 / 스테이크

```sk
{_api}.getBread({_player}, {_amount})
{_api}.getSteak({_player}, {_amount})
```

### 경험치 병

```sk
{_api}.getExpBottle({_player}, {_donorName})
```

### 랜덤 버프

```sk
{_api}.getRandomBuff({_player}, {_donorName})
```

### 채팅 채굴

채팅창에 특정 단어를 입력한 플레이어에게 아이템을 지급합니다.

```sk
# getChatMining(player, seconds, word1, word2, radius)
{_api}.getChatMining({_player}, 30, "곡괭이", "pick", 10)
```

### 채팅 슈팅

채팅창에 특정 단어를 입력하면 불덩이를 발사합니다.

```sk
# getChatShooting(player, seconds, word)
{_api}.getChatShooting({_player}, 30, "발사")
```

---

## target 지정

모든 API 메서드는 마지막 인자로 `DonationTarget`을 받아 대상을 지정할 수 있습니다.

| target | 설명 |
|---|---|
| `DonationTarget.PLAYER` | 후원받은 플레이어 본인 (기본값) |
| `DonationTarget.RANDOM` | 온라인 플레이어 중 무작위 1명 |
| `DonationTarget.ALL` | 서버 전체 온라인 플레이어 |

```sk
{_api}.getBread({_player}, {_amount}, DonationTarget.RANDOM)
{_api}.getSteak({_player}, {_amount}, DonationTarget.ALL)
```
