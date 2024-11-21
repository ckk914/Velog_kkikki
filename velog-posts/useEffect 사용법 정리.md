<pre><code class="language-react">useEffect(() =&gt; {
setIsSearchbuttonClicked(true); // 초기 렌더링 시 검색 트리거
}, []); // 컴포넌트 마운트 시 1회만 실행</code></pre>
<blockquote>
<p>빈 배열([])을 전달하면 컴포넌트가 처음 마운트될 때 단 한 번만 실행됩니다</p>
</blockquote>
<blockquote>
<p>useEffect의 의존성 배열([])에 값을 넣으면!
해당 값이 변경될 때마다 useEffect 내부의 코드가 실행됩니다</p>
</blockquote>
<pre><code class="language-react">// 1. 빈 배열: 컴포넌트 마운트 시 1회만 실행
useEffect(() =&gt; {
    // 코드
}, []);

// 2. 의존성 있는 경우: searchParam이 변경될 때마다 실행
useEffect(() =&gt; {
    // 코드
}, [searchParam]);

// 3. 여러 의존성: searchParam 또는 isLoading이 변경될 때마다 실행
useEffect(() =&gt; {
    // 코드
}, [searchParam, isLoading]);

// 4. 의존성 배열 생략: 모든 상태 변경 시 실행
useEffect(() =&gt; {
    // 코드
});</code></pre>