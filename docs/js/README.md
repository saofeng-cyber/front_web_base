# 这里是javaScript页面

## JSON.stringify的正确使用

- JSON 通常用于与服务端交换数据。
- 在向服务器发送数据时一般是字符串。
- 我们可以使用 `JSON.stringify()` 方法将 JavaScript 对象转换为字符串。

### 语法

```js
JSON.stringify(value[, replacer[, space]])
```

>[!note]
参数说明

- `value` 必需， 要转换的 JavaScript 值（通常为对象或数组）。
- `replacer` 可选。用于转换结果的函数或数组。

- 如果 `replacer` 为函数，则 `JSON.stringify` 将调用该函数，并传入每个成员的键和值。使用返回值而不是原始值。如果此函数返回 `undefined`，则排除成员。根对象的键是一个空字符串：""。如果 `replacer` 是一个数组，则仅转换该数组中具有键值的成员。成员的转换顺序与键在数组中的顺序一样。当 `value` 参数也为数组时，将忽略 `replacer` 数组。
- `space`: 可选，文本添加缩进、空格和换行符，如果 `space` 是一个数字，则返回值文本在每个级别缩进指定数目的空格，如果 `space` 大于 10，则文本缩进 10 个空格。`space` 也可以使用非数字，如：`\t`。

### 用法详解

```js
        const obj = {
            name: '骚风',
            age: 24,
            gender: 1
        }
        const res = JSON.stringify(obj) // {"name":"骚风","age":24,"gender":1}
        const res = JSON.stringify(obj, (key, value) => {
            if (typeof value == "string") {
                return undefined
            } else {
                return value
            }
        }) // {"age":24,"gender":1}
        const res = JSON.stringify(obj, ['age'], '**') // {**"age": 24}
```
