# WispUO shard list

`shards.json` is the list of known shards that WispUO's Shards dialog and first-run wizard offer under "From the list". Choosing
one fills the address, port, type, encryption and client version; the user's UO folder and proxy are never part of it.

The copy in the WispUO repository (`shard-list/`) is built into the program. The panel also downloads the published copy at start
from `https://raw.githubusercontent.com/ArdXxX/wispuo-shard-list/main/shards.json` (the address can be changed or cleared in Help →
Panel settings) and keeps the last good one in `%APPDATA%\WispUO\shards-cache.json`, so a shard added here reaches every
installation without a new release. To publish, copy this folder to the public `wispuo-shard-list` repository (https://github.com/ArdXxX/wispuo-shard-list).

## Format

```json
{
  "format": 1,
  "shards": [
    {
      "name": "Shard name as shown in the list",
      "host": "login.example.com",
      "port": 2593,
      "kind": "Standard",
      "encrypt": false,
      "clientVersion": "7.0.117.1",
      "defaultShard": "",
      "relayUsesLoginHost": false,
      "website": "https://example.com",
      "notes": "Anything worth knowing (shown in the shard's notes)."
    }
  ]
}
```

| Field | Required | Meaning |
|---|---|---|
| `name` | yes | Unique (case does not matter). |
| `host`, `port` | yes | The login server. |
| `kind` | no | `Standard` (ServUO, ModernUO, RunUO, Sphere, POL…; the default) or `Official` (EA/OSI). |
| `encrypt` | no | Login and game encryption (official servers and the shards that require it). |
| `clientVersion` | yes | The client version the shard expects, four numbers (`7.0.117.1`). |
| `defaultShard` | no | Name in the login's shard list to enter; empty = the first one. |
| `relayUsesLoginHost` | no | Connect to the game server through the login address (shards behind NAT). |
| `website`, `notes` | no | Shown in the shard's notes. |

Entries with a missing name, address or version, or a version that is not four numbers, are skipped. A file with another
`format` number, or that is not valid JSON, is ignored as a whole and the previous list stays. Only add a shard after checking its
address and client version against the shard's own site or a working client.
