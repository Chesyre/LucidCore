<!-- Copied from https://lucidcore.tv/wiki/lucidpush by the site's docs export: change the site, not this file. -->

# LucidPush

Show a message in the Emby apps people have open: when something happens on your server, at a time you choose, or whenever your own scripts ask for it through the API.

## Ideas to start with

- **Welcome new people**: When: user logs in. Send to: the user involved. Messages per user: 1. “Welcome {User.Name}. Search works even with typos.”
- **Announce new films**: When: item added to library. Only when: item type is Movie. Send to: everyone. Messages per day: 1.
- **Warn before maintenance**: When: scheduled time, Saturday at 22:00. Send to: everyone. “The server restarts in 10 minutes.”
- **Tell everyone the server is back**: Your backup or update script calls the API when it’s done: “Back online.”

## Create a rule

1. In **LucidCore › Overview**, switch on **Enable LucidPush**, save and restart Emby.
2. Open the **LucidPush** tab and add a rule.
3. Give it a name, choose when it sends, who receives it, and write the title and message.
4. Select **Test** to see a preview on your own screen, even before saving.
5. Save. Each rule can be switched on or off from the list.

The tab also shows the devices connected right now and a history of messages sent.

## When a message can be sent

- **User logs in**: Someone signs in, with a password, a PIN or quick connect.
- **App connects**: An Emby app opens or wakes up, even if the person stayed signed in.
- **Playback starts**: Someone starts watching or listening.
- **Item added to library**: A new title appears on your server.
- **Scheduled time**: At a time and on days you pick, for example 22:00 on Saturday. Checked every 15 minutes.
- **API**: Another app or script asks for it. See the next section.

## Control it by API

Everything LucidPush does can also be driven from outside Emby: a script, a scheduled job, or your home automation. The LucidPush tab shows an **API key** for this. With it you can:

- **Send a message right away**, to everyone or to chosen people, with `/LucidPush/Notify`.
- **Run a saved rule** that uses the API trigger, with `/LucidPush/Fire`. Its conditions, recipients and limits still apply.
- **Manage rules** and read the users, connected devices and message history.

```
curl -X POST "http://YOUR-EMBY:8096/LucidPush/Notify" \
  -H "X-LucidPush-Key: YOUR-KEY" \
  -H "Content-Type: application/json" \
  -d '{"title":"Back online","body":"The server is up again."}'
```

```
curl -X POST "http://YOUR-EMBY:8096/LucidPush/Fire" \
  -H "X-LucidPush-Key: YOUR-KEY" \
  -H "Content-Type: application/json" \
  -d '{"id":"RULE-ID"}'
```

Leave out `userIds` to send to everyone. The Help tab of the plugin lists every address and how to find a rule’s ID.

> [!NOTE]
> **Keep the key private**
>
> Anyone with the key can manage your LucidPush rules. Regenerate it in the LucidPush tab if it leaks.

## Only in some cases

Add conditions to narrow a rule down. Choose whether **all** of them must match, or **any** one. You can check:

- the person: their name, whether they’re an administrator, what they’re allowed to do;
- the device and app, and whether they’re at home or away;
- the title: movie or episode, genre, year, rating, length, already watched or not;
- the time: hour, day of the week, weekend, date.

## Personal touches

Put details in curly brackets and LucidPush fills them in: `{User.Name}`, `{Item.Name}`, `{Device.Name}`, `{Time.Date}` and more.

What’s available depends on the trigger. A scheduled message, for example, has no “person involved”, so `{User.Name}` only works once the message is addressed to specific people.

## Limits, so nobody gets spammed

- **Minimum delay between messages** (0 = none): In minutes, per person.
- **Messages per user** (0 = no limit): Total per person. Set 1 for a one-time message.
- **Messages per day** (0 = no limit): For the whole server.
- **Delete this rule after** (0 = never): In days, for temporary announcements.
- **How long to show the message** (0): In milliseconds: 5000 is five seconds. 0 keeps it on screen until closed.

## Good to know

> [!NOTE]
> - Messages reach the Emby apps that are open at that moment. They are not phone notifications, emails or chat messages, and they are not kept for later.
> - “Item added”, “Scheduled time” and “API” rules have no person involved. Send those to everyone or to people you pick. Their conditions about the user apply to each person: “Account disabled” set to no leaves disabled accounts out.
> - Rules limited to certain devices can’t work with those three triggers.
> - In the history, “Sent” counts devices reached, not messages read.
