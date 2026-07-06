# 액션 설정

GTDonation-Event는 후원 금액별로 인게임 액션을 자동 실행합니다. `plugins/GTDonationEvent/config.yml`에서 설정합니다.

> `script-mode: true`이면 config.yml의 액션이 실행되지 않습니다. Skript로 직접 처리할 때 사용하는 모드입니다. → [Skript 연동](skript.md)

---

## 기본 구조

```yaml
script-mode: true  # 기본값. 액션을 사용하려면 false로 변경

events:
  1000:
    action: BREAD
    target: player
  5000:
    action: STEAK
    target: random
  10000:
    action: BUFF
    target: all
```

`events` 아래에 후원 금액을 키로 작성합니다. 정확히 일치하는 금액에만 액션이 실행됩니다.

---

## action 목록

| action | 설명 |
|---|---|
| `BREAD` | 플레이어에게 빵 지급 |
| `STEAK` | 플레이어에게 스테이크 지급 |
| `EXP_BOTTLE` | 경험치 병 여러 개 투척 |
| `BUFF` | 랜덤 포션 효과 부여 |

---

## target 목록

| target | 설명 |
|---|---|
| `player` | 후원을 받은 플레이어 본인 |
| `random` | 온라인 플레이어 중 무작위 1명 |
| `all` | 서버 전체 온라인 플레이어 |

---

## 액션별 추가 설정

### EXP_BOTTLE

투척할 경험치 병 개수의 범위를 설정합니다.

```yaml
exp-bottle:
  min-count: 3
  max-count: 8
```

### BUFF (랜덤 포션)

부여할 포션 효과의 지속 시간, 강도, 제외 목록을 설정합니다.

```yaml
random-buff:
  duration-seconds: 60
  amplifier: 1
  exclude-effects:
    - POISON
    - WITHER
    - BLINDNESS
    - NAUSEA
```

`exclude-effects`에 등록된 효과는 랜덤 후보에서 제외됩니다. 부정적인 효과를 제외할 때 사용하세요.

---

## 전체 예시

```yaml
script-mode: false  # 액션을 사용하려면 false로 변경

exp-bottle:
  min-count: 3
  max-count: 8

random-buff:
  duration-seconds: 60
  amplifier: 1
  exclude-effects:
    - POISON
    - WITHER
    - BLINDNESS

events:
  1000:
    action: BREAD
    target: player
  3000:
    action: STEAK
    target: random
  5000:
    action: EXP_BOTTLE
    target: player
  10000:
    action: BUFF
    target: all
```
