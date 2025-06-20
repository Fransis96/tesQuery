# Membuat Aplikasi Web Responsif Sederhana dengan CSS dan JavaScript

Membuat aplikasi web responsif memungkinkan situs Anda menyesuaikan tampilan dengan baik di berbagai perangkat, mulai dari desktop hingga ponsel. Dalam artikel ini, kita akan membahas cara membuat aplikasi web sederhana berupa **Todo List** menggunakan HTML, CSS, dan JavaScript dengan pendekatan responsif.

## Langkah 1: Struktur HTML
Buat file `index.html` dengan struktur dasar untuk menampung elemen aplikasi. Kita akan menggunakan semantic HTML dan memastikan layout yang fleksibel.

```html
<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Todo List Responsif</title>
    <link rel="stylesheet" href="styles.css">
</head>
<body>
    <div class="container">
        <h1>Todo List</h1>
        <div class="input-section">
            <input type="text" id="taskInput" placeholder="Tambah tugas baru...">
            <button onclick="addTask()">Tambah</button>
        </div>
        <ul id="taskList"></ul>
    </div>
    <script src="script.js"></script>
</body>
</html>
```

Penjelasan:
- **Meta viewport**: Memastikan halaman responsif di berbagai perangkat.
- **Container**: Membungkus konten utama untuk pengaturan tata letak.
- **Input dan Button**: Untuk menambahkan tugas.
- **Ul#taskList**: Menampilkan daftar tugas.

## Langkah 2: Styling dengan CSS
Buat file `styles.css` untuk memberikan tampilan yang responsif dan menarik. Kita akan menggunakan Flexbox untuk layout dan media queries untuk responsivitas.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Arial, sans-serif;
}

body {
    background-color: #f0f2f5;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 20px;
}

.container {
    background: white;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 500px;
}

h1 {
    text-align: center;
    margin-bottom: 20px;
    color: #333;
}

.input-section {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

#taskInput {
    flex: 1;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
    font-size: 16px;
}

button {
    padding: 10px 20px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
}

button:hover {
    background-color: #218838;
}

ul {
    list-style: none;
}

li {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    border-bottom: 1px solid #eee;
}

li.completed {
    text-decoration: line-through;
    color: #888;
}

.delete-btn {
    background-color: #dc3545;
    padding: 5px 10px;
}

/* Media Queries untuk Responsivitas */
@media (max-width: 600px) {
    .container {
        padding: 15px;
    }

    .input-section {
        flex-direction: column;
    }

    #taskInput, button {
        width: 100%;
    }

    button {
        padding: 10px;
    }
}
```

Penjelasan:
- **Flexbox**: Mengatur layout input dan tombol agar sejajar.
- **Media Queries**: Menyesuaikan tampilan untuk layar kecil (misalnya, mengubah flex-direction menjadi column).
- **Box-shadow dan Border-radius**: Memberikan tampilan modern.
- **Hover Effects**: Meningkatkan interaktivitas.

## Langkah 3: Logika dengan JavaScript
Buat file `script.js` untuk menangani fungsi tambah dan hapus tugas, serta menyimpan data ke localStorage agar data tetap ada setelah refresh.

```javascript
document.addEventListener('DOMContentLoaded', () => {
    loadTasks();
});

function addTask() {
    const taskInput = document.getElementById('taskInput');
    const taskText = taskInput.value.trim();

    if (taskText === '') return;

    const taskList = document.getElementById('taskList');
    const li = document.createElement('li');
    li.innerHTML = `
        <span onclick="toggleTask(this)">${taskText}</span>
        <button class="delete-btn" onclick="deleteTask(this)">Hapus</button>
    `;
    taskList.appendChild(li);
    saveTask(taskText);
    taskInput.value = '';
}

function toggleTask(element) {
    element.parentElement.classList.toggle('completed');
    updateTasks();
}

function deleteTask(element) {
    element.parentElement.remove();
    updateTasks();
}

function saveTask(task) {
    let tasks = JSON.parse(localStorage.getItem('tasks')) || [];
    tasks.push({ text: task, completed: false });
    localStorage.setItem('tasks', JSON.stringify(tasks));
}

function loadTasks() {
    const tasks = JSON.parse(localStorage.getItem('tasks')) || [];
    const taskList = document.getElementById('taskList');
    tasks.forEach(task => {
        const li = document.createElement('li');
        if (task.completed) li.classList.add('completed');
        li.innerHTML = `
            <span onclick="toggleTask(this)">${task.text}</span>
            <button class="delete-btn" onclick="deleteTask(this)">Hapus</button>
        `;
        taskList.appendChild(li);
    });
}

function updateTasks() {
    const tasks = [];
    document.querySelectorAll('#taskList li').forEach(li => {
        tasks.push({
            text: li.querySelector('span').textContent,
            completed: li.classList.contains('completed')
        });
    });
    localStorage.setItem('tasks', JSON.stringify(tasks));
}
```

Penjelasan:
- **localStorage**: Menyimpan tugas agar tetap ada setelah refresh.
- **Event Listeners**: Menangani klik untuk menandai tugas selesai atau menghapusnya.
- **Dynamic DOM**: Membuat elemen `<li>` secara dinamis untuk setiap tugas.

## Langkah 4: Menjalankan Aplikasi
1. Simpan ketiga file (`index.html`, `styles.css`, `script.js`) dalam satu folder.
2. Buka `index.html` di browser (bisa melalui `file://` atau server lokal seperti Live Server).
3. Coba tambahkan tugas, tandai sebagai selesai, atau hapus. Perhatikan responsivitas dengan mengubah ukuran jendela browser atau membuka di perangkat mobile.

## Tips untuk Pengembangan Lebih Lanjut
- **Validasi Input**: Tambahkan validasi untuk mencegah input kosong atau duplikat.
- **Filter Tugas**: Tambahkan tombol untuk memfilter tugas selesai/belum selesai.
- **Animasi**: Gunakan CSS transitions untuk animasi saat menambah/menghapus tugas.
- **Aksesibilitas**: Tambahkan atribut ARIA untuk mendukung screen reader.

Dengan pendekatan ini, Anda memiliki aplikasi web responsif sederhana yang fungsional dan dapat dikembangkan lebih lanjut sesuai kebutuhan!
