# Slack Project Notifier

> A GitHub Action :rainbow:

Magical slack updates for transparent GitHub project movement.

---

1. Move project card.
2. Receive Slack notification of the new column.
3. Click button to view issue.

## Adding Environment Variables

GitHub has [excellent documentation](https://docs.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets#creating-encrypted-secrets-for-a-repository).

Retrieve the values using the below instructions.

Once you have them, create them as secrets!

### Retrieve Slack WebHook URL

Slack has [juicy documentation](https://slack.com/intl/en-ca/help/articles/115005265063-Incoming-Webhooks-for-Slack).

It looks like this:

```
https://hooks.slack.com/services/WARGARBLE/GURBLE
```

### Retrieve GitHub Token

GitHub has [dandy documentation](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token).

It looks like this:

```
lkfdl;skf;ldskf;ldskfl;dskf;ldks9239239821
```

### Set Single Project Mode

You can set the Action to work only on one project.

You can then setup multiple actions on multiple projects, if you want.

1. Setup the action and move a card once in the project you want to "lock".
2. View the console output for the "Magical Slack Notifier" step.
3. Look for the line that says: `Your PROJECT variable for the current project is:`
4. Add that as PROJECT.



### Example Workflow

```yaml
name: Slack Project Notifier

on:
  project_card:
      types: [moved]

jobs:
  notify:
    runs-on: ubuntu-latest
    steps:
      - name: Magical Slack Notifier
        uses: hayuna/github-action-slack-project-notifier@1.2
        with:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}
          PROJECT: ${{ secrets.PROJECT }}
          TOKEN: ${{ secrets.TOKEN }}
```
