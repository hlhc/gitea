---
date: "2020-07-06T16:00:00+02:00"
title: "Usage: Push To Create"
slug: "push-to-create"
weight: 15
toc: false
draft: false
menu:
  sidebar:
    parent: "usage"
    name: "Push To Create"
    weight: 15
    identifier: "push-to-create"
---

# Push To Create

Push to create is a feature that allows you to push to a repository that does not exist yet in Gitea. This is useful for automation and for allowing users to create repositories without having to go through the web interface. This feature is disabled by default.

## Enabling Push To Create

In the `app.ini` file, set `ENABLE_PUSH_CREATE_USER` to `true` and `ENABLE_PUSH_CREATE_ORG` to `true` if you want to allow users to create repositories in their own user account and in organizations they are a member of respectively. Restart Gitea for the changes to take effect. You can read more about these two options in the [Configuration Cheat Sheet]({{< relref "doc/administration/config-cheat-sheet.en-us.md#repository-repository" >}}).

## Using Push To Create

Assuming you have a git repository in the current directory, you can push to a repository that does not exist yet in Gitea by running the following command:

```shell
# Add the remote you want to push to
git remote add origin git@{domain}:{username}/{repo name that does not exist yet}.git

# push to the remote
git push -u origin main
```

This assumes you are using an SSH remote, but you can also use HTTPS remotes as well.

## Push options (bonus)

Push-to-create will default to the visibility defined by `DEFAULT_PUSH_CREATE_PRIVATE` in `app.ini`. To explicitly set the visibility, you can use a [push option]({{< relref "doc/usage/push-options.en-us.md" >}}).
