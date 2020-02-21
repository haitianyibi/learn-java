版本：JavaSE-13

# Java.base模块

定义Java S平台的基础API

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

# Java.compller模块

定义语言模型，注释处理和Java编译器API

# Java.datatransfer模块

定义用于在应用程序之间和应用户程序内部传输数据的API

# Java.desktop模块

定义AWT和Swing用户界面工具包，以及用于辅助功能，音频，图像，打印和JavaBean的API。

# java.instrument 

定义允许代理检测在JVM上运行的程序的服务。

# java.logging	
定义Java Logging API。
# java.management	
定义Java管理扩展（JMX）API。
# java.management.rmi	
为Java管理扩展（JMX）远程API 定义RMI连接器。
# java.naming	
定义Java命名和目录接口（JNDI）API。
# java.net.http	
定义HTTP客户端和WebSocket API。
# java.prefs	
定义首选项API。
# java.rmi	
定义远程方法调用（RMI）API。
# Java.scripiting	
定义脚本API。
# java.se	
定义Java SE平台的API。

# java.security.jgss	

定义IETF通用安全服务API（GSS-API）的Java绑定。

# java.security.sasl	

为IETF简单身份验证和安全层（SASL）定义Java支持。

# java.smartcardio	

定义Java智能卡I / O API。

# java.sql	

定义JDBC API。

# java.sql.rowset	

定义JDBC RowSet API。

# java.transaction.xa	

定义用于支持JDBC中的分布式事务的API。

# java.xml	

定义用于XML处理的Java API（JAXP），用于XML的流API（StAX），用于XML的简单API（SAX）和W3C文档对象模型（DOM）API。

# java.xml.crypto	

定义用于XML加密的API。

# jdk.accessibility	

定义辅助技术的实现者使用的JDK实用工具类。

# jdk.attach	

定义附加API。

# java.charsets

提供charsets不在其中的内容java.base（主要是双字节和IBM字符集）。

# jdk.compiler	

定义系统Java编译器的实现 及其等效的命令行javac。

# jdk.crypto.cryptoki	

提供SunPKCS11安全提供程序的实现。

# jdk.crypto.ec	

提供SunEC安全提供程序的实现。

# jdk.dynalink	

定义用于动态链接对象高级操作的API。

# jdk.editpad	

提供实现所使用的编辑板服务jdk.jshell。

# jdk.hotspot.agent	

定义HotSpot可服务性代理的实现。

# jdk.httpserver	

定义特定于JDK的HTTP服务器API。

# jdk.jar工具	

定义用于操作Java Archive（JAR）文件的工具，包括jar和 jarsigner工具。

# jdk.javadoc	

定义系统文档工具的实现 及其等效的命令行javadoc。

# jdk.jcmd	

定义用于诊断和排除JVM故障的工具，例如jcmd，jps， jstat工具。

# jdk.jconsole	

定义JMX图形工具jconsole，用于监视和管理正在运行的应用程序。

# jdk.jdeps	

定义用于分析Java库和程序中的依赖关系的工具，包括jdeps， javap和 jdeprscan工具。

# jdk.jdi	

定义Java调试接口。

# jdk.jdwp.agent	

提供Java调试线协议（JDWP）代理的实现。

# jdk.jfr	

定义JDK Flight Recorder的API。

# jdk.jlink	

定义JLINK创建运行时图像，工具JMOD用于创建和操作JMOD文件的工具，以及jimage用于检查类和资源的JDK实现特定的容器文件的工具。

# jdk.jshell	

提供用于评估Java代码段的jshell工具，并定义了JDK特定的API，用于建模和执行代码段。

# jdk.js对象	

定义JavaScript对象的API。

# jdk.jstatd	

定义用于启动守护程序的jstatd工具，该守护程序用于jstat工具以远程监视JVM统计信息。

# jdk.localedata	

提供除美国语言环境之外的其他语言环境的语言环境数据。

# jdk.management	

为JVM定义特定于JDK的管理接口。

# jdk.management.agent	

定义JMX管理代理。

# jdk.management.jfr	

定义JDK Flight Recorder的管理接口。

# jdk.naming.dns	

提供DNS Java命名提供程序的实现。

#  jdk.naming.rmi	

提供RMI Java命名提供程序的实现。

# jdk.net	

定义特定于JDK的网络API。

# jdk.pack	

定义用于将JAR文件转换为压缩的pack200文件并将打包的文件转换为JAR文件的工具，包括 pack200和 unpack200工具。

# jdk.rmic	

定义用于使用远程对象的Java远程方法协议（JRMP）生成存根和框架的rmic编译器。

# jdk.scripting.nashorn	

为使用ECMAScript 5.1编写的程序提供Nashorn脚本引擎和运行时环境的实现。

# jdk.sctp	

为SCTP定义特定于JDK的API。

# jdk.security.auth	

提供javax.security.auth.* 接口和各种身份验证模块的实现。

# jdk.security.jgss	

定义对GSS-API的JDK扩展以及SASL GSSAPI机制的实现。

# jdk.xml.dom	

定义不属于Java SE API的W3C文档对象模型（DOM）API的子集。

# jdk.zipfs	

提供Zip文件系统提供程序的实现。