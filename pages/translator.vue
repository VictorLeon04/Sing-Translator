<template>
    <div class="app">
      <header>
        <h1>Sign language translator</h1>
      </header>
  
      <main>
        <div class="controls">
          <button @click="importText">
            <i class="fa-solid fa-download"></i> Importar
          </button>
          <button @click="exportText">
            <i class="fa-solid fa-upload"></i> Exportar
          </button>
          <button @click="selectLanguage">
            <i class="fa-solid fa-language"></i> Idioma
          </button>
        </div>
  
        <!-- Imagen entre los botones y el textarea -->
        <div class="content-box">
          <div class="translator-image">
            <img src="/sing.jpg" alt="Imagen de señas" />
          </div>
  
          <div class="text-box">
            <textarea v-model="textArea" placeholder="Escribe para traducir..."></textarea>
          </div>
        </div>
  
        <button class="translate-btn" @click="translate">
          <i class="fa-solid fa-hourglass-end"></i> Traducir
        </button>
  
        <div id="versionNumber">Versión: 1.0</div>
      </main>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import { useHead } from '@unhead/vue'
  
  // Cambiamos el título de la página y agregamos los estilos de FontAwesome
  useHead({
    title: 'Traductor de señas',
    link: [
      {
        rel: 'stylesheet',
        href: 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css'
      }
    ]
  })
  
  // Variable para el contenido del área de texto
  const textArea = ref('')
  
  // Función de traducción (simulada)
  const translate = () => {
    textArea.value += ' (traducido a señas)'
  }
  
  // Función para importar un archivo de texto
  const importText = () => {
    const input = document.createElement('input')
    input.type = 'file'
    input.accept = '.txt'
    input.addEventListener('change', (event) => {
      const file = event.target.files[0]
      const reader = new FileReader()
      reader.onload = (e) => {
        textArea.value = e.target.result
      }
      if (file) reader.readAsText(file)
    })
    input.click()
  }
  
  // Función para exportar el texto como un archivo `.txt`
  const exportText = () => {
    const blob = new Blob([textArea.value], { type: 'text/plain' })
    const url = URL.createObjectURL(blob)
    const a = document.createElement('a')
    a.href = url
    a.download = 'traduccion.txt'
    a.click()
    URL.revokeObjectURL(url)
  }
  
  // Función para seleccionar el idioma (simulada)
  const selectLanguage = () => {
    const lang = prompt('Selecciona un idioma (es, en, fr):', 'es')
    if (lang) {
      alert(`Idioma seleccionado: ${lang}`)
    }
  }
  </script>
  
  <style scoped>
  /* Estilos generales */
  .app {
    min-height: 100vh;
    background-color: #f4f9ff;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0 1rem;
    font-family: 'Segoe UI', sans-serif;
  }
  
  /* Estilos del header */
  header {
    text-align: center;
    margin-top: 6rem; /* Separación del navbar */
    margin-bottom: 2rem;
  }
  
  h1 {
    color: #007bff;
    font-size: 2rem;
    margin: 0;
  }
  
  /* Estilos del main */
  main {
    width: 100%;
    max-width: 600px;
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  
  /* Contenedor de los botones de acción */
  .controls {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 10px;
    margin-bottom: 1.5rem;
  }
  
  /* Estilos para los botones */
  button {
    background-color: #007bff;
    color: white;
    border: none;
    padding: 0.6rem 1rem;
    border-radius: 6px;
    cursor: pointer;
    font-size: 1rem;
    display: flex;
    align-items: center;
    gap: 8px;
    transition: background 0.2s;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  
  /* Estilo para el botón de traducción */
  .translate-btn {
    background-color: #28a745;
    margin-top: 1rem;
  }
  
  .translate-btn:hover {
    background-color: #1e7e34;
  }
  
  /* Estilo para el área de texto */
  .text-box {
    width: 100%;
    margin-top: 1rem;
  }
  
  textarea {
    width: 100%;
    height: 150px;
    padding: 0.8rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 6px;
    resize: none;
  }
  
  /* Versión */
  #versionNumber {
    margin-top: 1.5rem;
    font-size: 0.9rem;
    color: #888;
  }
  
  /* Contenedor de la imagen */
  .translator-image {
    margin: 1rem 0;
    display: flex;
    justify-content: center;
    width: 100%;
  }
  
  .translator-image img {
    width: 100%;
    max-width: 100%;
    max-height: 350px; /* Imagen más grande */
    border-radius: 10px;
    object-fit: cover;
  }
  
  /* Responsive */
  @media (max-width: 500px) {
    h1 {
      font-size: 1.5rem;
    }
  
    button {
      font-size: 0.9rem;
      padding: 0.5rem 0.8rem;
    }
  
    textarea {
      height: 120px;
    }
  
    .translator-image img {
      max-height: 250px;
    }
  }
  </style>
  