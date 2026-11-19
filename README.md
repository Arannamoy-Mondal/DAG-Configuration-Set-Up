# DAG-Configuration-Set-Up
# DAG 1 service autorun bash code
```bash
[Unit]
Description=DAG1 Service
After=network.target


[Service]
#Type=oneshot
User=root
ExecStart=
#RemainAfterExit=yes
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```
# DAG 2 service autorun bash code
```bash
[Unit]
Description=DAG2 Service
After=network.target

[Service]
User=root
ExecStart=loop.sh
Restart=always
RestartSec=10

[Install]
WantedBy=multi-user.target
```

# loop.sh
```bash
#!/bin/bash
#nvidia-smi -pm 1
nvidia-smi -pl 120
while true; do
    timeout 600 command
    sleep 120
done
```

# podman with nvidia container toolkit

```bash
podman run -it --name AI-Agents --device nvidia.com/gpu=all -v /host/AI-Agents/:/root/Projects ubuntu
```

