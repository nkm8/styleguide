# Branding Brand JavaScript style guide. 

Focus on the first 3 headings.

## 1. Consistency
Keep things consistent. Don't vary your indent, spacing, braces, etc... across lines, files and project.

## 2. Readability
Make sure your code is easy on the eyes. If you're supposedly showing someone what your code does, line by line, make sure they aren't struggling to follow it.

## 3. Indent
2 spaces.

### Wrong
```javascript
function foo() {
    var a = j;
    doThing(function() {
        thingy();
    });
}
```

### Very Wrong
```javascript
function foo() {
   var a = j;
            doThing(function() {
          thingy();
            });
   }
```

### Right
```javascript
function foo() {
  var a = j;
  doThing(function() {
    thingy();
  });
}
```

## 4. Spacing 
Give operators, keywords and braces room to breathe.

### Wrong
```javascript
//a cramped comment
var a=5;
var b=c+d;
var g='Hello'+'world';
var e={foo:'bar',zoo:'zar'};

var f=function(arg1,arg2);
function f(arg1,arg2) {}

for(i=0;i<=4;i++) {}
for( i=0; i<=4; i++ ) {}
for( i=0 ; i<=4 ; i++ ) {}

```

### Very Wrong
```javascript
//a cramped comment
var a=5;
var b = c+d;
var g= 'Hello' +  'world';
var e={foo:'bar'  ,zoo : 'zar' };

var f= function(arg1, arg2) ;
function f ( arg1,arg2) {}

for( i=0;i<=4;i++) {}
for( i=0; i<=4; i++ ) {}
for( i=0 ; i<=4 ; i++ ) {}

```

### Right
```javascript
// the space in front of this comment is easy on the eyes
var a = 5;
var b = c + d;
var g = 'Hello' + 'World';
var e = { foo: 'bar', zoo: 'zar' };

var f = function (arg1, arg2);
// OR
var f = function(arg1, arg2);

function f(arg1, arg2) {}
// OR
function f (arg1, arg2) {}

for (i = 0; i <= 4; i++) {}
// '++' and '--' operators are OK to place flush to the variable
```

## 5. Strings
Use single quotes.

### Wrong
```javascript
var s = "an \"ugly\" string";
```

### Very Wrong
```javascript
var s = "a string in doublequotes"
  , k = 'a string in singlequotes'
```

### Right
```javascript
var s = 'a "pretty" string';
```

## 6. Variable Declarations.
 - Keep declarations grouped semantically.
 - Avoid too many vars
 - Use commas in front of line for **simple** declarations.

### Ugly
```javascript
// var soup
var a = 5;
var b = 6;
var c = { foo: 'bar' };

// comma hell
var a = 5
  , b = (function () {
    return {
      foo : 'bar'
    }
  })()
  , c = 6;
  
// semantic mess
var mom = person()
  , dad = person()
  , somethingTotallyUnrelated = foobar(1, 2, 3)
  , son = person()
  , daughter = person();
```

### Pretty
```javascript
var a = 5
  , b = 6
  , c = { foo: 'bar' };

var a = 5
  , c = 6;
  
var b = (function () {
  return {
    foo : 'bar'
  }
})();

var mom = person()
  , dad = person()
  , son = person()
  , daughter = person();
  
var somethingTotallyUnrelated = foobar(1, 2, 3);
```

## 7. Object Variables
Commas at the end of line to preserve indent.

### Wrong
```javascript
var a = {
  foo : 'bar'
  , bar : 'foo'
  , zoo : {
    goo : 'gar'
    , too : 'tar'
  }
};
```

### Right
```javascript
var a = {
  foo : 'bar',
  bar : 'foo',
  zoo : {
    goo : 'gar',
    too : 'tar'
  }
};
```

## 8. Conditionals
No new lines before `else` and `else if`

### Wrong
```javascript
if (foo === bar) {
  doThing();
}
else if (thing === widget) {
  doAnotherThing();
}
else {
  blah();
}
```

### Right
```javascript
if (foo === bar) {
  doThing();
} else if (thing === widget) {
  doAnotherThing();
} else {
  blah();
}
```

## 9. Switch
Give the code some room to breathe.

### Wrong
```javascript
switch (foo) {
  case 'bar': doThing(); doAnotherThing(); frobWidgets(widget1, widget2); break;
  case 'widget': doADifferentThing(); doAnotherDifferentThing(); frobExtraWidgets(widget3, widget4); break;
  default: frobDefaultWidgets(); break;
}
```

### Right
```javascript
switch (foo) {
  case 'bar':
    doThing();
    doAnotherThing();
    frobWidgets(widget1, widget2);
    break;
  case 'widget':
    doADifferentThing();
    doAnotherDifferentThing();
    frobExtraWidgets(widget3, widget4);
    break;
  default:
    frobDefaultWidgets();
    break;
}
```

## 10. Semicolons 1
Use them. Unless you know when you **have** to use them.

### Wrong
```javascript
var g = 6
var a = 7

(function() {
  return {
    foo : 'bar'
  }
})()

frob(1, 2, 3)
```

### Right
```javascript
var g = 6;
var a = 7;

(function() {
  return {
    foo : 'bar'
  };
})();

frob(1, 2, 3);
```

## 10.1 More Semicolons

### Wrong
```javascript
var g = function () {
  return true
}

function f () {
  return true
};

for (var i = 0; i < 10; i++) {
  f();
};
```

### Right
```javascript
var g = function () {
  return true;
};

function f () {
  return true;
}

for (var i = 0; i < 10; i++) {
  f();
}
```

## 11. Line Breaks
Keep your lines **under** 100 - 130 characters.

### Wrong
```javascript
if ((thingExists(thing1) || thingExists(thing2)) && (thingExists(thing2) && thingExists(thing3)) || (thingExists(thing4) && thingExists(thing5))) {
  doStuff();
}

var g = isDone(something + anotherThing) ? someValue + someFunction(arg1, arg2) : anotherValue + anotherFunction(arg3, arg4));
```

### Right
```javascript
if ((thingExists(thing1) || thingExists(thing2)) 
  && (thingExists(thing2) && thingExists(thing3)) 
  || (thingExists(thing4) && thingExists(thing5))) {

  doStuff();
}

var g = isDone(something + anotherThing) 
  ? someValue + someFunction(arg1, arg2) 
  : anotherValue + anotherFunction(arg3, arg4));
```