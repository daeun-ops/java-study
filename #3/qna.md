### Q1 instanceof 연산자의 반환값은 Boolean 뿐인가요?
- 네, boolean (true 또는 false) 입니다.

### Q2 ((int)num / 100) * 100이 제대로 동작하지 않는 이유
- num이 double이면 (int)num 변환 과정에서 소수점이 버려져서
- int라도  음수일 경우 정수 나눗셈이 반올림 없이 처리되어서

###  Q3 if 할 떄 꼭 else 로 끝내야하는지
- else if로 끝내는 경우, 반드시 else로 끝낼 필요는 없습니다.
조건을 모두 확인한 후, 만약 다른 경우에 대한 처리가 필요 없다면 else를 생략해도 됩니다.

### Q4 "car변수가 Object타입으로 형변환이 가능한지? => true"
- null 값은 어떤 타입으로든 형변환이 가능합니다. 즉, null은 Object 타입으로도 형변환이 가능합니다. 따라서 이 부분은 true입니다.
### `Car car = null;`

- `car` 변수는 `Car` 타입으로 선언되었고, `null` 값을 할당합니다. `null`은 어떤 객체도 참조하지 않기 때문에 `instanceof` 연산자와 함께 사용하면 항상 `false`를 반환할 것 같지만, 예외적으로 `null`에 대해서는 어떤 클래스의 인스턴스도 아니기 때문에 `false`로 평가되지 않습니다.

### `System.out.println(car instanceof Object); // false`

- `car`가 `null`이기 때문에 `instanceof` 연산자는 `false`를 반환합니다. `null`은 어떤 객체도 참조하지 않기 때문에 `instanceof` 연산자를 사용할 수 없습니다.

### Q5  객체가 특정 클래스 또는 인터페이스의 인스턴스인지 확인하는 연산자입니다. 각 줄을 하나씩 자세히 알고 싶음!
```java
class Animal{}
class Dog extends Animal{}
class Cat extends Animal{}

public class T {
    public static void main(String[] args){
        Animal animal = new Animal();
                System.out.println(animal instanceof Object); // true
        System.out.println(animal instanceof Animal); // true
        System.out.println(animal instanceof Dog); // false
        System.out.println(animal instanceof Cat); // false

        Animal cat = new Cat();
                System.out.println(cat instanceof Object); // true
        System.out.println(cat instanceof Animal); // true
        System.out.println(cat instanceof Dog); // false
        System.out.println(cat instanceof Cat); // true

        Animal dog = new Dog();
                System.out.println(dog instanceof Object); // true
        System.out.println(dog instanceof Animal); // true
        System.out.println(dog instanceof Dog); // ture
        System.out.println(dog instanceof Cat); // false
```

### 1. `Animal animal = new Animal();`

- `Animal` 클래스를 인스턴스화한 객체를 `animal` 변수에 할당합니다.

### 2. `System.out.println(animal instanceof Object); // true`

- `animal` 객체는 `Animal` 클래스의 인스턴스이고, 모든 클래스는 `Object` 클래스를 상속받기 때문에 `instanceof Object`는 항상 `true`입니다.

### 3. `System.out.println(animal instanceof Animal); // true`

- `animal` 객체는 `Animal` 클래스의 인스턴스이므로 `instanceof Animal`은 `true`입니다.

### 4. `System.out.println(animal instanceof Dog); // false`

- `animal` 객체는 `Dog` 클래스의 인스턴스가 아니므로 `instanceof Dog`는 `false`입니다.

### 5. `System.out.println(animal instanceof Cat); // false`

- `animal` 객체는 `Cat` 클래스의 인스턴스가 아니므로 `instanceof Cat`은 `false`입니다.

---

### 6. `Animal cat = new Cat();`

- `Animal` 타입의 `cat` 변수에 `Cat` 클래스의 객체를 할당합니다. 여기서 다형성(상속 관계)을 활용하고 있습니다.

### 7. `System.out.println(cat instanceof Object); // true`

- `cat` 객체는 `Object` 클래스를 상속한 `Cat` 클래스의 인스턴스이므로 `instanceof Object`는 `true`입니다.

### 8. `System.out.println(cat instanceof Animal); // true`

- `cat` 객체는 `Animal` 클래스를 상속한 `Cat` 클래스의 인스턴스이므로 `instanceof Animal`은 `true`입니다.

### 9. `System.out.println(cat instanceof Dog); // false`

- `cat` 객체는 `Dog` 클래스의 인스턴스가 아니므로 `instanceof Dog`는 `false`입니다.

### 10. `System.out.println(cat instanceof Cat); // true`

- `cat` 객체는 `Cat` 클래스의 인스턴스이므로 `instanceof Cat`은 `true`입니다.

---

### 11. `Animal dog = new Dog();`

- `Animal` 타입의 `dog` 변수에 `Dog` 클래스의 객체를 할당합니다.

### 12. `System.out.println(dog instanceof Object); // true`

- `dog` 객체는 `Object` 클래스를 상속받은 `Dog` 클래스의 인스턴스이므로 `instanceof Object`는 `true`입니다.

### 13. `System.out.println(dog instanceof Animal); // true`

- `dog` 객체는 `Animal` 클래스를 상속한 `Dog` 클래스의 인스턴스이므로 `instanceof Animal`은 `true`입니다.

### 14. `System.out.println(dog instanceof Dog); // true`

- `dog` 객체는 `Dog` 클래스의 인스턴스이므로 `instanceof Dog`는 `true`입니다.

### 15. `System.out.println(dog instanceof Cat); // false`

- `dog` 객체는 `Cat` 클래스의 인스턴스가 아니므로 `instanceof Cat`은 `false`입니다.



---


