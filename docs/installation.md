<!-- Copied from https://lucidcore.tv/wiki/installation by the site's docs export: change the site, not this file. -->

# Install LucidCore

About five minutes. You need access to the computer, NAS or container that runs Emby Server, and an Emby administrator account.

## Before you start

- Emby Server 4.10 or newer, on Windows or Linux (Docker included).
- Nothing to install in the Emby apps. The old Android TV app only partly works, without LucidTop rows.
- Access to Emby’s files, to copy the plugin.
- A free license key, no email needed. Emby must reach lucidcore.tv to check it.

## 1. Download the plugin

It’s one file, the same for every plan. Your license key sets your usage allowances.

**[Download LucidCore.dll](https://github.com/Chesyre/LucidCore/releases/latest/download/LucidCore.dll)**

<details>
<summary>Need an older version?</summary>

Older versions may not work with recent Emby releases; use one only if the latest causes a problem.

[Every version](https://lucidcore.tv/wiki/installation#download) is listed on lucidcore.tv.

</details>

## 2. Put it in Emby’s plugins folder

Copy the file directly into the plugins folder, not into a subfolder. The usual locations are:

- **Windows**: `%AppData%\Emby-Server\programdata\plugins`
- **Linux**: `/var/lib/emby/plugins`
- **Docker**: `/config/plugins` inside the container, which is the `plugins` folder in whatever folder you mapped to `/config`.

Updating from an older version? Replace the old file with the new one.

## 3. Restart Emby

Restart the Emby server completely (refreshing the web page is not enough). LucidCore then appears in **Dashboard › Plugins**.

## 4. Add your license key

This step is required. Create a free key, no email needed.

1. Sign in on this site (Create a free key, or use the key you already have) and open your [account page](https://lucidcore.tv/dashboard). Copy your license key.
2. In Emby, open **Dashboard › Plugins › LucidCore › Overview**.
3. Paste the key in **License Key** and select **Verify License**. The status shows your plan.

## 5. Switch features on

Still in the Overview tab, switch on the features you want. Save, then restart Emby one more time.

Then set up each feature in its own tab:

- [LucidSearch](lucidsearch.md): works straight away, nothing to set up.
- [LucidPush](lucidpush.md): create your first message rule.
- [Requests with Seerr](seerr-integration.md): connect your Seerr server.
- [LucidTop](lucidtop.md): choose your home screen rows.
- [LucidFlow](lucidflow.md): describe the request destinations connected to Seerr.

## Your license and your servers

Each Emby server that verifies your key takes one place: Free, Plus and Pro cover 1 server, Harbor 2, and Whale 5. Users and devices are unlimited.

Your [account page](https://lucidcore.tv/dashboard) lists your servers. You can rename them, or remove one to free its place, for example when you move Emby to a new machine. If the plugin says *max servers limit reached*, every place is taken.

## Updates

LucidCore checks for a new version every day. Depending on your plan:

- **Automatic updates:** the new version downloads and installs itself. Restart Emby to switch to it.
- **Manual updates:** Emby tells you a new version is out. Download it here and replace the file.

> [!NOTE]
> **After a big Emby update**
>
> LucidCore works closely with Emby, so a major Emby update can occasionally need a LucidCore update too. If a feature stops working after updating Emby, check that you have the latest LucidCore, restart, and [contact us](https://lucidcore.tv/contact) with your Emby version.

## Uninstalling

1. Stop Emby.
2. Delete LucidCore.dll from the plugins folder.
3. Start Emby. Your library is exactly as it was.

LucidCore keeps its settings and its search database in folders named `LucidCore` inside Emby’s program data. Delete them too if you want nothing left behind.
