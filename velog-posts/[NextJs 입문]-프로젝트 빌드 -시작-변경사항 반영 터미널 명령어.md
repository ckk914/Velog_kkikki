<p>Next.js 프로젝트를 시작하는 올바른 명령어는 npm run dev 입니다</p>
<h3 id="개발-환경과-프로덕션-환경의-차이">개발 환경과 프로덕션 환경의 차이</h3>
<ul>
<li><p>개발 환경 실행
npm run dev: 개발 모드로 서버를 실행하며, 코드 변경 시 자동으로 새로고침됩니다</p>
</li>
<li><p>프로덕션 환경 실행
npm run build: 프로덕션용 빌드를 생성
npm run start: 프로덕션 모드로 서버를 실행</p>
</li>
</ul>
<h3 id="주의사항">주의사항</h3>
<ul>
<li>npm run start를 실행하기 전에 반드시 npm run build를 먼저 실행해야 합니다</li>
<li>프로덕션 모드에서는 개발 모드와 달리 코드 변경사항이 자동으로 반영되지 않습니다</li>
<li>기본적으로 서버는 3000번 포트에서 실행되며,     <a href="http://localhost:3000%EC%9C%BC%EB%A1%9C">http://localhost:3000으로</a> 접속할 수 있습니다</li>
</ul>
<hr />