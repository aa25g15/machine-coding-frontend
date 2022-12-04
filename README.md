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
* Prepare to code from scratch - Create a Vanilla JS template that you are comfortable with
* Don't get lost in coding!
  * Revisit your code, see how you have progressed every 15 minutes, re-align yourself if needed, things may not go according to plan!
  * Keep check on time!
  * In the last 15 minutes, even if you have implemented 3/10 features, make sure they work! Make sure that 15 minutes before, your code is submittable
* Technical things you should prepare
  * Shortcuts in your IDE
  * Fetching data from API calls (specifically GET requests)
  * Library functions (Eg. Lodash)
  * DOM manipulation using Vanilla JS - https://github.com/aa25g15/dom-manipulation-js/blob/main/README.md
  * Local storage - They sometimes expect you to maintain state even after hard refresh
  * UI:
    * Searching
    * Sorting
    * Filtering
    * Tagging
    * Flexbox in CSS
    * Responsiveness of App
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
