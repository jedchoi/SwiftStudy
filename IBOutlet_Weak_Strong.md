

# InterfaceBuilder IBOutlet의 Strong과 Weak 이야기

- IBOutlet을 UIViewContoller로 연결할 때 weak strong 2가지 타입으로 만들 수 있다.


#### Strong으로 연결시 Reference Count
```swift
    @IBOutlet var photo: UIImageView!
    @IBOutlet var artist: UILabel!
    @IBOutlet var sponsored: UILabel!
```
  - 위 경우 UIImageView, UILabel들 모두 reference count가 증가한다.
  - dealloc 되는 시점에 이들은 모두 reference count가 0이 되고, ARC에 의해서 메모리가 정리된다.


### 그런 왜 strong으로 사용하면 안되는 것일까?
   - 메모리가 부족한경우
     - 시스템이 메모리가 부족하면 didReceiveMemoryWarning이 호출된다.
     - 이 때 main view를 nil로 만들어 메모리를 확보한다.
     - 하지만 이 경우 strong으로 subview들을 갖고 있다면 reference count를 감소시킬 수 없어서 메모리 누수가 발생한다.

## 결론 : 특별한 경우가 아니면 IBOutlet 객체를 생성할 때는 항상 weak를 사용하자!

  - 복잡한 Hierachy를 가진 구조에서 필요시 strong을 사용할 수 있지만, 이는 잘 알아보고 써야한다. (필요할 때 찾아보자)
