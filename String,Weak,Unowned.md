# Strong
1. 해당 인스턴스의 소유권을 가짐
2. 자신이 참조하는 인스턴스의 retain count를 증가시킴
3. 값 지정시점에 retain이 증가되고 참조가 종료되는 시점에 release됨
4. 선언할 때 아무것도 적지 않으면 기본적으로 stong임


# Weak
1. 해당 인스턴스의 소유권을 가지지 않고, 주소값만을 가지고 있는 포인터 개념
2. 자신이 참조하는 인스턴스의 retain count를 증가시키지 않고, release도 발생하지 않음
3. 자신이 참조하는 하지만 weak 메모리를 해제시킬 수 있는 권한은 다른 클래스에 있다.
4. 메모리가 해제될 경우 자동으로 레퍼런스가 nil로 초기화 해준다.
5. Weak 속성을 사용하는 객체는 항상 optional 이어야한다.


# Unowned
1. 해당 인스턴스의 소유권을 가지지 않는다.
2. 자신이 참조하는 인스턴스의 retain count를 증가시키지 않는다.
3. Nil이 될 수 없다. optional로 선언되면 안된다.



# Weak, unowned 차이
1. weak는 객체를 계속 추적하면서 객체가 사라지게 되면 nil로 바꾼다.
2. 하지만 unowned는 객체가 사라지게 되면 댕글링 포인터가 남는다. 이 때 참조하면crash가 발생한다. 그래서 unowned는 사라지지 않을거라고 보장되는 객체에만 설정하여야 한다.