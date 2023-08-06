# CORS

프로젝트를 진행하면서 프론트와 연결을 하면서 CORS라는 것을 알게되었다.  
그리고 그것이 무엇인지, 어떻게 어떻게 사용하는지, 왜 사용하는지, 누가 사용하는지, 언제 사용하는지, 어디서 사용하는지에 대해서 이번 포스팅에 작성해보려고 한다

나는 DJango와 FastAPI를 사용하니 이 두개의 프레임워크의 CORS 사용법에 대해서 작성하려고 한다.

## 🤔 CORS는 무엇인가?

우선 CORS에 대해서 설명하기 전에 SOP(Same-Origin Policy)에 대해서 설명해보려고 한다.

SOP(Same-Origin Policy)란 웹 브라우저에서 실행되는 스크립트나 리소스가 동일한 출처에서 온 것인지 여부를 검사하는 웹 보안 메커니즘입니다.  
"출처"란 프로토콜, 도메인, 포트 번호를 포함한 웹 리소스의 주소를 의미합니다.  
SOP는 웹 보안을 강화하기 위해 다른 출처로부터의 스크립트 실행 및 리소스 액세스를 제한하여 웹 애플리케이션의 취약성을 줄입니다.

-같은 오리진 길이만 데이터를 송수신 하고자 한다 라는 것이 Same Origin Policy 라는 것입니다.

CORS(Cross-Origin Resource Sharing)이란 **다른 도메인(Origin)** 간에 데이터 및 리소스를 안전하게 공유하기 위한 보안 메커니즘입니다.

웹 브라우저의 동일 출처 정책(Same-Origin Policy) 때문에 웹 페이지는 동일한 출처에서만 리소스를 요청하고 받을 수 있습니다.  
웹 보안을 위해 중요한 조치이지만, 때로는 다른 도메인 간에 데이터 공유가 필요한 상황이 발생할 수 있습니다.  
CORS는 이러한 상황에서 안전하게 데이터를 공유할 수 있도록 도와줍니다.

## 🧐 왜 필요한가?

CORS가 없이 모든 곳에서 데이터를 요청할 수 있게 된다면, 다른 사이트에서 원래 사이트를 흉내낼 수 있게 된다.

만약 기존 사이트와 완전히 동일하게 동작하도록 하여 사용자가 로그인을 하도록 하고,  
로그인했던 세션 또는 토큰을 탈취하여 악의적으로 정보를 꺼내오거나 다른 사용자의 정보를 입력하는 등 해킹을 할 수 있다.

하지만 이런 공격을 할 수 없도록 브라우저에서 보호하고,  
필요한 경우에만 서버와 협의하여 요청할 수 있도록 하기 위해서 필요한 것이다.

## ⇲ 어떻게 적용해야 되나? (Django)

django-cors-header : Cross-Origin Resource Sharing(CORS) 에 필요한 서버의 헤더를 조작하기 위한 Django 앱을 설치해야 합니다.

`pip install django-cors-header`

setiings.py 설정

```python
INSTALLED_APPS = [
...

'corsheaders',

...
]

INSTALLED_APPS 에 "corsheders" 을 추가한다.


MIDDLEWARE = [
    'corsheaders.middleware.CorsMiddleware',
    'django.middleware.common.CommonMiddleware',

    ...
]
```

MIDDELWARE 에 CorsMiddleware 소스를 추가해줍니다.  
이때 주의할점은 MIDDELWARE 최상단에 추가해 주어야 합니다.

미들웨어는 http 요청 / 응답 처리 중간에서 작동하는 시스템입니다.  
그렇기 때문에 CorsMiddleware 가 다른 미들웨어보다 아래에 있을경우, 위쪽에 있는 미들웨어들은 응답들에 CORS 헤더를 추가 할수 없게됩니다.  
그렇기 때문에 CorsMiddleware는 최상단에 추가해 주어야 합니다.

```python
##CORS
CORS_ORIGIN_ALLOW_ALL=True # <- 모든 호스트 허용
CORS_ALLOW_CREDENTIALS = True # <-쿠키가 cross-site HTTP 요청에 포함될 수 있다

CORS_ALLOW_METHODS = (  #<-실제 요청에 허용되는 HTTP 동사 리스트
    'DELETE',
    'GET',
    'OPTIONS',
    'PATCH',
    'POST',
    'PUT',
)

CORS_ALLOW_HEADERS = ( <-실제 요청을 할 때 사용될 수 있는 non-standard HTTP 헤더 목록// 현재 기본값
    'accept',
    'accept-encoding',
    'authorization',
    'content-type',
    'dnt',
    'origin',
    'user-agent',
    'x-csrftoken',
    'x-requested-with',
)

APPEND_SLASH = False #<- / 관련 에러 제거
```

## ⇲ 어떻게 적용해야 되나? (FastAPI)

아래 코드를 추가시키면 됩니다.

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=["*"],
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

- allow_origins: API에 액세스할 수 있는 허용된 오리진 목록을 지정
- allow_credentials: 쿠키를 포함시킬 수 있는지 여부를 지정
- allow_methods: HTTP 메서드의 목록을 지정
- HTTP 헤더의 목록을 지정
