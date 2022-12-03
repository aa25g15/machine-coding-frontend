# Machine Coding Frontend Questions and Solutions

## Resources
* https://youtu.be/9mPNtzRu_RU

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
