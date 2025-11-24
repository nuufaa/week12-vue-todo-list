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
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/472b878a-70b5-4b87-9fe0-7253e7f224ca" />

2. Screenshot Hasil Program
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/8524dc3c-61e4-4906-9054-43f0ecc42ec3" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b7ffa756-bd0f-467f-a80d-7e6e3abf75c0" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/09cbb260-49fc-445c-aa79-218e9ed9e61c" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/f83e96e7-441f-476b-b9e0-6824bd6db328" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/38a24f67-c716-4cbc-a113-a740fb5ce0a2" />

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
Fungsi addTask() dipanggil ketika pengguna menekan tombol submit pada form. Pertama, fungsi memeriksa apakah input tidak kosong dengan mengecek newTask.value.trim(). Jika masih ada isi, maka teks tugas dimasukkan ke dalam array tasks menggunakan push(). Karena tasks adalah state reaktif berbasis ref(), perubahan data secara otomatis memperbarui tampilan tanpa refresh.Setelah item berhasil ditambahkan, program akan mengosongkan input agar siap digunakan lagi dan menampilkan alert “Tugas berhasil ditambahkan!” sebagai umpan balik kepada pengguna.

- v-for untuk menampilkan daftar tugas
```
<li v-for="(task, index) in tasks" :key="index" class="task-item">
  {{ task }}
  <button @click="deleteTask(index)">Hapus</button>
</li>
```
v-for berfungsi sebagai perulangan untuk menampilkan daftar tugas berdasarkan isi array tasks.Selama ada data di dalam tasks, setiap elemen array di-render menjadi li. Binding :key="index" digunakan agar Vue dapat melacak setiap item dalam list dan mencegah error rendering. Setiap baris juga memiliki tombol hapus yang terhubung dengan fungsi deleteTask(index).

- deleteTask(index)
```
function deleteTask(index) {
  tasks.value.splice(index, 1);
  alert("Tugas berhasil dihapus!");
}
```
Saat tombol hapus ditekan, fungsi deleteTask() menerima posisi item dalam list melalui parameter index.Lalu item pada posisi tersebut dihapus dari array menggunakan splice(). Karena tasks adalah data reaktif, tampilan langsung diperbarui dan item hilang dari daftar. Setelah penghapusan sukses, muncul alert “Tugas berhasil dihapus!” sebagai notifikasi ke pengguna.

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

Vue mengecek apakah tasks.length === 0. Jika belum ada tugas sama sekali, maka komponen akan menampilkan teks “Tidak ada tugas”.
Namun jika tugas sudah ada minimal satu, teks tersebut otomatis hilang dan daftar tugas akan muncul. Mekanisme ini membuat UI terasa dinamis karena berubah berdasarkan keadaan data.
