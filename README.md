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

## Comparison App
An app to compare 2 or more things

### Features:
* Can use GitHub API for example to get details of different users and compare information such as number of commits, stars, repos etc.
* Ability to change the comparison objects
* Different color schemes for who is better
* Responsiveness
