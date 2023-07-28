# Avoiding game Interpretation

이번 포스팅에서는 pang-game을 제작하기 전에 간단하게 pygame에 대해서 알아가기 위해서 제작한 피하기 게임에 대한 코드 해석을 작성하려고 한다.

- <a href="https://github.com/python-personal-project/Pang-Game/blob/main/Avoiding%20game/Avoding-Game_ReadMe.md">Avoding game Interpretation</a>

먼저 목차는

1. 창 생성
2. 배경화면 생성
3. 캐릭터(스프라이트) 불러오기
4. 키보드 이벤트
5. FPS(Frame Per Second) 초당 프레임 수
6. Collision(충돌 처리)
7. text(글자 처리)

이렇게 작성하려고 한다.

## 1. Create Frame(창 생성)

```python
import pygame


pygame.init()  # 초기화(반드시 필요)

# 화면 크기 설정
screen_width = 480  # 가로 크기
screen_height = 640  # 세로 크기

screen = pygame.display.set_mode((screen_width, screen_height))

# 화면 타이틀 설정
pygame.display.set_caption("Pang-Pygame")

# 이벤트 루프
running = True  # 게임이 진행중인가?
while running:
    for event in pygame.event.get():  # 어떤 이벤트가 발생하였는가?
        if event.type == pygame.QUIT:  # 창이 닫히는 이벤트가 발생하였는가?
            running = False  # 게임이 진행중이 아님

# pygame 종료
pygame.quit()
```

### 코드 해석

#### Pygame

---

먼저 pygame이란 python을 기반으로 한 2D 게임 라이브러리입니다.  
pygame은 오픈 소스 라이브러리로서 무료로 사용할 수 있으며 다양한 운영체제에서 동작합니다.

**주요 기능**

1. 2D 그래픽 지원: Pygame은 2D 그래픽을 손쉽게 표현할 수 있도록 다양한 그래픽 함수와 도구들을 제공합니다.  
   이미지, 도형, 텍스트 등을 그릴 수 있으며, 게임 객체와 배경을 다루는 기능을 제공합니다.
2. 이벤트 처리: 사용자 입력(키보드, 마우스 등)에 대한 이벤트를 처리할 수 있습니다.  
   이벤트를 감지하고 해당 이벤트에 따른 동작을 수행할 수 있도록 지원합니다.
3. 사운드 지원: Pygame은 게임에 음향 효과를 추가할 수 있는 사운드 기능을 제공합니다.  
   오디오 파일 재생, 음악 루프, 음량 조절 등의 기능을 사용할 수 있습니다.
4. 충돌 감지: 게임 객체들 간의 충돌을 감지하고 처리하는 기능을 제공합니다.  
   충돌 감지를 통해 게임의 상호작용과 충돌 시의 동작을 제어할 수 있습니다.
5. 사용자 정의 가능: Pygame은 파이썬 언어의 특성을 그대로 활용하므로,  
   개발자들은 강력한 파이썬 기능을 활용하여 게임을 더욱 자유롭게 제작할 수 있습니다.

#### pygame.init()

---

`pygame.init()`은 Pygame 라이브러리를 사용하기 전에 초기화하는 함수입니다.  
Pygame을 사용하여 게임 또는 그래픽 애플리케이션을 개발하기 전에 반드시 호출해야 합니다.  
이 함수는 Pygame 라이브러리를 사용할 준비를 하고 필요한 모든 모듈을 초기화합니다.

#### pygame.display

---

`pygame.display는 Pygame 라이브러리에서 게임 창과 관련된 기능을 제공하는 모듈입니다.  
이 모듈은 게임 창을 생성하고 조작하는 데 필요한 상수들을 포함하고 있습니다.

주요 기능과 상수들

1. `set_mode()` : 게임 창을 생성하고 크기와 옵션을 설정하는 함수로, 앞서 설명한 대로 게임 창을 만듭니다.
2. `update()` : 게임 화면을 업데이트하는 함수로, 게임 창에 변경된 그래픽을 표시합니다.
3. `set_caption()` : 게임 창의 제목(타이틀)을 설정하는 함수입니다.
4. `flip()` : update()와 비슷하게 게임 화면을 업데이트하는 함수로, 두 함수 모두 그래픽을 화면에 표시합니다.
5. `get_surface()` : 현재 게임 창의 Surface 객체를 가져옵니다. Surface는 그림을 그리거나 이미지를 표시하는 데 사용되는 객체입니다.
6. `quit()` : Pygame의 기능을 종료하고 메모리를 해제하는 함수로, 프로그램 종료 시에 호출합니다.

**pygame.display.set_mode()**

`pygame.display.set_mode()`은 Pygame에서 게임 창 또는 화면을 생성하는 함수입니다.  
이 함수를 사용하여 게임의 그래픽 출력을 담당하는 창을 만들 수 있습니다.

`pygame.display.set_mode()` 함수는 다음과 같은 형식으로 호출됩니다.

```python
pygame.display.set_mode((width, height), flags=0, depth=0)
```

- `width` : 게임 창의 가로 너비를 나타내는 정수값입니다.
- `height` : 게임 창의 세로 높이를 나타내는 정수값입니다.
- `flags` : 게임 창에 대한 여러 옵션을 지정할 수 있는 플래그(Flag)입니다.  
  기본값은 0으로, 특별한 옵션을 사용하지 않을 때는 생략하거나 0을 넣으면 됩니다.
- `depth`: 색 깊이를 나타내는 정수값으로, 기본값은 0으로, 특별한 색상 깊이를 지정하지
  않을 때는 생략하거나 0을 넣으면 됩니다.

**pygame.display.set_caption()**

`pygame.display.set_caption`은 Pygame에서 게임 창의 제목(타이틀)을 설정하는 함수입니다.  
이 함수를 사용하면 게임 창의 제목을 원하는 문자열로 변경할 수 있습니다.

`pygame.display.set_caption()` 함수는 다음과 같은 형식으로 호출됩니다.

```python
pygame.display.set_caption(title)
```

#### pygame.event

---

`pygame.event`는 Pygame 라이브러리에서 이벤트 처리와 관련된 기능을 포함하는 모듈입니다.  
이 모듈은 사용자 입력(키보드, 마우스) 및 시스템 이벤트(창 종료 등)를 감지하고 처리하는 데 사용됩니다.

Pygame에서 이벤트란 사용자의 입력이나 시스템의 상태 변화와 같은 다양한 상호작용을 의미합니다.  
이벤트를 적절히 처리함으로써 게임이나 애플리케이션은 사용자와 상호작용하고 반응하는 동적인 동작을 보여줄 수 있습니다.

`pygame.event` 모듈은 이벤트 처리를 위해 다양한 기능을 제공합니다. 주요 기능과 함수들은 다음과 같습니다:

1. `pygame.event.get()` : 이벤트 큐에서 현재 발생한 이벤트들을 리스트로 가져옵니다.  
   이 함수는 앞서 설명한 대로 사용자 입력과 시스템 이벤트 등을 감지합니다.
2. `pygame.event.poll()` : 큐에 이벤트가 있으면 첫 번째 이벤트를 가져오고, 큐가 비어있으면 바로 리턴합니다.  
   get()과 다르게 기다리지 않고 바로 이벤트를 가져오므로 비동기적으로 사용할 수 있습니다.
3. `pygame.event.wait()` : 이벤트 큐에서 이벤트가 발생할 때까지 대기합니다. 이벤트가 발생하면 첫 번째 이벤트를 가져옵니다.  
   블로킹 함수이므로 이벤트가 발생할 때까지 프로그램의 실행이 멈춥니다.
4. `pygame.event.set_blocked(), pygame.event.set_allowed()` : 특정 이벤트의 발생을 막거나 허용할 수 있습니다.
5. `pygame.event.Event` : 이벤트 객체를 생성할 때 사용하는 클래스입니다. 다양한 종류의 이벤트를 생성하고 사용할 수 있습니다.

이 외에도 다양한 함수와 상수들이 pygame.event 모듈에서 제공됩니다.  
이들 함수와 상수를 적절히 사용하여 이벤트를 감지하고 처리함으로써 게임이나 애플리케이션의 동작을 제어할 수 있습니다.

**pygame.event.get()**  
`pygame.event.get()`은 Pygame에서 발생한 이벤트들을 가져오는 함수입니다.  
이 함수를 호출하면 이벤트 큐(Event Queue)에 저장된 모든 이벤트들을 리스트로 반환합니다.

Pygame에서 이벤트란 사용자 입력(키보드, 마우스)이나 윈도우 관련 이벤트(창 종료 등) 등 다양한 상호작용을 의미합니다.  
사용자의 입력을 감지하고 이벤트를 처리하는 것은 게임 또는 애플리케이션의 동작에 중요한 역할을 합니다.

`pygame.event.get()` 함수는 다음과 같이 호출됩니다:

```python
event_list = pygame.event.get()
```

위의 호출 결과로 event_list에는 현재 발생한 이벤트들이 리스트 형태로 저장됩니다.  
리스트에 저장된 각각의 이벤트는 pygame.event.Event 객체로서 다양한 속성과 메서드를 가지고 있습니다.  
이벤트 종류, 키보드 키의 코드, 마우스의 위치 등의 정보를 확인하여 원하는 동작을 수행할 수 있습니다.

일반적으로 게임 루프 안에서 pygame.event.get() 함수를 반복해서 호출하여 발생한 이벤트들을 처리합니다.

### 실행 이미지

![Alt text](/python/Python-Interpretation/img/image.png)

## 2. 배경화면 생성
