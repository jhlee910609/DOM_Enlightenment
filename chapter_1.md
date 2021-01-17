## Chapter 1

### 1.1. 문서 객체 모델(DOM)은 Javascript Node 객체의 트리형 계층 구조이다.

> 우리가 HTML 문서를 작성할 때, 다른 HTML 콘텐츠 안에 HTML 콘텐츠를 캡슐화한다. 이렇게 HTML 문서를 작성함으로써 우리는 트리형태로 표현할 수 있는 계층 구조를 만들 수 있다. 이런 계층구조나 캡슐화 시스캠은 HTML 문서 내에서 들여쓰기(indenting)으로 자주 표현된다. HTML 문서가 로딩될 때, 브라우저(Chrome, safari, firefox etc..)는 이 계층에 간섭하고, 구문분석하여 캡슐화된 마크업 방식을 시뮬레이션하는 '노드 객체 트리를' 만든다.

```html
<!DOCTYPE html>
    <html lang="ko">
        <head>
            <title>HTML</title>
        </head>
        <body>
            <!-- 추가하고자 하는 콘텐츠 코드 작성 위치 -->
        </body>
    </html>
```



### 1.2. Node Object Types(노드 객체 타입들)

> 아래는 보편적으로 자주 사용하는 노드들이다.

- `DOCUEMTN_NODE` ex) `window.document`
- `ELEMENT_NODE` ex) `<body>, <a>, <p>, <script>, <style>, <html>, <h1>`
- `ATTRIBUTE_NODE` ex) `class='funEdges'`
- `TEXT_NODE` 
- `DOCUMENT_FRAGMENT_NODE` ex) `document.createDocumentFragment()`
- `DOCUMENT_TYPE_NODE` ex) `<!DOCTYPE html>`

