<pre><code> npm start

&gt; mcs-admin@0.1.0 start
&gt; export PORT=3600 &amp;&amp; env-cmd -f .env.local react-scripts start

sh: env-cmd: command not found</code></pre><h3 id="해결방안">해결방안</h3>
<blockquote>
<p>  npm install -g env-cmd</p>
</blockquote>
<p>이후에 </p>
<blockquote>
<p>npm start</p>
</blockquote>