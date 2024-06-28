# remote-shred-VPS
Script to remote shred a VPS via SSH and perform a shutdown.

## Instructions
1. Copy script to `/dev/shm/shred_all.sh`
2. Enable execution:
```
chmod +x /dev/shm/shred_all.sh
```
3. To run:
```
nohup bash -c 'coproc (bash -c "source /dev/shm/shred_all.sh")' &
```
