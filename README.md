# enproto-protobuf

**Protocol Definitions for enproto — a lightweight, multi-language secure communication protocol.**

This repository contains the official `.proto` files for [enproto](https://github.com/enproto), defining the message formats used in secure communication via asymmetric (RSA) and symmetric (AES-GCM) encryption.

These definitions serve as the canonical source for all language-specific implementations.

---

## 📦 Repository Structure

```
proto/
├── common/
│   └── types.proto           # Shared types like Timestamp, Nonce, Version, etc.
├── session/
│   ├── rsa.proto             # RSA-based session initialization messages
│   └── aes.proto             # AES-GCM encrypted packet messages
└── enproto.proto             # (Optional) Root import file aggregating all .proto definitions
```

---

## 🔧 Usage

You can use the `.proto` files in this repository to generate language-specific SDKs.

### Example: Generate Go code

```bash
protoc --go_out=pb \
       --go_opt=paths=source_relative \
       --proto_path=../enproto-protobuf \
         enproto.proto
```

---

## 🗂 Defined Files

| File | Purpose |
|------|---------|
| `common/types.proto` | Shared structures like `Timestamp`, `Nonce`, `Version`, etc. |
| `session/rsa.proto` | RSA handshake messages (`SPRSAClientPacket`, `SPRSAServerPacket`, etc.) |
| `session/aes.proto` | AES-GCM encrypted packet structure (`AESGCMPacket`) |
| `enproto.proto` | (Optional) Aggregator file to import all definitions at once |

---

## 🧩 Related Projects

- [spec](https://github.com/enproto/specs) — Full specification and design documents
- [go-enproto](https://github.com/enproto/go-enproto) — Go implementation (in development)

---

## 📜 License

MIT License © enproto contributors