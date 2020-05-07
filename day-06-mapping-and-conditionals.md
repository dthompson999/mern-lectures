# Day 6 - Mapping and Conditionals

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/React-icon.svg" width="256px" alt="React" />

## Iterating in React

We're probably familiar with using `for` loops to iterate through lists in our Views

#### SomeView.html
```html
<ul>
  {% for book in books %}
    <li>{{ book.title }} ({{ book.author }})</li>
  {% endfor %}
</ul>
```

But how should we do this in our React Components? We'll be using `Array.prototype.map()`.

#### BookList.jsx
```js
const BookList = props => {
  return (
    <ul>
      {props.books.map( (book, i) => 
        <li key={ i }>{ book.title } ({ book.author })</li>
      )}
    </ul>
  );
}
```

Here we're going to receive an array of books through props, and using these props we can map throug the array to display the books. If we give React a `<li>War and Peace (Tolstoy)</li>` or `[<li>War and Peace (Tolstoy)</li>]` it will be able to figure out how to display it. But when we give it an array, it will want each child (`<li>`) in the array to have a unique `key` property. We can get the loop index `i` from the `.map()` method and this can serve as a suitablly unique `key`.
