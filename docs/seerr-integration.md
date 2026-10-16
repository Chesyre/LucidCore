<!-- Copied from https://lucidcore.tv/wiki/seerr-integration by the site's docs export: change the site, not this file. -->

# Requests with Seerr

Let your Emby users request titles outside your library from search. Requests go to your Seerr request manager and follow your approval rules.

## What your viewers do

1. They search in Emby as usual.
2. Title information outside your library appears under **Requestable**.
3. They open one and press the heart.
4. A message confirms the request. It is now in Seerr, under their name, and your usual approval rules apply.

Posters then show where the request stands:

- **Pending**: Waiting for your approval.
- **Processing**: Approved in Seerr; not yet available in your library.
- **Partially available**: Some episodes of a show are already there.
- **Available**: It’s in your library.
- **Declined**: Turned down in Seerr. It can be asked for again.
- **Failed**: Approved, but Seerr couldn’t pass it on to your movie or series server. You can retry it in Seerr.

Declined and Failed only show to the person who asked, on the title’s page and in their [My requests](lucidtop.md#the-rows-you-can-add) row on the home screen.

> [!NOTE]
> On Requestable titles, the heart submits a request instead of marking a favourite. A series request includes all seasons and follows the account’s Seerr permissions.

LucidCore doesn’t provide films or shows: use it with content you have the right to use.

## Your monthly requests

Counts are per calendar month. They start again on the 1st (UTC). One series request counts once, whatever the number of seasons. Clicking a title already requested does not count.

Requests on the Seerr website itself are not counted as requests from Emby. When requests run out, people still see titles they could request, with a message that requests are used up, unless extra requests are left: once you turn them on under Credits on your account page, 1 credit adds 25 requests and 25 sorts that never expire.

When requests are counted, lucidcore.tv must be reachable when a request is made. Only the license key and server ID are sent for the count, not the title or who asked.

## Before you start

- A compatible Seerr request manager that your Emby server can reach.
- LucidSearch switched on. Requestable titles appear through LucidSearch’s search, so without it Seerr shows nothing in Emby.
- An admin account on Seerr, to create a user and copy the API key.

## Set it up

1. In Seerr, create a local user for LucidCore, for example **EmbyBot**, with the **Request** permission. Don’t make it an administrator, and leave **Auto-Approve** off.
2. Copy the API key from **Seerr › Settings › General**.
3. In Emby, open **LucidCore › Overview** and, under **Seerr**, fill in the Seerr address as the Emby server sees it (for example `http://192.168.1.20:5055`) and the API key. LucidFlow uses the same two.
4. In **LucidCore › Seerr**, fill in EmbyBot’s email and password, then select **Test Connection**.
5. In **Overview**, switch on **Enable Seerr**, and LucidSearch if it isn’t on yet, then save.

## Why a Seerr account, and not just the API key?

Seerr counts a request sent with the API key alone as made by its administrator, and approves it at once. You would lose the approval step, and LucidFlow could not choose which server gets it. A request made under an ordinary account waits for approval in Seerr: you approve it yourself, or LucidFlow picks its server and approves it if you allowed that.

## Whose name is on the request?

LucidCore looks for the Seerr user linked to the Emby user who pressed the heart. Seerr creates that link when it imports your Emby users. If there is one, the request is theirs, with their own limits and permissions. If not, it is made by the LucidCore user (EmbyBot). Either way, Seerr applies that account’s permissions: requests from an account with Auto-Approve are approved at once, and LucidFlow never sees them.

## Settings

- **Max results** (10): How many Requestable titles to show in search (1 to 50).
- **Hide items without a poster** (Off): Leaves out obscure titles that have no artwork.
- **Poster quality** (90): Image quality of the posters and backgrounds of these titles, from 10 to 100. Lower loads faster on slow connections.
- **Overlay Seerr status icon on posters** (On): Adds the status icon. You can set its corner, size, distance from the edge and opacity.
- **Custom status icons folder** (Optional): Use your own icons: a folder with `pending.png`, `processing.png`, `partially_available.png`, `available.png`, `declined.png` and `failed.png`.
- **Texts**: Every label and message viewers see can be reworded. Leave a Notification badge empty to show none. On a title’s page, your message comes first, in bold, with the title’s own description below it. They are in English by default, so translate them if your users speak another language.

## Good to know

> [!NOTE]
> - Searches need at least two letters.
> - Requestable can also list titles someone already asked for or that are already available. Their status is shown, so nobody asks twice.
> - Statuses follow Seerr: a declined request can be made again. LucidCore checks Seerr every 15 minutes; change it in **Dashboard › Scheduled Tasks › Seerr**.
> - LucidCore waits about two seconds for Seerr at most, so a slow Seerr never makes Emby slow. It just shows fewer Requestable results.
> - Requests use the heart button that is already on every title’s page, so they work in the official Emby apps with nothing to install.
