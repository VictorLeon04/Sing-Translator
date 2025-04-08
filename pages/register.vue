<template>
    <div class="register-container">
      <h2>Crear Cuenta</h2>
      <form>
        <input type="text" placeholder="Nombres" required />
        <input type="text" placeholder="Apellidos" required />
        <input type="email" placeholder="Correo Electrónico" required />
        <input type="number" placeholder="Edad" required />
        <button type="submit">Registrarse</button>
      </form>
    </div>
  </template>
  
  <style scoped>
  .register-container {
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
    background: #28a745;
    color: white;
    padding: 0.7rem;
    width: 100%;
    border: none;
    border-radius: 5px;
    cursor: pointer;
  }
  
  button:hover {
    background: #218838;
  }
  
  /* Responsive */
  @media (max-width: 600px) {
    .register-container {
      width: 90%;
    }
  }
  </style>
  