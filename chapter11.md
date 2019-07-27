Chapter 11. 구조체(Structure)
===========================

### 여러 값을 하나로 묶기\
구조체는 여러 데이터를 한데 모아햐 할 때 유용하게 사용할 수 있다.
~~~
struct SpaceShip {
  int x_coord;
  int y_coord;
  string mane;
}; // 세미콜론 빠뜨리지 말 것!

// 선언 및 초기화
SpaceShpi my_ship;

my_ship.x_coord = 40;
my_ship.y_coord = 40;
my_ship.name = "USS Enterprise (NCC - 1701 - D)";
~~~

### 구조체 전달하기
구조체에서 인수로 받거나 리턴하는 함수를 작성해야 할 때가 있다.
Example 1. upgrade.cpp
~~~
struct EnemySpaceShip {
  int x_coord;
  int y_coord;
  int weapon_power;
};

EnemySpaceShip getNewEnemy() {
  EnemySpaceShip ship;
  ship.x_coord = 0;
  ship.y_coor = 0;
  ship.weapon_power = 20;
  return ship;
}

EnemySpaceShip upgradeWeapons ( EnemySpaceShip Ship) {
  ship.weapon_power += 10;
  return ship;
}

int main() {
  EnemySpaceShip enemy = getNewEnemy();
  enemy = upgradeWeapons ( enemy);
}
~~~
하지만 이렇게 해봐야 한 번에 처리할 수 있는 우주선은 고작 10척이다. 더 많은 우주선을 처리하기 위해선 '포인터'라는 개념이 필요하다.
