<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Task List</title>
</head>
<body>

    <!-- Input alanı ve liste -->
    <input type="text" id="txtTaskName" placeholder="Yeni görev girin">
    <button id="btnAddNewTask">Görev Ekle</button>
    <ul id="task-list"></ul>

    
<body>
    <div class="container mt-5">
        <div class="row">
            <div class="col-12">
                <div class="card">
                    <div class="card-header">
                        Todo App
                    </div>
                    <div class="card-body">
                        <form id="taskForm">
                            <div class="input-group">
                                <input type="text" id="txtTaskName" class="form-control" placeholder="Yeni görev girin" required>
                                <button type="button" class="btn btn-primary" id="btnAddNewTask">Ekle</button>
                            </div>
                        </form>
                    </div>
                    <div class="card mt-3">
                        <div class="card-header">
                            <button class="btn btn-danger btn-sm float-end" id="btnClearTasks">Temizle</button>
                        </div>
                        <div class="card-body">
                            <ul id="task-list" class="list-group list-group-flush"></ul>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
    
    <script>
        "use strict";

        // Görev listesi başlangıç verileri
        let gorevListesi = [
            { "id": 1, "gorevAdi": "Görev 1" },
            { "id": 2, "gorevAdi": "Görev 2" },
            { "id": 3, "gorevAdi": "Görev 3" },
            { "id": 4, "gorevAdi": "Görev 4" }
        ];

        // Görevleri görüntülemek için fonksiyon
        function displayTask() {
            let ul = document.getElementById("task-list");
            ul.innerHTML = '';  // Mevcut görevleri temizle

            // Görev listesine göre her bir görevi listeye ekle
            for (let gorev of gorevListesi) {
                let li = `
                    <li class="task list-group-item">
                        <div class="form-check">
                            <input type="checkbox" id="${gorev.id}" class="form-check-input">
                        </div>
                        <label for="${gorev.id}" class="form-check-input">${gorev.gorevAdi}</label>
                    </li>`;
                ul.insertAdjacentHTML("beforeend", li);
            }
        }

        // Görev ekleme işlevi
        function newTask(event) {
            let taskInput = document.querySelector('#txtTaskName');
            if (taskInput.value.trim() !== '') {
                gorevListesi.push({
                    "id": gorevListesi.length + 1, 
                    "gorevAdi": taskInput.value
                });
                displayTask();
                taskInput.value = '';  // Girdi kutusunu temizle
            }
            event.preventDefault();
        }

        // Yeni görev eklemek için buton olay dinleyicisi
        document.querySelector("#btnAddNewTask").addEventListener("click", newTask);

        // Sayfa yüklendiğinde mevcut görevleri görüntüle
        displayTask();
    </script>

</body>
</html>
