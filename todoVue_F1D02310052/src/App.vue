<template>
  <div class="container">
    <div class="app">
      <h1 class="title">To-Do List Tugas</h1>

      <form class="task-form" @submit.prevent="addTask">
        <input
          v-model="newTask"
          type="text"
          placeholder="Tambah tugas baru..."
          @keyup.enter="addTask"
          class="input-task"
        />
        <button type="submit" class="btn">Tambah</button>
      </form>

      <div class="task-list">
        <p v-if="tasks.length === 0" class="empty">Tidak ada tugas</p>

        <ul v-else>
          <li
            v-for="(task, index) in tasks"
            :key="index"
            class="task-item"
          >
            <span class="task-text">{{ task }}</span>
            <button class="btn-delete" @click="deleteTask(index)">Hapus</button>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

// state
const tasks = ref([])
const newTask = ref('')

// method untuk menambah tugas
function addTask() {
  const text = newTask.value.trim()
  if (!text) return
  tasks.value.push(text)
  newTask.value = ''
  alert("Tugas berhasil ditambahkan!")
}

// method untuk menghapus tugas berdasarkan index
function deleteTask(index) {
  const deleted = tasks.value[index]
  tasks.value.splice(index, 1)
  alert(`Tugas "${deleted}" berhasil dihapus!`)
}
</script>

<style scoped>
/* Latar halaman */
.container {
  min-height: 100vh;
  background: linear-gradient(145deg, #e0f2ff, #f0faff);
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 32px;
}

/* Card Utama */
.app {
  width: 100%;
  max-width: 600px;
  background: linear-gradient(135deg, #ffffff, #eaf6ff);
  border-radius: 14px;
  padding: 28px;
  box-shadow: 0 8px 24px rgba(0, 96, 160, 0.15);
}

/* Judul */
.title {
  margin: 0 0 18px;
  text-align: center;
  font-size: 26px;
  font-weight: 700;
  color: #004b91;
}

/* Form */
.task-form {
  display: flex;
  gap: 10px;
  margin-bottom: 18px;
}

.input-task {
  flex: 1;
  padding: 11px 12px;
  font-size: 15px;
  border-radius: 8px;
  border: 1px solid #bcd8ef;
  outline: none;
  transition: all 0.25s;
}
.input-task:focus {
  border-color: #0077e6;
  box-shadow: 0 0 0 2px rgba(0, 131, 224, 0.15);
}

/* Tombol tambah */
.btn {
  padding: 11px 18px;
  font-size: 15px;
  cursor: pointer;
  border: none;
  border-radius: 8px;
  background: #1d77ff;
  color: #fff;
  font-weight: 600;
  transition: 0.25s;
}
.btn:hover {
  background: #005ce6;
}

/* List tugas */
.empty {
  text-align: center;
  padding: 18px 0;
  font-size: 15px;
  font-weight: 500;
  color: #708090;
}

ul {
  padding: 0;
  margin: 0;
  list-style: none;
}

.task-item {
  background: #ffffff;
  border: 1px solid #d8ebff;
  padding: 11px 13px;
  margin-bottom: 8px;
  border-radius: 9px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  transition: 0.25s;
}
.task-item:hover {
  background: #f5faff;
  transform: translateY(-2px);
}

/* Teks tugas */
.task-text {
  font-size: 15px;
  margin-right: 10px;
  flex: 1;
  word-break: break-word;
  color: #083b63;
}

/* Tombol hapus */
.btn-delete {
  border: none;
  border-radius: 6px;
  padding: 7px 12px;
  cursor: pointer;
  background: #ff4a4a;
  color: white;
  font-size: 14px;
  font-weight: 600;
  transition: 0.25s;
}
.btn-delete:hover {
  background: #d72626;
}
</style>
