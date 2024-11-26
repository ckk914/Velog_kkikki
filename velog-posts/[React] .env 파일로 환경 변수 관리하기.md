<blockquote>
<p>환경 변수란?
컴퓨터 시스템에서 프로그램이 실행될 때 동작을 제어하거나 설정하기 위해 사용되는 값들의 모임</p>
</blockquote>
<blockquote>
<p>환경 변수 종류?
 API Key, 비밀키, 서버 URL, DB URL, DB Password 등등</p>
</blockquote>
<hr />
<p> 우리가 작성한 코드는 깃허브의 공개된 리포지토리에 올리게 되면
 별다른 조치를 하지 않는 이상 그대로 올라가게 됩니다.</p>
<p> 위에 있는 내 API Key를 아무나 볼 수 있고
 또, 무분별하게 사용될 수도 있습니다. 그렇기 때문에 공개되어서는
 안되는 민감한 정보들을 .env 파일에 저장하여 필요할 때 환경 변수로 불러오는 것입니다.</p>
<p> <img alt="" src="https://velog.velcdn.com/images/kkikki/post/98444927-bbfe-4626-8356-aef1c099c500/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/08cd569d-2bd9-452c-be92-00e550de5ad7/image.png" /></p>
<p>⭐️루트 디렉토리에 .env 파일을 생성하고 .gitignore 파일에 .env를 작성
.env 파일은 반드시 루트 디렉토리에 생성해야 적용됩니다</p>
<hr />
<h3 id="env-작성-방법-및-사용">.env 작성 방법 및 사용</h3>
<h3 id="지켜야-할-규칙들을-3가지">지켜야 할 규칙들을 3가지</h3>
<blockquote>
<ol>
<li>React에서 변수명은 REACT_APP_ 으로 시작되어야 한다.<ol start="2">
<li>변수명과 값 사이에는 공백 또는 따옴표(&quot;&quot;)가 존재해서는 안된다.</li>
<li>변수명은 대문자로 작성하는 것이 관례이다.</li>
</ol>
</li>
</ol>
</blockquote>
<p> <img alt="" src="https://velog.velcdn.com/images/kkikki/post/f27fa00f-e735-4f89-90d0-166249837589/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/66eea7de-1b8f-4873-80b7-055fbc51c856/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/ed4e41e8-3fba-41af-8929-e89984a672c8/image.png" /></p>