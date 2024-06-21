  <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>To-Do List Manager</title>
<style>
  body {
    font-family: Arial, sans-serif;
    margin: 0;
    padding: 20px;
  }

  #console {
    border: 1px solid #ccc;
    padding: 10px;
    min-height: 200px;
    background-color: #f8f8f8;
    overflow-y: auto;
  }

  input[type="text"] {
    width: calc(100% - 20px);
    padding: 8px;
  }

  button {
    padding: 8px 20px;
    margin-left: 10px;
    background-color: #4CAF50;
    color: white;
    border: none;
    cursor: pointer;
  }

  button:hover {
    background-color: #45a049;
  }
</style>
</head>
<body>

<div id="console"></div>

<div>
  <input type="text" id="taskInput" placeholder="Enter task...">
  <button onclick="addTask()">Add Task</button>
  <button onclick="viewTasks()">View Tasks</button>
  <button onclick="clearConsole()">Clear Console</button>
</div>

<script>
  var consoleDiv = document.getElementById("console");
  var tasks = [];

  function addTask() {
    var taskInput = document.getElementById("taskInput").value.trim();
    if (taskInput === "") {
      writeToConsole("Please enter a task.");
      return;
    }
    tasks.push(taskInput);
    writeToConsole("Task added: " + taskInput);
    document.getElementById("taskInput").value = "";
  }

  function viewTasks() {
    if (tasks.length === 0) {
      writeToConsole("No tasks found.");
    } else {
      writeToConsole("Tasks:");
      for (var i = 0; i < tasks.length; i++) {
        writeToConsole((i + 1) + ". " + tasks[i]);
      }
    }
  }

  function clearConsole() {
    consoleDiv.innerHTML = "";
  }

  function writeToConsole(message) {
    consoleDiv.innerHTML += "<p>" + message + "</p>";
    consoleDiv.scrollTop = consoleDiv.scrollHeight;
  }
</script>

</body>
</html>
