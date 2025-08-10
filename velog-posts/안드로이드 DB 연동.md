<h3 id="안드로이드-스튜디오와-닷홈-호스팅-php를-통한-서버-활용">안드로이드 스튜디오와 닷홈 호스팅, php를 통한 서버 활용</h3>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/d73dac03-fbae-487a-9297-0c3c28f6a521/image.png" />
닷홈을 통해 호스팅을 했는데,
서버 연결이 안되는 문제가 있었어요
지금은 메시지가 뜨지만, 처음에는 회원가입 버튼을 눌러도
아무 반응이 없었습니다.</p>
<hr />
<p>먼저 작성한 서버 상태를 보기 위해 
PostMan을 통해 테스트를 먼저 진행했어요~</p>
<p>php내 변수가 안맞는 문제는 Postman 호출을 통해 에러 파악 후 
올바르게 고쳤고,
<img alt="" src="https://velog.velcdn.com/images/kkikki/post/8479ef53-5602-4f81-a623-4b3dfd054236/image.png" />
정상적으로 되는 코드로 만들었습니다.
[Register.php][호스팅 서버]</p>
<pre><code class="language-php">$userID = $_POST[&quot;userID&quot;];
    $userPassword = $_POST[&quot;userPassword&quot;];
    $userName = $_POST[&quot;userName&quot;];
    $userAge = $_POST[&quot;userAge&quot;];

    $statement = mysqli_prepare($con, &quot;INSERT INTO USER VALUES (?, ?, ?, ?)&quot;);
    mysqli_stmt_bind_param($statement, &quot;sssi&quot;, $userID, $userPassword, $userName, $userAge);</code></pre>
<p>post로 넘어온 변수가 변수명이 일치하지 않아, 문제를 일으켰던걸 찾았고
정상적으로 이루어지도록 했습니다.
정상적인 동작 확인을 통해 서버 구동에 문제가 없다는 것을 알게 되었고, 기존 진행한 안드로이드 작업을 이어가기로 했습니다.</p>
<hr />
<p>[RegisterRequest.java] [Android]</p>
<pre><code class="language-java">    public RegisterRequest(String userID, String userPassword, String userName, String userAge, Response.Listener&lt;String&gt; listener, Response.ErrorListener errorListener){
    super(Method.POST,URL,listener,errorListener); //해당 url로 post방식으로 데이터를 전송
        parameters = new HashMap&lt;&gt;();
        parameters.put(&quot;userID&quot;,userID);
        parameters.put(&quot;userPassword&quot;,userPassword);
        parameters.put(&quot;userName&quot;,userName);
        parameters.put(&quot;userAge&quot;,userAge+&quot;&quot;); //문자열을 하나 더해줘서 문자열로 변환시킴.!
    }</code></pre>
<p>추가로 
AndroidManifest.xml에서
http를 허용하기 위한</p>
<pre><code> android:usesCleartextTraffic=&quot;true&quot;</code></pre><p> 세팅을 추가함</p>
<p>호스팅 서버에 
login, register에 대해 프로그램을 작성해서
FileZilla를 통해서
<img alt="" src="https://velog.velcdn.com/images/kkikki/post/6ac19395-ff2c-463d-a896-a98984a12ba9/image.png" /></p>
<p>전송하여 연동하였습니다</p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/f524efff-9378-4364-a727-80839cc6a0b7/image.png" /></p>
<p>미리 만들어둔 테이블에 정상적으로 회원정보가 적재되는 것을 볼 수 있습니다.</p>
<p>가벼운 로직 테스트를 위해 별도 암호화는 하지 않고 했는데, 
구현하면 더더욱 좋죠~</p>