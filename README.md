# Xiaomi Toolbox catalog

Public HTTP catalog for [xiaomi-toolbox](https://github.com/b1nhm1nh/xiaomi-toolbox) (`com.xiaomi.toolbox`).

The app is private. These files are public so devices can `GET` them without a GitHub token.

Base:

```
https://raw.githubusercontent.com/b1nhm1nh/xiaomi-toolbox-public/main/Toolbox-data/
```

| File | Consumed as |
|---|---|
| `Pif-props.json` | `kaorios_pif_json` (+ digits → `kaorios_security_patch`) |
| `device-model.json` | device picker cache |
| `app-props.json` | game auto-import cache |

HTTP: `User-Agent: Xiaomi-Toolbox/1.0`.

## Security

This catalog intentionally contains **no keybox XML**. A keybox holds the private key material of an Android attestation certificate chain — publishing one leaks credentials, and a revoked keybox fails Play Integrity. Import keyboxes from device storage in the app (`Settings.Global["kaorios_keybox_xml"]` is set locally, per device).

## Update this catalog

Source of truth for edits: `D:\w\git\tools-org\xiaomi-toolbox\Toolbox-data\`.

```
pwsh D:\w\git\tools-org\xiaomi-toolbox\tools\catalog-push.ps1
pwsh D:\w\git\tools-org\xiaomi-toolbox\tools\catalog-verify.ps1
```

Do not point the APK at this private app repo’s raw URLs — they 404 without a token.
