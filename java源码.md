版本：JavaSE-13

# Java.base模块

## Java.lang包

### Object类

#### 1.Object()构造方法

```java
public Object() {}
```



#### 2.registerNatives()方法

```java
private static native void registerNatives();
```

* 使用native修饰的方法没有方法体，将调用c/c++实现的方法
* **JNI**是Java Native Interface的缩写，建立语言标准可以使用不同语言编写代码，也允许 Java代码调用 C/C++或汇编语言编写的程序和库，
* 让JVM找到本地函数，JNI函数registerNatives()

#### 3.getclass()方法

```java
public final native Class<?> getClass();
```

class java.land.class

#### 4.hashCode()方法

```java
  public native int hashCode();
```

#### 5.equals(Object)方法

```java
    public boolean equals(Object obj) {
        return (this == obj);
    }
```

#### 6.clone()方法

```java
    protected native Object clone() throws CloneNotSupportedException;
```

#### 7.toString()方法

```java
    public String toString() {
        return getClass().getName() + "@" + Integer.toHexString(hashCode());
    }
```

#### 8.notify()方法

```java
    public final native void notify();
```



#### 9.notifyAll()方法

```java
    public final native void notifyAll();
```



#### 10wait()方法

```java
    public final void wait() throws InterruptedException {
        wait(0L);
    }
```



#### 11.wait(long)方法

```java
   public final native void wait(long timeoutMillis) throws InterruptedException;
```



#### 12.wait(long,int)方法

```java
    public final void wait(long timeoutMillis, int nanos) throws InterruptedException {
        if (timeoutMillis < 0) {
            throw new IllegalArgumentException("timeoutMillis value is negative");
        }

        if (nanos < 0 || nanos > 999999) {
            throw new IllegalArgumentException(
                                "nanosecond timeout value out of range");
        }

        if (nanos > 0 && timeoutMillis < Long.MAX_VALUE) {
            timeoutMillis++;
        }

        wait(timeoutMillis);
    }
```



#### 13.finalize()方法

​    @Deprecated(since="9")

```java
protected void finalize() throws Throwable { }
```

### Class类

#### 1.getName()方法

```java
public String getName() {
    String name = this.name;
    return name != null ? name : initClassName();
}
```
#### 2.initClassName()方法

```java
    private native String initClassName();
```

### Boolean类

```
public final class Boolean implements java.io.Serializable,Comparable<Boolean>{}
```

#### 1.TRUE

```java
public static final Boolean TRUE = new Boolean(true);
```

#### 2.FALSE

```java
public static final Boolean FALSE = new Boolean(false);
```

#### 3.TYPE

```
public static final Class<Boolean> TYPE=(Class<Boolean>) Class.getPrimitiveClass("boolean");
```

#### 4.value

```
private final boolean value;
```

#### 5.Boolean()构造方法

```

```

#### 6.serialVersionUID()

```
private static final long serialVersionUID = -3665804199014368530L;
```

#### 7.praseBoolean()

```
public static boolean parseBoolean(String s) {return "true".equalsIgnoreCase(s);}
```

#### 8.booleanValue()

```
public boolean booleanValue(){return value;}
```

#### 9.valueOf()

```
public static Boolean valueOf(boolean b) {return (b ? TRUE : FALSE);}
public static Boolean valueOf(String s){return parseBoolean(s) ? TRUE : FALSE;}
```

#### 10.toString()

```
public String toString() {return value ? "true" : "false";}
public static String toString(boolean b) {return b ? "true" : "false";}
```

#### 11.hashCode()

```
public int hashCode() {return Boolean.hashCode(value);}
public static int hashCode(boolean value) {return value ? 1231 : 1237;}

```

#### 12.equals()

```
public boolean equals(Object obj) {if (obj instanceof Boolean) {return value == ((Boolean)obj).booleanValue();}return false;}
```

#### 13.getBoolean()

```
public static boolean getBoolean(String name) {boolean result = false;try { result = parseBoolean(System.getProperty(name));} catch (IllegalArgumentException | NullPointerException e) {}return result;}
```

#### 14.compareTo()

```
 public int compareTo(Boolean b) {
        return compare(this.value, b.value);
    }
```

#### 15.compare()

```
public static int compare(boolean x, boolean y) {
        return (x == y) ? 0 : (x ? 1 : -1);
    }
```

#### 16.logicalAnd()

```
public static boolean logicalAnd(boolean a, boolean b) {
        return a && b;
    }
```

#### 17.logicalOr()

```
public static boolean logicalOr(boolean a, boolean b) {
        return a || b;
    }
```

#### 18.logicalXor()

```
public static boolean logicalXor(boolean a, boolean b) {
        return a ^ b;
}
```

### Byte类

#### 1.MIN_VALUE

```
public static final byte   MIN_VALUE = -128;
```

#### 2.MAX_VALUE

```
public static final byte   MAX_VALUE = 127;
```

#### 3.TYPE

```
public static final Class<Byte>     TYPE = (Class<Byte>) Class.getPrimitiveClass("byte");
```

#### 4.toString()

```
public static String toString(byte b) {return Integer.toString((int)b, 10);}
```







### Character类

### Double类

### Float类

### Integer类

### Long类

### Short类

### String类

### Void类

### Math类

#### 1.math()构造方法

```java
    private Math() {}
```

#### 2.E和PI字段

```java
 public static final double E = 2.7182818284590452354;
 public static final double PI = 3.14159265358979323846;
```

#### 3.角度与弧度

```java
private static final double DEGREES_TO_RADIANS = 0.017453292519943295;
private static final double RADIANS_TO_DEGREES = 57.29577951308232;
public static double toRadians(double angdeg) {return angdeg * DEGREES_TO_RADIANS;}
public static double toDegrees(double angrad) {return angrad * RADIANS_TO_DEGREES;}
```

#### 4.三角函数

```java
public static double sin(double a){return StrictMath.sin(a);}
public static double cos(double a){return StrictMath.cos(a);}
public static double tan(double a){return StrictMath.tan(a);}
public static double asin(double a){return StrictMath.asin(a);}
public static double acos(double a){return StrictMath.acos(a);}
public static double atan(double a){return StrictMath.atan(a);}
```



### StrictMath类

#### 1.StrictMath()构造方法

```java
private StrictMath() {}
```

#### 2.E和PI字段

```java
 public static final double E = 2.7182818284590452354;
 public static final double PI = 3.14159265358979323846;
```

#### 3.角度与弧度

```java
private static final double DEGREES_TO_RADIANS = 0.017453292519943295;
private static final double RADIANS_TO_DEGREES = 57.29577951308232;
public static strictfp double toRadians(double angdeg){return angdeg*GREES_TO_RADIANS;}
public static strictfp double toDegrees(double angrad){return angrad *RADIANS_TO_DEGREES;}
```

#### 4.三角函数

```java
public static native double sin(double a);
public static native double cos(double a);
public static native double tan(double a);
public static native double asin(double a);
public static native double acos(double a);
public static native double atan(double a);
```



### 