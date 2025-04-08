<template>
    <nav class="navbar">
      <div class="nav-container">
        <NuxtLink to="/" class="logo">Sing Translator</NuxtLink>
        <div class="nav-buttons">
          <NuxtLink to="/login" class="button login">Iniciar Sesión</NuxtLink>
          <NuxtLink to="/register" class="button register">Registrarse</NuxtLink>
        </div>
      </div>
    </nav>
  </template>
  
  <style scoped>
  .navbar {
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1rem 2rem;
    background: #007bff;
    color: white;
    position: fixed;
    width: 100%;
    top: 0;
    left: 0;
    z-index: 1000;
  }
  
  .nav-container {
    display: flex;
    align-items: center;
    width: 100%;
    max-width: 1200px;
    justify-content: space-between; /* Espaciado entre logo y botones */
  }
  
  .logo {
    font-size: 1.8rem;
    font-weight: bold;
    text-decoration: none;
    color: white;
    flex-grow: 1;
    text-align: center; /* Centra el texto "Sing Translator" */
  }
  
  .nav-buttons {
    display: flex;
    gap: 1.5rem;
    margin-right: 3rem; /* Ajuste para mover los botones más hacia adentro */
  }
  
  .button {
    text-decoration: none;
    padding: 0.8rem 1.5rem;
    border-radius: 5px;
    font-weight: bold;
    white-space: nowrap;
    text-align: center;
  }
  
  .login {
    background: white;
    color: #007bff;
    border: 2px solid white;
  }
  
  .register {
    background: #0056b3;
    color: white;
    border: 2px solid #0056b3;
  }
  
  .button:hover {
    opacity: 0.8;
  }
  
  /* Ajuste en pantallas pequeñas */
  @media (max-width: 600px) {
    .nav-container {
      flex-direction: column;
      text-align: center;
    }
  
    .logo {
      order: -1; /* Mantiene el logo arriba en móviles */
    }
  
    .nav-buttons {
      margin-top: 0.5rem;
      gap: 0.5rem;
      margin-right: 0; /* Elimina el margen derecho en móviles */
    }
  }
  </style>
  