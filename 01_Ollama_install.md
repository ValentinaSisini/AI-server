-  curl -fsSL https://ollama.com/install.sh | sh
- ollama serve > ~/ai-stack/log_ollama.txt 2>&1 &
- curl -s http://localhost:11434/api/version && echo
  
Scarichiamo un modello leggero per il test (CPU va benissimo):
- ollama pull llama3:8b-instruct-q4_K_M

Test di generazione:

- curl -s http://localhost:11434/api/generate \
  -d '{"model": "llama3:8b-instruct-q4_K_M", "prompt": "Dimmi in 3 frasi cosa posso fare con questa VM."}' \
  | jq -r '.response' 2>/dev/null || echo "Risposta ricevuta (magari non formattata)."
