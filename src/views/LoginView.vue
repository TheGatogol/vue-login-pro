<template>
  <div class="login-container">
    <form class="login-form" @submit.prevent="handleLogin">
      <h2>Iniciar Sesión</h2>
      <div class="form-group">
        <label for="username">Usuario</label>
        <input
          id="username"
          v-model="username"
          type="text"
          name="username"
          autocomplete="username"
          placeholder="Ingresa tu usuario"
          @input="usernameError = ''"
        />
        <span v-if="usernameError" class="error">{{ usernameError }}</span>
      </div>
      <div class="form-group">
        <label for="userpassword">Contraseña</label>
        <div class="password-wrapper">
          <input
            id="userpassword"
            v-model="password"
            :type="showPassword ? 'text' : 'password'"
            name="userpassword"
            autocomplete="current-password"
            placeholder="Ingresa tu contraseña"
            @input="passwordError = ''"
          />
          <button type="button" class="show-btn" @click="togglePassword" :aria-label="showPassword ? 'Ocultar contraseña' : 'Mostrar contraseña'">
            <span v-if="showPassword">🙈</span>
            <span v-else>👁️</span>
          </button>
        </div>
        <span v-if="passwordError" class="error">{{ passwordError }}</span>
      </div>
      <div class="form-actions">
        <router-link to="/forgot-password" class="forgot-link">¿Olvidaste tu contraseña?</router-link>
        <button type="submit" class="login-btn">Iniciar Sesión</button>
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const username = ref('');
const password = ref('');
const showPassword = ref(false);
const usernameError = ref('');
const passwordError = ref('');
const router = useRouter();

function togglePassword() {
  showPassword.value = !showPassword.value;
}

function validateUsername() {
  if (username.value.length < 2) {
    usernameError.value = 'El usuario debe contener mínimo 2 caracteres.';
    return false;
  }
  if (username.value.length > 20) {
    usernameError.value = 'El usuario debe contener máximo 20 caracteres.';
    return false;
  }
  if (!/^[a-zA-Z0-9]+$/.test(username.value)) {
    usernameError.value = 'El usuario solo puede contener letras y números, sin espacios ni símbolos.';
    return false;
  }
  usernameError.value = '';
  return true;
}

function validatePassword() {
  if (password.value.length < 6) {
    passwordError.value = 'La contraseña debe contener mínimo 6 caracteres.';
    return false;
  }
  if (password.value.length > 20) {
    passwordError.value = 'La contraseña debe contener máximo 20 caracteres.';
    return false;
  }
  passwordError.value = '';
  return true;
}

function handleLogin() {
  const validUser = validateUsername();
  const validPass = validatePassword();
  if (!validUser || !validPass) return;
  if (username.value !== 'admin123456') {
    usernameError.value = 'Usuario incorrecto. Debe ser "admin123456".';
    return;
  }
  if (password.value !== 'admin123456') {
    passwordError.value = 'Contraseña incorrecta. Debe ser "admin123456".';
    return;
  }
  router.push('/dashboard');
}
</script>

<style scoped>
.login-container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(120deg, #f0f4f8 0%, #d9e7ff 100%);
}
.login-form {
  background: #fff;
  padding: 2.5rem 2rem;
  border-radius: 1.5rem;
  box-shadow: 0 8px 32px rgba(60, 80, 120, 0.15);
  width: 100%;
  max-width: 400px;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
.login-form h2 {
  text-align: center;
  margin-bottom: 1rem;
  color: #2a3a5e;
  font-weight: 700;
}
.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}
.form-group label {
  font-weight: 600;
  color: #2a3a5e;
}
.form-group input {
  padding: 0.75rem 1rem;
  border: 1px solid #cfd8dc;
  border-radius: 0.75rem;
  font-size: 1rem;
  transition: border-color 0.2s;
}
.form-group input:focus {
  border-color: #5b9aff;
  outline: none;
}
.password-wrapper {
  display: flex;
  align-items: center;
  position: relative;
}
.show-btn {
  background: none;
  border: none;
  position: absolute;
  right: 0.75rem;
  top: 50%;
  transform: translateY(-50%);
  cursor: pointer;
  font-size: 1.2rem;
  color: #5b9aff;
}
.error {
  color: #e53935;
  font-size: 0.9rem;
  margin-top: 0.25rem;
}
.form-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}
.forgot-link {
  color: #5b9aff;
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.2s;
}
.forgot-link:hover {
  color: #2a3a5e;
}
.login-btn {
  background: #5b9aff;
  color: #fff;
  border: none;
  border-radius: 0.75rem;
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}
.login-btn:hover {
  background: #2a3a5e;
}
</style>
