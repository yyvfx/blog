---
author: yyvf
data: "2025-08-22"
title: bootstrap gopass
summary: How to configure gopass in a new system
tags: [gopass, pass]
---

1. Export you GPG key
2. Import your GPG key in the destination machine
3. Clone your pass repository

```sh
# Source machine:
gpg2 --export-secret-keys $KEY_ID > key.gpg

# Destine machine:
gpg2 --import key.gpg
git clone $REPO
export PASSWORD_STORE_DIR=$PATH_TO_REPO
```
