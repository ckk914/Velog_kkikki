<p>스프링 빈(Bean) 이란?
빈(Bean)은 스프링 컨테이너에 의해 관리되는 재사용 가능한 소프트웨어 컴포넌트이다. 
즉, 스프링 컨테이너가 관리하는 자바 객체를 뜻하며, 하나 이상의 빈(Bean)을 관리한다.</p>
<hr />
<p>빈은 인스턴스화된 *객체를 의미하며, *(스프링 컨테이너)에 등록된 객체를 스프링 빈이라고 한다. </p>
<hr />
<p>*스프링 컨테이너란 무엇인가?
스프링 컨테이너를 설명하기 전에 컨테이너란 뭔지 짚고 넘어가자.</p>
<p>컨테이너의 정의를 구글에서 잘 설명하고 있는 것 같아 인용해왔다.</p>
<blockquote>
<p>구글에서는 컨테이너를 컨테이너는 어떤 환경에서나 실행하기 위해 필요한 모든 요소를 포함하는 소프트웨어 패키지라고 설명하고 있다.</p>
</blockquote>
<hr />
<p>스프링 컨테이너는 Spring에서 빈(Bean)들의 생명주기를 관리하는 Spring Framework의 *코어(Core)이다. </p>
<p> ### 객체</p>
<blockquote>
<p>실세계에 존재하거나 생각할 수 있는 것을 뜻합니다.
 
우리가 개발을 하면서 접하게 될 프로그래밍에서의 객체는 속성과 기능을 가지는 프로그램 단위를 뜻합니다.</p>
</blockquote>
<ol>
<li>객체 : 소프트웨어 세계에 구현할 대상<pre><code>  속성과 기능을 가지는 프로그램 단위</code></pre></li>
<li>클래스 : 객체에 속성과 기능을 넣어줄 설계도</li>
<li>인스턴스 : 클래스에 따라 메모리상에 구현된 실체</li>
</ol>
<hr />
<h3 id="spring-core">Spring Core</h3>
<p>Spring은 최신 Java 기반 기업형(enterprise) 애플리케이션을 위한 포괄적인 프로그래밍 및 구성 모델을 제공하는 오픈 소스 프레임워크(framework)이다. </p>
<p>Spring Core 모듈이라고도 알려진 Spring의 핵심 모듈은 프레임워크의 핵심이며, 
Dependency Injection(DI)(의존성 주입) 및 Inversion Of Control(IoC)(제어의 역전)에 대한 기본 기능을 제공한다.
의존성 주입 외에도 Spring Core 모듈은 다음과 같은 몇 가지 다른 기능도 제공한다.</p>
<ul>
<li>유연하고 확장 가능한 검증된 프레임워크</li>
<li>타입 변환(type conversion) 시스템</li>
<li>일관된 메시징(messaging) 프레임워크</li>
</ul>
<hr />
<h3 id="spring-boot">Spring Boot</h3>
<p>Spring Boot는 (Java 기반 기업형 애플리케이션 빌딩(building)을 위해 널리 사용되는 오픈 소스 프레임워크인) Spring Framework를 기반으로 애플리케이션을 빌딩하기 위한 프레임워크이다.
Spring Boot는 “그냥 실행할 수 있는(just run)” 독립형(stand-alone) 프로덕션급(production-grade) Spring 기반 애플리케이션을 쉽게 생성할 수 있도록 하는 것을 목표로 한다.</p>
<hr />
<p>다시 돌아가서,</p>
<p> @Configuration이라고 하면
: 설정파일을 만들기 위한 애노테이션 또는
  Bean을 등록하기 위한 애노테이션이다.</p>
<p>  @Configuration 애노테이션을 사용하면 가시적으로 설정파일이야 ~ , Bean 등록할꺼야 ~= 라는건 알수있다.</p>
<p>&lt;역할&gt;</p>
<ul>
<li>Bean을 등록할때 *싱글톤(singleton)이 되도록 보장해준다.</li>
<li>스프링컨테이너에서 Bean을 관리할수있게 됨.</li>
</ul>
<h3 id="싱글톤-패턴이란">*싱글톤 패턴이란?</h3>
<p>싱글톤은 프로그램 전체에서 단 하나의 객체만 생성하여 공유하는 방식.</p>
<p>쉽게 말해서, 여러 곳에서 동일한 객체를 새로 만들지 않고
이미 만들어진 하나의 객체를 함께 사용하는 것입니다.</p>
<h3 id="싱글톤의-장점">싱글톤의 장점</h3>
<ul>
<li>메모리 절약: 객체를 매번 새로 만들지 않고 하나만 만들어서 사용하므로 메모리가 절약됩니다</li>
<li>데이터 공유: 여러 곳에서 같은 객체를 사용하므로 데이터 공유가 쉽습니다</li>
</ul>
<h3 id="스프링의-bean과-싱글톤">스프링의 Bean과 싱글톤</h3>
<p>스프링에서는 Bean으로 등록된 객체들을 자동으로 싱글톤으로 관리해줍니다</p>
<h3 id="스프링이-하는-일">스프링이 하는 일:</h3>
<p>Bean으로 등록된 객체를 딱 한 번만 생성합니다
이 객체를 스프링 컨테이너가 보관하고 관리합니다
필요한 곳에서 이 객체를 가져다 사용할 수 있습니다</p>
<hr />
<p>코드 실행 결과
@Configuration 있을 때:
text
AppConfig.calculate
AppConfig.calculator
@Configuration 없을 때:
text
AppConfig.calculate
AppConfig.calculator
AppConfig.calculate
코드 설명
이 예제는 스프링의 @Configuration이 싱글톤을 보장하는 방식을 보여주는 테스트입니다.</p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/93f8c067-3ddc-4ab2-b7e6-d06df85cb5b8/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/38a2542f-3c06-4f42-a983-0e68e31055a5/image.png" /></p>
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/d96e1161-30d4-48c9-b953-74c7fd6ec096/image.png" /></p>
<hr />
<p><img alt="" src="https://velog.velcdn.com/images/kkikki/post/ea445db1-07cf-43cf-af09-20c67d8905e3/image.png" /></p>
<hr />
<p>@Bean만 사용하면 스프링 빈으로는 등록되지만, 싱글톤은 보장되지 않습니다
따라서 스프링 빈을 등록할 때는 @Configuration과 @Bean을 함께 사용하는 것이 좋습니다</p>
<hr />