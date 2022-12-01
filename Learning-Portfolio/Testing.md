# Testing

## 1. Check that passing a given input into our tests returns the expected output

In the below code snippet, the test checks whether submitting a new task adds it to the list. It is first calling a function that generates a test, then checks whether length of the array has changed (become 1). 

```
test("Submitting a new task adds it to the list", () => {
  createTestTask("Task1");
  equal(testList.children.length, 1, "One task is added to the list");
  clearTest();
});
```

This test passed. 

![image](https://user-images.githubusercontent.com/108976875/205121268-3a148589-9385-43a3-a8fb-04f59e4b4aaa.png)

## 2. Write tests to mimic the behaviour of a user performing different actions

The test above calls the `createTestTask` function. This mimics the behaviour of a user by adding the value of 'task' to the input box and simulates clicking the submit button. It then clears the value.

```
function createTestTask(task) {
  testInput.value = task;
  testBtn.click();
  testInput.value = "";
}
```

## 3. Write testable, modular functions

When developing the js code, we aimed to ensure that functions were built in a modular way to ensure testing capability. The code below is a function to display an error message, and is called multiple times by other functions.

```
function displayError() {
  error.textContent = "Please enter a task!";
  setTimeout(() => {
    error.textContent = "";
  }, 2000);
}
```

## 4. Write functions that add, remove or modify DOM nodes

The below function removes the task element from the DOM when the associated delete button is clicked.

```
function deleteCheck(e) {
  const item = e.target;

  //Delete task
  if (item.classList[0] === "trash-btn") {
    const todo = item.parentElement;
    removeLocalTodos(todo);
    todo.remove();
  }

  //Check Mark
  if (item.classList[0] === "complete-btn") {
    const todo = item.parentElement;
    todo.classList.toggle("completed");
  }
}
```

## 5. Apply event listeners to HTML form elements

Below is an extract of the code where variable are created to select the relevant DOM element with event listeners which wait for 'click' events and in one instance the 'dom content loaded' event.

```
//Selectors
const taskInput = document.getElementById("task-input");
const taskBtn = document.getElementById("addtaskbtn");
const taskList = document.getElementById("tasklist");
const filterOption = document.querySelector(".filter-todo");
const form = document.getElementById("form");
const error = document.getElementById("errorMsg");

//Event listeners
document.addEventListener("DOMContentLoaded", getTasks);
taskBtn.addEventListener("click", validateTask);
taskList.addEventListener("click", deleteCheck);
filterOption.addEventListener("click", filterTodo);
```


## 6. Use scope to control what variables are accessible inside functions and blocks

Below is a function which saves the tasks to local storage. A let variable 'todos' is declared within the function and can only be read in the function.

```
function saveLocalTasks(todo) {
  let todos;
  if (localStorage.getItem("todos") === null) {
    todos = [];
  } else {
    todos = JSON.parse(localStorage.getItem("todos"));
  }
  todos.push(todo);
  localStorage.setItem("todos", JSON.stringify(todos));
}
```

## 7. Use CSS grid to create complex layouts

We did not use CSS grid to create the layout. I have used this on other projects, such as the more recently completed Advent Calender project. 

```
#calendar-grid {
    display: grid;
    width: 98%;
    max-width: 940px;
    margin: 2% auto;
    grid-template-columns: repeat(7, 1fr);
    grid-template-rows: 4;
    grid-gap: 25px;
  }

#window-24 {
    grid-column-start: 1;
    grid-column: span 2;
    grid-row-start: 1;
    grid-row: span 2;
}
```

## 8. Use CSS grid to make layouts that adapt to the viewport size

Due to the above grid code example being built using fractions, the width of the elements varies when the viewport width changes. A media query is used to change the number of columns once the viewport width reduces to less than 500px.

```
/* media queries */
@media only screen and (max-width: 500px) {
.calendar-grid {
    grid-template-columns: repeat(3, 1fr);
}
}
```
