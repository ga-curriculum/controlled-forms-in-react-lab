# ![Controlled Forms in React Lab - Exercise](./assets/hero.png)

## Introduction

In this lab, you'll implement what you've learned about state and controlled forms in React to create a form that adds book cards to a virtual bookshelf.  

## A quick note before you dive in

Don't hesitate to collaborate with your classmates when working through labs.

If you get stuck during the lab, we recommend revisiting the lesson materials first. They're designed to provide you with the information and examples that will help you complete the exercises.

## What You'll Build

You're going to create a single component that holds your controlled form as well as bookshelf. You'll need to utilize the `useState` React hook for your form to work effectively. 

## Lab exercises

Before getting started, add the following style rules to `index.css`:

First, change the existing style rules for `body` to this:
```css
body {
  margin: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-width: 100vw;
  min-height: 100vh;
}
```

Then, add these rules above the `@media` rule:
```css
form {
  display: flex;
  flex-direction: column;
  width: 90%;
}

input{
  padding: 5px;

} 

.bookshelfDiv {
  padding: 10px;
  width: 80%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.formDiv {
  width: 60%;
  border: 1px solid white;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 20px;
}

.bookCardsDiv {
  display: flex;
  flex-direction: column;
  flex-wrap: wrap;
  width: 90%;
  margin-top: 20px;
}

.bookCard {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  border: 1px solid white;
  padding: 5px;
  width: 40%;
  margin: 15px 10px;
  background-color: rgb(155, 155, 155);
  color: black;
}
```


### Exercise 1: Create your component

Create a new component called `Bookshelf.jsx`, and import `useState` at the top of the file:

```jsx
import { useState } from 'react';
```

Add the following code inside of your return statement:

```jsx
<div className="bookshelfDiv">
  <div className="formDiv">
    <h3>Add a Book</h3>
      {/* form will go here */}
  </div>
  <div className="bookCardsDiv">
    {/* Book cards will go here */}
  </div>
</div>
```

### Exercise 2: Define the initial state

Create a new state variable called `books`. We'll want to populate our bookshelf with some existing data, so add the following array of objects as `books` initial state:

```jsx
const [books, setBooks] = useState([
    {
      title: 'Fourth Wing',
      author: 'Rebecca Yarros',
    },
    {
      title: 'The Lion, the Witch and the Wardrobe',
      author: 'C.S. Lewis',
    }
]);
```

You'll also need a second state variable called `newBook`. This will be an object with a `title` key and an `author` key, both of which will hold empty strings for now. 


### Exercise 3: Create event handlers

For this lab you'll need three event handlers:

#### 1. `handleInputChange`
This function will be triggered whenever a user types in an input field. It should accept an event object as a parameter.

Use the spread operator (...) to create a new copy of the `newBook` object, updating only the relevant property with the new value from the input field.

Update `newBook` state to the copied newBook object using the `setNewBook` setter function.


#### 2. `handleAddBook`
This function will be triggered when the user submits the form.

Inside this function, create a copy of the existing books array using the spread operator. Add the `newBook` object (containing the user's input) to this copied array.

Use the `setBooks` setter function to update state with the new array - effectively adding the book to our collection.


#### 3. `handleSubmit`
This function will handle form submission. It should accept an event object as a parameter.

Inside this function, prevent the default form submission behavior using `event.preventDefault()`.

Call the `handleAddBook` function to add the new book to our collection.

Clear the `newBook` state object by setting it back to an empty object, ready for the next addition.


### Exercise 4: Form creation

Use JSX to create a form with sections for "Title" and "Author". Add input fields for each, where users can type in their book details.

Make sure to connect these input fields to their corresponding properties in the `newBook` state object using the `value` and `onChange` attributes.

Finally, add a submit button to your form. Don't forget to attach your `onSubmit` handler to the form as well! 


### Exercise 5: Map through your books

Iterate through the `books` array in your `Bookshelf` component using the `map` function.

For each book, create a "book card" using a `<div>`, and display the book's title and author within the card.

