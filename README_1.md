# Aquarium

A small living aquarium that runs in the browser. Everything is in one file, `index.html`. There is nothing to build or install.

## The fish

| Fish | Latin name | Eats |
|---|---|---|
| Northern pike | *Esox lucius* | shrimp, bloodworms |
| Ropefish (calabaricus) | *Erpetoichthys calabaricus* | bloodworms, shrimp |
| Goldfish | *Carassius auratus* | flakes, pellets, bloodworms |
| Angelfish | *Pterophyllum scalare* | flakes, bloodworms |
| Neon tetra | *Paracheirodon innesi* | flakes, bloodworms |
| Panda cory | *Corydoras panda* | pellets, bloodworms, flakes |

## The cleaners

| Cleaner | Latin name | Eats |
|---|---|---|
| Nerite snail | *Neritina natalensis* | algae, leftovers, plants |
| Bristlenose pleco | *Ancistrus cirrhosus* | algae, leftovers, plants |

## How it works

- The tank holds 10 fish (a new tank starts with five). Pick a food on the shelf, then tap the water to drop it. Keys 1 to 4 pick a food and space feeds.
- Fish get hungry over time. A fish that is kept fed grows from juvenile to full size in 10 to 15 minutes; a hungry fish stops growing, and a starving one weakens and eventually dies.
- The pike and the ropefish grow until they are nearly as long as the tank. The others stay smaller.
- Fish eat the way fish do: they notice food after a moment, point their mouth at it, suck it in and chew. A small fish tears pieces off food that is too big for its mouth; a full fish has a rounder belly.
- When a fish is fully grown it is netted, fried in a pan over a gas flame, served on a plate and eaten, which frees its place for a new fish. Under "More" you can switch this to manual; then tap a grown fish and choose "Catch and cook".
- A hungry fish shows a bubble with the foods it eats. Picking a food rings the fish that eat it, and the line above the dishes names them. "Diets" opens the full chart.
- Tap any fish to see its belly, health, size and age, or to rename it.
- Touch a fish and it darts away from your finger; drag through the water to scatter them. The goldfish comes back to look.
- "Plants" lets you add up to 20 plants from eight kinds. Pick one, then tap the sand as many times as you like; tap Done when finished. Tap a plant's base to see its name and state, trim it or remove it.
- Plants start as sprouts and grow while the light is on. Left alone they become overgrown: leaves yellow and dead leaves foul the water. Tap the plant to open its panel, which offers "Trim a little" or "Cut right back" to the size it was planted at. Healthy plants keep the water clean for longer.
- "Trim" at the top is a cutting tool you can use at any time: tap a plant at the height where you want it cut. Whatever is cut off floats up as cuttings. Tap them (or drag across them) to take them out; cuttings left for over a minute sink and rot, which fouls the water.
- Algae slowly films the front glass, faster with the light on and in dirty water. Drag across the tank to wipe it off. The "Glass" meter shows how clean it is.
- Uneaten food rots and makes the water murky. "Change water" lowers a hose end into the tank and drains it to 30%; a second hose then pours fresh water in until it is full again.
- "Add fish" also offers two cleaners, a nerite snail and a bristlenose pleco. You can keep up to three, in any mix, and they do not count toward the 10 fish. They are never fed, never grow and are never cooked, and the pike leaves them alone. They eat only the dirt and the plants:
  - they scrape algae off the glass, heading for the dirtiest patch each time (the snail leaves a clean trail wherever it crawls), and algae also forms more slowly. Three snails keep the glass clean on their own as long as the water is changed often enough to stay fresh. In murky water they turn sluggish, the algae gets ahead of them and the glass goes green, so then you have to change the water and wipe;
  - they eat food and plant cuttings lying on the sand before these can rot, and the water goes off more slowly, so it needs changing less often. One snail slows it by about 15%, one pleco by about 30%, and three cleaners together by about half;
  - when the glass is clean they nibble plants, the overgrown ones first, which means a little less trimming. They never eat a plant down to nothing.
- Tap a cleaner to see what it is doing or to rehome it. A touched snail pulls into its shell; the pleco darts off.
- A starving pike hunts tank-mates much smaller than itself. Turn this off under "More".
- "Auto-feeder" drops each hungry fish's favourite food. It does not change the water, wipe the glass or trim plants, so a tank left completely alone still goes downhill after about half an hour.
- "Time" makes hunger and growth run at 1, 2 or 5 times normal speed.
- The tank is saved in the browser (localStorage), so it is still there when you come back.

## Put it on GitHub Pages

1. Create a new public repository on GitHub, for example `aquarium`.
2. Upload `index.html` (and this `README.md`) with **Add file → Upload files**, then commit.
3. Open **Settings → Pages**. Under "Build and deployment" choose **Deploy from a branch**, pick the `main` branch and the `/ (root)` folder, and save.
4. After a minute or so the site is live at `https://YOUR-USERNAME.github.io/aquarium/`.

To try it without GitHub, open `index.html` in any modern browser.

## Changing things

All the tuning lives near the top of the script in `index.html`:

- `SP` holds one entry per species: speed, diet, how fast it gets hungry, its body shape, and `maxW` (full-grown length as a share of the tank width).
- `FOODS` holds the four foods: how filling each is, how fast it sinks, how long before it rots.
- `defaultTank()` sets which fish a new tank starts with.
- `PLANTS` holds the plant kinds, with `max` (largest size) and `over` (the size at which a plant counts as overgrown). `GROW_PLANT` is how many seconds a plant takes to reach its largest size.
- `SNAIL_V` and `SNAIL_R` are a snail's speed and half the width of the trail it cleans. `cleanAct` in `updCleaners` sets how murky the water must be before cleaners slow down.
- `CLEAN` holds the two cleaners. `water` and `alg` are how much each one slows the water going off and the algae forming (0.85 means 15% slower). `MAX_CLEAN` is how many the tank takes.
- `MAX_FISH` is the tank limit. Each species has `growMin`, the minutes it takes a well-fed fish to reach full size.

The page loads the Fraunces typeface from Google Fonts for headings and falls back to a system serif when offline.
