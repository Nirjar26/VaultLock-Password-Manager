<div align="center">

# VaultLock

### Zero-Knowledge Offline Password Manager for secure, local credential storage

</div>

## Problem Statement
Most password managers depend on cloud infrastructure, which introduces trust, privacy, and breach exposure concerns.
VaultLock solves this by keeping everything local: encryption, storage, and access control happen fully on-device.
Your master password and plaintext credentials never leave your machine.

## Features
- ● **Zero-knowledge vault:** All credential protection and key handling happen locally, with no cloud dependency.
- ● **Strong cryptography:** Credentials are encrypted with AES-based primitives and secured with Argon2id-derived keys.
- ● **Organized storage:** Credentials can be grouped with folders and marked as favorites for quick access.
- ● **Fast lookup:** Search and detail panels make finding account data quick during daily use.
- ● **Clipboard safety:** Copied secrets are automatically cleared from clipboard after use.
- ● **Logo enrichment:** Domain logos are fetched and cached to improve visual identification.
- ● **Modern desktop UI:** Fluent-style QML interface provides a clean Windows-native experience.
- ● **Portable distribution:** Build a self-contained executable for easy local deployment.

## Architecture / Flow
<div align="center">
    <img src="diagram/Architecture.png" alt="VaultLock Architecture Diagram" width="680" />
</div>

Flow summary:
1. User authenticates with master password.
2. Key is derived via Argon2id using local salt.
3. Credentials are encrypted/decrypted locally.
4. Data is persisted in local SQLite database.
5. UI reads decrypted data only in memory for active session.

Note: If you do not yet have an architecture image, add one at ./vaultlock/assets/architecture.png.

## Tech Stack
Frontend:
- PyQt6
- QML (Qt Quick)

Backend / Application Logic:
- Python 3.10+

Database:
- SQLite

Security / Crypto:
- cryptography
- argon2-cffi

Build / Packaging:
- PyInstaller

## How It Works
1. On first run, user creates a master password.
2. VaultLock derives a secure key locally using Argon2id.
3. New credentials are encrypted before being written to SQLite.
4. Credential list, folder tree, and details are rendered in QML.
5. Copy actions are protected by auto-clear clipboard behavior.

## Installation / Setup
```bash
git clone https://github.com/Nirjar26/VaultLock---Password-Manager.git
cd VaultLock---Password-Manager

python -m venv .venv
.venv\Scripts\activate
pip install -r requirements.txt

python main.py
```

## Environment Variables
No mandatory environment variables are required for local usage.

Optional examples:
```env
APP_ENV=development
VAULTLOCK_LOG_LEVEL=INFO
```

## API Endpoints
Not applicable for this project.
VaultLock is an offline desktop app and does not expose HTTP API endpoints.

## Folder Structure
```text
.
├── main.py
├── build.py
├── convert_icon.py
├── requirements.txt
├── README.md
├── release/
│   └── config/
└── vaultlock/
    ├── __init__.py
    ├── assets/
    │   └── logos/
    ├── controllers/
    │   └── main_controller.py
    ├── core/
    │   ├── config.py
    │   └── window_effects.py
    ├── database/
    │   ├── __init__.py
    │   └── db_manager.py
    ├── services/
    │   ├── encryption_service.py
    │   └── logo_manager.py
    └── ui/
        ├── Main.qml
        └── ...
```

## License
MIT License

## Author / Contact
Nirjar Goswami

GitHub: https://github.com/Nirjar26
Portfolio: https://nirjxr.dev
LinkedIn: https://www.linkedin.com/in/nirjarbharthigoswami-b593633a7
