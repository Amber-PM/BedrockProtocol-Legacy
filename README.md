<p align="center">
	<a href="https://github.com/Amber-PM/Amber">
		<img src="https://raw.githubusercontent.com/Amber-PM/Amber/main/.github/readme/amberpm.png" width="128" height="128" alt="AmberPM Logo" title="AmberPM" />
	</a><br>
	<b>Part of AmberPM — a high-performance, multi-version fork of PocketMine-MP written in PHP</b>
</p>

<p align="center">
	<a href="https://github.com/Amber-PM/Amber"><img alt="AmberPM main repo" src="https://img.shields.io/badge/AmberPM-main%20repo-blue"></a>
	<a href="https://discord.gg/k55gScjTs3"><img src="https://img.shields.io/badge/Discord-Chat-5865F2?logo=discord&logoColor=white" alt="Discord" /></a>
	<a href="LICENSE"><img src="https://img.shields.io/badge/License-LGPL--3.0-blue.svg" alt="License" /></a>
</p>

# BedrockProtocol-Legacy (Amber-PM) — MCPE 1.2.13 (protocol 223)

Complete, original implementation of the network protocol packets for **Minecraft: Pocket Edition 1.2.13** (protocol **223**), as defined by PocketMine-MP for that version — real packet classes, not a translation/compatibility layer.

## Contents

```
src/protocol/
├── ProtocolInfo.php          # CURRENT_PROTOCOL = 223, MINECRAFT_VERSION = 'v1.2.13', all packet IDs
├── PacketPool.php            # Packet registry/factory
├── DataPacket.php / Packet.php
├── LoginPacket.php, LevelEventPacket.php, MovePlayerPacket.php, StartGamePacket.php, ... (one class per packet)
└── types/                    # Helper types used inside packets
```

122 files total (packet classes + types).

## Known issues

AmberPM's legacy compatibility layer for this exact protocol (223 / MCPE 1.2.13) is **experimental** and has known, unresolved gameplay issues:

1. **Crafting results are granted and then rolled back** — the crafted item briefly appears, then the transaction is rolled back and ingredients are restored.
2. **Recipe-book category switching and search crash the client**.
3. **Modern players become invisible to legacy clients** after combat or command execution.

Full details, reproduction steps, and status: see [`KNOWN_ISSUES.md`](KNOWN_ISSUES.md).

Guidance for extending or fixing legacy-protocol support (how the compatibility layer is organized, what's required to add another legacy version, the full implementation/testing checklist): see [`ADDING_LEGACY_VERSIONS.md`](ADDING_LEGACY_VERSIONS.md).

## Origin

Extracted from `src/pocketmine/network/mcpe/protocol/` of the `PocketMine-MP-MultiProtocol` project (`master` branch).

Sibling repo: [BedrockData-Legacy](https://github.com/Amber-PM/BedrockData-Legacy) · Full source: [Bedrock-MultiProtocol-Legacy](https://github.com/Amber-PM/Bedrock-MultiProtocol-Legacy)
