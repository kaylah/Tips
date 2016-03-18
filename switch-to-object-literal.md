# Switch to Object Literal

The ol' `switch` statement. Other languages love it, but I'm not a fan of it in JavaScript. I prefer Objects. Objects are more flexible, easier to read and if you're a JavaScript developer, you're already familiar with Objects. Let's look at some simple comparisons.

## The `switch`

A typical `switch` statement looks like this:

```
  var pet = 'dachshund';
  var petType;

  switch(pet) {
    case 'dachshund':
    case 'mastiff':
      petType = 'dog';
      break;
    case 'goldfish':
      petType = 'fish';
      break;
    case 'bobcat':
      petType = 'cat';
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
  else if (pet === 'mastiff') {
    petType = 'dog';
  }
  else if (pet === 'goldfish') {
    petType = 'fish';
  }
  else if (pet === 'bobcat') {
    petType = 'cat';
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

Objects make up the JavaScript language, so chances are you're familiar with them. Let's see the simple examples above written out as a simple Object literal (You may hear other developers refer to this as a `Dictionary`, a `Hash Map` or simply `Map`):

```
  var pet = 'dachshund';

  var pets = {
    'dachshund': 'dog',
    'mastiff': 'dog',
    'goldfish': 'fish',
    'bobcat': 'cat',
    'default': 'giraffe'
  }

  var petType = pets[pet] || pets['default'];

console.log('petType', petType);
//petType dog
```

Do you find this easier to read? I do. :+1:

Ok, that's great for when you need a `String`, but what if you need something more complex, like a `function`? You can set it up like this:

```
  var pet = 'dachshund';

  var pets = {
    'dachshund': function() {
      return 'dog';
    },
    'mastiff': function() {
      return 'dog';
    },
    'goldfish': function() {
      return 'fish';
    },
    'bobcat': function() {
      return 'cat';
    },
    'default': function() {
      return 'giraffe';
    },
  }

  var petType = (pets[pet] || pets['default'])();

console.log('petType', petType);
//petType dog
```

Granted your `function` logic will most likely be more complex than this simple example, but the structure is the same.

## Wrap Up

Have I convinced you? I have a friend who prefers the `switch`. I don't think lesser of him because of it. I know he'll come around. (I did win in our last discussion on how to implement something and he used the Object Literal.) Personally, I prefer the Object Literal. It is easier to read, is better for maintainability and less prone to bugs.
