<p>app-src-main-res-laylot-activity_main.xml없을때</p>
<p>comment</p>
<pre><code>프로젝트 생성 시 Empty Activity를 선택하면
예전에는 자동으로 activity_main.xml이 생성됐지만, 

최신 버전에서는 Jetpack Compose가 적용되어 있으면 XML 파일이 생성되지 않습니다.</code></pre><p>트러블 슈팅</p>
<pre><code>만약 XML 기반 레이아웃을 사용하고 싶다면,
**프로젝트 생성 시 Empty Views Activity
또는 Basic Views Activity**
를 선택해야 합니다. 

이 옵션을 선택하면 
기존처럼 activity_main.xml 파일과
layout 폴더가 자동으로 생성됩니다</code></pre>