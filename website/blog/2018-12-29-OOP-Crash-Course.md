---
author: Vibhanshu Chaturvedi
authorURL: https://twitter.com/vibhanshu86
authorFBID: 901405709933351
title: OOP Crash Course
---

### Object Literals

```javascript
const book1 = {
  title: "Book One",
  author: "John Doe",
  year: "2013",
  getSummary: function() {
    return `${this.title} was written by ${this.author} in ${this.year}.`;
  }
};

const book2 = {
  title: "Book Two",
  author: "John Doe",
  year: "2016",
  getSummary: function() {
    return `${this.title} was written by ${this.author} in ${this.year}.`;
  }
};

console.log(book1);
console.log(book1.getSummary());

console.log(book2);
console.log(book2.getSummary());
```

<p data-height="488" data-theme-id="0" data-slug-hash="EGwpoE" data-default-tab="js" data-user="vibhanshu" data-pen-title="JS - OOP - Object Literal" data-preview="true" class="codepen">See the Pen <a href="https://codepen.io/vibhanshu/pen/EGwpoE/">JS - OOP - Object Literal</a> by vibhanshu chaturvedi (<a href="https://codepen.io/vibhanshu">@vibhanshu</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

### Constructor and this

```javascript
function Book(title, author, year) {
  this.title = title;
  this.author = author;
  this.year = year;
}

Book.protoype.getSummary = function() {
  return `${this.title} was written by ${this.author} in ${this.year}.`;
};

Book.prototype.getAge = function() {
  const years = new Date().getFullYear() - this.year;
  return `${this.title} is ${years} years old.`;
};

Book.prototype.revise = function(year) {
  this.year = year;
  this.revise = true;
};

const book1 = new Book("Book One", "John Doe", "2013");
const book2 = new Book("Book Two", "John Doe", "2016");

console.log(book2.getSummary()); // Book Two was written by John Doe in 2016.
console.log(book2.getAge()); // Book Two is 2 years old.

book2.revise(2018);
console.log(book2.getSummary()); // Book Two was written by John Doe in 2018.
```

### Inheritance

```javascript
function Book(title, author, year) {
  this.title = title;
  this.author = author;
  this.year = year;
}

Book.protoype.getSummary = function() {
  return `${this.title} was written by ${this.author} in ${this.year}.`;
};

Book.prototype.getAge = function() {
  const years = new Date().getFullYear() - this.year;
  return `${this.title} is ${years} years old.`;
};

Book.prototype.revise = function(year) {
  this.year = year;
  this.revise = true;
};

function Magazine(title, author, year, month) {
  Book.call(this, title, author, year);
  this.month = month;
}

Magazine.prototype = Object.create(Book.prototype);

Magazine.prototype.constructor = Magazine;

const magazine = new Magazine("Magazine Title", "John Doe", "2017", "May");

console.log(magazine);
```

### Prototypes

```javasript

const bookProtos = {
    getSummary: function() {
      return `${this.title} was written by ${this.author} in ${this.year}.`;
    },
    getAge = function() {
      const years = new Date().getFullYear() - this.year;
      return `${this.title} is ${years} years old.`;
    },
    revise = function(year) {
      this.year = year;
      this.revise = true;
    }
};

const book1 = Object.create(bookProtos, {
    title: { value: 'Book One'},
    author: { value: 'John Doe'},
    year: { value: '2013'},
});

console.log(book1.getSummary()); // Book One was written by John Doe in 2013.

```

### Classes and Subclasses

```javascript Class
class Book {
  constructor(title, author, year) {
    this.title = title;
    this.author = author;
    this.year = year;
  }

  getSummary() {
    return `${this.title} was written by ${this.author} in ${this.year}.`;
  }

  getAge() {
    const years = new Date().getFullYear() - this.year;
    return `${this.title} is ${years} years old.`;
  }

  revise(year) {
    this.year = year;
    this.revise = true;
  }
}

const book1 = new Book("Book One", "John Doe", "2013");
const book2 = new Book("Book Two", "John Doe", "2016");

console.log(book2.getSummary()); // Book Two was written by John Doe in 2016.
console.log(book2.getAge()); // Book Two is 2 years old.

book2.revise(2018);
console.log(book2.getSummary()); // Book Two was written by John Doe in 2018.

class Magazine extends Book {
  constructor(title, author, year, month) {
    super(title, author, year);
    this.month = month;
  }
}

const magazine = new Magazine("Magazine title", "John Doe", "2018", "Dec");

console.log(magazine.getAge()); // Magazine title is 0 years old.
```
