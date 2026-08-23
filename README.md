# Delve

**Dungeon Crawl Pets** — Send pets on automated timed expeditions for loot while they still live on the desktop.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) universe. Map: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. Gameplay contract is frozen. Engine choice is the one in the brief. Implementation comes next.

## Loop

You cannot watch Rui 24h. Delve is the off-duty dungeon: a pet leaves the overlay for N hours, returns with loot or a scratch. Overlay shows 'away on delve'.

## Genre & engine

- Genre: **Idle / text RPG**
- Engine: **Spring Boot**
- Stack: Java 21 · Spring Boot 3.3 · scheduler expeditions · PostgreSQL loot · Companion UI later
- Default surface: `8095`

## How you play

1. POST /v1/delve — pick pet + dungeon + duration.
2. Pet is not on the desktop until return.
3. Loot table keyed by species biome (panda ≠ reef).
4. Scratch = medicine care on return.

## Talks to

- computerpets-visitation (away state)
- computerpets-ledger
- computerpets-quests
- computerpets-companion
- computerpets-forensics (stuck jobs)

## Failure doctrine

Server crash mid-delve → job is durable, pet returns on restart. Double-send → 409. Death of a line is not a loot outcome.

Canon rules that never yield:

- 210 living kinds. No illegal hybrids.
- Overlay pets can get tired, sick, or hide. Tokens are not burned by a minigame.
- Desktop walk stays the main quest. Closing Delve must leave Rui walking.

## Layout

```
computerpets-delve/
  README.md
  LICENSE
  docs/DESIGN.md
  src/                implementation lands here
```

## Run (Windows)

```powershell
mvn -q -DskipTests package; java -jar target/delve-1.0.0-SNAPSHOT.jar
```

Meet Rui first via the [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md). This game is optional.

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
