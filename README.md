# Apex-task-4
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My Portfolio</title>
  <style>
    body { font-family: Arial; margin: 0; padding: 0; }
    nav { background: #333; padding: 10px; }
    nav a { color: #d66666; margin: 0 10px; text-decoration: none; }
    section { padding: 20px; }
    footer { background: #eee; text-align: center; padding: 10px; }
  </style>
</head>
<body>
  <nav>
    <a href="#about">About</a>
    <a href="#projects">Projects</a>
    <a href="#contact">Contact</a>
  </nav>
  <section id="about">
    <h2>About Me</h2>
    <p>Hello! I'm Serene, a web developer.</p>
  </section>
  <section id="projects">
    <h2>Projects</h2>
    <p>Coming Soon...</p>
  </section>
  <section id="contact">
    <h2>Contact</h2>
    <p>Email: serene@example.com</p>
  </section>
  <footer>
    <p>&copy; 2025 Serene</p>
  </footer>
</body>
</html>


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>To-Do App</title>
  <style>
    body { font-family: sans-serif; padding: 20px; }
    input, button { margin: 5px; }
  </style>
</head>
<body>
  <h2>To-Do List</h2>
  <input id="taskInput" type="text" placeholder="New task">
  <button onclick="addTask()">Add</button>
  <ul id="taskList"></ul>

  <script>
    function loadTasks() {
      const tasks = JSON.parse(localStorage.getItem('tasks') || '[]');
      document.getElementById('taskList').innerHTML = tasks.map((task, i) =>
        `<li>${task} <button onclick="removeTask(${i})">X</button></li>`).join('');
    }

    function addTask() {
      const input = document.getElementById('taskInput');
      const tasks = JSON.parse(localStorage.getItem('tasks') || '[]');
      if (input.value) {
        tasks.push(input.value);
        localStorage.setItem('tasks', JSON.stringify(tasks));
        input.value = '';
        loadTasks();
      }
    }

    function removeTask(index) {
      const tasks = JSON.parse(localStorage.getItem('tasks'));
      tasks.splice(index, 1);
      localStorage.setItem('tasks', JSON.stringify(tasks));
      loadTasks();
    }

    loadTasks();
  </script>
</body>
</html>


<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Products</title>
  <style>
    .product { border: 1px solid #ccc; margin: 10px; padding: 10px; }
  </style>
</head>
<body>
  <h2>Product List</h2>
  <label>Sort:
    <select id="sort" onchange="render()">
      <option value="price">Price</option>
      <option value="rating">Rating</option>
    </select>
  </label>
  <div id="products"></div>

  <script>
    const products = [
      { name: "Item A", price: 100, rating: 4.5 },
      { name: "Item B", price: 50, rating: 4.0 },
      { name: "Item C", price: 150, rating: 5.0 },
    ];

    function render() {
      const sortBy = document.getElementById('sort').value;
      const sorted = [...products].sort((a, b) => a[sortBy] - b[sortBy]);
      document.getElementById('products').innerHTML = sorted.map(p =>
        `<div class='product'><h3>${p.name}</h3><p>Price: $${p.price}</p><p>Rating: ${p.rating}</p></div>`).join('');
    }

    render();
  </script>
</body>
</html>
