<hr />
<ul>
<li>Web.xml 파일 삭제, 스프링 관련 파일 삭제</li>
<li>pom.xml 수정, 스프링 버전 변경</li>
<li>java 설정 관련 패키지 생성</li>
</ul>
<hr />
<h3 id="xml-파일-삭제">XML 파일 삭제</h3>
<ul>
<li>web.xml, servlet-context.xml, root-context.xml</li>
</ul>
<hr />
<p>web.xml을 삭제하면 , pom.xml에서 에러 발생</p>
<p>: 과거의 웹 프로젝트들이 기본적으로 web.xml을 사용하는 것을
  기본으로 설정했기 때문</p>
<p>해결방법
pom.xml 하단에 plugins 추가 설정</p>
<pre><code class="language-java">&lt;plugin&gt;
&lt;groupId&gt;org.apache.maven.plugins&lt;/groupId&gt;
&lt;arttidactId&gt;maven-war-plugin&lt;/arttidactId&gt;
&lt;version&gt;3.2.0&lt;/version&gt;
&lt;configuration&gt;
  &lt;failOnMissingWebXml&gt;false&lt;/failOnMissingWebXml&gt;
&lt;/configuration&gt;
&lt;/plugin&gt;
</code></pre>
<p>pom.xml 의 스프링 버전도 같이 변경할 것</p>
<hr />
<p>컴파일 관련 버전도 수정 후 </p>
<p>Maven&gt; Update Project</p>
<hr />