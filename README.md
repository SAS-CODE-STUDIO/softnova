# softnova
amazing chatbot ask any thin give reply with voice
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>🌍 Multi-Language TTS App</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600&display=swap" rel="stylesheet">
  <style>
    body {
      background: #111;
      color: #fff;
      font-family: 'Inter', sans-serif;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 2rem;
      flex-direction: column;
    }

    .app {
      background: #1c1c1e;
      padding: 2rem;
      border-radius: 16px;
      max-width: 700px;
      width: 100%;
      box-shadow: 0 0 20px rgba(0,0,0,0.3);
    }

    h1 {
      text-align: center;
      margin-bottom: 1rem;
      color: #00ffcc;
    }

    .developer-line {
      text-align: center;
      font-weight: bold;
      margin-top: 1rem;
      font-size: 1rem;
      background: linear-gradient(90deg, #ff4d4d, #ffaa00, #00ffcc, #00bfff, #cc66ff);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }

    textarea, select, button {
      width: 100%;
      margin-top: 1rem;
      padding: 12px;
      font-size: 16px;
      border-radius: 10px;
      border: none;
    }

    textarea {
      height: 120px;
      background: #2a2a2e;
      color: #fff;
      resize: vertical;
    }

    select {
      background: #2a2a2e;
      color: #fff;
    }

    button {
      background: #00ffcc;
      color: #000;
      font-weight: bold;
      cursor: pointer;
      margin-top: 1.5rem;
      transition: 0.3s;
    }

    button:hover {
      background: #00ccaa;
    }

    audio {
      margin-top: 2rem;
      width: 100%;
      display: none;
    }
  </style>
</head>
<body>
  <div class="developer-line">
    Developed by soft nova | إنشاؤه من قبل soft novaه | Desarrollado por soft nova | Développé par soft nova | Entwickelt von soft nova
  </div>
  <div class="app">
    <h1>🌍 AI Text-to-Speech App</h1>
    <textarea id="text" placeholder="Enter text in any language..."></textarea>

    <select id="voice">
      <!-- Add 50+ voices -->
      <option value="21m00Tcm4TlvDq8ikWAM">Rachel - English</option>
      <option value="AZnzlk1XvdvUeBnXmlld">Domi - English</option>
      <option value="EXAVITQu4vr4xnSDxMaL">Bella - English</option>
      <option value="MF3mGyEYCl7XYWbV9V6O">Elli - German</option>
      <option value="ErXwobaYiN019PkySvjV">Antoni - English (UK)</option>
      <option value="TxGEqnHWrfWFTfGW9XjX">Thomas - Spanish</option>
      <option value="LcfcDJNUP1GQjkzn1xUU">Nicole - French</option>
      <option value="VR6AewLTigWG4xSOukaG">Arnold - English (Movie)</option>
      <option value="yoZ06aMxZJJ28mfd3POQ">Adam - Deep</option>
      <option value="pNInz6obpgDQGcFmaJgB">Sam - English</option>
      <!-- Add more voices from ElevenLabs here -->
    </select>

    <select id="language">
      <!-- Add 50+ languages -->
      <option value="en">English</option>
      <option value="es">Spanish</option>
      <option value="fr">French</option>
      <option value="de">German</option>
      <option value="hi">Hindi</option>
      <option value="ar">Arabic</option>
      <option value="ru">Russian</option>
      <option value="pt">Portuguese</option>
      <option value="it">Italian</option>
      <option value="ja">Japanese</option>
      <option value="ko">Korean</option>
      <option value="zh">Chinese</option>
      <option value="ml">Malayalam</option>
      <option value="ta">Tamil</option>
      <option value="te">Telugu</option>
      <option value="ur">Urdu</option>
      <option value="bn">Bengali</option>
      <!-- Add more languages as needed -->
    </select>

    <button onclick="speak()">🔊 Speak</button>
    <audio id="audio" controls></audio>
  </div>

  <script>
    const API_KEY = 'sk_151cf0db6ff80227d5a9232600b7692512bc40fe2e872cbe';

    async function speak() {
      const text = document.getElementById('text').value.trim();
      const voiceId = document.getElementById('voice').value;
      const audio = document.getElementById('audio');

      if (!text) {
        alert("Please enter some text.");
        return;
      }

      const response = await fetch(`https://api.elevenlabs.io/v1/text-to-speech/${voiceId}`, {
        method: 'POST',
        headers: {
          'Content-Type': 'application/json',
          'xi-api-key': API_KEY
        },
        body: JSON.stringify({
          text: text,
          model_id: "eleven_multilingual_v2",
          voice_settings: {
            stability: 0.5,
            similarity_boost: 0.75
          }
        })
      });

      if (!response.ok) {
        alert("Error: " + response.status);
        return;
      }

      const blob = await response.blob();
      const url = URL.createObjectURL(blob);
      audio.src = url;
      audio.style.display = 'block';
      audio.play();
    }
  </script>
</body>
</html>
