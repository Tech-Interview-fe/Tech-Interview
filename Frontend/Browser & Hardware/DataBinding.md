### 데이터 바인딩에 대해 설명해주세요.

화면상에 보여지는 데이터(view)와  브라우저 메모리상에 있는 데이터(Model)를  묶어서 (binding) 서로 간의 데이터를 동기화하는 것을 의미합니다. 

자바스크립트 웹 애플리케이션의 복잡도가 증가하면서 브라우저의 메모리에 있는 여러개의 자바스크립트 객체와 화면에 있는 데이터를 일치시키기가 매우 어려워졌습니다. 그래서 이러한 어려운 작업을 쉽게 해주는 것이 데이터 바인딩 개념이라고 볼 수 있습니다. 따라서 정확히는 “두 데이터 혹은 정보의 소스를 모두 일치시키는 기법. 즉 화면에 보이는 데이터와 브라우저 메모리에 있는 데이터를 일치시키는 기법”을 의미합니다.

대다수의 자바스크립트 프레임워크가 단방향 데이터 바인딩을 지원하는 반면 AngularJS는 양방향 데이터 바인딩을 제공합니다.

### 단반향 바인딩과 양방향 바인딩에 대해 설명해주세요.

컴포넌트 내에서 '**단방향 데이터 바인딩**'은 Javascript(Model)에서 HTML(View)로 한 방향으로만 데이터를 동기화하는 것을 의미합니다. [JS(Model) -> HTML(View)] 단방향 데이터 바인딩이기에 역으로 HTML(View)에서 JS(Model)로의 직접적인 데이터 갱신은 불가능하며,컴포넌트 간에서 단방향 데이터 바인딩은 부모 컴포넌트에서 자식 컴포넌트로만 데이터가 전달되는 구조입니다. 대표적으로 SPA Framework에서는 React에서 단방향 데이터 바인딩을 합니다.

컴포넌트 내에서 **'양방향 데이터 바인딩'**은 Javascript(Model)와 HTML(View) 사이에 ViewModel이 존재하여 하나로 묶여서(Binding) 되어서 **둘 중 하나만 변경되어도 함께 변경되는 것을 의미합니다. [HTML(View)** <-> ViewModel <-> Javascript(Model)] 컴포넌트 간에서는 부모 컴포넌트에서 자식 컴포넌트로는 Props를 통해 데이터를 전달하고, 자식 컴포넌트에서 부모 컴포넌트로는 Emit Event를 통해서 데이터를 전달하는 구조입니다.대표적으로 SPA Framework에서는 Vue.js, Angular에서 양방향 데이터 바인딩을 합니다.

정리하면 단반향 바인딩과 양방향 바인딩은 HTML에서 변경된 내용이 데이터 영향을 미치는가에 대한 차이입니다.단방향은 데이터와 템플릿을 결합하여 화면을 생성하는 반면,양방향은 데이터의 변화를 감지해 템플릿과 결합하여 화면을 갱신하고 화면에서의 입력에 따라 데이터를 갱신합니다

단방향 바인딩은 모든 자바스크립트 코드가 데이터에 집중되어 있어 일관된 데이터 관리 로직을 갖는다는 점이 장점이 있습니다. 

양방향 데이터 바인딩은 웹 애플리케이션의 복잡도가 증가하면 증가할수록 수많은 코드의 양을 줄여줄 뿐만 아니라 유지보수나 코드를 관리하기 매우 쉽게 해준다는 장점이 있습니다. 

출처

[https://sungjk.github.io/2015/11/22/AngularJS(2).html](https://sungjk.github.io/2015/11/22/AngularJS(2).html)

https://kyung-a.tistory.com/9
