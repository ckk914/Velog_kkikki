<pre><code>this.sequence = new AtomicInteger(1);</code></pre><p>멀티쓰레드로 들어오니까 Integer로는 겹칠수가 있어서,
atomicInteger 사용</p>