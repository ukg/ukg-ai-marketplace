# Set up UKG Bryte for your organization

This guide shows an admin how to turn on UKG Bryte for your organization. UKG Bryte has two parts that you set up:

- The **plugin**. It adds the skills that help Claude handle HR tasks.
- The **connector**. It connects Claude to the UKG Bryte MCP server, the UKG service that looks up and updates your UKG data.

You install the plugin, and then you add the connector with the URL that UKG gave you. Installing the plugin does not add the connector. Users then connect with their own UKG account.

## Before you start

You need:

- A Claude Team or Enterprise plan.
- The Owner or Primary Owner role. On Enterprise, a custom role that can manage the organization's libraries also works.
- The MCP server URL for your organization.

UKG gives you the URL during onboarding. The URL depends on your environment:

- Production: `https://<tenant>.connector.ukg.net/mcp`
- UAT: `https://<tenant>.staging.connector.ukg.net/mcp`

Use the URL exactly as UKG gave it, from `https://` through `/mcp`. Do not add a slash at the end, and do not change the capitals. Claude accepts only these formats, so a URL on any other host does not work. If you cannot find your URL, ask your UKG contact.

## Step 1: Install the plugin

The plugin adds the skills, and it carries the UKG Bryte connector entry.

1. Open Organization settings, then Plugins & skills.
2. On the Inventory tab, select UKG Bryte.
3. Under Distribution, find Install. Choose how the plugin installs for the people it is available to:

| Setting | What users get |
|---|---|
| Available to install | The plugin appears in the plugin marketplace. Users can install or uninstall it at any time. |
| Installed by default | The plugin is pre-installed for all users. Users can disable or uninstall it. |
| Not available | The plugin is hidden from the plugin marketplace. Users cannot see it or install it. |
| Required | The plugin is pre-installed and always on. Users cannot disable or uninstall it. |

For all users to have UKG Bryte, choose Installed by default or Required. To give specific groups a different setting, use Install targeting on the same page.

## Step 2: Add the connector

When you install the plugin, the UKG Bryte connector shows as Not added. An Owner must add it. Do this one time.

1. In Claude, open Customize, then Plugins. Select UKG Bryte.
2. On the Connectors tab, find UKG Bryte. Its status is Not added. Select Add for your team.
3. Enter the URL that UKG gave you. For a UAT environment, use the UAT URL.
4. Save.

You can also add the connector in Organization settings, then Connectors.

Users then connect with their own UKG account. If UKG gives you a new URL later, remove the connector and add it again with the new URL. Users must then connect again.

## Step 3: Make sure that it works

Test with one account first.

1. Open Customize, then Plugins. Make sure that UKG Bryte is installed and that its Connectors tab does not say Not added.
2. Connect UKG Bryte. Sign in with your UKG account when the browser window opens.
3. Start a new chat. Ask Claude "Who is my manager?". Claude must answer with your UKG data.

When this works for one account, tell your other users that they can connect.

## What your users see

- If you chose Installed by default or Required, UKG Bryte is already in Customize, then Plugins, with its two skills.
- The Connectors tab of the plugin shows UKG Bryte as Not added, Not connected, or Connected.
- Each user connects one time and signs in with their own UKG account.

## If something goes wrong

| Problem | What to do |
|---|---|
| Claude does not accept the URL when you add the connector | Check the URL against the formats in "Before you start". It must start with `https://`, use lowercase, end with `/mcp` with no slash after it, and be a production or UAT address. |
| The Connectors tab shows UKG Bryte as Not added | An Owner must add the connector (Step 2). Users cannot add it for the team. |
| UKG Bryte shows as Not connected | Connect it and sign in with your UKG account. If there is nothing to connect, ask an Owner to add the connector (Step 2). |
| The connector does not connect, or sign-in fails | Make sure that the URL matches the URL from UKG exactly. Ask your UKG contact to confirm that your organization is onboarded. |
| The plugin is not in Customize, then Plugins | Ask an Owner to set the Install setting to Available to install or higher (Step 1). |
| In the CLI, the browser shows a redirect error after sign-in | Make sure that no other program uses port 8080. Then sign in again. |

## Use UKG Bryte in Claude Code

A user of Claude Code can add the plugin without the admin settings. The user runs these commands:

```bash
claude plugin marketplace add ukg/ukg-ai-marketplace
claude plugin install ukg-bryte@ukg
```

The plugin adds the skills. The connection comes from the UKG Bryte connector that your organization added, so an Owner must complete Step 2 first. The user needs network access to github.com to install the plugin.

In the CLI, sign-in uses the redirect address `http://localhost:8080/callback`. This is the page where the browser returns after sign-in. Port 8080 must be free on the computer of each CLI user when they sign in. If another program uses port 8080, sign-in fails.

## Limits and removal

- Each connector uses the one URL that you entered.
- To turn UKG Bryte off, remove the UKG Bryte connector in Organization settings, then Connectors. Then set the plugin's Install setting to Not available.

## More help

- [Connectors directory](https://claude.com/docs/connectors/directory)
- [Manage plugins for your organization](https://claude.com/docs/plugins/admin)
