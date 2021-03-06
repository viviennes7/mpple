# mpple

## init 

### example

```java

public class Foo {

    private String firstName;
    private String lastName;

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }
}


public class FooDto {

    private String firstName;
    private String lastName;

    public String getFirstName() {
        return firstName;
    }

    public void setFirstName(String firstName) {
        this.firstName = firstName;
    }

    public String getLastName() {
        return lastName;
    }

    public void setLastName(String lastName) {
        this.lastName = lastName;
    }
}


public interface FooMapper {

    FooDto foo(Foo foo);
}

public static void main(String[] args) {
    FooMapper fooMapper = Mpple.builder()
        .target(FooMapper.class);
    Foo foo = new Foo();
    foo.setFirstName("wonwoo");
    foo.setLastName("lee");
    assertThat(fooMapper.bar(foo)).isEqualTo("wonwoo");
}

```


### for spring 

```java
@EnableMppled
public class MppleSpringConfig {

}

@Mppled
public interface FooMapper {
    FooDto bar(Foo foo);
}

@Autowired
private FooMapper fooMapper;

@Test
public void mappingTest() {
    Foo foo = new Foo();
    foo.setFirstName("wonwoo");
    foo.setLastName("lee");
    FooDto fooDto = fooMapper.foo(foo);
    assertThat(fooDto.getFirstName()).isEqualTo("wonwoo");
    assertThat(fooDto.getLastName()).isEqualTo("lee");
}

```

### for spring boot

```java
@Mppled
public interface FooMapper {

    FooDto foo(Foo foo);   
}

@Autowired
private FooMapper fooMapper;

@Test
public void mappingTest() {
    Foo foo = new Foo();
    foo.setFirstName("wonwoo");
    foo.setLastName("lee");
    FooDto fooDto = fooMapper.foo(foo);
    assertThat(fooDto.getFirstName()).isEqualTo("wonwoo");
    assertThat(fooDto.getLastName()).isEqualTo("lee");
}

```
