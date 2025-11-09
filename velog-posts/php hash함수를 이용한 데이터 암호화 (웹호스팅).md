<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/52dee5a4-fb3c-412a-8945-0332cf59c40f/image.png" /></p>
<p>php 자체 함수를 이용해, 데이터 암호화 진행</p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/82d4e998-49c7-40bc-a04f-664b018873f1/image.png" /></p>
<p>로그인 시, password_verify 체크</p>
<h3 id="hash-사용으로-인한-패스워드-사이즈-변경">hash 사용으로 인한, 패스워드 사이즈 변경</h3>
<pre><code class="language-java">ALTER TABLE STUDENT MODIFY studentPassword VARCHAR(255);</code></pre>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/ab3fe1de-39b9-4c09-b2f3-950d35fcfe3d/image.png" /></p>
<p>[기존과 달리 암호화된 상태]</p>