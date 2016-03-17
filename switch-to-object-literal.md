# Switch to Object Literal

The ol' `switch` statement. Other languages love it, but I'm not a fan of it in JavaScript. I prefer Objects. Objects are more flexible, easier to read and if you're a JavaScript developer, you're already familiar with Objects. Plus, the more complicated your logic gets, the better performant an Object literal will be. Let's look at some simple comparisons.

## The `switch`

Your typical `switch` statement looks like this:

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