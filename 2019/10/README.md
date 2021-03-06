10월부터 링크 연결 및 간단한 요약 정리 

## 2019.10.06(26개)
* [Cache-Aside Pattern in Redis](https://brunch.co.kr/@springboot/151)
* [[번역] OOP를 빨리 잊을 수록 여러분과 여러분의 소프트웨어에 좋습니다](https://rinae.dev/posts/the-faster-you-unlearn-oop-the-better-for-you-and-your-software-kr)
    - 단점
        - 간단한 문제가 OOP 방식으로 프로그램을 짰더니 엄청난 양의 코드가 되어버린 이유는 언제나 추상화할 구석이 남아있기 때문입니다.
        - 당신은 바나나를 원했지만 실제로는 바나나를 들고 있는 고릴라와 정글 전체를 얻고 말았다.
        - 간단한 데이터 변형을 하는데 이상하고, 배배 꼬인 메서드끼리 호출
        - 수많은 보일러플레이트를 만들게 되죠. 게터(getter), 세터(setter), 다중 생성자, 이상한 메서드들 모두 실제로는 거의 일어나지 않을 실수로부터 보호하기 위한 방책입니다
* 3년차 웹 개발자
* 자바 메모리 관리 - 스택 & 힙
    * 메서드 호출시 파라미터(메서드 파라미터)가 스택에 쌓인다.
* 기능 요구사항 명세(Specification)
* 154. [Security] SSL과 인증서 구조 이해하기 : CA (Certificate Authority) 를 중심으로 
    * 인증서 내용물
       * ![image](https://user-images.githubusercontent.com/20143765/66271998-2766bf80-e89f-11e9-95c0-29dfaca7103e.png)
* [기술블로그 구독서비스 개발 후기 - 3부](https://taetaetae.github.io/2019/02/17/daily-dev-blog-3/)
* [Spring Guide - Domain](https://cheese10yun.github.io/spring-guide-domain/)
    * 객체지향에서 중요한 것들이 많겠지만 그중에 하나가 객체 본인의 책임을 다하는 것입니다. 여러번 반복해서 언급하지만, 객체가 자기 자신의 책임을 다하지 않으면 그 책임은 다른 객체에게 넘어가게 됩니다.
* [Effective Java3/E - 람다와 스트림](https://brunch.co.kr/@oemilk/207)
* [스프링 애플리케이션이 시작, 종료될 때 수행할 메서드 지정하는 방법 + 스프링 빈(Bean)이 생성, 소멸될 때 수행할 메서드 지정하는 방법(graceful 종료, CommandLineRunner, ApplicationListener, InitializingBea..](https://jeong-pro.tistory.com/179)
   - 요약
      - PostConstruct, CommandLineRunner(run method), ApplicationRunner(run method), ApplicationListener(onApplicationEvent method), InitializingBean(afterPropertiesSet method), DisposableBean(destory method)
      - PostConstruct 메서드 다음에 afterPropertiesSet 호출
``` java
@Service
public class TestService implements CommandLineRunner, APplicationRunner, ApplicationListener<ContextClosedEvent>, InitializingBean, DisposableBean {
    @PostConstruct
    private void init() {
        System.err.println("PostConstruct annotation으로 빈이 완전히 생성된 후에 한 번 수행될 메서드에 붙입니다.");
    }
    @Override
    public void run(ApplicationArguments args) throws Exception {
        System.err.println("ApplicationRunner 인터페이스 구현 메서드입니다. '애플리케이션'이 실행될 때 '한 번' 실행됩니다.");
    }
    @Override
    public void run(String... args) throws Exception {
        System.err.println("commandLineRunner 인터페이스 구현 메서드입니다. '애플리케이션'이 실행될 때 '한 번' 실행됩니다.");
    }
    @Override
    public void onApplicationEvent(ContextClosedEvent event) {
        System.err.println("ApplicationListener<ContextClosedEvent> 인터페이스 구현 메서드 입니다. '애플리케이션'이 죽었을 때 '한 번' 실행됩니다.");
        System.err.println("이벤트 발생 시간(timestamp) : " + event.getTimestamp());
    }
    @Override
    public void afterPropertiesSet() throws Exception {
        System.err.println("InitializingBean 인터페이스 구현 메서드입니다. TestService 'Bean'이 생성될 때 마다 호출되는 메서드 입니다.");
    }
    @Override
    public void destroy() throws Exception {
        System.err.println("DisposableBean 인터페이스 구현 메서드입니다. TestService 'Bean'이 소멸될 때 마다 호출되는 메서드입니다");
    }
}
```
* [테스트 코드 없이 레거시 코드를 다 감수하시겠습니까?](http://woowabros.github.io/experience/2019/02/27/Working_Effectively_with_Legacy_Code.html)
* [aop를 이용한 oauth2 캐시 적용하기](http://woowabros.github.io/experience/2019/03/05/aop-oauth2-redis.html)
* [테크니컬 라이팅 컨퍼런스: API the Docs Chicago 2019 방문기](https://engineering.linecorp.com/ko/blog/api-the-docs-chicago-2019-recap/)
    * Docsops
    * 포드는 DocsOps를 통해 분산되어 있는 API 접근 채널을 단일화
    * 리퀘스트 바디(body) 파라미터는 적어도 문단 하나 정도의 분량은 있어야 하며, 파라미터 예제 값과 엔드포인트를 호출하는 예제 코드도 함께 있는게 좋다.
* [로우 레벨로 살펴보는 Node.js 이벤트 루프](https://evan-moon.github.io/2019/08/01/nodejs-event-loop-workflow/index.html)
   * 요약
      * 이벤트 루프는 작업 스택을 가지고 있지 않다.
      * 이벤트 루프가 별도의 스레드에서 실행되고 자바스크립트 실행은 어떤 큐에서 하나씩 꺼내와서 다른 곳에서 하는 것이 아니라 자바스크립트의 실행 자체가 이벤트 루프 안에서 수행되는 것이다.
      * setImmediate는 콜백을 작업 큐의 앞 쪽에 밀어넣는 것이 아니라 setImmediate 만을 처리하기 위한 전용 페이즈와 큐가 존재한다.
      * setImmediate은 실질적으로 다음 페이즈 혹은 다음 이벤트 루프의 순회에서 실행되고, nextTick이 오히려 실질적으로 더 빠르게 실행된다.
      * nextTickQueue에 담긴 작업이 재귀 호출을 수행하는 경우 Node.js의 작업 프로세스를 블록킹할 수 있다. 주의하도록 하자.
* [[Shell Script] 산술식 수행하기 (더하기, 곱하기, 나누기, 빼기)](https://rim0621.tistory.com/90)
* [[Shell Script] 파일인지 폴더인지 if문 및 옵션](https://rim0621.tistory.com/91)
* [[Shell Script] case문 (요일별로 동작하기 좋네)](https://rim0621.tistory.com/92)
* [[Shell Script] for문 여러 형식](https://rim0621.tistory.com/93)
* [[Shell Script] while문, until문](https://rim0621.tistory.com/94)
* [Spring5 리액티브 스트림 정리 및 api 전달 방식 정리](https://wedul.site/624)
* [디자인 패턴 06 - 어댑터 (Adapter)](https://dhsim86.github.io/programming/2019/08/17/design_patterns_06-post.html)
* [디자인 패턴 07 - 가교 (Bridge)](https://dhsim86.github.io/programming/2019/08/17/design_patterns_07-post.html)
* [LINE Manga 데이터베이스 샤딩 – 데이터베이스 엔지니어 편](https://engineering.linecorp.com/ko/blog/line-manga-database/)
* [gRPC](https://ssup2.github.io/theory_analysis/gRPC/)
   * 아키텍처
      * ![image](https://user-images.githubusercontent.com/20143765/66271895-4749b380-e89e-11e9-9f86-a5c21266218b.png)
   * Protobuf 이용
      * ![image](https://user-images.githubusercontent.com/20143765/66271890-313bf300-e89e-11e9-8559-1d619d59fe60.png)
   * vs HTTP/1.1 + JSON
      * gRPC가 현재 주목받는 가장큰 이유는 기존의 HTTP/1.1 + JSON Protocol보다 빠르기 때문이다. HTTP/1.1과 JSON은 Text Protocol인 만큼 성능면에서는 불리하다. gRPC에서 이용하는 HTTP/2와 ProtoBuf는 Binray Protocol인만큼 상대적으로 적은양의 Packet을 주고 받는다. 또한 gRPC는 HTTP/2에서 지원하는 Connection Multiplexing, Server/Client Streaming을 이용하여 효율성을 좀더 끌어 올리고 있다.
* [빅데이터 처리 후기 (검색엔진 처리)](https://blog.lael.be/post/9242)
* [GeoJSON Format(형식)](http://www.gisdeveloper.co.kr/?p=8002)
```
{
    "type": "FeatureCollection",
    "features": [
        {
            "type": "Feature",
            "geometry": {
                "type": "Point",
                "coordinates": [102.0, 0.5]
            },
            "properties": {
                "prop0": "value0"
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "LineString",
                "coordinates": [[102.0, 0.0], [103.0, 1.0], [104.0, 0.0], [105.0, 1.0]]
            },
            "properties": {
                "prop0": "value0",
                "prop1": 0.0
            }
        },
        {
            "type": "Feature",
            "geometry": {
                "type": "Polygon",
                "coordinates": [[[100.0, 0.0], [101.0, 0.0], [101.0, 1.0],[100.0, 1.0], [100.0, 0.0]]]
            },
            "properties": {
                "prop0": "value0",
                "prop1": { "this": "that" }
            }
        }
    ]
}
```

--- 

## 2019.10.12(3개)
 * [Jackson 관련](https://happyer16.tistory.com/entry/Jackson-%EA%B4%80%EB%A0%A8)
     * @JsonManagedReference : 해당 부분이 serialize 된다
     * @JsonBackReference : serialize 에서 제외 된다.
 * [효율적인 도커 이미지 만들기 #1 - 작은 도커 이미지](https://bcho.tistory.com/1356?category=731548)
 * [효율적인 도커 이미지 만들기 #2 - 도커 레이어 캐슁을 통한 빌드/배포 속도 높이기](https://bcho.tistory.com/1357)
     * jar 파일을 풀어서 라이브러리 jar파일들이 캐싱 대도록 레이어 분리

--- 

## 2019.10.15(5개)
 * [2019.10.10 - 토비의 스프링을 읽으며](https://blog.naver.com/writer0713/221674259511)
 * [Outsider 기술 뉴스 #136 : 19-10-15](https://blog.outsider.ne.kr/1463)
 * [Outsider 기술 뉴스 #136 : 19-09-02](https://blog.outsider.ne.kr/1458)
 * [Outsider 기술 뉴스 #136 : 19-09-15](https://blog.outsider.ne.kr/1460)
 * [Leon Sans : 동적으로 폰트의 웨이트를 바꿀 수 있고 애니메이션을 추가할 수 있는 폰트.](https://github.com/cmiscm/leonsans)
    * 인터렉티브 웹개발 토이프로젝트시 참고할만할듯

--- 

## 2019.10.22(1개)
* [키바나 Aggregation Size 옵션 특징](http://kangmyounghun.blogspot.com/2019/10/aggregation-size.html)

--- 

## 2019.10.26(8개)
* [Redis에서 Pub/Sub 방식 소개 및 Spring Boot에서 구현해보기](https://wedul.site/627)
* [[logstash] plugin-input-mongodb을 이용하여 mongoldb 기반 pipeline 구축](https://blog.naver.com/pjt3591oo/221624138418)
    * logstash-input-mongodb
    * logstash-output-mongodb 
        * 위 플러그인들을 이용하여 몽고와 logstash를 바로 연결 가능 
* [python scikit learn 데이터 전처리 방법 - 머신러닝 data preparecessing](https://lsjsj92.tistory.com/511)
    * Label encoding, one-hot encoding, feature scaling(StandardScaler, MinMaxScaler) 
* [[Kubernetes] 쿠버네티스 POD 란?](https://blog.wonizz.tk/2019/08/19/kubernetes-pod/)
* [[Kubernetes] 쿠버네티스 Service 란?](https://blog.wonizz.tk/2019/08/21/kubernetes-service/)
* [머신러닝 평가지표 방법 - 정확도, 재현율(recall), 정밀도(precision), 오차 행렬(confusion matrix)](https://lsjsj92.tistory.com/513)
    * Confusion maxtirx
        * ![image](https://user-images.githubusercontent.com/20143765/67615925-41941d80-f80d-11e9-9339-f770a87a93a1.png)
        * ![image](https://user-images.githubusercontent.com/20143765/67615930-4e187600-f80d-11e9-89ec-8a40655f22f1.png)
    * 정확도
        * TN + TP / (TN + FP + FN + TP)
    * 정밀도(precision)
        * TP / (FP + TP)
    * 재현율(recall)
        * TP (FN + TP)
* [Selenium, Puppeteer 비교하기](https://yangeok.github.io/node.js/2019/08/31/selenium-puppeteer-comparison.html)
    * Puppeteer
        * 빠른속도, nodejs기반, 크롬에서만 사용 가능, 빠른 업데이트
    * Selenium
        * 상대적 느린속도, java, python기반, 다른 브라우저 사용 가능,  selenium grid로 허브를 구축해 사용 가능
* [redux에 Immutable.js을 끼얹어 상태 관리를 해보자(불변성 관리)](https://velog.io/@cyranocoding/redux%EC%97%90-Immutable.js%EC%9D%84-%EB%81%BC%EC%96%B9%EC%96%B4-%EC%83%81%ED%83%9C-%EA%B4%80%EB%A6%AC%EB%A5%BC-%ED%95%B4%EB%B3%B4%EC%9E%90%EB%B6%88%EB%B3%80%EC%84%B1-%EA%B4%80%EB%A6%AC)
    * 기자 어드민 react 프로젝트에서 피봐서 알겠지만 immutable 라이브러리 사용은 필수다.. 

--- 

## 2019.10.27(5개)
* [if kakao 2019 2일차 후기](https://zzsza.github.io/etc/2019/08/30/ifkakao-2019-review/)
* [if kakao day 1 후기](https://nesoy.github.io/articles/2019-08/if-kakao-day1)
    * [ghz](https://github.com/bojand/ghz) - gRPC Load Test
    * [grpcui](https://github.com/fullstorydev/grpcui) - Postman과 유사하나 gRPC 테스트 용
* [파이콘 한국 2019 스포카 코드 챌린지 수상작 및 참여작을 소개합니다.](https://spoqa.github.io/2019/08/30/pycon-kr-code-challenge.html)
* [MySQL 파티셔닝 테이블 SELECT가 느려요.](https://gywn.net/2019/08/mysql-poor-performance-with-super-many-partitions/)
    * InnoDB. 파티셔닝에서 실행계획을 세우는 단계에서 모든 파티션에 약 1~3개 정도의 페이지를 읽게되는데 이런 동작으로 인하여 엄청난 비효율이 발생
    * 엄청난 갯수의 파티셔닝을 가진 상황에서, 파티셔닝 테이블 조회 시 이와 같은 이슈로 리소스가 충분히 활용되고 있지 않은지를 한번쯤 확인
* [JavaScript SDK 성능개선 방법 – 압축과 최적화로 실행시간 단축하기](https://engineering.linecorp.com/ko/blog/improve-javascript-sdk-performance/)
    * 성능 개선 방법 – 최소화(minimization)
        * 개발 모드 확인
            * mode: production
        *  Tree shaking 개선(사용하지 않는 모듈 제거)
            * ![image](https://user-images.githubusercontent.com/20143765/67639283-5c5fb280-f931-11e9-8683-1a3160f38338.png)
        * 자원 외부화
            * ![image](https://user-images.githubusercontent.com/20143765/67639286-608bd000-f931-11e9-8f19-d0f5bb057a5e.png)
        * 자원 파일 크기 축소
            * 이미지 파일 축소 툴:  [imageOptim](https://imageoptim.com/mac)
        * 필요 없는 모듈 제외 
            * 애플리케이션에서 특정 국가의 언어만 지원할 때는 moment.js에 포함된 그 외 국가들의 로캘(locale) 정보 제거
               * ![image](https://user-images.githubusercontent.com/20143765/68521775-b2e0cf80-02e7-11ea-9dcb-45d33c990ad0.png)
        * 압축 파일 활용
    * 성능 개선 방법 – 최적화(optimization)
        * Dynamic Import와 모듈 chunk, Promise.all 조합
            * ![image](https://user-images.githubusercontent.com/20143765/67639291-68e40b00-f931-11e9-8c99-105661de3dbe.png)
            
--- 

## 2019.10.31(7개)
* [스프링 - 생성자 주입을 사용해야 하는 이유, 필드인젝션이 좋지 않은 이유](https://yaboong.github.io/spring/2019/08/29/why-field-injection-is-bad/)
    1. Component를 변경이 불가능한 immutable 상태로 선언이 가능합니다.(의존성 주입이 필요한 필드를 final 로 선언가능)
    2. 더 나아가 생성자의 Parameter를 통해 의존관계를 한눈에 파악하고 Refactoring의 필요성을 얻을 수 있습니다.
    3. Component간 순환 참조를 하고 있다면 컴파일 타임에 BeanCurrentlyInCreationException이 발생해서 순환 의존성을 쉽게 알 수 있습니다.(순환참조시 앱구동 실패)
    4. 특정 DI Container에 의존하지 않으며 쉽게 단위 테스트도 가능하고 필요하다면 다른 DI Container로 전환이 가능합니다.(객체 생성시 모든 의존관계를 주입할수 있으므로 단위테스트시 의존관계를 커스텀하게 주입가능)
    5. DI Container가 Component를 주입을 못한 경우 실제 Method가 호출되기 이전인 생성자에서 Handling 할 수 있습니다.(의존관계 설정이 되지 않으면 객체생성 불가 -> 컴파일 타임에 인지 가능, NPE 방지)
* [파이썬(Python) 3.8 릴리스와 주요 변경 사항](https://www.44bits.io/ko/post/python-3-8-release-note-summary?fbclid=IwAR2w2tDWn2VijXQ1QHtZQPjaXF2VVfw1HyBmpvbKz0J4PPZQpVDxI258IW0)
    * 할당 표현식assignment expressions
    * 위치 고정 파라미터positional-only parameter
    * f-문자열에서 평가식self-documenting expressions을 위한 = 기호 추가
* [Java Optional 바르게 쓰기](http://homoefficio.github.io/2019/10/03/Java-Optional-%EB%B0%94%EB%A5%B4%EA%B2%8C-%EC%93%B0%EA%B8%B0/?fbclid=IwAR0ruUDGSwMf0UATvHE0XsJ2lCar_u_W8tXpfQIazXmDiTDRlFI1v3T4Whk)
    1. isPresent()-get() 대신 orElse()/orElseGet()/orElseThrow()
    2. orElse(new ...) 대신 orElseGet(() -> new ...)
        * orElse는 Optional에 값이 있든 없든 무조건 실행, orElseGet(Supplier)에서 Supplier는 Optional에 값이 없을 때만 실행
        * 따라서 객체를 생성하거나 새로운 연산을 수행하는 경우에는 orElse() 대신 orElseGet()을 써야한다.
    3. 단지 값을 얻을 목적이라면 Optional 대신 null 비교
        * ![image](https://user-images.githubusercontent.com/20143765/68016148-42c6be00-fcd7-11e9-9062-ce22dd863d90.png)
    4. Optional 대신 비어있는 컬렉션 반환
    5. Optional을 필드로 사용 금지
    6. Optional을 생성자나 메서드 인자로 사용 금지
    7. Optional을 컬렉션의 원소로 사용 금지
        * getOrDefault(), putIfAbsent(), computeIfAbsent(), computeIfPresent() 처럼 null 체크가 포함된 메서드를 잘 이용하자
    8. of(), ofNullable() 혼동 주의
        * of(X)은 X가 null이 아님이 확실할 때만 사용해야 하며, X가 null이면 NullPointerException 이 발생한다.
        * ofNullable(X)은 X가 null일 수도 있을 때만 사용해야 하며, X가 null이 아님이 확실하면 of(X)를 사용해야 한다.
    9. Optional<T> 대신 OptionalInt, OptionalLong, OptionalDouble
* [글로벌 네트워크 에뮬레이터 prism_pacman 소개](https://d2.naver.com/helloworld/7847943)
    * 네트워크 환경의 성능을 좌우하는 가장 큰 2가지 요소는 레이턴시(latency)와 대역폭(bandwidth)
        * 레이턴시: 송신자부터 수신자까지 패킷이 도달하는 시간
            * 전파지연
            * 전송지연
            * 프로세싱 지연
            * 큐잉 지연
            * 최종 마일 레이턴시
        * 대역폭: 통신 채널의 최대 처리량
            * 코어 네트워크 대역폭
            * 네트워크 에지 대역폭
        * 무선 네트워크 특징, 성능 제한 요소
            * 무선 통신의 채널 용량 계산식(C)
            * 무선 통신의 대역폭
            * 무선 통신의 신호대 잡음비(SNR)
    * 네트워크 환경 영향 정리(physical layer, data link layer)
        * 통신 선로 길이
        * 매질의 굴절율
        * 링크의 용량
        * 라우터 incoming buffer의 크기
        * 무선 주파수 대역폭
        * 안테나 중계기 등 무선 통신 인프라 밀집도
        * 무선 통신 전송 전력
        * 무선 통신 SNR
    * TCP에 의한 네트워크 환경 영향
        * 흐름 제어(flow control)
        * 느린 시작(slow start)
        * 대역폭 지연곱(bandwidth delay product)
        * 혼잡 회피(conjestion avoidance)
    * prism_pacman(package manager의 약자 pacman)
* [15 Best Animation Libraries For React App](https://onaircode.com/best-animation-libraries-for-react-app/?fbclid=IwAR04EAjzK_GGwXqLKB5sGwDfjgRYCCCswe5EWOPc72GKf0YgN-Hr2t9Vx2M)
* [🚫 안티 패턴으로서의 CSS background-image 속성](https://velog.io/@chris/the-css-background-image-property-as-an-anti-pattern)
    * css background-image 단점
        * seo에 좋지 않다.
        * 접근성에 좋지 않다
        * 성능에 좋지 않다
        * CMS와 CDN에 좋지 않다.
    * ``<PICTURE>`` 를 사용
        * SEO 친화적 이미지
        * 접근성 친화적 이미지 (alt="" 속성 사용)
        * CMS-generated 이미지, CDN과 함께 잘 동작함
        * 이미지 최적화를 위한 srcset과 함께 잘 동작함
        * .webp 같은 next-generation 이미지 포맷을 위해 <source>를 사용 가능
        * 최종 예시 코드
            * ![image](https://user-images.githubusercontent.com/20143765/68020315-6e4ea600-fce1-11e9-844e-41a6f0615692.png)
                * object-fit 사용으로 background-size: cover; 대체
                * 브라우저가 지원하는경우 Lazy lading(지원하지 않으면 기본동작)
                * 브라우저가 선택할 수 있는 최적화된 반응형 이미지의 srcset.
                * 브라우저가 지원하는 경우 webp 포맷 (지원하지 않으면 skip)
* [도커 파일(Dockerfile) 작성 Best Practices](https://yeomko.tistory.com/10?fbclid=IwAR040dmDud1cEq7IJVj2tJxPpq5bXxZCXPz7tc5-3SndrgeFmrb12_zjSjw)
    * Tip #1. 순서는 캐싱에 중요하다.
        * 가장 변하지 않는 스텝을 먼저, 자주 변경되는 스텝은 아래로 배치함으로서 캐싱 최적화
    * Tip #2. 더 구체적인 COPY는 캐시 부담을 줄여준다.
    * Tip #3. 캐시할 수 있는 단위들을 구별해내라 
    * Tip #4. 불필요한 의존성을 제거하라
        * no-install-recommends 플래그 사용
    * Tip #5. 패키지 매니저 캐시를 제거하라
    * Tip #6. 가능하면 공식 이미지를 사용하라
    * Tip #7. 더 구체적인 태그를 사용하라
    * Tip #8. 가장 작은 이미지를 고르라 (Look for minimal flavors)
    * Tip #9. 일관된 환경에서 소스 코드를 빌드하라
    * Tip #10. Fetch dependencies in a separate step
        *  빌드 시에만 필요한 의존성들을 포함하느라 크기가 더 커져버릴수 있다.
    * Tip #11. 빌드 의존성을 제거하기 위해서 다단계 빌드(Multi-stage build)를 사용하라
        * AS 키워드 사용하여 참조

--- 
## 10월 블로그 총 본 개수: 55개
