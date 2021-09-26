# ForcePack

Envoyez votre resource pack à chaque joueur qui se connecte, et poussez-en un nouveau à ceux déjà en ligne sans redémarrer le serveur.

## Fonctionnalités

- Applique le resource pack de la configuration quand un joueur se connecte au serveur.
- `/forcepack reload [hash]` réapplique le pack à tous les joueurs en ligne : une mise à jour du pack prend donc effet immédiatement, et le nouveau hash peut être donné directement dans la commande.
- Les joueurs qui refusent le pack, ou dont le téléchargement échoue, sont expulsés ou simplement avertis, selon `Server.kick`.
- Le hash SHA-1 de la configuration est transmis au client : un pack modifié est donc retéléchargé au lieu d'être servi depuis le cache du client.

## Prérequis

- Spigot/Paper 1.17 ou supérieur.
- Gradle pour compiler : le wrapper `gradlew` est inclus.

## Installation

1. Compilez le plugin (voir plus bas) et déposez le jar dans le dossier `plugins/` de votre serveur.
2. Éditez `plugins/ForcePack/config.yml` avec l'URL et le hash de votre pack.
3. Lancez `/forcepack reload` pour l'envoyer aux joueurs déjà en ligne.

## Configuration

```yaml
Server:
  ResourcePack:
    url: https://example.com/pack.zip
    hash: bb3cb6741d9bae330f868f43edcdcebbed5550db
  kick: true
```

- `url` : l'adresse de téléchargement du pack, qui doit être joignable par les joueurs.
- `hash` : le SHA-1 du zip, en hexadécimal minuscule.
- `kick` : `true` expulse un joueur qui refuse le pack ou dont le téléchargement échoue, `false` se contente de l'avertir.

## Commandes

| Commande | Description | Permission |
| --- | --- | --- |
| `/forcepack reload [hash]` | Renvoie le pack à tous les joueurs en ligne, éventuellement avec un nouveau hash | `forcepack.reload` |

La console peut toujours lancer la commande.

## Crédits

Écrit à l'origine par SamB440, maintenu ici par Uxzylon.

## Compilation

```sh
./gradlew shadowJar
```

Le jar est écrit dans `build/libs/`.
