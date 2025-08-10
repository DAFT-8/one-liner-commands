## Linux

```bash
while :; do printf "> "; read c; $c > /dev/pts/X; done # Constantly reads input and executes command, redirecting output to specified terminal.
```
```bash
while :; do sleep 1; lsblk -Jo RM,VENDOR | jq -r '.blockdevices[] | select(.rm == true) | select(.vendor != null) | .vendor' | { read -r line || shutdown now; } done # Simple USB kill switch; in this case, it shuts down the system.
```

## Windows

```powershell
```

## macOS

```zsh
```
