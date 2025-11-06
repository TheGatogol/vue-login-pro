
<template>
  <div class="dashboard-header">
    <span class="logo">Dashboard</span>
    <button class="logout-btn" @click="confirmLogout">Cerrar sesión</button>
  </div>
  <div class="dashboard-container">
    <h1>Vista de Dashboard</h1>
  </div>
  <div v-if="showConfirm" class="confirm-modal">
    <div class="confirm-box">
      <p>¿Seguro que deseas cerrar sesión?</p>
      <div class="confirm-actions">
        <button @click="logout" class="confirm-yes">Sí</button>
        <button @click="showConfirm = false" class="confirm-no">No</button>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import { useRouter } from 'vue-router';

const showConfirm = ref(false);
const router = useRouter();

function confirmLogout() {
  showConfirm.value = true;
}

function logout() {
  showConfirm.value = false;
  router.push('/');
}
</script>

<style scoped>

.dashboard-header {
  width: 100vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 2rem;
  background: #fff;
  box-shadow: 0 2px 8px rgba(60, 80, 120, 0.08);
  position: fixed;
  top: 0;
  left: 0;
  z-index: 10;
}
.logo {
  font-size: 1.3rem;
  font-weight: 700;
  color: #2a3a5e;
}
.logout-btn {
  background: #e53935;
  color: #fff;
  border: none;
  border-radius: 0.75rem;
  padding: 0.6rem 1.2rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}
.logout-btn:hover {
  background: #b71c1c;
}
.dashboard-container {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f0f4f8;
  padding-top: 5rem;
}
.dashboard-container h1 {
  color: #2a3a5e;
  font-size: 2.2rem;
  font-weight: 700;
}
.confirm-modal {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(44, 62, 80, 0.25);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 100;
}
.confirm-box {
  background: #fff;
  padding: 2rem 2.5rem;
  border-radius: 1rem;
  box-shadow: 0 8px 32px rgba(60, 80, 120, 0.15);
  text-align: center;
}
.confirm-actions {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  margin-top: 1.2rem;
}
.confirm-yes {
  background: #e53935;
  color: #fff;
  border: none;
  border-radius: 0.75rem;
  padding: 0.6rem 1.2rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}
.confirm-yes:hover {
  background: #b71c1c;
}
.confirm-no {
  background: #cfd8dc;
  color: #2a3a5e;
  border: none;
  border-radius: 0.75rem;
  padding: 0.6rem 1.2rem;
  font-size: 1rem;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s;
}
.confirm-no:hover {
  background: #b0bec5;
}
</style>
