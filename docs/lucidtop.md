<!-- Copied from https://lucidcore.tv/wiki/lucidtop by the site's docs export: change the site, not this file. -->

# LucidTop

New rows for the Emby home screen: recommendations for each person, what’s trending, what’s top rated and what others on your server are watching. Every row only shows titles you already have.

## The rows you can add

### From your library

- **Recommended for you**: Titles from your library that match what this person likes and hasn’t started yet.
- **Recently watched on this server**: What people on your server watched lately, most recent first. It doesn’t say who watched it.

### What’s trending

These lists come from TMDB, the free film database, and are narrowed down to what you own.

- **Trending movies**: Today, or this week.
- **Trending TV**: Today, or this week.
- **Trending, movies and TV together**: Today, or this week.
- **Popular movies, Popular TV**: What people are watching the most right now.
- **Top rated movies, Top rated TV**: The best-rated titles of all time.

## Set it up

1. Get a free TMDB key and paste it in **Overview**. The steps are on the [LucidSearch page](lucidsearch.md#add-alternative-titles); one key serves both. It’s needed for trending, popular and top rated rows only.
2. In **LucidCore › LucidTop**, set the **Language** of the lists as a two-letter code, such as `en` or `zh`.
3. Pick a ready-made layout, or build your own list of rows.
4. In **Overview**, switch on **Enable LucidTop**, save and restart Emby.
5. Rows are filled overnight. To see them right away, run **Generate Recommendations**, **TMDB Sections** and **Users Recently Watched** once, in **Dashboard › Scheduled Tasks › LucidTop**.

## Ready-made layouts

**Replace with preset** swaps your rows for one of these. You can change any row afterwards.

- **Cinéphile**: Top rated movies, Trending movies this week, Popular movies.
- **Series Fan**: Popular TV, Trending TV this week, Top rated TV.
- **Balanced**: Trending this week (movies and TV), Popular movies, Popular TV.
- **Discovery**: Recommended for you, plus Trending today and this week.
- **Minimal**: Just Recommended for you.

## Settings for each row

- **Display name**: The title shown above the row, in any language.
- **Max items** (20 or 30): How many titles the row shows, from 1 to 100.
- **Media filter**: Movies, TV series, or both.
- **Position** (−1): 0 puts the row first. A higher number places it among Emby’s own rows. −1 adds it after them, −2 after that, and so on.
- **Enabled** (On): Hide a row without deleting it.

## How recommendations work

For each person, LucidTop looks at what they watched, finished, gave up on, marked as favourite or rated, and how recently; a series counts more for each season they finished. It then prefers titles from your library that share genres, actors, directors, studios, writers or tags with what they enjoyed, leaves out everything they have already started, even a series stopped after one episode, and mixes things up so the row doesn’t repeat itself every day. A title they start leaves their row straight away and the next one takes its place.

Someone with little history sees popular titles from your library until LucidTop knows them better.

### Fine-tuning

You can change how much each clue counts, from 0 to 100:

- **Genre** (45): Same kind of film or show.
- **Director** (25): Same director.
- **Actor** (20): Same actors.
- **Studio** (10): Same studio or network.
- **Tag, Writer** (8): Same tags, same writers.
- **Producer** (5): Same producers.

Two more options skip people who can’t watch anything anyway: disabled accounts, and users without permission to play media. Both are on by default.

## When rows update

- **Generate Recommendations** (Daily, 4 am): Rebuilds Recommended for you.
- **TMDB Sections** (Daily, 5 am): Refreshes trending, popular and top rated rows.
- **Users Recently Watched** (Daily, 6 am): Refreshes Recently watched on this server.

## Good to know

> [!NOTE]
> - Rows only contain titles in your library. Nothing leads to a dead end.
> - Recently watched on this server shows what others watched, without names. Think about whether everyone on your server is comfortable with that before adding it.
> - Disabled accounts, and users who can’t see any library, don’t get the extra rows.
> - Rows appear in every official Emby app, except the old Emby app for Android TV: it isn’t officially supported and can’t show LucidTop rows.
