# reext
> java regular expression extension library

Maven configuration:

    <dependency>
        <groupId>com.github.jeppeter</groupId>
        <artifactId>reext</artifactId>
        <version>1.0</version>
    </dependency>

Gradle configuration

```groovy
    compile group: 'com.github.jeppeter', name: 'reext', version: '1.0'
```

### Split string
```java
    import com.github.jeppeter.reext.ReExt;
    public class ReExtTest {
        public static void main(String[] args) {
            String restr="\\s+";
            String instr ="hello world";
            String[] retstr = ReExt.Split(restr,instr);
            int i;
            for (i=0;i<retstr.length;i++) {
                System.out.println(String.format("[%d]=%s",i,retstr[i]));
            }
            instr = "cc ss bb";
            retstr = ReExt.Split(restr,instr,2);
            System.out.println("split max limit");
            for (i=0;i<retstr.length;i++) {
                System.out.println(String.format("[%d]=%s",i,retstr[i]));
            }
        }
    }
```
> result is
```shell
[0]=hello
[1]=world
split max limit
[0]=cc
[1]=ss bb
```

### get match part
```java
    import com.github.jeppeter.reext.ReExt;
    public class ReExtTest {
        public static void main(String[] args) {
            ReExt ext = new ReExt("([\\d]+)cc([\\d]+)");
            int maxcnt;
            int i;
            ext.FindAll("33cc55");
            maxcnt = ext.getCount(0);
            for (i=0;i<maxcnt;i++) {
                System.out.println(String.format("[0,%d]=%s",i,ext.getMatch(0,i)));
            }
            System.out.println(String.format("[-1,0]=%s",ext.getMatch(-1,0)));
            System.out.println(String.format("[0,2]=%s",ext.getMatch(0,2)));
        }
    }
```

> result is
```shell
[0,0]=33
[0,1]=55
[-1,0]=null
[0,2]=null
```

