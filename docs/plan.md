# Low Meridian

Low Meridian is an autochess. Eight auditors buy repossessed citizens from a shared pool, file them onto a hex board, and stop controlling them when the round starts. The last auditor with life owns the ledger.

This page records why the project is shaped this way. Lookup values live in [the reference](reference.md).

## The city

The sea left the basin. The salt stayed. The Census stayed longer. Every resident owes a presence tax in scrip. Miss the payment, and the Census repossesses the name and files the body as a piece.

You play an Auditor. Three copies of the same piece are the Census agreeing the name is the same person. The filing is promoted. That promotion is a star. Scrip left unspent earns interest, one coin per ten held, and never more than five. The Census pays that interest to keep scrip off the street.

Origins are where the Census filed a piece. Classes are the job stamped on the filing. Each piece has one origin and one class. The roster is hand-built. A random piece generator would make the traits unreadable.

## Where it runs

Build the game as a Next.js app in TypeScript, and deploy it to Vercel.

The game is the shop, the interest, and a fight the player does not control. Those are tables plus a tick loop. A browser can show them while the numbers are still wrong. Unity is a later client, and only after the rules are already fun and you want a store build. Unreal is the wrong tool. Godot 4 in 2D is the fallback only if the game must be a download on day one.

This assumes one or two people who can ship TypeScript. A team that already lives in Unity should say so. That fact would move the plan.

## Why the board is 2D

The board and the pieces are flat tokens on an SVG hex grid. The name and the origin color stay readable at a glance. A player spends the planning phase reading the board, and a labeled token is easier to read than a 3D box.

Combat stores axial hex coordinates. A later 3D skin can replace the drawing. It must not rewrite the fight.

## How the code is split

Nothing under `src/` is game code yet. `src/app/page.tsx` is the create-next-app starter. Keep the split below when you add the game.

`src/sim` owns the reducer and `simulate(snapshot, seed)`. It has no DOM. Tests call it directly.

`src/content` owns the tables. Pieces, traits, items, shop odds, and the round calendar are parsed once at load.

`src/view` draws the hexes and the shop, and it sends commands. It does not know the damage formula.

A match is one state and a phase. The phases are planning, combat, resolve, and item draft. A command is legal only in the phase that owns it. Combat copies the boards and returns a result. Resolve is the only writer of life and gold.

## What exists today

- Next.js 16, React 19, TypeScript, Tailwind 4, App Router, `src/` directory.
- Scripts in `package.json`: `dev`, `build`, `start`, `lint`.
- No shop, no combat, no `/bench`, and no Vercel project link.

## Build order

Build one unit, prove it, then start the next.

1. Two pieces and one seed. A fight ends, and the same seed ends the same way.
2. Shop, pool, and stars. Buying three copies makes a 2-star, and the pool count moves.
3. Interest, experience, and the board cap. A planning round changes gold and refuses an illegal placement.
4. Traits as rows. A new breakpoint does not add a branch in the view.
5. Items. Two components become one item, or the command fails cleanly.
6. Seven auditors. A local match finishes. Their play is a heuristic. They buy pairs and put melee on the front rank.

The other seven auditors are a command source, same as a human. Network play is the same reducer on a server, after local matches are worth playing.

## The manual test

The first page is `/bench`. You set a seed, press Run, and read the winner, the remaining health, and the tick count. Run again with the same seed and the numbers match. Step walks one tick. Reset restores the start. Prove that in the browser before a deploy.

The two pieces on that page are Silt Warden and Kiln Singer.

## Left out of set 1

Carousel, trait emblems, a sixth origin, dual-trait pieces, 6-piece breakpoints, an economy class, and any piece script outside the ability union. Add them after the 21-piece loop is fun to lose.

## Numbers

Every number in the reference is a starting spec. No match has been simulated. Change health, burn, odds, and player damage in the content tables, then replay the seeds. Do not retune those numbers in the view.
