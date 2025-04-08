<template>
    <div class="login-container">
      <h2>Iniciar Sesión</h2>
      <form>
        <input type="email" placeholder="Correo electrónico" required />
        <input type="password" placeholder="Contraseña" required />
        <button type="submit">Entrar</button>
      </form>
      <p class="register-text">
        ¿No tienes una cuenta?  
        <NuxtLink to="/register" class="register-link">Regístrate aquí</NuxtLink>
      </p>
    </div>
  </template>
  
  <style scoped>
  .login-container {
    text-align: center;
    padding: 5rem 2rem 2rem;
    max-width: 400px;
    margin: 8rem auto 0; /* Ajuste para evitar que el navbar lo tape */
    background: #f9f9f9;
    border-radius: 10px;
    box-shadow: 0px 4px 8px rgba(0, 0, 0, 0.1);
  }
  
  input {
    display: block;
    width: 100%;
    margin: 1rem 0;
    padding: 0.8rem;
    border: 1px solid #ccc;
    border-radius: 5px;
  }
  
  button {
    background: #007bff;
    color: white;
    padding: 0.7rem;
    width: 100%;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background: #0056b3;
  }
  
  .register-text {
    margin-top: 1rem;
  }
  
  .register-link {
    color: #007bff;
    text-decoration: none;
    font-weight: bold;
  }
  
  .register-link:hover {
    text-decoration: underline;
  }
  
  /* Responsive */
  @media (max-width: 600px) {
    .login-container {
      width: 90%;
    }
  }
  </style>
  