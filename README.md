# 前端学习笔记 📚

记录自己前端开发的学习过程，从 HTML 基础开始。

---

## 📂 学习路径

### [2026-06-29 — HTML 基础](HTML学习/2026-06-29/)

| 文件 | 学习内容 |
|------|----------|
| 01.新浪新闻-标题排版.html | 标题标签、段落标签 |
| 02.新浪新闻-标题样式1.html | 字体样式 |
| 02.新浪新闻-标题样式2.html | CSS 基础样式 |
| 03.新浪新闻-标题超链接3.html | 超链接标签 `<a>` |
| 04.新浪新闻-标题正文.html | 正文排版、图片标签 |
| 05.新浪新闻-页面布局.html | 页面整体布局 |
| HTML-表单标签.html | 表单标签：`<form>`、`<input>`、`<button>` 等 |

---

### [2026-06-30 — JavaScript 基础 + Vue 入门](HTML学习/206-6-30/)

---

## 一、JavaScript 引入方式

| 引入方式 | 写法 | 说明 |
|----------|------|------|
| **内部脚本** | `<script> ... </script>` | 在 HTML 文件中直接编写 JS 代码 |
| **外部脚本** | `<script src="js/demo.js"></script>` | 引入外部独立的 `.js` 文件，便于维护和复用 |

---

## 二、JavaScript 三种输出方式

| 方法 | 用途 | 示例 |
|------|------|------|
| `window.alert()` / `alert()` | 弹出警告框 | `alert("Hello JS")` |
| `document.write()` | 将内容写入 HTML 页面中 | `document.write("Hello JS")` |
| `console.log()` | 在浏览器控制台输出，常用于调试 | `console.log("Hello JS")` |

---

## 三、JavaScript 变量声明（var / let / const）

| 关键字 | 特点 | 示例 |
|--------|------|------|
| `var` | ① **作用域较大**，是全局变量；② **可以重复定义**，但后面的值会覆盖前面的，只保留最后一个值 | `var a = 10; a = "张三";` |
| `let` | ① **局部变量**，只在 `{}` 代码块内有效；② **不可重复定义**（同一作用域内） | `{ let x = 1; }` |
| `const` | **常量**，一旦赋值不能改变 | `const p1 = 3;` |

> **核心区别总结**：`var` 作用域大、可重复声明；`let` 块级作用域、不可重复声明；`const` 声明常量不可修改。

---

## 四、JavaScript 函数

### 4.1 两种定义方式

| 方式 | 语法 | 说明 |
|------|------|------|
| **方式一：命名函数** | `function add(a, b) { return a + b; }` | 标准函数定义 |
| **方式二：匿名函数 / 函数表达式** | `var add = function(a, b) { return a + b; }` | 将匿名函数赋值给一个变量 |

> 调用方式相同：`var result = add(10, 6);`

---

## 五、JavaScript 对象

### 5.1 Array（数组）

```js
// 创建数组
var arr = new Array(1, 2, 3, 4);  // 方式一：构造函数
var arr = [1, 2, 3, 4];           // 方式二：字面量（常用）

// 数组特点：长度可变、类型可变
arr[0] = 12;
arr[1] = "hello";   // 同一个数组可以存不同类型的数据
```

| 方法 | 作用 | 示例 |
|------|------|------|
| `forEach()` | 遍历数组中有值的元素（参数必须是函数） | `arr.forEach(function(e) { console.log(e); })` |
| **箭头函数** | forEach 的简化写法，去掉 `function` 加上 `=>` | `arr.forEach((e) => { console.log(e); })` |
| `push()` | 添加元素到数组尾部 | `arr.push(10, 29)` |
| `splice(起始索引, 删除个数)` | 删除元素，从哪开始删，删几个 | `arr.splice(2, 2)` |

### 5.2 String（字符串）

```js
var str = new String("Hello");  // 方式一
var str = "Hello";              // 方式二（常用）
```

| 方法 | 作用 | 示例 |
|------|------|------|
| `charAt(index)` | 获取指定位置索引的字符 | `str.charAt(2)` |
| `indexOf(str)` | 检索字符串首次出现的位置，未找到返回 -1 | `str.indexOf("lo")` |
| `trim()` | 去除字符串左右两侧空格 | `var s = str.trim();` |
| `substring(start, end)` | 截取字符串，**含头不含尾** | `s.substring(0, 5)` |

### 5.3 自定义对象

```js
var user = {
    name: "Tom",        // 属性
    age: 20,
    gender: "male",
    eat() {             // 方法
        alert("吃饭");
    }
};

// 访问属性和方法
alert(user.name);      // 输出：Tom
user.eat();             // 弹出：吃饭
```

### 5.4 JSON（JavaScript Object Notation）

> **定义**：通过 JavaScript 对象标记法书写的**文本**，多用于作为**数据载体**，在网络中进行数据传输。

| 方向 | 方法 | 说明 |
|------|------|------|
| JSON 字符串 → JS 对象 | `JSON.parse(jsonStr)` | 将 JSON 格式的字符串解析为 JS 对象 |
| JS 对象 → JSON 字符串 | `JSON.stringify(obj)` | 将 JS 对象序列化为 JSON 字符串 |

```js
var userStr = '{"name":"Tom","age":18,"addr":["北京","上海"]}';
var obj = JSON.parse(userStr);    // 字符串 → 对象
alert(obj.name);                   // 输出：Tom
alert(JSON.stringify(obj));        // 对象 → 字符串
```

---

## 六、BOM（Browser Object Model — 浏览器对象模型）

| API | 说明 |
|-----|------|
| `window.alert()` / `alert()` | 弹出警告对话框 |
| `confirm("提示文本")` | 弹出确认对话框，点击确定返回 `true`，取消返回 `false` |
| `setInterval(回调函数, 毫秒)` | **周期性定时器**，每隔指定时间反复执行某一函数 |
| `setTimeout(回调函数, 毫秒)` | **一次性定时器**，延迟指定时间后执行一次 |
| `location.href` | 获取当前完整 URL 或**设置新 URL 实现页面跳转** |

```js
// 周期性定时器——每 2 秒执行一次
var i = 0;
setInterval(() => {
    i++;
    console.log("定时器执行了" + i + "次");
}, 2000);

// 一次性定时器——3 秒后执行一次
setTimeout(() => {
    console.log("JS");
}, 3000);

// 页面跳转
location.href = "https://www.baidu.com";
```

---

## 七、DOM（Document Object Model — 文档对象模型）

> 用于获取和修改页面中的 HTML 元素。

| 方法 | 说明 | 返回值 |
|------|------|--------|
| `document.getElementById('id名')` | 按 **id** 获取元素 | 单个元素 |
| `document.getElementsByTagName('div')` | 按**标签名**获取元素 | HTML 集合（类数组） |
| `document.getElementsByClassName('类名')` | 按 **class 属性**获取元素 | HTML 集合（类数组） |
| `document.getElementsByName('name值')` | 按 **name 属性**获取元素 | HTML 集合（类数组） |

---

## 八、JavaScript 事件监听

### 两种事件绑定方式

| 方式 | 写法 | 说明 |
|------|------|------|
| **标签属性绑定** | `<input onclick="on()">` | 直接在 HTML 标签上通过 `onclick` 等属性绑定函数 |
| **DOM 属性绑定** | `document.getElementById("btn2").onclick = function() {...}` | 通过 JS 获取 DOM 元素后给其 `onclick` 属性赋值一个函数 |

```html
<!-- 方式一：标签属性绑定 -->
<input type="button" id="btn1" value="事件绑定1" onclick="on()">

<!-- 方式二：DOM 属性绑定 -->
<input type="button" id="btn2" value="事件绑定2">

<script>
    function on() {
        alert("按钮1被点击了");
    }

    document.getElementById("btn2").onclick = function() {
        alert("按钮2被点击了");
    };
</script>
```

---

## 九、Vue 快速入门

### 9.1 基本步骤

1. **引入 Vue.js**：`<script src="js/vue.js"></script>`
2. **创建 Vue 实例**：

```js
new Vue({
    el: "#app",        // Vue 接管的区域（CSS 选择器）
    data: {
        message: "Hello Vue"   // 数据
    }
});
```

3. **在 HTML 中使用**：

```html
<div id="app">
    <input type="text" v-model="message">
    {{message}}   <!-- 插值表达式，显示数据 -->
</div>
```

### 9.2 核心概念

| 概念 | 说明 |
|------|------|
| `el` | Vue 接管的 DOM 区域，值为 CSS 选择器 |
| `data` | Vue 的数据对象，页面中可响应式使用 |
| `{{ }}` | **插值表达式**，在页面中显示 data 中的数据 |
| `v-model` | **双向数据绑定**，视图和数据互相影响 |

---

## 十、Vue 常用指令

### 10.1 v-bind — 动态绑定属性

> 用于动态地为 HTML 标签的属性绑定一个 Vue 变量。

| 写法 | 示例 |
|------|------|
| 完整写法 | `<a v-bind:href="url">链接</a>` |
| **简写** | `<a :href="url">链接</a>` |

### 10.2 v-model — 双向数据绑定

> 在**表单元素**上创建双向数据绑定（视图 ↔ 数据）。

```html
<input type="text" v-model="url">
```

### 10.3 v-on — 事件绑定

> 为 HTML 标签绑定事件。

| 写法 | 示例 |
|------|------|
| 完整写法 | `<input v-on:click="handle()">` |
| **简写** | `<input @click="handle()">` |

> 事件处理函数写在 Vue 实例的 `methods` 属性中：

```js
new Vue({
    el: '#app',
    data: { ... },
    methods: {
        handle: function() {
            alert("你点我了一下");
        }
    }
});
```

### 10.4 v-if / v-else-if / v-else — 条件渲染

> 条件性地渲染某元素——判定为 `true` 时渲染，否则**不渲染（元素不生成到 DOM 中）**。

```html
<span v-if="age <= 35">年轻人(35及以下)</span>
<span v-else-if="age > 35 && age < 60">中年人(35-60)</span>
<span v-else>老年人(60及以上)</span>
```

### 10.5 v-for — 列表遍历

> 用于遍历数组或对象。

| 写法 | 说明 |
|------|------|
| `v-for="x in addrs"` | 遍历元素，`x` 为当前项 |
| `v-for="(x, index) in addrs"` | 遍历元素，`x` 为当前项，`index` 为索引 |

```html
<div v-for="x in addrs">{{x}}</div>
<div v-for="(x, index) in addrs">{{index + 1}} : {{x}}</div>
```

---

## 十一、Vue 生命周期

> Vue 的生命周期指的是 **Vue 对象从创建到销毁的过程**。  
> 每触发一个生命周期事件，会自动执行一个生命周期方法，这些方法也被称为**钩子方法（Hook）**。

| 状态 | 阶段周期 | 说明 |
|------|----------|------|
| `beforeCreate` | 创建前 | Vue 实例刚被创建，数据和事件还未初始化 |
| `created` | 创建后 | 实例创建完毕，data/methods 已可用，但 DOM 未挂载 |
| `beforeMount` | 挂载前 | 模板编译完成，即将挂载到 DOM |
| **`mounted`** | **挂载完成** | ⭐ **最重要**，DOM 挂载完毕，可以操作页面元素 |
| `beforeUpdate` | 更新前 | 数据变化，但 DOM 尚未重新渲染 |
| `updated` | 更新后 | 数据变化导致的 DOM 更新完成 |
| `beforeDestroy` | 销毁前 | 实例销毁前，仍可访问 data/methods |
| `destroyed` | 销毁后 | 实例完全销毁，所有事件监听和数据绑定被移除 |

---

## 📊 Vue 常用指令速查表

| 指令 | 简写 | 用途 |
|------|------|------|
| `v-bind:属性="变量"` | `:属性="变量"` | 动态绑定 HTML 属性 |
| `v-model="变量"` | — | 表单元素双向数据绑定 |
| `v-on:事件="函数"` | `@事件="函数"` | 绑定事件 |
| `v-if="条件"` | — | 条件渲染（true 渲染 / false 不渲染） |
| `v-else-if="条件"` | — | 条件分支 |
| `v-else` | — | 条件 else |
| `v-for="项 in 数组"` | — | 遍历数组 |

---

## 🗓️ 学习进度

```
✅ 2026-06-29  HTML 基础（新浪新闻排版 + 表单标签）
✅ 2026-06-30  JavaScript 基础（变量/函数/对象/BOM/DOM/事件） + Vue 入门（指令/生命周期）
⬜ 待更新...
```

---

> 🚀 每天进步一点点！
