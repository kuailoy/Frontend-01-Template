# 每周总结可以写在这里

## Range API

```javascript
var range = new Range();
range.setStart(element, 9);
range.setEnd(element, 4);
var range = document.getSelection().getRangeAt(0);

var fragment = range.extractContents();
range.insertNode(docuemnt.createTextNode('aaaa'));
```

- range.setStartBefore
- range.setEndBefore
- range.setStartAfter
- range.setEndAfter
- range.selectNode
- range.selectNodeContent
