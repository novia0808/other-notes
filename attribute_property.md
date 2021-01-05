## Attribute(特性) 与 Property(屬性) 區別

1.  attribute 特性由 HTML 定義，所有出現在 HTML 標籤內的描述節點都是 attribute 特性

   注：attribute 特性的類型總是 String 字符串類型

2. property 屬性屬於 DOM 對象，DOM 實質就是 JavaScript 中的對象。property 屬性可以是任意類型（對於自定義屬性）。而對於 DOM 原始屬性，返回一律都是 String 字符串類型。



HTML5 定義的 data 屬性，獲取的也是字符串。

-

1. 非自定義（固有）的 attribute 特性 與 property 有 1:1 映射關係，比如：id, class, title 等。
2. 通過 property 屬性進行設置或獲取 class 時，需要使用 ‘className’。（因為 js 中 class 是關鍵字）
3. 非自定義（固有）的property（attribute）改變的時候，其對應的attribute（property）在多數情況下也會改變。
4. 當對應的 property 改變的時候，attribute 特性的 value 值一直為默認值，不會隨之改變。

在 JS 中 推薦使用 property 屬性，因為這個屬性相對於 attribute 更快，更簡便。



例子：

```html
<input id="the-input" type="typo" value="Name:" /> // 頁面加載後, 在 input 中輸入 "Jack"
//type="typo" 並不是 input 支持的類型
```

```js
// attribute still remains the original value
input.getAttribute('id') // the-input
input.getAttribute('type') // typo
input.getAttribute('value') // Name:

// property is a different story
input.id // the-input
input.type //  text
input.value // Jack
```

如上所示：attribute 會始終保持 html 代碼中的初始值，而 property 是有可能變化的。

+ `attribute` 傾向於 不可變更的
+ `property`傾向於 在其生命週期中是可變的

--

attribute 可以自定義 | property 不可以自定義

```html
<input value="customInput" customeAttr="custome attribute value" />
```

```js
input.getAttribute('customAttr') // custome attribute value
input.customAttr // undefined
```

**attribute（特性）**: 是赋予某个事物的特质。
**property（属性）**，是早已存在的不需要外界赋予的特质。





reference: 

ssthouse
https://juejin.cn/post/6844903712721387534
来源：掘金

[译]HTML attribute与DOM property之间的区别？
https://segmentfault.com/a/1190000008781121

















