<pre><code class="language-java">registerButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                //로그인 화면에서 회원가입 화면으로 이동하도록 설정
                Intent registerIntent = new Intent(LoginActivity.this, RegisterActivity.class);
                LoginActivity.this.startActivity(registerIntent);
            }
        });</code></pre>
<p>Intent를 통한 화면 이동하는 코드를 구현했는데,
이동이 안되는 문제가 있었다</p>
<h3 id="원인">원인</h3>
<pre><code>AndroidManifest.xml을 열어서
액티비티를 등록하지 않아서 발생한 문제</code></pre><h3 id="해결-방법">해결 방법</h3>
<pre><code class="language-java">...
&lt;activity android:name=&quot;.RegisterActivity&quot; /&gt;
&lt;activity android:name=&quot;.MainActivity&quot; /&gt;
&lt;/application&gt;
</code></pre>
<p>액티비티들을 등록해준 후 정상적으로 액티비티 전환 가능해짐!</p>