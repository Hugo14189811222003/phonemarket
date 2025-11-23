<template>
  <div class="login-page">
    <!-- Background Elements -->
    <div class="background-shapes">
      <div class="shape-blue"></div>
      <div class="shape-white"></div>
    </div>

    <!-- Main Container -->
    <div class="container">
  

      <div class="content-wrapper">
        <!-- Login Card -->
        <div class="login-card">
          <div class="card-header">
            <div class="user-icon-wrapper">
              <svg xmlns="http://www.w3.org/2000/svg" class="user-icon" viewBox="0 0 24 24" fill="currentColor">
                <path fill-rule="evenodd" d="M7.5 6a4.5 4.5 0 119 0 4.5 4.5 0 01-9 0zM3.751 20.105a8.25 8.25 0 0116.498 0 .75.75 0 01-.437.695A18.683 18.683 0 0112 22.5c-2.786 0-5.433-.608-7.812-1.7a.75.75 0 01-.437-.695z" clip-rule="evenodd" />
              </svg>
            </div>
            <h1>Inicio de sesión</h1>
          </div>

          <form @submit.prevent="handleLogin" class="login-form">
            <div class="form-group">
              <label for="username">Nombre del usuario o Gmail</label>
              <input type="text" id="username" v-model="username" placeholder="Nombre del usuario o Gmail" />
            </div>

            <div class="form-group">
              <label for="password">Contraseña</label>
              <input type="password" id="password" v-model="password" placeholder="••••••••••••" />
            </div>

            <div class="form-actions">
              <div class="checkbox-wrapper">
                <!-- Optional checkbox if needed, reference doesn't clearly show one but standard -->
              </div>
              <a href="#" class="forgot-password">Olvidé mi contraseña</a>
            </div>

            <button type="submit" class="btn-primary" @click="$router.push('/home')">Entrar</button>

            <button type="button" class="btn-google">
              <img src="https://www.svgrepo.com/show/475656/google-color.svg" alt="Google" class="google-icon" />
            </button>
          </form>

        <div class="card-footer">
            <p>¿No tienes cuenta? <a href="#">¡Crea una ahora!</a></p>
          </div>
        </div>
        
      </div>
    </div>
  </div>
</template>

<script setup>
const username = ref('')
const password = ref('')

const handleLogin = () => {
  console.log('Login attempt', username.value, password.value)
  // Implement login logic here
}
</script>

<style scoped>
a {
  text-decoration: none;
  color: var(--white);
}
.login-page {
  min-height: 100vh;
  width: 100%;
  position: relative;
  overflow: hidden;
  display: flex;
  align-items: center;
  justify-content: center;
}

.background-shapes {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 0;
  display: flex;
}

.shape-blue {
  width: 80%;
  height: 100%;
  background-color: #2563EB;
  clip-path: polygon(0 0, 100% 0, 80% 100%, 0% 100%); 
}

.shape-white {
  width: 60%;
  height: 100%;
  background-color: #ffffff;
}

.container {
  position: absolute;
  z-index: 1000;
  width: 100%;
  padding: 2rem;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}

.logo-container {
  margin: 1rem;
}

.logo {
  position: fixed;
  left: 2rem;
  top: 2rem;
  width: 80px;
  filter: invert(1) brightness(3000%);
}

.content-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 4rem;
}

.login-card {
  background: white;
  padding: 3rem;
  border-radius: 2rem;
  box-shadow: 0 20px 40px rgba(0,0,0,0.1);
  width: 100%;
  max-width: 450px;
  text-align: center;
  position: relative;
}

.card-header {
  margin-bottom: 2rem;
}

.user-icon-wrapper {
  width: 60px;
  height: 60px;
  background: white;
  border-radius: 50%;
  margin: -60px auto 1rem; /* Pull up */
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  border: 2px solid #2563EB;
  color: #2563EB;
}

.user-icon {
  width: 32px;
  height: 32px;
}

h1 {
  color: #1e3a8a;
  font-size: 1.75rem;
  font-weight: 700;
  margin: 0;
}

.login-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  text-align: left;
}

label {
  display: block;
  color: #3b82f6;
  font-weight: 600;
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

input {
  width: 100%;
  padding: 0.75rem 1rem;
  border: none;
  background-color: #f3f4f6;
  border-radius: 1rem;
  font-size: 0.95rem;
  color: #374151;
  outline: none;
  transition: box-shadow 0.2s;
}

input:focus {
  box-shadow: 0 0 0 2px #2563EB;
}

.form-actions {
  display: flex;
  justify-content: flex-end; /* Or space-between if checkbox added */
}

.forgot-password {
  color: #6b7280;
  font-size: 0.85rem;
  text-decoration: none;
}

.btn-primary {
  background-color: #2563EB;
  color: white;
  border: none;
  padding: 0.75rem;
  border-radius: 2rem;
  font-weight: 600;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.2s;
  box-shadow: 0 4px 6px rgba(37, 99, 235, 0.2);
}

.btn-primary:hover {
  background-color: #1d4ed8;
}

.btn-google {
  background-color: white;
  border: 1px solid #e5e7eb;
  padding: 0.5rem;
  border-radius: 2rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: background-color 0.2s;
}

.btn-google:hover {
  background-color: #f9fafb;
}

.google-icon {
  width: 24px;
  height: 24px;
}

.card-footer {
  margin-top: 2rem;
  font-size: 0.9rem;
  color: #6b7280;
}

.card-footer a {
  color: #374151;
  font-weight: 600;
  text-decoration: none;
}

.illustration-area {
  flex: 1;
  position: relative;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100%;
}

.decoration-bg {
  position: absolute;
  width: 120%;
  max-width: none;
  z-index: 1;
  opacity: 0.8;
  /* Adjust positioning based on image content */
}

.main-illustration {
  position: relative;
  z-index: 2;
  max-width: 100%;
  height: auto;
  filter: drop-shadow(0 10px 20px rgba(0,0,0,0.1));
}

/* ... existing styles ... */

.decoration-image {
  max-width: 100%;
  height: auto;
  object-fit: contain;
}

/* Responsive */
@media (max-width: 768px) {
  .content-wrapper {
    flex-direction: column;
  }
  
  .decoration-image {
    display: none;
  }
  
  .shape-blue {
    width: 100%;
    height: 30%;
    clip-path: none;
    border-radius: 0 0 50% 50%;
  }
}
</style>
