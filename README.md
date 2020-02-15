# Dynamic Module Import

### Dynamically load a JavaScript module file

Here, we late-bind an ES6 module via an `import` construct that looks like a 
function. It actually is a special construct, somewhat like `super`. It
returns a promise whose `then` function receives the module object.

``` javascript
    const modulePath = prompt("Specify a module path:");
    
    import(modulePath)
      .then(obj => /* use module object*/)
      .catch(err => /* Not found or other error */)
```

In this demo, we use `async` / `await` from an html `<script>` container 
that is an implicit `async` function.

``` html
    <script>
        ...
        const module = await import(namespace);
        ...
    </script>
```

### Run the demo
Click or debug the index.html file in a browser or linked debug session. 
Click on the buttons on its page.

### Invoke a JavaScript function by its string Name

The `index.html` illustrates dynamically loading a JavaScript module using 
a string that names a namespace file. 

This demo calls functions by their string names, assuming the function names
are known ahead of time.

Similarly, the demo assumes parameter known signatures.

Dynamic reflection of function names would be a subject of another demo.

### Invoke a function by its string name, from a loaded module

In JavaScript, a loaded module is a JavaScript object. We normally invoke a function of
that object by using the function name as a key, like this:

```javascript
    module.aFunc(arg);
```

We could use the function name string for the key instead:

```javascript
    module["aFunc"](arg);
```

Note that a function exported as default would be invoked thus:

```javascript
    module["default"](arg);
```

### So ...
This demo sequentially executes three functions by string name from three modules, each
loaded dynamically at execution time by path name. We assumes the same set of three 
signatures exists in each module. The implementations of each functino varies per-module.

-Lou Mauget, 2020-02-15

