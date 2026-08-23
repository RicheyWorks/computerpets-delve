# Delve design

Implement against this file, not folklore.

## Identity

- Product: **Delve**
- Repo: `computerpets-delve`
- Idea: Dungeon Crawl Pets
- Genre: Idle / text RPG
- Engine: Spring Boot
- Surface: `8095`

## Loop

You cannot watch Rui 24h. Delve is the off-duty dungeon: a pet leaves the overlay for N hours, returns with loot or a scratch. Overlay shows 'away on delve'.

## Play beats

- POST /v1/delve — pick pet + dungeon + duration.
- Pet is not on the desktop until return.
- Loot table keyed by species biome (panda ≠ reef).
- Scratch = medicine care on return.

## Neighbors

- computerpets-visitation (away state)
- computerpets-ledger
- computerpets-quests
- computerpets-companion
- computerpets-forensics (stuck jobs)

## Failure doctrine

Server crash mid-delve → job is durable, pet returns on restart. Double-send → 409. Death of a line is not a loot outcome.

## Hard rules

1. Minigames cannot mint or burn NFTs by themselves (Minter is the write path).
2. Stats come from lived overlay care + Dojo caps, not cash shop.
3. Species kits stay inside Lore. Illegal hybrids never spawn.
4. Fail soft: the desktop overlay process is not this process.
