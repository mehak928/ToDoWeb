# ToDoWeb
<!DOCTYPE html>
<html lang="en">
</html>
<head>
 <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>To-Do List App</title>
  <style>
    body {
      font-family: sans-serif;
      background-color: #f4f6f8;
      margin: 0;
      padding: 20px;
      display: flex;
      justify-content: center;
    }

    .todo-container {
      background: rgb(12, 12, 12);
      padding: 30px;
      border-radius: 10px;
      box-shadow: 0 4px 10px rgba(0,0,0,0.1);
      width: 100%;
      }
    h1 {
      text-align: center;
      color: #333;
    }

    form {
      display: flex;
      gap: 10px;
    }

    input[type="text"] {
      flex: 1;
      padding: 10px;
      font-size: 16px;
    }

    button {
      padding: 10px 15px;
      font-size: 16px;
      background-color: #5c6bc0;
      color: white;
      border-radius: 4px;
      cursor: pointer;
    }

    ul {
      list-style: none;
      padding: 0;
      margin-top: 20px;
    }

    li {
      background: #141414;
      padding: 10px;
      margin-bottom: 10px;
      display: flex;
      justify-content: space-between;
      align-items: center;
      border-radius: 5px;
    }

    li.completed span {
      text-decoration: line-through;
      color: #888;
    }

    .actions button {
      margin-left: 5px;
      background-color: #d32f2f;
    }

    .complete-btn {
      background-color: #388e3c;
    }
  </style>
</head>
<body>
  <div class="todo-container">
    <h1>To-Do List</h1>
    <form id="todo-form">
      <input type="text" id="todo-input" placeholder="Enter a task..." />
      <button type="submit">Add</button>
    </form>
    <ul id="todo-list"></ul>
  </div>

  <script>
    const form = document.getElementById('todo-form');
    const input = document.getElementById('todo-input');
    const list = document.getElementById('todo-list');

    form.addEventListener('submit', function(e) {
      e.preventDefault();
      const taskText = input.value.trim();
      if (taskText === '') return;

      const li = document.createElement('li');

      const span = document.createElement('span');
      span.textContent = taskText;

      const actions = document.createElement('div');
      actions.className = 'actions';

      const completeBtn = document.createElement('button');
      completeBtn.textContent = '✔';
      completeBtn.className = 'complete-btn';
      completeBtn.onclick = function() {
        li.classList.toggle('completed');
      };

      const deleteBtn = document.createElement('button');
      deleteBtn.textContent = '✖';
      deleteBtn.onclick = function() {
        list.removeChild(li);
      };

      actions.appendChild(completeBtn);
      actions.appendChild(deleteBtn);

      li.appendChild(span);
      li.appendChild(actions);
      list.appendChild(li);

      input.value = '';
    });
  </script>
</body>
</html>
