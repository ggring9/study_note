# Junit

## [Junit 사용법](https://javadoc.io/doc/junit/junit/latest/index.html)

클래스별로 Annotation을 이용해서 테스트 방법을 정의하며,
사용되는 Annotation은 다음과 같다.

- Before

  테스트 메서드를 실행하기 전에 클래스 객체 초기화할때 사용함. 
  
- Rule



- AfterClass  



- Test

  테스트케이스로 수행될 수 있는 public void 형태의 메서드임을 명시하며
  2가지 옵션을 제공함.
  - Exception 테스트
    
    특정 예외처리를 예상할때 사용함. 예외유형만 확인가능하며, 특정코드를 지정하지는 않음

  - Timeout 테스트
    
    해당 메서드가 지정된 시간보다 오래 걸리는 경우에 실패함

- After

  테스트 메서드 수행 후 실행하는 작업으로, 자원반환 혹은 생성된 파일 삭제등의 작업을 진행함

- FixMethodOrder



- Ignore



- BeforeClass



- ClassRule

---

- @Test(timeout=5000) //millisecond
  시간 테스트 

- 예외처리 테스트 

``` java
package lee.junit;
 
import static org.junit.jupiter.api.Assertions.assertEquals;
import org.junit.Test;
 
public class CalculatorTest {
  //@Test(timeout=5000)  : 시간단위 : 밀리초
  //@Test(expected=RuntimeException.class) : RuntimeException이 발생해야 성공
  //@Ignore(value=”test”)
  //@Before 해당 테스트 클래스의 객체를 초기화하는 작업
  //@After 해당 테스트  실행 수 실행
  //@BeforeClass 테스트 클래스 실행 전 한번 실행
  //@AfterClass 테스트 클래스 실행 후 한번 실행
  @Test
  public void testSum( ) {
    Calculator cal = new Calculator();
    int result = cal.sum(10, 20);
    assertEquals(20,  result, 10);
  }
}

// 출처: https://lee-mandu.tistory.com/398?category=633568 [개발/일상_Mr.lee]
```