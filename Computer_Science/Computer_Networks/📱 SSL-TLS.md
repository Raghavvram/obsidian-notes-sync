### 🛠️ **SSL/TLS Handshake Flow: Three Phases**

|Phase|Step|Description|
|---|---|---|
|**1. Hello Phase**|🟢 Client Hello →|Client initiates handshake with: <br> - Supported SSL/TLS versions <br> - Cipher suites <br> - Compression methods <br> - Random nonce <br> - Optional extensions like SNI, ALPN|
||🔵 Server Hello →|Server responds with: <br> - Chosen version <br> - Cipher suite <br> - Random nonce <br> - Session ID (optional) <br> - Extensions (if any)|
||🟣 Server Certificate →|Server sends its certificate (usually X.509) to prove identity|
||🟡 Server Key Exchange →|Sent only if using ephemeral key exchange (e.g. ECDHE)|
||🔶 Certificate Request →|(Optional) Server may request client certificate (for mutual auth)|
||🔷 Server Hello Done →|Indicates server finished initial hello steps|

---

|Phase|Step|Description|
|---|---|---|
|**2. Key Exchange Phase**|🟩 Client Certificate →|(Optional) Client sends its certificate if requested|
||🟦 Client Key Exchange →|Client generates pre-master secret and encrypts it with server’s public key|
||🟨 Certificate Verify →|(Optional) Client proves ownership of private key with a signature|
||🟥 Change Cipher Spec →|Client tells server future messages will be encrypted|
||🟪 Finished →|Client sends an encrypted hash of all prior handshake messages|
||⬜ Server: Change Cipher Spec →|Server switches to encrypted mode|
||🧩 Server Finished →|Server sends its encrypted hash of handshake messages|

---

|Phase|Step|Description|
|---|---|---|
|**3. Session Phase**|✅ Secure Session Established →|Both sides now have: <br> - Verified identities (if mutual auth) <br> - Shared symmetric key (derived from pre-master secret) <br> - Encrypted communication using chosen cipher suite|
||🔄 Application Data Flow →|Data packets encrypted with symmetric keys; integrity protected|
||⛔ Connection Close (Optional) →|Either side may send a “close_notify” alert to end the secure session cleanly|

---

### 🧠 Extras You’ll Appreciate

- The **Finished** messages are the first to be encrypted and verify the handshake’s integrity.
- In modern TLS (1.2 and 1.3), many optimizations (e.g. 0-RTT in TLS 1.3) reduce this flow’s complexity.
- TLS 1.3 drops many legacy components like separate Key Exchange and Change Cipher Spec.
