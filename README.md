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

# BedrockProtocol (Amber-PM)

Protocol packet implementation used by **AmberPM** for its primary multi-version range: **v1.20.0 (protocol 589)** through **v1.26.30/40 (protocol ~1001-2168)**.

Sourced from `vendor/vapebw/bedrock-protocol` inside the AmberPM project.

## Contents

```
src/
```

Packet classes, serializers, and type definitions for every modern protocol version AmberPM handles through its dynamic multi-version translation layer.

## Note

This repo does **not** include protocol handling for legacy protocol 223 (MCPE 1.2.13). That client predates several modern Bedrock networking concepts (the item type dictionary handshake, block-palette/runtime-ID handshake, `ItemStackRequestPacket`, `CreativeContentPacket`, `AvailableActorIdentifiersPacket`, `BiomeDefinitionListPacket`, modern crafting stations, the current `EntityMetadataFlags` layout, and the current `AvailableCommandsPacket` layout) and is handled by a dedicated legacy compatibility layer instead. See [BedrockProtocol-Legacy](https://github.com/Amber-PM/BedrockProtocol-Legacy).

Protocol 223 support is **experimental** and has known unresolved issues — see [Known issues with the multiprotocol / legacy layer](#known-issues-with-the-multiprotocol--legacy-layer) below.

## Known issues with the multiprotocol / legacy layer

These affect legacy protocol 223 (MCPE 1.2.13) clients specifically; modern-protocol clients (589-1001) are not affected.

1. **Crafting results are granted and then rolled back** — ingredients are consumed, the result briefly appears, then the transaction is rolled back and ingredients are restored. The legacy inventory-transaction conversion path is currently unreliable.
2. **Recipe-book category switching and search crash the client** — opening the recipe book's search UI or switching categories closes the 1.2.13 client.
3. **Modern players become invisible to legacy clients** — after combat or a command is executed, a modern-protocol player disappears from a 1.2.13 client's view (while still connected and visible to modern clients). Root cause not yet verified.

Full details, reproduction steps, and status tracking: `KNOWN_ISSUES.md` in the full Amber source repo. Guidance for adding/fixing support for legacy versions: `ADDING_LEGACY_VERSIONS.md` in the same repo.

## Origin

Extracted from `PockeT/vendor/vapebw/bedrock-protocol/` of the Amber-PM/Amber project.
