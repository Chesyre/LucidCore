<!-- Copied from https://lucidcore.tv/wiki/lucidsearch by the site's docs export: change the site, not this file. -->

# LucidSearch

Find films and shows in your library by their alternative names, even with a typo. Choose the languages and result types. Results come from LucidSearch’s own index.

## Every name a title goes by

Emby stores one title per film or show. People don’t always type that one. They type the Chinese release name, the original Japanese title, the name they remember from TV, or they misspell it. With Emby’s own search, if the words don’t match, the film looks missing even when it’s right there.

LucidSearch fixes this by enriching your library with the alternative titles known to TMDB, the free film database Emby also uses: the original title, translations and other release names, in the languages you pick. A well-known film can carry dozens of them. They are stored in LucidSearch’s index, so Emby’s own information is never changed.

- **“肖申克的救赎”**: The Shawshank Redemption, by its Chinese title.
- **“nyckeln till friheten”**: The Shawshank Redemption, by its Swedish title.
- **“sen to chihiro”**: Spirited Away, by its original title.
- **“la casa de papel”**: Money Heist, by its Spanish title.

The steps to switch this on are [below](#add-alternative-titles). It needs a free TMDB key.

## What else your viewers notice

- **Typos are forgiven.** “avengrs” finds The Avengers. Short words must be typed right; words of 4 to 8 letters can have one mistake, longer words two.
- **Accents are optional.** “amelie” finds Amélie, “pokemon” finds Pokémon.
- **Results appear as you type**, even when the last word is only half typed.

## Choose what search shows

Search can return movies, shows, seasons, episodes, people, collections and studios. You decide which ones appear, and in what order. For example, turn off episodes and seasons, and a search for a show returns the show itself instead of a long list of its episodes.

- Switch each kind of result on or off.
- Give each kind a priority from 1 to 10 to push movies or shows to the top.
- Set how many results of each kind to show, and hide weak matches.

These settings apply as soon as you save. The full list is in [Settings](#settings).

## Fast, by design

Emby’s built-in search looks through its database for every search, and that gets slow as a library grows. LucidSearch keeps its own index, built for one job: finding titles. It lives on your server’s disk, updates within seconds when your library changes, and answers as fast as people type, even on very large libraries.

## Turn it on

1. Open **Dashboard › Plugins › LucidCore › Overview**.
2. Switch on **Enable LucidSearch**, save and restart Emby.
3. LucidSearch reads your library once. On a big library this can take a few minutes, during which some titles may be missing from results.

## Add alternative titles

1. Create a free account on themoviedb.org, then go to your account settings, **API**, and request a key for personal use.
2. Copy the **API Key**: the short one, not the long “API Read Access Token”.
3. In **LucidCore › Overview**, paste the key under **TMDB**.
4. In **LucidCore › Search**, switch on **Enrich movie and series search with TMDB metadata**.
5. In **Additional translated title languages**, list the languages people on your server type in, as two-letter codes: for example `zh, en, es, ja`. Your server’s own language is always included.
6. Run **Force Refresh TMDB Metadata** once, in **Dashboard › Scheduled Tasks › LucidSearch**. It goes through your whole library and can take a while.

After that, a weekly task refreshes title metadata for new and upcoming releases.

## Settings

In **LucidCore › Search**. The defaults suit most servers.

- **Update search when Emby starts** (On): Checks your library for changes each time Emby starts.
- **Update search when the library changes** (On): New and removed titles show up in search within seconds.
- **Enrich movie and series search with TMDB metadata** (Off): Adds alternative titles from TMDB. Needs a TMDB key.
- **Additional translated title languages**: Two-letter codes, separated by commas. Your server’s language is always included.
- **Max results per type** (10): How many movies, shows, people and so on to show for each kind (1 to 500).
- **Minimum match quality** (0 %): Hides weak matches. Leave at 0 to show everything.
- **Movies, TV shows, Episodes, Seasons, People, Collections, Studios** (All on): Choose which kinds of results appear.
- **Priority for each kind (1 to 10)**: Higher numbers come first. Movies and shows start at 6, people at 4, the rest at 2.

## Scheduled tasks

In **Dashboard › Scheduled Tasks › LucidSearch**:

- **Rebuild Search Database** (When needed): Reads the whole library again. Run it if results look wrong or incomplete.
- **Refresh TMDB Metadata** (Sundays, 3 am): Refreshes title metadata for movies and shows released in the last 30 days or coming soon.
- **Force Refresh TMDB Metadata** (When needed): Applies a new TMDB key or new languages to the whole library.

## Good to know

> [!NOTE]
> - Music isn’t part of LucidSearch. Searches that include music use Emby’s normal search.
> - With [Seerr requests](seerr-integration.md) on, search also shows titles people can ask for.
