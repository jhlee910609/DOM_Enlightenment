## Chapter 8 - DocumentFragment Nodes

### 8.1. DocumentFragment 객체 개요

> `DocumentFragment` 노드의 생성과 사용은 live DOM 트리 외부에 있는 가벼운 document DOM을 제공한다. DocumentFragment를 메모리 상에서만 살아 있고, DocumentFragment의 자식 노드들은 메모리 상에서 쉽게 조작 가능하며, live DOM에 부착 가능한 live DOM 트리처럼 동작하는 빈 문서 템플릿으로 생각할 수 있습니다.



### 8.2. DocumentFragments 생성을 위한 createDocumentFragment() 사용하기

- 어렵지 않다. 아래 코드를 따라하면 된다.

```html
<!DOCTYPE html>
<html lang="en">
<body>
<script>
// DocumentFragments 생성
var docFrag = document.createDocumentFragment();
["blue", "green", "red", "blue", "pink"].forEach(function(e) {
    var li = document.createElement("li");
    li.textContent = e;
    docFrag.appendChild(li); // append
});
console.log(docFrag.textContent); //logs bluegreenredbluepink
</script>
    </body>
    </html>
```

- node 구조를 만들기 위해 메모리 상에서 document fragment를 사용하는 것은, live node 구조에 document fragment를 주입할 때 매우 효과적입니다.
- document fragment를 사용하는 것은 단순히 메모리에 <div> 태그를 만들어 작업하는 것에 비해 어떤 이점이 있는지 궁금할 수 있습니다. document fragment를 사용하는 것과 <div>를 사용하는 것의 차이점은 아래와 같습니다.
  - document fragment는 <body>와 <html>를 제외하고 모든 종류의 node를 담을 수 있습니다.
  - document fragment 자체는 실제 DOM에 추가되지 않습니다. node의 내용은 다음과 같습니다. 이는 요소 자체가 추가 작업의 일부인 요소 노드를 추가하는 것과 대조적입니다.
  - document fragment가 DOM에 추가되면 document fragment에서 추가된 위치로 전송됩니다. 더 이상 사용자가 만든 메모리 상에 있지 않습니다. 노드를 잠깐 포함하는데만 사용된 다음 live DOM으로 이동하는 element node는 그렇지 않습니다.

### 8.3. DocumentFragment를 Live DOM에 붙히기

- document fragment 인자를 `appendChild()`와 `insertBefore()` node 메서드로 넘길 때, document fragment의 자식 node들은 메소드가 불려진 DOM node의 자식 노드가 됩니다. 아래 코드와 같이, document fragment를 만들고, 몇 개의 <li> 들을 document fragment에 붙히고, 이 새로운 element node들을 `appendChild()`를 활용하여 live DOM 트리에 붙힙니다.

```html
<!DOCTYPE html>
<html lang="en">
<body>
<ul></ul>
<script>
var ulElm = document.queryselector('ul');
var docFrag = document.createDocumentFragment();
["blue", "green", "red", "blue", "pink"].forEach(function(e) {
    var li = document.createElement("li");
    li.textContent = e;
    docFrag.appendChild(li);
});
Live code
 96 | Chapter 8: DocumentFragment Nodes
ulElm.appendChild(docFrag);
//logs <ul><li>blue</li><li>green</li><li>red</li><li>blue</li><li>pink</li></ul>
    console.log(document.body.innerHTML);
    </script>
    </body>
    </html>
```



### 8.5. Cloning 함으로써 Node들을 담고 있는 Fragments를 메모리 상에서 남기기

- document fragment를 추가할 때, fragment에 포함된 노드들은 fragment로부터 추가하고자 하는 구조로 이동하게 됩니다. fragment의 콘텐츠들을 메모리 상에 남기기 위해서, 간단하게 `cloneNode()`를 사용할 수 있고, 추가할 때, document fragment를 복제할 수 있습니다. 아래 코드를 보면, document fragment로 부터 전송하는 대신, document fragment 노드 안에 <li>태그 들을 복제하여 메모리상에 유지할 수 있도록 <li>를 복제하였습니다.

```html
<!DOCTYPE html>
<html lang="en">
<body>
<ul></ul>
<script>
//create ul element and document fragment
var ulElm = document.querySelector('ul');
var docFrag = document.createDocumentFragment();
//append li's to document fragment
["blue", "green", "red", "blue", "pink"].forEach(function(e) {
    var li = document.createElement("li");
    li.textContent = e;
    docFrag.appendChild(li);
});
//append cloned document fragment to ul in live DOM
ulElm.appendChild(docFrag.cloneNode(true));
//logs <li>blue</li><li>green</li><li>red</li><li>blue</li><li>pink</li>
console.log(document.querySelector('ul').innerHTML);
//logs [li,li,li,li,li]
console.log(docFrag.childNodes);
</script>
</body>
</html>
```



















