<!-- Copied from https://lucidcore.tv/wiki/lucidflow by the site's docs export: change the site, not this file. -->

# LucidFlow

LucidFlow sorts requests between the servers connected to your Seerr request manager. Describe each server in a sentence; LucidFlow assigns each request.

## Is it for you?

It helps when Seerr has more than one movie server or more than one series server, such as separate servers for anime and other shows. With a single server of each kind, Seerr already sends each request to the right one.

LucidFlow only picks which server a request is assigned to in Seerr. It never handles the films or shows themselves.

It works on its own: LucidFlow sorts requests made on the Seerr website as well as those made from Emby, so you can use it without turning on requests from Emby or LucidSearch. It only needs your Seerr address and API key.

## What happens to a request

1. Someone asks for a movie or show in Seerr.
2. Seerr tells LucidFlow that a request is waiting for approval.
3. LucidFlow looks up the title: genres, language, studios, networks, story.
4. It chooses the server whose description fits best: a movie server for a movie, a series server for a show.
5. The request is updated in Seerr with that server, and approved if you allowed it for that server.

If no server clearly fits, the request is left untouched for you to handle.

LucidFlow only sees requests that wait for approval. A request Seerr approves at once, because the account behind it is an administrator or has Auto-Approve, goes to Seerr’s default server.

Every sort counts, whether the request came from Emby or the Seerr website. When sorts run out, new requests wait in Seerr for your approval, as without LucidFlow, unless extra sorts are left (Credits, on your account page). Nothing is lost.

## Set it up

1. In **LucidCore › Overview**, fill in your Seerr address and API key under **Seerr**. If requests with Seerr already work, this is done.
2. In **LucidCore › LucidFlow**, select **Import servers from Seerr** to import the movie and series servers configured in Seerr.
3. Write a description for each server (see below) and choose whether requests sent there are approved automatically. Remove servers LucidFlow shouldn’t use.
4. In **Overview**, switch on **Enable LucidFlow**, save and restart Emby.
5. In Seerr, open **Settings › Notifications › Webhook** and:
   - enable the agent;
   - tick the notification type **Request Pending Approval**;
   - paste the **Webhook URL** shown in the LucidFlow tab;
   - paste the **Webhook Authorization secret** from the LucidFlow tab as the Authorization header;
   - replace the JSON payload with the one below, then save.

```
{
  "notification_type": "{{notification_type}}",
  "media": {
    "media_type": "{{media_type}}",
    "tmdbId": "{{media_tmdbid}}"
  },
  "request": {
    "request_id": "{{request_id}}"
  }
}
```

> [!NOTE]
> **Heads up**
>
> Seerr must be able to reach the Webhook URL. If Seerr runs in Docker, `localhost` means the container itself: use the Emby server’s IP address instead.
>
> Older setups used the license key as the Authorization value. It still works for now, but switch to the dedicated secret: it’s safer.

## Writing good descriptions

Write which requests each server should handle, with more than one clue: genre, language, studio, network. Up to 600 characters each. Some examples:

- **Series, Anime**: “Japanese anime only: keyword anime, original language Japanese, or studios like ufotable, MAPPA, Toei. Not Western animation.”
- **Movies, Animation**: “Animation in English, studios like Pixar, Disney, DreamWorks. No Japanese anime.”
- **Movies, Documentaries**: “Documentaries only: nature, history, science, biographies.”
- **Movies, Other**: “Default: anything that doesn’t clearly match another server.”

A default destination handles requests that do not match another description. LucidFlow can’t tell 4K from HD: quality isn’t part of a title’s details.

## History

The LucidFlow tab lists the last 50 decisions: the title, the server chosen, the folder, and whether it was approved automatically. You can clear it at any time.

## What is sent, and where

For each new request, the public details of the title (name, summary, dates, language, genres, keywords, studios, networks, streaming services) and your server descriptions are sent to lucidcore.tv. It asks an AI to choose a server, and sends the answer back. Nothing about your users, their viewing or your library is sent. Each sort also sends one count, with your license key and server ID. More in the [FAQ](https://lucidcore.tv/faq#privacy).

## Good to know

> [!NOTE]
> - Only requests waiting for approval are handled. Seerr’s test notification is accepted and ignored.
> - To stop LucidFlow completely, switch it off in Overview **and** disable the webhook in Seerr.
> - Seerr gets its answer right away; the choice itself usually follows within seconds.
