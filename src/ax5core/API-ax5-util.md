# Type

## ax5.util.getType
Return argument object type
```js
<script type="text/javascript">
    ax5.util.getType(1); // "number"
    ax5.util.getType("1"); // "string"
    ax5.util.getType([0, 1, 2]); // "array"
    ax5.util.getType({a: 1}); // "object"
    ax5.util.getType(function () {}); // "function"
    ax5.util.getType(document.querySelectorAll("div")); // "nodelist"
    ax5.util.getType(document.createDocumentFragment()); // "fragment"
</script>
```
Javascript object type name is not clear. so util.getType method very useful.

---

## ax5.util.is(Type)
Return argument object type is [type] result.
```js
<script type="text/javascript">
    // return is window.
    ax5.util.isWindow(window);
 
    // return is element.
    ax5.util.isElement(document.getElementById("#ax5-util-is-type"));
 
    // return is Object.
    ax5.util.isObject({});
 
    // return is Array.
    ax5.util.isArray([]);
 
    // return is Functon.
    ax5.util.isFunction(new Function);
 
    // return is String.
    ax5.util.isString('');
 
    // return is Number.
    ax5.util.isNumber(1);
 
    // return is nodeList.
    ax5.util.isNodelist(document.querySelectorAll(".content"));
 
    // return is undefined.
    ax5.util.isUndefined();
 
    // return is undefined|''|null.
    ax5.util.isNothing();
</script>
```

---


# Object
## ax5.util.filter
The first item is delivered to the second argument of the filter function. The second argument is an anonymous function, the result is True, the items will be collected.
```js
<script type="text/javascript">
    var result, aarray = [5, 4, 3, 2, 1];
 
    result = ax5.util.filter(aarray, function () {
        return this % 2;
    });
    console.log(result);
 
    var list = [
        {isdel: 1, name: "ax5-1"}, {name: "ax5-2"}, {
            isdel: 1,
            name: "ax5-3"
        }, {name: "ax5-4"}, {name: "ax5-5"}
    ];
    result = ax5.util.filter(list, function () {
        return (this.isdel != 1);
    });
    console.log(JSON.stringify(result));
</script>
```

---

## ax5.util.search
It returns the first item of the result of the function is True.
```js
<script type="text/javascript">
    var a = ["A", "X", "5"];
    var idx = ax5.util.search(a, function () {
        return this == "X";
    });
    console.log(a[idx]);
    // X
 
    console.log(a[
        ax5.util.search(a, function (idx) {
            return idx == 2;
        })
        ]);
    // 5
 
    var b = {a: "AX5-0", x: "AX5-1", 5: "AX5-2"};
    console.log(b[
        ax5.util.search(b, function (k, v) {
            return k == "x";
        })
        ]);
    // AX5-1
</script>
```
---

## ax5.util.map
`"map"` creating a new array features set into an array or object. In the example I've created a simple object array as a numeric array.
```js
<script type="text/javascript">
    var a = [1, 2, 3, 4, 5];
    a = ax5.util.map(a, function () {
        return {id: this};
    });
    console.log(ax5.util.toJson(a));
 
    console.log(
        ax5.util.map({a: 1, b: 2}, function (k, v) {
            return {id: k, value: v};
        })
    );
</script>
```
---

## ax5.util.merge
`"array like"` the type of object `"concat"`.
```js
<script type="text/javascript">
    var a = [1, 2, 3], b = [7, 8, 9];
    console.log(ax5.util.merge(a, b));
</script>
```
---

## ax5.util.reduce
As a result of the process performed in the operation from the left to the right of the array it will be reflected to the left side item. It returns the final value of the item.
```js
<script type="text/javascript">
    var aarray = [5, 4, 3, 2, 1], result;
    console.log(ax5.util.reduce(aarray, function (p, n) {
        return p * n;
    }));
    // 120
 
    console.log(ax5.util.reduce({a: 1, b: 2}, function (p, n) {
        // If the "Object" is the first "p" value is "undefined".
        return parseInt(p | 0) + parseInt(n);
    }));
    // 3
</script>
```
---

## ax5.util.reduceRight
Same as "reduce" but with a different direction.
```js
<script type="text/javascript">
    var aarray = [5, 4, 3, 2, 1];
    console.log(ax5.util.reduceRight(aarray, function (p, n) {
        return p - n;
    }));
    // -13
</script>
```
---

## ax5.util.first
It returns the first element in the Array, or Object. However, it is faster to use Array in the "Array [0]" rather than using the "first" method.
```js
<script type="text/javascript">
    var _arr = ["ax5", "axisj"];
    var _obj = {k: "ax5", z: "axisj"};
 
    console.log(ax5.util.first(_arr));
    // ax5
 
    console.log(ax5.util.toJson(ax5.util.first(_obj)));
    // {"k": "ax5"}
</script>
```
---

## ax5.util.last
It returns the last element in the Array, or Object.
```js
<script type="text/javascript">
    var _arr = ["ax5", "axisj"];
    var _obj = {k: "ax5", z: "axisj"};
 
    console.log(ax5.util.last(_arr));
    // axisj
 
    console.log(ax5.util.toJson(ax5.util.last(_obj)));
    // {"z": "axisj"}
</script>
```
---

# String

## ax5.util.left
Returns. Since the beginning of the string to the index, up to a certain character in a string from the beginning of the string.
```js
<script type="text/javascript">
    console.log(ax5.util.left("abcd.efd", 3));
    // abc
    console.log(ax5.util.left("abcd.efd", "."));
    // abcd
</script>
```
---

## ax5.util.right
Returns. Up from the end of the string index, up to a certain character in a string from the end of the string
```js
<script type="text/javascript">
    console.log(ax5.util.right("abcd.efd", 3));
    // efd
    console.log(ax5.util.right("abcd.efd", "."));
    // efd
</script>
```
---

## ax5.util.camelCase
It converts a string to "Camel Case". "a-b", "aB" will be the "aB".
```js
<script type="text/javascript">
    console.log(ax5.util.camelCase("inner-width"));
    console.log(ax5.util.camelCase("innerWidth"));
    // innerWidth
    console.log(ax5.util.camelCase("camelCase"));
    // camelCase
    console.log(ax5.util.camelCase("aBc"));
    // aBc
</script>
```
---

## ax5.util.snakeCase
It converts a string to "Snake Case". "aB" will be the "a-b".
```js
<script type="text/javascript">
    console.log(ax5.util.snakeCase("inner-width"));
    // inner-width
    console.log(ax5.util.snakeCase("camelCase"));
    // camel-case
    console.log(ax5.util.snakeCase("aBc"));
    // a-bc
</script>
```
---

# Number

## ax5.util.number
When the number covers the development, often it requires multiple steps. The syntax is very complex and it is difficult to maintain. "ax5.util.number" command to convert a number that were resolved by passing a JSON format.
```js
<script type="text/javascript">
    console.log('round(1) : ' + ax5.util.number(123456789.678, {round: 1}));
    // round(1) : 123456789.7
 
    console.log('round(1) money() : '
        + ax5.util.number(123456789.678, {round: 1, money: true}));
    // round(1) money() : 123,456,789.7
 
    console.log('round(2) byte() : '
        + ax5.util.number(123456789.678, {round: 2, byte: true}));
    // round(2) byte() : 117.7MB
 
    console.log('abs() round(2) money() : '
        + ax5.util.number(-123456789.678, {abs: true, round: 2, money: true}));
    // abs() round(2) money() : 123,456,789.68
 
    console.log('abs() round(2) money() : '
        + ax5.util.number("A-1234~~56789.8~888PX", {abs: true, round: 2, money: true}));
    // abs() round(2) money() : 123,456,789.89
</script>
```
---

# Misc.
## ax5.util.param
The parameter values may in some cases be the "Object" or "String". At this time, useing the "param", it can be the same as verifying the parameter value.
```js
<script type="text/javascript">
    console.log(ax5.util.param({a: 1, b: '123\'"2&'}, "param"));
    // a=1&b=123%27%222%26
    console.log(ax5.util.param("a=1&b=12'\"32", "param"));
    //a=1&b=12'"32
    console.log(ax5.util.toJson(util.param("a=1&b=1232")));
    // {"a": "1", "b": "1232"}
</script>
```
---

## ax5.util.parseJson
parsing a little more than the less sensitive the JSON syntax "JSON.parse".
```js
<script type="text/javascript">
    console.log(ax5.util.toJson(ax5.util.parseJson("[{'a':'99'},'2','3']")[0]));
    // {"a": "99"}
    console.log(ax5.util.parseJson("{a:1}").a);
    // 1
    console.log(ax5.util.toJson(ax5.util.parseJson("{'a':1, 'b':function(){return 1;}}", false)));
    // {"error": 500, "msg": "syntax error"}
    console.log(ax5.util.toJson(ax5.util.parseJson("{'a':1, 'b':function(){return 1;}}", true)));
    // {"a": 1, "b": "{Function}"}
</script>
```
---

## ax5.util.toJson
```js
<script type="text/javascript">
    console.log(ax5.util.toJson(1));
    // 1
    console.log(ax5.util.toJson("A"));
    // "A"
    console.log(ax5.util.toJson([1, 2, 3, 'A']));
    // [1,2,3,"A"]
    console.log(ax5.util.toJson({a: 'a', x: 'x'}));
    // {"a": "a", "x": "x"}
    console.log(ax5.util.toJson([1, {a: 'a', x: 'x'}]));
    // [1,{"a": "a", "x": "x"}]
    console.log(ax5.util.toJson({a: 'a', x: 'x', list: [1, 2, 3]}));
    // {"a": "a", "x": "x", "list": [1,2,3]}
    console.log(ax5.util.toJson(function () {}));
    // "{Function}"
</script>
```
---

## ax5.util.alert
```js
<script type="text/javascript">
    ax5.util.alert({a: 1, b: 2});
</script>
```
--- 
## ax5.util.toArray
"nodelist" or on the Array Like such "arguments", has properties such as "length", but you can not use functions defined in Array.prototype. With "toArray" because it is easy to convert an array.
```js
<script type="text/javascript">
    function something() {
        var arr = ax5.util.toArray(arguments);
        console.log(ax5.util.toJson(arr));
    }
    something("A", "X", "I", "S", "J");
</script>
```
---

## ax5.getCookie / setCookie
```js
<script type="text/javascript">
    ax5.util.setCookie("ax5-cookie", "abcde");
    ax5.util.setCookie("ax5-cookie-path", "abcde", 2, {path: "/"});
    console.log(ax5.util.getCookie("ax5-cookie"));
    // abcde
    console.log(ax5.util.getCookie("ax5-cookie-path"));
    // abcde
</script>
```