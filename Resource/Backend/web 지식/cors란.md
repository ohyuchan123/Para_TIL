### CORS란 무엇인가?

---

브라우저에서는 보안적인 이유로 `cross-origin` HTTP 요청들을 제한합니다. 그래서 `cross-origin` 요청을 하려면 서버의 동의가 필요합니다. 만약 서버가 동의한다면 브라우저에서는 요청을 허락하고, 동의하지 않는다면 브라우저에서 거절합니다.

이러한 허락을 구하고 거절하는 메커니즘을 HTTP-header를 이용해서 가능한데, 이를 CORS(Cross-Origin Resource Sharing)라고 부릅니다.

그래서 브라우저에서 `cross-origin` 요청을 안전하게 할 수 있도록 하는 메커니즘이다.

**cross-origin**

`cross-origin` 이란 다음 한 가지라도 다른 경우를 말합니다.

1. [프로토콜](https://www.notion.so/81a4fd94a64c4cc4b4dd3843baab3c74) - http와 https는 프로토콜이 다르다
2. [도메인](https://www.notion.so/62d9d1061bee430c8e184a77c6af9486) - domain.com과 other-domain.com은 다르다
3. 포트 번호 - 8080 포트와 3000 포트는 다르다.

### CORS는 어떻게 동작하나

---

**Simple requests인 경우**

1. 서버로 요청을 합니다.
2. 서버의 응답이 왔을 때 브러우저가 요청한 Origin과 응답한 헤더 `Access-Control-Request-Headers` 의 값을 비교하여 요효한 요청이라면 리소스를 응답합니ㅏㄷ. 만약 유효하지 않은 요청이라면 브라우저에서 이를 막고 에러가 발생합니다.

**simple request란?**

HTTP method가 다음 중 하나이면서

- GET
- HEAD
- POST

자동으로 설정되는 헤더는 제외하고, 설정할 수 있는 다음 헤더들만 변경하면서

- Accept
- Accept-Language
- Conent-Language

`Content-Type`이 다음과 같은 경우

- application/x-www-form-urlencoded
- multipart/form-data
- text/plain

Simple requqets라고 부릅니다. 이 요청은 추가적으로 확인하지 않고 바로 본 요청을 보냅니다.