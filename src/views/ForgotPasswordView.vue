<template>
  <div class="forgot-container">
    <form class="forgot-form" @submit.prevent="handleForgot">
      <h2>Recuperar Contraseña</h2>
      <div class="form-group">
        <label for="email">Correo electrónico</label>
        <input
          id="email"
          v-model="email"
          type="email"
          name="email"
          autocomplete="email"
          placeholder="Ingresa tu correo"
          @input="emailError = ''"
        />
        <span v-if="emailError" class="error">{{ emailError }}</span>
      </div>
      <div class="form-actions">
        <router-link to="/" class="back-link">Volver al login</router-link>
        <button type="submit" class="forgot-btn">Enviar</button>
      </div>
      <div v-if="successMessage" class="success">{{ successMessage }}</div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const email = ref('');
const emailError = ref('');
const successMessage = ref('');
const router = useRouter();

function validateEmail() {
  if (email.value.length < 5) {
    emailError.value = 'El correo debe contener mínimo 5 caracteres.';
    return false;
  }
  if (email.value.length > 50) {
    emailError.value = 'El correo debe contener máximo 50 caracteres.';
    return false;
  }
  // Simple email regex
  if (!/^\S+@\S+\.\S+$/.test(email.value)) {
    emailError.value = 'El formato del correo es inválido. Ejemplo: usuario@dominio.com';
    return false;
  }
  emailError.value = '';
  return true;
}

function handleForgot() {
  if (validateEmail()) {
    successMessage.value = 'Si el correo existe, recibirás instrucciones para recuperar tu contraseña.';
    setTimeout(() => {
      router.push('/');
    }, 2500);
  }
}
</script>

<style scoped>
.forgot-container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: linear-gradient(120deg, #f0f4f8 0%, #d9e7ff 100%);
}
.forgot-form {
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
.forgot-form h2 {
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
.error {
  color: #e53935;
  font-size: 0.9rem;
  margin-top: 0.25rem;
}
.success {
  color: #43a047;
  font-size: 0.95rem;
  margin-top: 1rem;
  text-align: center;
}
.form-actions {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 1rem;
}
.back-link {
  color: #5b9aff;
  text-decoration: none;
  font-size: 0.95rem;
  transition: color 0.2s;
}
.back-link:hover {
  color: #2a3a5e;
}
.forgot-btn {
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
.forgot-btn:hover {
  background: #2a3a5e;
}
</style>
