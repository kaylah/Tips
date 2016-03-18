# Switch to Object Literal

The ol' `switch` statement. Other languages love it, but I'm not a fan of it in JavaScript. I prefer Objects. Objects are more flexible, easier to read and if you're a JavaScript developer, you're already familiar with Objects. Plus, the more complicated your logic gets, the better performant an Object literal will be. Let's look at some simple comparisons.

## The `switch`

A typical `switch` statement looks like this:

```
  var pet = 'dachshund';
  var petType;

  switch(pet) {
    case 'dachshund':
      petType = 'dog';
      break;
    case 'goldfish':
      petType = 'fish';
      break;
    case 'bobcat':
      petType = 'cat';
      break;
    case 'mastiff':
      petType = 'dog';
      break;
    default:
      petType = 'giraffe';
  }

  console.log('petType', petType);
  //petType dog
```

The `switch` statement takes an input, in the above case the input is `pet`, which is set to `dachshund`. It goes through each case, until it finds a match and hits a `break;`. It's very similar to an `if/else` statement. Here would be the same logic written as an `if/else`:

```
  var pet = 'dachshund';
  var petType;

  if (pet === 'dachshund') {
    petType = 'dog';
  }
  else if (pet === 'goldfish') {
    petType = 'fish';
  }
  else if (pet === 'bobcat') {
    petType = 'cat';
  }
  else if (pet === 'mastiff') {
    petType = 'dog';
  }
  else {
    petType = 'giraffe';
  }

  console.log('petType', petType);
  //petType dog
```

Smell something? No, it's not your deodorant failing. It's the code. Anytime you see a large `else if` list, your nose should wrinkle at the putridness. This is prone to bugs and a common code smell. You are much better off using a `switch`.

So why not use a `switch`? You can, but there are things you have to keep in mind when using a `switch`.
- Order matters - Since a `switch` evaluates top down, the order of your cases matter.
- Remember to `break;` - A `switch` stops evaluating once it hits a `break;` after a `true` `case`. Since more than one `case` could evaulate as `true`, a missing `break;` could fall through to another truthy `case` - sounds like a troubleshooting nightmare waiting to haunt you. But there's hope.

## The Object Literal

Objects make up the JavaScript language, so chances are you're familiar with them. Let's see the simple examples above written out as a simple Object literal:

```
  var pet = 'dachshund';

  var pets = {
    'dachshund': 'dog',
    'goldfish': 'fish',
    'bobcat': 'cat',
    'mastiff': 'dog'
    'default': 'giraffe'
  }

  var petType = pets[pet] || pets['default'];

console.log('petType', petType);
//petType dog
```
