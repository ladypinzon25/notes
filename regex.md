# Regex

## Basics
### Create
```javascript
const regex = /String to search/;
```

## Methods
### Test
```javascript
const str = 'Here we have cats.';
const regex = /cats/;
console.log(regex.test(str));
// true
```

### Match
Matches a string with a regular expression, and returns an array containing the results of that search.
```javascript
const str = 'We are going to extract a cat from here.';
const regex = /cat/;
console.log(str.match(regex));
// [ 'cat' ]
```


## Flags
### Not-sensitive case ```i``` 
```javascript
const str = 'Mr. Cat is a feline.';
const regex = /cat/i;
console.log(regex.test(str));
// true
```

### Global
```javascript
const str = 'We are going to extract two animals, the cat and Mr. Cat';
const regex = /cat/ig; // We are using i and g flags
console.log(str.match(regex));
// [ 'cat', 'Cat' ]
```


## Operators
### OR ```|```
```javascript
const strings = [
  'Here are cats.',
  'Here are dogs.',
  'Here are not animals.'
];
const regex = /cats|dogs/;
console.log(strings.map(s => regex.test(s)));
// [ true, true, false ]
```

### Wildcard ```.```
```javascript
const str = 'Here is a cat and car.';
const regex = /ca./;
console.log(regex.test(str));
// true
``` 

### Multiple possibilities ```[]``` 
```javascript
const str = 'Michin, Misifus, Lulu';
const regex = /[iu]/g; // It will select all occurrences of i or u
console.log(str.match(regex));
// [ 'i', 'i', 'i', 'i', 'u', 'u', 'u' ]
```
```javascript
const str = 'Here is a cat, a car, a can and a cab.';
const regex = /ca[trn]/g;
console.log(str.match(regex));
// [ 'cat', 'car', 'can' ]
```

### Ranges ```[a - b]```
```javascript
const str = 'Here we have numbers(1,2,3,4,5) and letters.';
const regex = /[1-5]/g; // We could use [a-z] too. To use both, use:[a-z1-5] 
console.log(str.match(regex));
// [ '1', '2', '3', '4', '5' ]
```

### Negative match ```[^...]```
```javascript
const str = 'Dog 1 and cat 2';
const regex = /[^1-5aeiou]/ig; // Everything that is not a number from 1 to 5 nor a vowel.
console.log(str.match(regex));
// [ 'D', 'g', ' ', ' ', 'n', 'd', ' ', 'c', 't', ' ' ]
```

### Zero or more times ```*```
```javascript
const strings = [
  'It is goooooooal!',
  'It is gun.',
  'It is a cat.'
];
const regex = /go*/;
console.log(strings.map(s => regex.test(s)));
// [ true, true, false ]
```

### One or more times ```+```
```javascript
const strings = [
  'It is goooooooal!',
  'It is gun.'
];
const regex = /go*/;
console.log(strings.map(s => regex.test(s)));
// [ true, false ]
```

### Lazy matching ```?```
As default regex is greedy, which that it returns the longest substring that satisfies the regex. On the other hand, the
lazy matching is going to return the shortest substring.
```javascript
const str = 'Michin';
const regex = [
  /m.*i/i,
  /m.*?i/i
];
console.log(regex.map(r => str.match(r)).join('\n'));
// Michi
// Mi
```

### Search at the beginning ```^```
```javascript
const strings = [
  'Michin is at the beginning',
  'Now at the end is Michin'
];
const regex = /^michin/i;
console.log(strings.map(s => regex.test(s)));
// [ true, false ]
```

### Search at the ending ```$```
```javascript
const strings = [
  'Michin is at the beginning',
  'Now at the end is Michin'
];
const regex = /michin$/i;
console.log(strings.map(s => regex.test(s)));
// [ false, true ]
```

### Search for any number, letter or _ ```\w```
```javascript
const str= 'a2B1? c3_a2.';
const regex = /\w/g;
console.log(str.match(regex));
// [ 'a', '2', 'B', '1', 'c', '3', '_', 'a', '2' ]
```
