<p>event.observe(viewLifecycleOwner) { ... }는 Android에서 LiveData를 관찰(observe)하는 대표적인 코드</p>
<p>event: 보통 LiveData 객체 또는 그 하위 타입(MutableLiveData 등)입니다.</p>
<p>observe(): LiveData가 변할 때마다 알려주는 함수입니다.</p>
<p>viewLifecycleOwner: LiveData를 관찰할 생명주기 소유자(LifecycleOwner)로, 보통 Fragment의 뷰 생명주기입니다. 이 덕분에 UI 뷰가 살아있을 때만 이벤트를 받고, 뷰가 없어지면 자동 해제됩니다.</p>
<hr />
<pre><code class="language-java">event.observe(viewLifecycleOwner) { data -&gt;
    // data를 이용해 UI 업데이트
    if (data != null) {
        textView.text = data
    }
}</code></pre>
<p>위 코드는 event 데이터가 변할 때마다 호출됩니다.</p>
<p>viewLifecycleOwner가 살아있는 동안만 관찰하고, 사라지면 자동으로 옵저버가 해제되어 메모리 누수 방지.</p>