# 📝 Assignment: Vue.js – Simple To-Do List

## Identitas
- **Nama** : [Fitri Nufa Dastana]
- **NIM**  : [F1D02310052]

---

## Deskripsi Tugas
Pada tugas ini saya membangun aplikasi **To-Do List sederhana menggunakan Vue.js**.  
Aplikasi ini dibuat dengan menerapkan konsep:
- Reaktivitas data menggunakan `ref()`
- Two-way data binding menggunakan `v-model`
- Event handling dengan `@submit` dan `@click`
- Perulangan dinamis menggunakan `v-for`
- Conditional rendering menggunakan `v-if`

Fitur utama aplikasi:
- Menginput nama tugas dan menambahkannya ke daftar 
- Menghapus tugas tertentu dari daftar 
- Menampilkan daftar tugas secara dinamis  
- Muncul pesan **Tidak ada tugas** apabila daftar kosong  
- Notifikasi **alert** ketika tugas berhasil ditambahkan maupun dihapus
- State tugas dibuat menggunakan `ref()` sehingga daftar berubah secara real-time saat ditambah atau dihapus 

---

## Hasil
1. Screenshot Kode Program
2. Screenshot Hasil Program
3. Penjelasan Singkat
- addTask()
```
function addTask() {
  if (newTask.value.trim() !== "") {
    tasks.value.push(newTask.value);
    alert("Tugas berhasil ditambahkan!");
    newTask.value = "";
  }
}
```
Method ini mengambil teks dari input (terhubung dengan v-model), lalu memasukkannya ke array tasks. Jika tugas berhasil ditambahkan, input dikosongkan dan alert "Tugas berhasil ditambahkan!" muncul.

- v-for untuk menampilkan daftar tugas
```
<li v-for="(task, index) in tasks" :key="index" class="task-item">
  {{ task }}
  <button @click="deleteTask(index)">Hapus</button>
</li>
```
Perulangan v-for digunakan untuk menampilkan item dalam array tasks secara dinamis. Setiap elemen array otomatis menghasilkan satu elemen <li>.

- deleteTask(index)
```
function deleteTask(index) {
  tasks.value.splice(index, 1);
  alert("Tugas berhasil dihapus!");
}
```
Saat tombol hapus ditekan, elemen dalam tasks dihapus berdasarkan indeksnya. Setelah berhasil dihapus, muncul alert "Tugas berhasil dihapus!".

- Kondisi daftar kosong (v-if)
```
<p v-if="tasks.length === 0" class="empty-message">
  Tidak ada tugas
</p>
<ul v-else>
  <li v-for="(task, index) in tasks" :key="index">
    {{ task }}
  </li>
</ul>
```

Jika tasks.length === 0, maka pesan “Tidak ada tugas” ditampilkan.
Jika ada isi pada array, maka daftar tugas (v-for) yang ditampilkan menggantikan pesan tersebut.