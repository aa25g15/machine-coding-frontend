# Machine Coding Frontend Questions and Solutions

## Resources
* https://youtu.be/9mPNtzRu_RU
* https://www.youtube.com/watch?v=Ex0qS1qg6NI&ab_channel=AkshaySaini
* https://www.youtube.com/watch?v=uACMeA81QaM&ab_channel=AkshaySaini

## Tips
* Use Vanilla JS only
* Time management - One of the main reasons for failure
  * First 5 minutes:
    * Ask questions
    * Understand the problem statement
    * Take a pen and draw a UI
    * Think about the DS to use
    * Create a mental map of how you will spend the rest of the time
* Prepare to code from scratch - Create a Vanilla JS template that you are comfortable with - https://github.com/aa25g15/vanilla-js-template
* Don't get lost in coding!
  * Revisit your code, see how you have progressed every 15 minutes, re-align yourself if needed, things may not go according to plan!
  * Keep check on time!
  * In the last 15 minutes, even if you have implemented 3/10 features, make sure they work! Make sure that 15 minutes before, your code is submittable
* Technical things you should prepare
  * Shortcuts in your IDE
  * Fetching data from API calls (specifically GET requests) - https://github.com/aa25g15/fetch-api/blob/main/README.md
  * Library functions (Eg. Lodash)
  * DOM manipulation using Vanilla JS - https://github.com/aa25g15/dom-manipulation-js/blob/main/README.md
  * Local storage - They sometimes expect you to maintain state even after hard refresh - https://github.com/aa25g15/browsers-storage-and-cookies/blob/main/README.md
  * UI:
    * Searching
    * Sorting
    * Filtering
    * Tagging
    * Flexbox in CSS
    * Responsiveness of App
    ```javascript
    export const respondTo = {
     XSMALL: '@media only screen and (max-width: 479px)',
     SMALL: '@media only screen and (min-width: 480px)',
     MEDIUM: '@media only screen and (min-width: 768px)',
     LARGE: '@media only screen and (min-width: 1024px)',
     XLARGE: '@media only screen and (min-width: 1280px)',
     XXLARGE: '@media only screen and (min-width: 1600px)',
     MOBILELANDSCAPE:
       '@media only screen and (orientation: landscape) and (min-device-width: 319px) and (max-device-width: 1024px)',
    };
    ```
  * Thinking recursively - Is needed many times, for example, infinitely nested object
  * Code quality:
    * Is your code modular - Small functions that do 1 specific thing, break down code into chunks, separate HTML, CSS, JS
    * Is it scalable? - Would major adjustments be needed to implement new features?
    * Is it readable - Use camelCase and PascalCase, long descriptive names, anyone should understand the code without comments
* No distractions!
* Test your code every few minutes
* Cherry on cake - Impress the interviewer

## Implementing a Debounce
```javascript
const debounce = (func, debounceTime = 250) => {
 let timerId = null;
 return (...args) => {
  clearInterval(timerId);
  timerId = setTimeout(() => {
   func.apply(this, args);
  }, debounceTime);
 }
}
```

## Implementing a Throttle
```javascript
const throttle = (func, throttleTime = 250) => {
 let isPaused = false;
 return (...args) => {
  if(isPaused) return;
  isPaused = true;
  setTimeout(() => {
   func.apply(this, args);
   isPaused = false;
  }, throttleTime)
 }
}
```

## Develop a Comment Widget
### Features:
* Input box to make a comment
* Reply to commment - infinite nesting (Most critical feature, interviewer will be impressed)
* Edit comment, delete comment
* Some nice to have features:
  * Like comment

### My Solution:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, maximum-scale=1.0">
    <title>Machine Coding Round</title>
    <link rel="stylesheet" href="./styles.css"></link>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
    <script defer src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
    <script defer src="./app.js"></script>
</head>
<body>
    <div class="add-comment-card">
        <form class="add-comment-form">
            <input type="text" class="text-input" minlength="10" />
            <button type="submit" class="btn">Add Comment</button>
        </form>
    </div>
    <div class="added-comments-container">
        No comments
    </div>
</body>
</html>
```

```css
* {
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
}

html, body {
    background: whitesmoke;
    color: black;
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 2rem 1rem;
}

.add-comment-card{
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
    display: flex;
    padding: 1rem;
    border-radius: 1rem;
    width: calc(100vw - 1rem);
}

.add-comment-card > form {
    display: flex;
    width: 100%;
}

.added-comments-container{
    margin-top: 2rem;
    width: calc(100vw - 1rem);
    padding: 1rem;
    border-radius: 1rem;
    box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}

.comment-container{
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    border-radius: 1rem;
    padding: 2rem 1rem;
    margin: 1rem;
}

.comment-text-container {
    display: flex;
    align-items: center;
}

.delete-icon{
    margin-left: auto;
    color: white;
    cursor: pointer;
    padding: 0.5rem;
    background-color: red;
    border-radius: 50%;
}

.reply-container{
    display: flex;
    align-items: center;
    margin: 1rem 0;
}

.reply-input{
    width: 100%;
    margin-right: 1rem;
    border-radius: 100vh;
    padding: 0 1rem;
    min-height: 2rem;
}

.reply-icon{
    margin-left: auto;
    color: white;
    cursor: pointer;
    padding: 0.5rem;
    background-color: grey;
    border-radius: 50%;
}

.text-input{
    border-radius: 100vh;
    padding: 0 1rem;
    width: 100%;
}

.btn {
    height: 3rem;
    width: 10rem;
    background: green;
    color: white;
    box-shadow: rgba(0, 0, 0, 0.35) 0px 5px 15px;
    margin-left: 1rem;
    border-radius: 100vh;
}

@media screen and (min-width: 480px) {
    .added-comments-container{
        padding: 5rem; 
        width: calc(100vw - 10rem);
    }

    .add-comment-card{
        padding: 5rem;
        width: calc(100vw - 10rem);
    }

    html, body {
        padding: 2rem 5rem;
    }
}
```

```javascript
class CommentStore {
  store = [];
  idCounter = 0;

  addNewComment = (commentText) => {
    this.store.push({
      id: this.idCounter++,
      text: commentText,
      replies: [],
    });
  };

  deleteComment = (id, list) => {
    const index = list.findIndex((comment) => comment.id === id);
    if (index >= 0) {
      list.splice(index, 1);
    }
  };

  addReply = (commentObject, commentText) => {
    commentObject.replies.push({
      id: this.idCounter++,
      text: commentText,
      replies: [],
    });
  };
}

const commentStore = new CommentStore();
const form = document.querySelector("form.add-comment-form");
const textInput = document.querySelector("input.text-input");
let commentsContainer = document.querySelector("div.added-comments-container");

const createCommentElement = (commentObject, list) => {
  const commentContainer = document.createElement("div");
  commentContainer.classList.add("comment-container");
  commentContainer.dataset.id = commentObject.id;
  commentContainer.innerHTML = `
  <div class="comment-text-container">
    ${commentObject.text}
    <span class="material-symbols-outlined delete-icon">
      delete
    </span>
  </div>
  <form class="reply-container">
    <input minLength="10" class="reply-input" data-id=${commentObject.id} >
    <span type="submit" role="button" class="material-symbols-outlined reply-icon">reply</span>
  </form>
  `;
  commentContainer
    .querySelector(".delete-icon")
    ?.addEventListener("click", () => {
      commentStore.deleteComment(commentObject.id, list);
      updateCommentsDisplay();
    });

  commentContainer
    .querySelector(".reply-container")
    ?.addEventListener("submit", (event) => {
      event.preventDefault();
      const replyInput = commentContainer.querySelector(".reply-input");
      commentStore.addReply(commentObject, replyInput.value);
      updateCommentsDisplay();
    });
  return commentContainer;
};

const generateCommentsForList = (list, container) => {
  list.forEach((comment) => {
    const commentElement = createCommentElement(comment, list);
    container.appendChild(commentElement);
    if (comment.replies.length > 0) {
      const subContainer = document.createElement("div");
      subContainer.classList.add("replies-container");
      commentElement.appendChild(subContainer);
      generateCommentsForList(comment.replies, subContainer);
    }
  });
};

const updateCommentsDisplay = () => {
  if (commentsContainer) {
    commentsContainer.remove();
    commentsContainer = document.createElement("div");
    commentsContainer.classList.add("added-comments-container");
    generateCommentsForList(commentStore.store, commentsContainer);
    if (commentStore.store.length === 0) {
      commentsContainer.innerText = "No comments";
    }
    document.body.appendChild(commentsContainer);
  }
};

form.addEventListener("submit", (event) => {
  event.preventDefault();
  commentStore.addNewComment(textInput.value);
  updateCommentsDisplay();
});
```
  
## Develop a TODO list or a Kanban Board
### Features:
* Create new statuses to group tasks under
* Add a new tasks having a heading and a description for example
* The most difficult part is to add drag and drop functionality for tasks and even the whole lists (the YouTube explainer said that he had to use Google a lot for this)

### My Solution (Does Not Have All The Features):
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, maximum-scale=1.0">
    <title>Machine Coding Round</title>

    <link rel="stylesheet" href="./styles.css"></link>
    <script defer src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
    <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Material+Symbols+Outlined:opsz,wght,FILL,GRAD@48,400,0,0" />
    <script defer src="./app.js"></script>
</head>
<body>
    <div id="all-list-container"></div>
    <button id="add-new-list" class="icon-button">
        <span class="material-symbols-outlined">
            add
        </span>
    </button>
    <div id="add-list-form-container">
        <form id="add-list-form">
            <input name="taskHeading" placeholder="Task heading" id="add-task--heading-input" class="input" type="text" minlength="10" required>
            <input name="taskDescription" placeholder="Task description" id="add-task-description-input" class="input" type="text" minlength="10" required>
            <input name="listName" placeholder="List name" id="add-list-form-input" class="input" type="text" minlength="5" required>
            <button type="submit" class="btn">Submit</button>
        </form>
    </div>
</body>
</html>
```

```css
* {
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
}

html, body {
    background: whitesmoke;
    color: black;
}

#all-list-container{
  padding: 2rem;
  display: grid;
  grid-template-columns: repeat(1, minmax(0, 1fr));
  gap: 2rem;
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  overflow-x: hidden;
  overflow-y: auto;
}

.list-container{
    padding: 1rem;
    width: 100%;
    border: 1px solid black;
    position: relative;
    height: 20rem;
    overflow-y: auto;
    overflow-x: hidden;
}

.icon-button{
  height: 3rem;
  width: 3rem;
  border-radius: 50%;
  color: white;
  position: fixed;
  bottom: 2rem;
  right: 2rem;
  cursor: pointer;
}

#add-new-list{
  background: green;
}

.delete-list-button{
  background: red;
  position: absolute;
  top: 1rem;
  right: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.list-heading{
    font-size: 2rem;
    font-weight: bold;
}

.task{
  border: 1px solid black;
  padding: 1rem;
  margin: 2rem 0;
}

.task-heading{
    font-weight: bold;
    font-size: 16px;
}

.task-description{
    font-size: 12px;
}

#add-list-form-container{
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  display: flex;
  background: rgba(0,0,0,0.6);
  justify-content: center;
  align-items: center;
  display: none;
}

#add-list-form{
    background: white;
    padding: 2rem;
    border-radius: 1rem;
    animation: appear 0.3s ease-in;
    width: calc(100vw - 2rem);
}

.input {
    min-height: 2rem;
    padding: 0 1rem;
    width: 100%;
    margin: 1rem 0;
}

@keyframes appear {
    0% {
        opacity: 0;
        transform: scale(0.5);
    }
    100% {
        opacity: 1;
        transform: scale(1);
    }
}

.btn{
    min-height: 3rem;
    min-width: 10rem;
}

@media screen and (min-width: 480px) {
  #all-list-container {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
  
  #add-list-form{
    width: 60vw;
  }
}
```

```javascript
class Store {
  data = [];
  counter = 0;
  taskCounter = 0;

  addTask = (formData) => {
    const index = this.data.findIndex(
      (list) => list.name === formData.listName
    );

    if (index >= 0) {
      // list exists
      this.data[index].tasks.push({
        id: this.taskCounter++,
        heading: formData.taskHeading,
        description: formData.taskDescription,
      });
    } else {
      this.data.push({
        id: this.counter++, // unique list id
        name: formData.listName,
        tasks: [
          {
            id: this.taskCounter++,
            heading: formData.taskHeading,
            description: formData.taskDescription,
          },
        ],
      });
    }
  };

  deleteList = (listObject) => {
    const index = this.data.findIndex((list) => list.id === listObject.id);

    if (index >= 0) {
      this.data.splice(index, 1);
    }
  };
}

const debounce = (func, time = 1000) => {
  let timerId = null;
  return (...args) => {
    clearInterval(timerId);
    timerId = setTimeout(() => {
      func.apply(this, args);
    }, time);
  };
};

const dataStore = new Store();
const addListButton = document.getElementById("add-new-list");
const allListContainer = document.getElementById("all-list-container");
const addListForm = document.getElementById("add-list-form");
const addListFormModal = document.getElementById("add-list-form-container");

const render = () => {
  const children = [];
  dataStore.data.forEach((listObject) => {
    children.push(getListComponent(listObject));
  });
  allListContainer.replaceChildren(...children);
};

const getTaskComponent = (taskObject) => {
  const taskElement = document.createElement("div");
  taskElement.classList.add("task");
  taskElement.innerHTML = `
  <div class="task-heading">
    ${taskObject.heading}
  </div>
  <div class="task-description">
    ${taskObject.description}
  </div>
  `;

  return taskElement;
};

const getListComponent = (listObject) => {
  const listElement = document.createElement("div");
  listElement.classList.add("list-container");
  listElement.innerHTML = `
  <div contenteditable="true" class="list-heading" id=${listObject.id}>
    ${listObject.name}
  </div>
  <div class="task-container"></div>
  <div class="icon-button delete-list-button">
    <span class="material-symbols-outlined">
      delete
    </span>
  <div>
  `;

  const taskContainer = listElement.querySelector(".task-container");
  listObject.tasks.forEach((taskObject) => {
    taskContainer.appendChild(getTaskComponent(taskObject));
  });

  const deleteListbutton = listElement.querySelector(".delete-list-button");
  deleteListbutton?.addEventListener("click", () => {
    dataStore.deleteList(listObject);
    render();
  });

  listElement.querySelector(".list-heading")?.addEventListener(
    "input",
    debounce((event) => {
      listObject.name = event.target.innerText;
      console.log(dataStore.data);
      render();
    })
  );

  return listElement;
};

addListButton?.addEventListener("click", () => {
  if (addListFormModal) {
    addListFormModal.style.display = "flex";
  }
});

addListForm?.addEventListener("submit", (event) => {
  event.preventDefault();

  const formData = {};

  addListForm.querySelectorAll("input").forEach((input) => {
    formData[input.name] = input.value;
  });

  dataStore.addTask(formData);
  render();

  if (addListFormModal) {
    addListFormModal.style.display = "none";
  }
});
```

## Develop a Food Ordering App
### Features:
* Make a get all to get a list of restaurants with details such as ETA, rating, name, location, menu, tags such as veg/non-veg etc.
* Display those restaurants in the UI (you could make a card for each restaurant)
* Critical requirement is that the site should be responsive
* A search bar for searching restaurants (bonus - implement a debounce)
* A sorting functionality to sort by rating, name, etc.
* Filtering via tags

## Email Web App or Client
### Features:
* Had to look something like Outlook
* Don't have to fetch data but create you own data and store it in a data structure
* Three sections like in most clients
  * Section where inbox, sent etc. navigation is there
  * Section where list of emails is shown
  * Section where the email body of the selected email is shown
* The most difficult part is to maintain the read and unread state of the emails, when email is opened, it should be marked as read (the YouTube explainer used local storage for this)
* Additional features:
  * Favourite email
  * Delete email

## Sudoku Game
Basically, implement the sudoku game. It is a 9X9 grid.

The goal of sudoku is simple: fill in the numbers 1-9 exactly once in every row, column, and 3x3 region. For example, look at the above puzzle and compare it to the solved version below. Notice that every row, column and 3x3 region contain every number from 1-9 exactly once.

### My Solution - Took Some Figuring Out The Validations

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=no, maximum-scale=1.0">
    <title>Machine Coding Round</title>

    <link rel="stylesheet" href="./styles.css"></link>
    <script defer src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
    <script defer src="./app.js"></script>
</head>
<body>
    <div class="app-container">
        <div id="game-container"></div>
    </div>
</body>
</html>
```

```css
* {
    box-sizing: border-box;
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    margin: 0;
    padding: 0;
}

html, body {
    background: whitesmoke;
    color: black;
}

.app-container{
  display: flex;
  overflow: hidden;
  justify-content: center;
  align-items: center;
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
}

#game-container{
  display: grid;
  grid-template-columns: repeat(9, minmax(0, 1fr));
  grid-template-rows: repeat(9, minmax(0, 1fr));
  background: palegoldenrod;
  gap: 0;
  margin: 1rem;
  aspect-ratio: 1;
  max-height: 80vh;
  max-width: 80vw;
  border: 2px solid red;
}

.number-box{
  aspect-ratio: 1;
  text-align: center;
  width: 100%;
  font-size: 100%;
  border: 1px solid black;
}
```

```javascript
class State {
  state = [
    [1, 6, 8, 4, 5, 7, 9, 3, 2],
    [5, 7, 2, 3, 9, 1, 4, 6, 8],
    [9, 3, 4, 6, 2, 8, 5, 1, 7],
    [8, 2, 9, 7, 4, 3, 1, 5, 6],
    [6, 5, 1, 2, 8, 9, 3, 7, 4],
    [7, 4, 3, 5, 1, 6, 2, 8, 9],
    [3, 9, 5, 8, 7, 2, 6, 4, 1],
    [4, 1, 7, 9, 6, 5, 8, 2, 3],
    [2, 8, 6, 1, 3, 4, 7, 9, null],
  ];

  setState = (row, col, value) => {
    this.state[row][col] = value;
  };

  validateRow = (row, rowIndex) => {
    const set = new Set();
    for (let i = 0; i < row.length; i++) {
      if (!row[i] || set.has(row[i])) {
        console.log("row failed", rowIndex, row[i]);
        return false;
      }
      set.add(row[i]);
    }
    return true;
  };

  validateColumn = (colIndex) => {
    const set = new Set();
    this.state.forEach((row) => {
      if (!row[colIndex] || set.has(row[colIndex])) {
        console.log("col failed", colIndex, row[colIndex]);
        return false;
      }
      set.add(row[colIndex]);
    });
    return true;
  };

  validateRegion = (rowStart, rowEnd, colStart, colEnd) => {
    const set = new Set();
    for (let row = rowStart; row <= rowEnd; row++) {
      for (let col = colStart; col <= colEnd; col++) {
        if (!this.state[row][col] || set.has(this.state[row][col])) {
          console.log(
            "region failed",
            [rowStart, rowEnd, colStart, colEnd],
            this.state[row][col]
          );
          return false;
        }
        set.add(this.state[row][col]);
      }
    }
    return true;
  };

  validateSudoku = () => {
    /**
     * Fill in the numbers 1-9 exactly once in every row, column, and 3x3 region
     */
    console.log(this.state);

    this.state.forEach((row, index) => {
      if (!this.validateRow(row, index)) return false;
    });

    for (let i = 0; i < this.state.length; i++) {
      if (!this.validateColumn(i)) return false;
    }

    if (
      !this.validateRegion(0, 2, 0, 2) ||
      !this.validateRegion(3, 5, 0, 2) ||
      !this.validateRegion(6, 8, 0, 2) ||
      !this.validateRegion(0, 2, 3, 5) ||
      !this.validateRegion(3, 5, 3, 5) ||
      !this.validateRegion(6, 8, 3, 5) ||
      !this.validateRegion(0, 2, 6, 8) ||
      !this.validateRegion(3, 5, 6, 8) ||
      !this.validateRegion(6, 8, 6, 8)
    ) {
      return false;
    }

    return true;
  };
}

const gameState = new State();
const gameContainer = document.getElementById("game-container");

const setBorder = () => {
  if (gameState.validateSudoku()) {
    // Game has been solved!
    gameContainer.style.border = "2px solid green";
  } else {
    gameContainer.style.border = "2px solid red";
  }
};

const renderGame = () => {
  if (gameContainer) {
    gameState.state.forEach((row, rowIndex) => {
      row.forEach((value, colIndex) => {
        const numberBox = document.createElement("input");
        numberBox.classList.add("number-box");
        if (value) {
          numberBox.disabled = true;
        }
        numberBox.value = value;
        numberBox.type = "number";
        numberBox.maxLength = "1";
        gameContainer.appendChild(numberBox);
        numberBox.addEventListener("change", (event) => {
          if (!event.target.value.match(/^[1-9]{1}$/)) {
            numberBox.value = value;
            setBorder();
            return;
          }
          gameState.setState(rowIndex, colIndex, Number(event.target.value));
          setBorder();
        });
      });
    });
  }
};

renderGame();
```

## Comparison App
An app to compare 2 or more things

### Features:
* Can use GitHub API for example to get details of different users and compare information such as number of commits, stars, repos etc.
* Ability to change the comparison objects
* Different color schemes for who is better
* Responsiveness
