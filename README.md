# GitHub Status Notifier

> A Chrome extension to display your GitHub PR status notifications

## What it does

- Desktop notifications when a CI build passes, fails, gets approved, or is merged
- Popup shows the status of each PR and links to it (click on Desktop notifications to go to the tab)

*You need to add a token in the options on setup.*

![Notifications Screenshot](https://github.com/jeobrien/github-status-notifier/blob/master/extension/assets/images/notifications.png)
![Status Screenshot](https://github.com/jeobrien/github-status-notifier/blob/master/extension/assets/images/ok-status.png)


## To run this extension locally

- Clone the repo
- Go to chrome://extensions
- Click to enable Developer mode
- Click on Load unpacked extension and select the cloned repo
- Enable the extension

## How it works

Whenever a tab is open with a pull request, the background page requests the status of the PR and its head commit from the Github API using your access token to authenticate.

It stores the status and the last modified timestamp, and then polls the status API every minute to check for new updates. Since we are using the 'If Modified Since' header, any response that is a 304 Not Modified does not count towards API rate limits.

## For Github Enterprise
After cloning the repository, edit the manifest.json's github_url field to your git enterprise url (no leading http/https).

When creating an access token, copy from your git enterprise settings rather than through the provided link. Make sure to add the `repo` permission as well as `notification`.

All other steps are as normal.