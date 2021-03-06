# Dynamic JavaScript Module Import and Function Execute

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

- Browse or debug the `index.html` file from a server (e.g. IntelliJ Chrome debug). 
- Click buttons on its page.

#### (Sidebar: A Zero-Config Server)
Note that opening index.html directly from  the file system suffers a CORS violation during imports unless you have 
a plugin that bypasses CORS. Here's a quick zero-configuration approach:

1. Ensure install: `yarn install`
1. Start: `http-server <project directory>`
1. Open browser to http://localhost:8080 

### Invoke a JavaScript function by its string Name

- The `index.html` illustrates dynamically loading a JavaScript module via 
a string that names its namespace file. 

- This demo calls functions by their string names, assuming the function names
are known ahead of time.

- Similarly, the demo assumes parameters have known signatures.

- Dynamic reflection of function names would be a subject of another demo.

### Invoke a function by its string name, from a loaded module

In JavaScript, a loaded module is just another JavaScript object. 
We normally invoke a function of that object by using the function name as a key, like this:

```javascript
    module.aFunc(arg);
```

We could use the function name string for the key instead:

```javascript
    module["aFunc"](arg);
```

Note that a function exported as default would be invoked as key "default":

```javascript
    module["default"](arg);
```

### So ...

This demo sequentially executes three functions by string name from three modules. We load each
dynamically at execution time by path name. We assume a given set of three 
signatures exists in each module. The implementations of each function varies per-module.

## References

- [Javascript Info](https://javascript.info/modules-dynamic-imports) 
- [StackOverflow](https://stackoverflow.com/questions/359788/how-to-execute-a-javascript-function-when-i-have-its-name-as-a-string)

-Lou Mauget, 2020-02-15

