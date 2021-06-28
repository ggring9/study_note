# Refactoring
 
## 자바로 배우는 리팩토링 입문
 
0. 리팩토링이란

1. 매직 넘버를 기호 상수로 치환 
    - 소스 코드에 100이라고 적힌 경우
    - ReplaceMagicNumberWithSymbolicConstant
2. 제어 플래그 삭제 
    - 제어 플래그 때문에 코드가 읽기 어려운 경우
    - RemoveControlFlag
3. 어서션 도입 
    - ‘이렇게 될 것이다’라는 주석이 있는 경우
    - IntroduceAssertion
4. 널 객체 도입 
    - null 확인이 너무 많은 경우
    - IntroduceNullObject
5. 메서드 추출 
    - 코드가 너무 길어서 읽기 어려운 경우
    - ExtractMethod
6. 클래스 추출 
    - 클래스의 책임이 너무 많은 경우
    - ExtractClass
7. 분류 코드를 클래스로 치환 
    - int로 객체를 구분하는 경우
    - ReplaceTypeCodeWithClass
8. 분류 코드를 하위 클래스로 치환 
    - 분류 코드마다 동작이 다른 경우(1)
    - ReplaceTypeCodeWithSubclasses
9. 분류 코드를 상태/전략 패턴으로 치환 
    -  분류 코드마다 동작이 다른 경우(2)
    - ReplaceTypeCodeWithStateStrategy
10. 에러 코드를 예외로 치환 
    - 에러 처리가 흩어져 있는 경우
    - ReplaceErrorCodeWithException
11. 생성자를 팩토리 메서드로 치환 
    - 클래스 이름이 new로 하드 코딩된 경우
    - ReplaceConstructorWithFactoryMethod
12. 관측 데이터 복제 
    - 모델과 뷰가 뒤섞여 있는 경우
    - DuplicateObservedData
13. 상속을 위임으로 치환 
    - IS-A 관계가 아닌데 상속하고 있는 경우
    - ReplaceInheritanceWithDelegation
14. 대리자 은폐 
    - 위임 대상까지 노출되어 있는 경우
    - HideDelegate
15. 상속 구조 정리 
    - 상속이 엉켜 있는 경우
    - TeaseApartInheritance


---

## 2. 제어 플래그 삭제 

제어플래그 남용시 소스코드의 흐름을 이해하기 어렵게 되기 때문에
플래그 대신 break, continue, return 등을 통해서 처리흐름을 제어하는것이 읽기 좋다.

단 return을 여러개 두는 것은 개발자별로 호불호가 갈릴 수있음.
찬성) 결과값을 찾았다는 상태를 끝까지 가지고기 위해서 별도의 변수(플래그)가 필요하게 될 수도 있음. 혹은 변경될 수도 있음.

플래그는 최소 범위에서 사용하는것이 바람직함.
클래스단위의 인스턴스 필드를 사용하게 되면 메서드 종료 이후에도 상태를 유지하기때문에 코드를 읽기 어려워짐.
특히 public 형태의 필드로 사용하게된다면 더욱 어려워짐.

보편적인 플래그명(flag, state, mode)보다는 명확한 의미를 가진 플래그명을 사용하는 것이 바람직함.
- initialized (초기화 완료)
- debug (디버깅 중)
- error (객체에서 에러 발생)
- broken (데이터 손상됨)
- done (처리 완료)
- found (값 찾음)
- aborted (처리가 중단됨)
- interrupted (인터럽트 발생)
- _recurse_ (컴포지트 패턴을 사용할 경우, 재귀로 메서드를 사용할지에 대한 여부)

recurse는 아직 이해 못함. 컴포지트패턴? 디자인패턴 이해 필요할듯..






