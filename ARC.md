# ARC
1. Auto Reference Counting
3. 자동으로 메모리 관리해주는 친구
4. 객체에 대한 참조 카운트를 관리하고 0이되면 자동으로 매모리 해제
5. Build time에 실행됨


# Garbage Collection
1. Garbage Collector가 존재
2. 런타임에 Collector가 더이상 사용이 필요하지 않는 것들을 메모리에서 해제
3. 동작 원리
  - Garbage Collection Root : 힙 외부에서 접근할 수 있는 변수/object 
  - Mark : Root로 부터 참조로 연결된 모든 오브젝트를 mark 하는 행위
  - Sweep : mart되지 않은 모든 객체를 해제(reclaim)
  - 요약 : Root로부터 Unreachable한 모든 객체를 메모리에서 해제하는 방식


# ARC와 Garbage Collection과의 차이
1. 참조 계산 시점의 차이
 - ARC : Compile Time에 reference에 따라 retain/release 코드를 삽입
 - Garbage Collection : 런타임

2. 순환참조 해결
 - ARC : retain cycle이 생성되면 해제 불가. 메모리 누수 발생
 - Garbage Collection : cycle이 생겨 해제되지 않아 메모리 누수의 원인이 되는 object들을 메모리에서 해제
* 메모리 누수 : 순환참조로 인해 해제되지 않지만, 외부참조가 사라지면 이것이 메모리 누수가 된다.

3. 성능
 - ARC : Compile 타임에 참조/해제 시점을 모두 계산하기 때문에 런타임 성능에 영향을 주지 않는다.
 - Garbage Collection : Collector가 런타임에 계속 mark/sweep을 반복하므로 성능에 영향을 미친다.
