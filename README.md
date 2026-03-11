# Fleet Heartbeat

Real-time health monitoring for the BlackRoad Pi mesh. Probes 5 Raspberry Pi nodes via SSH, collects CPU temp, memory, disk, Ollama models, Docker containers, and stores history in SQLite.

## Nodes

| Name | IP | Role |
|------|-----|------|
| Alice | 192.168.4.49 | Gateway, Pi-hole, PostgreSQL |
| Cecilia | 192.168.4.96 | CECE AI, TTS, Hailo-8 |
| Octavia | 192.168.4.100 | Gitea, NVMe, Hailo-8 |
| Aria | 192.168.4.98 | Portainer, Headscale |
| Lucidia | 192.168.4.38 | Lucidia API, CarPool |

## API

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Live dashboard (auto-refresh 30s) |
| `/health` | GET | Service health |
| `/fleet` | GET | Probe all nodes, return live stats |
| `/fleet/history` | GET | Historical data (`?node=alice&limit=50`) |

## Run

```bash
pip install -r requirements.txt
python server.py  # http://localhost:8500
```

## Test

```bash
pip install pytest
pytest tests/
```
