# Set-1 reference

Facts for Low Meridian set 1. Decisions and build order live in [the plan](plan.md). Every number below is a starting spec. No match has been simulated.

## Match

Eight auditors. Each starts at 100 life, level 3, 2 scrip, and an empty bench. Level 3 fields 3 pieces. Level 9 fields 9.

The board is 4 ranks by 7 files. Your back rank is rank 0. Your front rank is rank 3. The enemy board is a mirror across the top. The bench holds 9 slots. Distance is axial hex distance, `max(|dq|, |dr|, |dq + dr|)`.

A piece is on one board hex or one bench slot. Star is 1, 2, or 3. A piece holds at most 3 items. Fielding a piece counts as 1 toward a trait, at every star.

## Phases

| Phase | Who acts | What ends it |
| --- | --- | --- |
| Planning | Every auditor. Buy, sell, move, reroll, buy experience, combine items. | 30 seconds. A local match can pause. The shipped loop does not. |
| Combat | Nobody. Pairings simulate from snapshots. | One side is gone, or 40 seconds, then true damage until someone dies. |
| Resolve | The reducer only. | Life, gold, streak, experience, and eliminations are written. |
| Item draft | Each auditor who cleared a creep board. | Pick 1 of 3 components. A creep loss skips the draft and costs 2 life. |

Rounds 1 and 2 are creeps. After that, every 5th round is a creep. The other rounds are auditor versus auditor. Stage is 1 plus the number of completed groups of 5 rounds. After stage 1, each later stage adds 2 to player damage.

Pairing avoids the previous opponent when another living auditor exists. An odd auditor fights the frozen board of the auditor who was eliminated most recently. A loss to that ghost still costs life. A win over a ghost pays a normal win. The ghost is the board at elimination.

If the last two auditors die in the same round, the one who entered with more life wins. If that life is tied, the one who dealt more player damage that round wins.

## Economy

Income is 5 base, plus 1 for a win, plus streak, plus interest. Interest is 1 per 10 scrip held before income is paid, and it caps at 5. Creeps count toward a streak. A streak of 2 or 3 pays 1. A streak of 4 pays 2. A streak of 5 or more pays 3.

Reroll costs 2 scrip and refreshes 5 shop slots. Unsold offers return to the pool. A shop lock holds the current offers.

Each planning phase grants 2 experience. 4 scrip buys 4 more experience.

A 1-star sells for its cost. A 2-star sells for 3 times cost. A 3-star sells for 9 times cost. The sale returns 1, 3, or 9 copies to the pool.

You cannot place a piece when the board count would pass the level cap. The reducer rejects the move.

Three copies of the same piece and the same star combine. The oldest of the three keeps its square and gains the star. Items move onto it until it holds 3. If a component would fall off and the bench is full, the combine fails. The combiner does not delete items.

## Level and shop odds

Odds are the chance a shop slot rolls that cost, before the pool filter. Slots are the board cap. Experience in the third column is the cost to reach the next level.

| Level | Slots | Experience to next | 1-cost | 2-cost | 3-cost | 4-cost | 5-cost |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 3 | 3 | 6 | 75 | 25 | 0 | 0 | 0 |
| 4 | 4 | 10 | 55 | 30 | 15 | 0 | 0 |
| 5 | 5 | 20 | 40 | 35 | 20 | 5 | 0 |
| 6 | 6 | 36 | 25 | 35 | 30 | 10 | 0 |
| 7 | 7 | 48 | 15 | 25 | 35 | 20 | 5 |
| 8 | 8 | 64 | 10 | 15 | 30 | 30 | 15 |
| 9 | 9 |  | 5 | 10 | 20 | 35 | 30 |

The pool is shared. Copy counts are 30, 22, 16, 12, and 10 for costs 1 through 5. A 3-star costs 9 copies, so a 3-star 5-cost is possible and leaves 1 copy in the pool. If a rolled cost is empty, fall through to the next lower cost that still has stock. One shop does not offer more copies than the pool holds.

## Roster

21 pieces. Five origins, six classes. The fight bench uses the first two rows only.

| Piece | Cost | Origin | Class | Ability |
| --- | --- | --- | --- | --- |
| Silt Warden | 1 | Brine | Warden | Shield the lowest-health adjacent ally for 4 seconds. |
| Kiln Singer | 1 | Cinder | Chorister | Cone of sparks toward the current target. Applies Burn. |
| Margin Clerk | 1 | Vellum | Clerk | Grant mana to the ally with the least mana. |
| Stamp Bailiff | 1 | Ironlot | Bailiff | Stun the current target on the first hit. |
| Lamplight Witness | 1 | Moth | Witness | A long poke that Marks the first enemy hit. |
| Tide Porter | 1 | Brine | Porter | Pull the nearest enemy one hex toward this piece. |
| Grate Warden | 2 | Cinder | Warden | Burn enemies standing next to this piece. |
| Index Witness | 2 | Vellum | Witness | Mark a target and cut its magic resist for 4 seconds. |
| Dock Porter | 2 | Ironlot | Porter | Shove the current target one hex away. |
| Night Clerk | 2 | Moth | Clerk | Pulse mana to adjacent allies. |
| Foam Chorister | 2 | Brine | Chorister | A wave that splashes to enemies beside the target. |
| Redact Bailiff | 3 | Vellum | Bailiff | Silence a line of enemies so they cannot cast. |
| Bulk Warden | 3 | Ironlot | Warden | Slam a shockwave through the front hexes. |
| Glass Chorister | 3 | Moth | Chorister | Fast splinter shots that splash one hex. |
| Ash Witness | 3 | Cinder | Witness | A burn nuke that refreshes Mark. |
| Anvil Chorister | 4 | Ironlot | Chorister | A slow circle slam around the target. |
| Seizure Bailiff | 4 | Moth | Bailiff | Leap to the farthest enemy and stun it. |
| Tide Clerk | 4 | Brine | Clerk | Grant mana to every ally and heal the lowest one. |
| Coal Porter | 4 | Cinder | Porter | Throw an enemy two hexes toward your back line. |
| Archivist Warden | 5 | Vellum | Warden | A large shield. While it holds, reflect part of the ability damage taken. |
| Last Porter | 5 | Moth | Porter | Pull the two farthest enemies one hex toward your front center, then strike both. |

Origin counts. Brine, Cinder, Vellum, and Ironlot have 4 pieces each. Moth has 5. There is no 5-piece Moth breakpoint.

Class counts. Warden, Chorister, and Porter have 4. Clerk, Bailiff, and Witness have 3.

Melee classes are Warden, Bailiff, and Porter, except where an ability says the piece leaps. Chorister range is 3. Clerk range is 3. Witness range is 4.

## Traits

Effects are data on the trait. Ability damage and shields grow 50% per star. Durations do not.

| Trait | Kind | At 2 | At the cap |
| --- | --- | --- | --- |
| Brine | Origin | 150 health. Attacks apply Soak. Soaked enemies take 10% more damage. | At 4. 400 health. Soak is 20%. Regen 1% max health per second. |
| Cinder | Origin | Attacks and abilities apply Burn, 20 damage per second for 4 seconds. Burn refreshes and does not stack. | At 4. Burn is 40 per second. Cinder pieces gain 20% attack speed. |
| Vellum | Origin | Start combat with 15 mana. | At 4. Start with 30 mana. Ability power is 25% higher. |
| Ironlot | Origin | 25 armor. | At 4. 60 armor, and a shield equal to 20% max health. |
| Moth | Origin | 15% dodge. | At 4. 30% dodge. At combat start, leap to the farthest enemy. |
| Warden | Class | Adjacent allies take 15% less damage. | At 4. 30% less, and wardens gain 20% max health. |
| Clerk | Class | An ally's attack grants that ally 4 extra mana. | At 3. The grant is 8 mana. |
| Bailiff | Class | First attack against a piece stuns it for 1 second. | At 3. The stun is 1.6 seconds and hits one adjacent enemy. |
| Chorister | Class | Damaging abilities splash 1 hex for 30%. | At 4. Splash is 2 hexes for 50%. |
| Witness | Class | First enemy damaged is Marked and takes 20% more damage. | At 3. Allies prefer the mark. A witness hit under 20% health executes. |
| Porter | Class | At combat start, pull the nearest enemy one hex closer. | At 4. Also push the attack target one hex away every 5 seconds. |

## Items

Creeps drop components. A component has a weak effect alone. Two specific components combine into one finished item. Other pairs do not combine in set 1. A piece holds 3 items. Combine fails if the result would drop a component and the bench has no empty slot.

| Component | Alone |
| --- | --- |
| Wax Seal | +20 armor |
| Ink Needle | +15% attack speed |
| Salt Lens | +20 ability power |
| Brine Phial | +15 starting mana |
| Cinder Nail | +20 attack damage |
| Ledger Chain | +200 health |
| Moth Thread | +15% dodge |
| Knot | Regenerate 8 health per second |

| Item | Made from | Effect |
| --- | --- | --- |
| Filing Plate | Wax Seal + Ledger Chain | +400 health, +30 armor |
| Brand Mail | Wax Seal + Cinder Nail | +25 armor. Attackers take 20 burn damage. |
| Quiet Seal | Wax Seal + Salt Lens | +20 armor, +25 ability power |
| Hasten Nail | Ink Needle + Cinder Nail | +20 attack damage, +25% attack speed |
| Margin Quill | Ink Needle + Salt Lens | +20% attack speed, +25 ability power. Attacks grant 5 mana. |
| Skip Thread | Ink Needle + Moth Thread | +20% attack speed, +20% dodge. The attack after a dodge crits. |
| Tide Lens | Brine Phial + Salt Lens | +30 ability power, +20 starting mana |
| Warm Chain | Brine Phial + Ledger Chain | +250 health, +20 starting mana |
| Lamp Pin | Cinder Nail + Moth Thread | +25 attack damage, +20% crit. Crits apply Burn. |
| Held Breath | Ledger Chain + Knot | +300 health. Regen 1.5% max health per second. |
| Green Ink | Knot + Salt Lens | +25 ability power. Heal the lowest ally for 15% of ability damage dealt. |
| Ash Cloak | Moth Thread + Wax Seal | +20 armor, +20% dodge |

Base crit chance is 0. A crit deals 150% physical damage.

## Combat

Ticks are 100 ms. Attack interval is 1000 ms divided by attack speed. An attack grants 10 mana. A hit taken grants 5 mana. A cast spends all mana.

Armor reduces physical damage. Magic resist reduces ability damage and Burn. Multiply the damage by 100, then divide by the sum of 100 and the defense.

The target is the nearest enemy. Ties go to the lowest health share, then to the piece that was created first. Dodge is rolled before damage. A Moth leap at combat start happens before the first cast.

The combat seed is a hash of match id, round, and the two auditor ids. The same seed replays the same fight.

Player damage on a loss is the stage flat bonus plus the sum of surviving enemy costs. A 2-star counts double. A 3-star counts triple.

## Bench contract

`/bench` imports one sim module. The page does not assemble combat from helpers.

```ts
simulate(snapshot, seed) => CombatResult
```

`simulate` is pure. It does not mutate the snapshot. The page may call it for a full fight or ask for one more tick. Same seed, same result.

The public types keep gold, life, mana, and hex coordinates distinct. A piece location is a board hex or a bench slot. Star is 1, 2, or 3.

Shop, interest, traits, items, and the other 19 pieces can exist as signatures. Unit 1 fills combat for Silt Warden versus Kiln Singer only.

## Suggested module map

```txt
src/sim/        reducer, shop, pool, pairing, combat, hex distance
src/content/    piece, trait, item, and odds tables
src/app/bench/  the manual fight page
```

The view sends commands. The reducer is the only writer of match state.
