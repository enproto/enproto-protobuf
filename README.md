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
protoc --go_out=. --go_opt=paths=source_relative \
       --proto_path=proto \
         proto/session/enproto.proto
```

### Example: Generate Python code

```bash
python -m grpc_tools.protoc \
       -I proto \
       --python_out=. \
         proto/session/enproto.proto
```

> ⚠️ Remember to add `proto` to your include path (`-I proto`) when compiling.

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

- [enproto-spec](https://github.com/enproto/enproto-spec) — Full specification and design documents
- [enproto-go](https://github.com/enproto/enproto-go) — Go implementation (in development)

---

## 📜 License

MIT License © enproto contributors