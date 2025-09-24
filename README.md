## Linux

```bash 1.
while :; do printf "> "; read c; $c > /dev/pts/1; done # Constantly reads input and executes command, redirecting output to the terminal.
```
```bash 2.
while :; do sleep 1; lsblk -Jo RM,VENDOR | jq -r '.blockdevices[] | select(.rm == true) | select(.vendor != null) | .vendor' | { read -r line || shutdown now; } done # Simple USB Kill Switch; in this case, it shuts down the system.
```
```bash 3.
while :; do sleep 1; { ssh 127.0.0.1 -p 22 '{ pbpaste 2>/dev/null || xclip -selection clipboard -o -display :0 2>/dev/null || wl-paste 2>/dev/null || powershell -NoProfile -Command "Get-Clipboard"; }'; } | { pbcopy 2>/dev/null || xclip -selection clipboard 2>/dev/null || wl-copy 2>/dev/null || powershell -NoProfile -Command "Set-Clipboard"; }; done # Constantly copies clipboard contents of remote machine to the local machine.
```

## Windows

```powershell 1.
while (1) { sleep 1; { ssh 127.0.0.1 -p 22 '{ pbpaste 2>/dev/null || xclip -selection clipboard -o -display :0 2>/dev/null || wl-paste 2>/dev/null || powershell -NoProfile -Command "Get-Clipboard"; }'; } | { pbcopy 2>/dev/null || xclip -selection clipboard 2>/dev/null || wl-copy 2>/dev/null || powershell -NoProfile -Command "Set-Clipboard"; }; } # Constantly copies clipboard contents of remote machine to the local machine.
```

## macOS

```zsh 1.
while :; do sleep 1; { ssh 127.0.0.1 -p 22 '{ pbpaste 2>/dev/null || xclip -selection clipboard -o -display :0 2>/dev/null || wl-paste 2>/dev/null || powershell -NoProfile -Command "Get-Clipboard"; }'; } | { pbcopy 2>/dev/null || xclip -selection clipboard 2>/dev/null || wl-copy 2>/dev/null || powershell -NoProfile -Command "Set-Clipboard"; }; done # Constantly copies clipboard contents of remote machine to the local machine.
```
