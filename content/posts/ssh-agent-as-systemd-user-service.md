---
author: yyvf
data: "2025-08-24"
title: ssh-agent as systemd user service
summary: How I configure ssh-agent as a systemd user service
tags: [systemd, ssh-agent]
---

Create `~/.config/systemd/user/ssh-agent.service` with:

```service
[Unit]
Description=OpenSSH Agent
Documentation=man:ssh-agent(1)
Requires=ssh-agent.socket

[Service]
Type=simple
Environment=SSH_AUTH_SOCK=%t/ssh-agent.socket
ExecStart=/usr/bin/ssh-agent -D -a $SSH_AUTH_SOCK

[Install]
WantedBy=default.target
```

```sh
# To start the service:
systemctl --user start ssh-agent.service

# To reload systemd daemon:
systemctl --user daemon-reload

# To start this service automatically:
systemctl --user enable ssh-agent.service
```

Let chezmoi manage this folder:

```sh
chezmoi add ~/.config/systemd/user
```

You can also do the same thing for other user services, such as `foot-server`
if you use foot as your terminal emulator.

My user services: <https://github.com/yyvfx/dotfiles/blob/main/home/private_dot_config/systemd/user>

## References

- Noah Bailey blog: <https://nbailey.ca/hacks/ssh-agent/>
