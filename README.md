# ForcePack

Send your resource pack to every player who joins, and push a new one to the players already online without restarting the server.

## Features

- Applies the resource pack from the configuration when a player joins the server.
- `/forcepack reload [hash]` re-applies the pack to everyone online, so a pack update takes effect immediately, and the new hash can be given straight on the command line.
- Players who decline the pack, or whose download fails, are kicked or only warned, depending on `Server.kick`.
- The SHA-1 hash from the configuration is passed to the client, so a changed pack is downloaded again instead of being served from the client cache.

## Requirements

- Spigot/Paper 1.17 or newer.
- Gradle to build it: the `gradlew` wrapper is included.

## Installation

1. Build the plugin (see below) and drop the jar in your server's `plugins/` folder.
2. Edit `plugins/ForcePack/config.yml` with the URL and the hash of your pack.
3. Run `/forcepack reload` to send it to the players who are already online.

## Configuration

```yaml
Server:
  ResourcePack:
    url: https://example.com/pack.zip
    hash: bb3cb6741d9bae330f868f43edcdcebbed5550db
  kick: true
```

- `url`: where the pack is downloaded from, and it has to be reachable by the players.
- `hash`: the SHA-1 of the zip, in lowercase hexadecimal.
- `kick`: `true` kicks a player who declines the pack or whose download fails, `false` only warns them.

## Commands

| Command | Description | Permission |
| --- | --- | --- |
| `/forcepack reload [hash]` | Re-sends the pack to every player online, optionally with a new hash | `forcepack.reload` |

The console can always run the command.

## Credits

Originally written by SamB440, maintained here by Uxzylon.

## Building

```sh
./gradlew shadowJar
```

The jar lands in `build/libs/`.
