```
docker run -d \
  --name openwebui \
  --restart unless-stopped \
  -p 3000:8080 \
  --add-host=host.docker.internal:host-gateway \
  -e OLLAMA_API_BASE=http://host.docker.internal:11434 \
  -v openwebui:/app/backend/data \
  ghcr.io/open-webui/open-webui:main
```

```
docker ps
```
