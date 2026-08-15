# BedrockProtocol-Legacy (Amber-PM) — MCPE 1.2.13 (protocol 223)

Implementación completa y original de los paquetes del protocolo de red de **Minecraft: Pocket Edition 1.2.13** (protocolo **223**), tal como los define PocketMine-MP en esa versión — clases de paquetes reales, no una capa de traducción/compatibilidad.

## Contenido

```
src/protocol/
├── ProtocolInfo.php          # CURRENT_PROTOCOL = 223, MINECRAFT_VERSION = 'v1.2.13', IDs de todos los paquetes
├── PacketPool.php            # Registro/fábrica de paquetes
├── DataPacket.php / Packet.php
├── LoginPacket.php, LevelEventPacket.php, MovePlayerPacket.php, StartGamePacket.php, ... (paquete por clase)
└── types/                    # Tipos auxiliares usados dentro de los paquetes
```

122 archivos en total (clases de paquetes + tipos).

## Origen

Extraído de `src/pocketmine/network/mcpe/protocol/` del proyecto `PocketMine-MP-MultiProtocol` (rama `master`).

Repo hermano: [BedrockData-Legacy](https://github.com/Amber-PM/BedrockData-Legacy) · Fuente completa: [Bedrock-MultiProtocol-Legacy](https://github.com/Amber-PM/Bedrock-MultiProtocol-Legacy)
