<!-- Copied from https://lucidcore.tv/wiki/troubleshooting by the site's docs export: change the site, not this file. -->

# Troubleshooting

Most problems come down to a handful of causes. Start with the logs, then find your problem below.

## Read the logs first

In Emby, open **Dashboard › Logs**, open the most recent server log and search for `Lucid`. Every LucidCore line starts with the feature it comes from, such as `LucidSearch` or `LucidTop`, and usually says what went wrong.

When you ask for help, paste those lines: it saves a lot of back and forth.

## LucidCore doesn’t appear in Emby

- The file must be called `LucidCore.dll` and sit directly in the plugins folder, not in a subfolder and not zipped. See the [usual locations](installation.md#2-put-it-in-embys-plugins-folder).
- Restart the Emby server completely. Reloading the web page isn’t enough.
- Check that you run Emby Server 4.10 or newer. Older versions are not supported.
- On Linux and Docker, check that Emby is allowed to read the file (it should belong to the same user as the other plugins).

## License and plan

<details>
<summary>My key isn’t accepted.</summary>

Copy it again from your [account page](https://lucidcore.tv/dashboard) with the Copy button, so no space or character is missing. Then select **Verify License**.

</details>

<details>
<summary>The plugin says “max servers limit reached”.</summary>

Every server place in your plan is taken. Remove a server you no longer use from your [account page](https://lucidcore.tv/dashboard), then select Verify License again. If a smaller plan starts at your next renewal, a new server it doesn’t cover is refused too: keep your current plan on your account page to add it.

</details>

<details>
<summary>My plan change hasn’t appeared yet.</summary>

Check your plan on your [account page](https://lucidcore.tv/dashboard): a plan that starts at your next renewal shows its date there. Once it has started, select Verify License in the plugin. No Emby restart is needed.

</details>

## Search

<details>
<summary>A title is missing from the results.</summary>

Check that Emby shows it in the library. Right after installing, wait for LucidSearch to finish reading your library. If it’s still missing, run **Rebuild Search Database** in **Scheduled Tasks › LucidSearch**.

</details>

<details>
<summary>Search feels slow.</summary>

If Seerr requests are on, a slow Seerr can delay the Requestable results. Switch Seerr off for a moment to check. If search is fast without it, look at your Seerr server.

</details>

## Requests with Seerr

<details>
<summary>The Requestable category doesn’t appear.</summary>

- Open the Seerr address in a browser on the Emby server to make sure it’s reachable from there.
- Check the email, password and API key, then select Test Connection.
- Check that Enable Seerr is on and that your license key is verified.

</details>

<details>
<summary>People can see titles but can’t request them.</summary>

Check your requests on your account page. Once all are used up, a message says so, unless extra requests are left (turned on under Credits on your account page, 1 credit adds 25, and they never expire). Monthly requests start again on the 1st (UTC).

</details>

<details>
<summary>The request went through under the wrong name.</summary>

That person’s Emby account isn’t linked to a Seerr user yet, so the LucidCore user made the request. Import or link their Emby account in Seerr.

</details>

<details>
<summary>Requests are approved straight away, and LucidFlow never sorts them.</summary>

The Seerr account behind those requests approves its own: it is an administrator or has Auto-Approve. In Seerr, open Users, then that account’s permissions, and turn Auto-Approve off. The account entered in LucidCore must also not be an administrator.

</details>

## Home screen rows

<details>
<summary>The new rows don’t appear.</summary>

- Check that Enable LucidTop is on and that your plan includes this many rows, then restart Emby.
- Run **Generate Recommendations** and **TMDB Sections** once in **Scheduled Tasks › LucidTop**.
- For trending rows, check the TMDB key: the short API Key, not the long token.
- On the old Emby app for Android TV, these rows can’t appear. Use the current Emby app for Android TV instead.

</details>

## LucidPush messages

<details>
<summary>Nobody sees my message.</summary>

- Check that Enable LucidPush is on, that Emby was restarted, and that the rule itself is on.
- The app must be open when the message is sent. Messages are not kept for later.
- For “Item added”, “Scheduled time” and “API” rules, send to everyone or to people you pick: there is no person involved.
- Check the limits: the rule may have already reached its maximum.
- Use Test to check the message on your own screen.

</details>

## LucidFlow

See the questions at the end of the [LucidFlow page](https://lucidcore.tv/wiki/lucidflow#faq): nearly every problem comes from the webhook settings in Seerr.

## After an Emby update

If something stopped working right after updating Emby, check your account page for a newer LucidCore, install it and restart. If it still doesn’t work, [contact us](https://lucidcore.tv/contact) with your Emby version.

## Clean reinstall

1. Stop Emby.
2. Delete LucidCore.dll from the plugins folder.
3. Download a fresh copy from your account page or the install guide.
4. Put it in the plugins folder and start Emby.

> [!NOTE]
> Your LucidCore settings are kept. Your library is never affected.

## Still stuck?

Tell us what you tried, your Emby version, and paste the LucidCore lines from the log.

**[Contact form](https://lucidcore.tv/contact)**
