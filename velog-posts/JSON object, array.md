<p>현재 데이터 예시로 정리하기</p>
<ul>
<li><p>예시 데이터</p>
<pre><code class="language-java">{
&quot;response&quot;: [
  { &quot;id&quot;: 1, &quot;name&quot;: &quot;홍길동&quot;, &quot;age&quot;: 30 },
  { &quot;id&quot;: 2, &quot;name&quot;: &quot;이순신&quot;, &quot;age&quot;: 45 },
  { &quot;id&quot;: 3, &quot;name&quot;: &quot;김철수&quot;, &quot;age&quot;: 22 }
]
}</code></pre>
</li>
<li><p>가장 바깥은 중괄호 {}로 감싼 JSON 객체입니다.</p>
</li>
<li><p>&quot;response&quot;라는 키에 여러 개의 JSON 객체를 담은 배열 []이 연결되어 있습니다.</p>
</li>
<li><p>배열 안에는 3개의 JSON 객체가 들어있고 각각의 객체는 또 다시 키(id, name, age)와 값으로 이루어진 구조</p>
</li>
</ul>
<pre><code class="language-java">JSONObject jsonObject = new JSONObject(result);
JSONArray jsonArray = jsonObject.getJSONArray(&quot;response&quot;);
int count = jsonArray.length();  // 3</code></pre>
<p>각 배열의 원소(JSON 객체)는 
인덱스 0부터 2까지 접근할 수 있습니다.</p>
<p>즉, JSON 객체 안에 있는 데이터는 배열의 크기만큼 여러 개 존재할 수 있는 구조</p>
<pre><code>int count = jsonArray.length();  // 3</code></pre><p>array.length로 갯수 확인 가능!</p>