
### 기본 타입과 커스텀 타입


#### 기본 타입

타입스크립트는 변수 선언후, 타입과 함께 세미콜론을 붙입니다.
```typescript
let firstName: string;
let age: number;
```

#### 원시 타입
+ string - 문자열
+ boolean - true / false 값
+ number - 숫자
+ symbol -  Symbol 생성자를 호출해 생성된 고윳값 (ES6에 추가된 변경 불가능한 원시타입)
+ any - 모든 타입을 허용하는 타입
+ unknown - any와 비슷하나 먼저 타입을 지정하거나 좁히지 않으면 조작이 허용되지 않음
+ never - 도달할 수 없는 코드를 나타냄
+ void - 값이 없음

symbol은 ES6에 추가된 변경 불가능한 원시 타입으로 객체 프로퍼티를 만들 수 있습니다.
```typescript
const sym1 = Symbol("ID");
const sym2 = Symbol("ID");
```

위 코드에 sym1과 sym2의 값은 동일하지 않습니다. 새 symbol을 추가할 때 new 키워드는 생략되고 객체 프로퍼티의 고유값을 가진 키를 생성할 떄 사용됩니다.
```typescript
const sym = Symbol("ID");
const test = {
    sym: "123"
};

console.log(test['sym']);    // 123 출력
```

타입스크립트 역시 자바스크립트에서 '값이 없음;을 나타내는 null과 undefined 타입을 가집니다.
값이 할당되지 않은 변수는 초기값으로 undefined를 가지며 그 자체로 undefined 타입입니다. 값을 반환하지 않는 함수 역시 undefined를 반환합니다. 반면 null은 명시적으로 값이 비어있음을 나타내며 객체입니다.
null과 undefined는 모든 변수에 할당할 수 있습니다.

아래 코드는 string 또는 null을 반환하는 함수입니다. (| 표시는 union타입입니다.)

```typescript
function getString(): string | null{

    // ..dosomething

    return null;
}
```

대부분 프로그래밍 언어와 마찬가지로 string을 반환하는 함수지만 null을 반환할 수 있는 가능성이 있지만 위와 같이 명시적으로 작성해주면 코드 가독성이 향상됩니다.


any 타입은 숫자, 문자열, boolean, 또는 커스텀 타입 값을 할당할 수 있지만 타입 체크의 장점을 잃고 코드 가독성이 떨어지기 때문에 되도록이면 사용하지 않는 걸 권장합니다.


never 타입은 절대 반환을 하지 않는 함수에 사용됩니다. 절대로 실행이 종료되지 않는 함수나 오류를 발생시키기 위해서만 존재하는 함수를 예로 들 수 있습니다. 아래 코드는 반환되지 않는 무한 루프이며 타입 검사기는 never타입으로 유추합니다.
```typescript
const logger = () => {
    while(true){
        console.log('서버가 실행중입니다.')
    }
}
```

void 타입은 변수 선언이 아니라, 값을 반환하지 않는 함수를 선언하는 데 사용합니다.
```typescript
function printError(err_msg: string) : void{
    console.log('Error!');
}
```
never 타입과는 다르게 void 함수는 실행을 완료하지만 값을 반환하지 않습니다.



