<h3 id="생성-방법">생성 방법</h3>
<p>npx create-react-app my-fluent-app --template typescript</p>
<p>my-fluent-app에 원하는 프로젝트명 입력</p>
<hr />
<p>cd my-fluent-app</p>
<hr />
<p>git branch -m master main
브랜치명 정리</p>
<hr />
<p>Fluent UI 패키지 설치</p>
<pre><code>npm install @fluentui/react</code></pre><p>필요한 타입 정의 설치
npm install @types/react @types/react-dom</p>
<pre><code>import React from 'react';
import { initializeIcons } from '@fluentui/react';
import { PrimaryButton } from '@fluentui/react';

initializeIcons();

function App() {
  return (
    &lt;div&gt;
      &lt;PrimaryButton text=&quot;Hello World&quot; /&gt;
    &lt;/div&gt;
  );
}

export default App;</code></pre><p>App.tsx 정의</p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/03dbc571-1405-4258-9a2e-4bd8e194eabc/image.png" /></p>
<p>이제 사용 가능</p>