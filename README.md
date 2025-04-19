<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>To-Do List</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: linear-gradient(to right, #a18cd1, #fbc2eb);
      margin: 0;
      padding: 0;
      display: flex;
      justify-content: center;
      align-items: center;
      height: 100vh;
    }

    .container {
      background: white;
      padding: 30px;
      border-radius: 15px;
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      width: 90%;
      max-width: 400px;
    }

    h1 {
      text-align: center;
      color: #6a3093;
      margin-bottom: 20px;
    }

    input[type="text"] {
      width: 100%;
      padding: 10px;
      border: 1px solid #ddd;
      border-radius: 8px;
      margin-bottom: 10px;
    }

    button {
      width: 100%;
      padding: 10px;
      background-color: #6a3093;
      color: white;
      border: none;
      border-radius: 8px;
      cursor: pointer;
    }

    button:hover {
      background-color: #8838b3;
    }

    ul {
      list-style: none;
      padding: 0;
    }

    li {
      background: #f3f3f3;
      padding: 10px;
      margin: 8px 0;
      border-radius: 6px;
      display: flex;
      justify-content: space-between;
      align-items: center;
    }

    li.done {
      text-decoration: line-through;
      color: gray;
    }

    .delete {
      background: none;
      border: none;
      color: red;
      font-size: 18px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>My To-Do List</h1>
    <input type="text" id="taskInput" placeholder="Add a new task..." />
    <button onclick="addTask()">Add Task</button>
    <ul id="taskList"></ul>
  </div>

  <script>
    function addTask() {
      const input = document.getElementById('taskInput');
      const taskText = input.value.trim();
      if (taskText === '') return;

      const li = document.createElement('li');
      li.innerHTML = `
        <span onclick="toggleDone(this)">${taskText}</span>
        <button class="delete" onclick="deleteTask(this)">✖</button>
      `;

      document.getElementById('taskList').appendChild(li);
      input.value = '';
    }

    function deleteTask(button) {
      button.parentElement.remove();
    }

    function toggleDone(span) {
      span.parentElement.classList.toggle('done');
    }
  </script>
</body>
</html>
