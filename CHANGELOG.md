# Changelog

What changed in each version of LucidCore. The plugin file of each version is on the [Releases](https://github.com/Chesyre/LucidCore/releases) page.

## 1.3.0 - 2026-10-16

### Seerr requests

- Request status now follows Seerr: approvals, declines and new arrivals show up, for older requests too.
- New Refresh Seerr Request Status scheduled task: it checks Seerr every 15 minutes. Change how often in Scheduled Tasks.
- New Declined and Failed status, with their own icons and texts in the Seerr tab. Only the person who asked sees them.
- A declined title can be requested again.
- A movie and a series with the same TMDB number no longer share a status.

### LucidTop

- New My Requests row: each person's Seerr requests, newest first, with where each one stands, including those made on the Seerr website. It updates on screen when a request changes.

## 1.2.3 - 2026-10-13

### LucidSearch

- Emby starts faster: the search index loads in the background, and Emby answers searches until it’s ready.
- The search index is saved more safely, including when Emby stops, so recent changes survive a restart.
- Result kinds turned off in the settings are no longer indexed. Turning one back on rebuilds the index.
- Fewer calls to TMDB when your library updates.

### Seerr requests

- Requestable titles show up the first time you search for them.
- Requestable title pages open much faster, and apps keep their posters in cache.
- The message after a request goes only to the person who made it.
- Requestable title pages no longer list unrelated extras or show an error when the heart is removed.

### LucidTop

- Recommended for you now takes actors, directors, writers and producers into account.
- Rows show watched marks, favourites and unwatched episode counts like Emby’s own rows, and refresh after you watch something.
- A row keeps its titles when an update fails.

### LucidFlow

- Seerr now shows a clear error when the webhook secret is wrong.

## 1.2.2 - 2026-10-12

- Settings page text updates.

## 1.2.1 - 2026-10-06

### Seerr requests

- On the page of a title people can request, your message now comes first, in bold, with the title’s own description below it.

### LucidTop

- Recommended for you leaves out everything a person has already started, even a series stopped after one episode. A title they start leaves their row straight away and the next one takes its place.
- A series now counts more for each season the person finished.
