# 설정 (config.json)

GTDonation-Chzzk의 설정 파일은 `plugins/GTDonationChzzk/config.json`입니다. 서버를 처음 실행하면 자동으로 생성됩니다.

---

## 전체 설정

```json
{
  "CLIENT_ID": "your-client-id-here",
  "CLIENT_SECRET": "your-client-secret-here",
  "displayHost": "localhost",
  "port": 20154,
  "https": false,
  "callbackPath": "/callback",
  "debug": false
}
```

---

## 항목 설명

### CLIENT_ID
- **타입:** `string`
- **설명:** 치지직 OpenAPI 앱의 Client ID
- 치지직 개발자 센터에서 발급받은 값을 입력하세요.

```json
"CLIENT_ID": "abc123xyz"
```

---

### CLIENT_SECRET
- **타입:** `string`
- **설명:** 치지직 OpenAPI 앱의 Client Secret

```json
"CLIENT_SECRET": "secret_key_here"
```

---

### Redirect URI 관련 설정

`displayHost`, `port`, `https`, `callbackPath` 4개 값이 합쳐져 Redirect URI가 완성됩니다.

```
{https ? "https" : "http"}://{displayHost}:{port}{callbackPath}
```

예시:
```json
"displayHost": "play.example.com",
"port": 20154,
"https": false,
"callbackPath": "/callback"
```
→ `http://play.example.com:20154/callback`

이 값을 치지직 개발자 센터 앱의 **Redirect URI**에 그대로 등록해야 합니다.

| 항목 | 타입 | 기본값 | 설명 |
|---|---|---|---|
| `displayHost` | string | `"localhost"` | Redirect URI에 사용할 도메인 또는 IP |
| `port` | number | `20154` | 콜백을 수신할 포트. 방화벽에서 개방 필요 |
| `https` | boolean | `false` | `true`이면 URL이 `https://`로 시작 |
| `callbackPath` | string | `"/callback"` | Redirect URI의 경로 부분 |

---

### debug
- **타입:** `boolean`
- **기본값:** `false`
- **설명:** `true`로 설정하면 채팅 및 후원 수신 시 콘솔에 상세 로그를 출력합니다.

```json
"debug": true
```

---

## 설정 후 할 일

설정 파일을 저장한 뒤 서버를 재시작하세요. 변경 사항은 재시작 후 적용됩니다.
