<template>
  <div class="page-container">
    <header>
      <h1>🧏‍♀️ Traductor a Lenguaje de Señas</h1>
      <p>Haz clic en el micrófono para convertir tu voz en texto y traducirlo a señas.</p>
    </header>

    <div class="translator-box">
      <div class="transcript-display">
        <p v-if="transcript">{{ transcript }}</p>
        <p v-else class="placeholder">Aquí aparecerá el texto reconocido…</p>
      </div>

      <button @click="startListening" :disabled="listening">
        {{ listening ? '🎙️ Escuchando...' : '🎤 Iniciar Grabación' }}
      </button>
    </div>

    <div class="sign-output">
      <h2>Traducción a Señas (imagen):</h2>
      <div v-if="transcript">
        <!-- Aquí se cargarán las imágenes de señas -->
        <p>Próximamente aquí se mostrarán las señas correspondientes a: "{{ transcript }}"</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      recognition: null,
      transcript: "",
      listening: false,
    };
  },
  methods: {
    startListening() {
      if (!('webkitSpeechRecognition' in window)) {
        alert("Tu navegador no soporta la Web Speech API");
        return;
      }

      this.recognition = new webkitSpeechRecognition();
      this.recognition.lang = "es-ES";
      this.recognition.continuous = false;
      this.recognition.interimResults = false;

      this.recognition.onstart = () => {
        this.listening = true;
        this.transcript = "";
      };

      this.recognition.onresult = (event) => {
        const result = event.results[0][0].transcript;
        this.transcript = result;
      };

      this.recognition.onerror = (event) => {
        console.error("Error:", event.error);
      };

      this.recognition.onend = () => {
        this.listening = false;
      };

      this.recognition.start();
    }
  }
};
</script>

<style scoped>
.page-container {
  max-width: 700px;
  margin: auto;
  padding: 30px;
  font-family: 'Segoe UI', sans-serif;
  text-align: center;
}

header {
  margin-bottom: 20px;
}

.translator-box {
  background-color: #f0f4ff;
  border: 2px dashed #6c63ff;
  border-radius: 15px;
  padding: 20px;
  margin-bottom: 30px;
}

.transcript-display {
  min-height: 60px;
  padding: 10px;
  background: #fff;
  border: 1px solid #ccc;
  border-radius: 10px;
  margin-bottom: 20px;
  font-size: 18px;
}

.placeholder {
  color: #888;
  font-style: italic;
}

button {
  background-color: #6c63ff;
  color: white;
  border: none;
  padding: 12px 24px;
  font-size: 18px;
  border-radius: 8px;
  cursor: pointer;
}

button:disabled {
  background-color: #bbb;
  cursor: not-allowed;
}

.sign-output {
  background-color: #eafaf1;
  border-radius: 15px;
  padding: 20px;
}
</style>
