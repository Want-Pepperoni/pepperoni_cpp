Chapter 7. switch case와 enum
=============================

이번 chapter에서는 if-else문을 대신할 수 있는 switch case문을 알아본다.

### switch case
switch case문의 기본 형식은 다음과 같다.
~~~
switch( <변수>) {
  case 이런 값:
    <변수> == 이런 값 일 때 실행될 코드
    break;
  case 저런 값:
    <변수> == 저런 값 일 때 실행될 코드
    break;
  default:
    <변수>가 case의 어떤 값도 아닐 때 실행될 코드
    break;
  }
~~~

example 1. 게임 메뉴를 띄우고 유저가 선택하는 번호에 따라 다음 메뉴로 넘어갈 수 있는 페이지를 만들어라.
~~~
#include <iostream>

using namespace std;

void playgame() {}
void loadgame() {}
void playmultiplayer() {}

int main() {
    int input = 0;
    while (input < 1 || input > 4){
        cout << "1. Play game\n";
        cout << "2. Load game\n";
        cout << "3. Play Multiplayer\n";
        cout << "4. Exit\n";
        cout << "Selection: ";
        cin >> input;
        switch( input) {
            case 1:
                playgame();
                break;
            case 2:
                loadgame();
                break;
            case 3:
                playmultiplayer();
                break;
            case 4:
                cout << "Thank you for playing!\n";
                break;
            default:
                cout << "Error, bad input, quitting\n";
                break;
        }
    }
}
~~~

### 열거형을 사용하여 단순 타입 만들기
무지개 색상을 열거형 타입(enumerated type)으로 만들어 보자.

~~~
enum RainbowColor {
  RC_RED, RC_ORANGE, RC_YELLOW, RC_GREEN, RC_BLUE, RC_INDIGO, RC_VIOLET
  };
~~~

- enum 키워드는 새로운 열거형 변수를 소개할 때 사용한다.
- 이제 이 새로운 타입에 고유 이름을 지정한다. 여기서는 RainbowColor가 새로운 변수의 이름이다.
- 이 타입으로 나타낼 수 있는 값들을 리스트로 열거한다.
- ;은 당연히 마지막에 붙인다.

이제 RainbowColor라는 새로운 타입을 다음과 같이 사용할 수 있다.
~~~
RainbowColor chosen_color = RC_RED;
~~~

또는 Switch case를 이용해 다음과 같이 사용할 수 있다.
~~~
switch (chosen_color) {
  case RC_RED:
  case RC_ORANGE:
  ...
  case RC_VIOLET:
  default:
}
~~~
