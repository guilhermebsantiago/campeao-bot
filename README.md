# Campeão 🏆

Bot de música do Discord controlado por voz, estilo Alexa. Fica no canal de voz e obedece:

> **"CAMPEÃO, TOCA WONDERWALL DO OASIS"**

## Comandos

**Por voz** (com o bot no canal): `toca <música>`, `pula`, `pausa`, `continua`, `para`, `radio`, `letra`, `sai` — sempre precedidos de "Campeão". Falar só "Campeão" toca um bip (ou abaixa a música) e abre uma janela ouvindo você.

**Slash**: `/tocar` (sugere músicas do Deezer enquanto você digita), `/pular`, `/pausar`, `/continuar`, `/parar`, `/fila`, `/radio`, `/letra`, `/sair`, `/ajuda`

**Por texto**: `!entra`, `!play <música>`, `!pula`, `!pausa`, `!continua`, `!para`, `!fila`, `!radio`, `!letra`, `!sai`, `!ajuda`

**Botões**: todo "Tocando agora" vem com pausar/continuar, pular, fila, letra e parar.

## Comportamentos

- **Status do canal de voz** mostra a faixa atual e é limpo ao sair.
- **Modo rádio**: acabou a fila, o bot segue sozinho com faixas do mix do YouTube.
- **Sai sozinho** 60s depois que o canal de voz esvazia.
- **Fila persistente**: sobrevive a restart/redeploy (salva em `/data/queue.json`).
- **Letras** via [lrclib.net](https://lrclib.net).

## Stack

- Node + discord.js + @discordjs/voice (playback e captura de voz)
- faster-whisper (STT local em português, CPU, sem API paga)
- yt-dlp (busca YouTube com fallback SoundCloud)

## Rodar

```bash
docker build -t campeao .
docker run -e DISCORD_TOKEN=... -e WHISPER_MODEL=small -v campeao-data:/data campeao
```

O bot avisa o que está tocando no canal de texto onde foi chamado (`!entra`/`!play`).
