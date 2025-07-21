---
date: '2025-07-20T22:19:28-03:00'
title: How to configure pass in a new system
tags:
- pass
- gopass
---

1. Export you GPG key
2. In the new machine, import you GPG key
3. Clone the your pass repository

```sh
# Old machine:
gpg2 --export-secret-keys $KEY_ID >> key.gpg

# New machine:
gpg2 --import key.gpg
git clone $REPO_LINK
export PASSWORD_STORE_DIR=$PATH_TO_REPO
```
