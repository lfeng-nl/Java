# Java高级

## 1.反射

> 在程序运行期间, 拿到对象的所有信息.

### 1.Class类

> 类似python的type, 用于创建类的类. 实例是类.

- 每加载一种类, JVM就为其创建一个`Class`类型的实例.
- 只有JVM能够创建`Class`的实例.
- JVM为加载的每个类都创建了对应的`Class`实例, 如果获取了这个`Class`实例, 就可以通过实例获取到对应的类信息. 这个方法就是反射.
- 获取`Class`实例的方式:
    - 1.类属性获取: `Class cls = String.class`
    - 2.实例`getClass`方法获取: `Class cls = s.getClass();`
    - 3.类名获取: `Class cls = Class.forName("java.lang.String");`

### 2.访问字段

- `Field cls.getField(name)`:根据字段名获取某个`public`的`field`.
    - 不存在时, 抛出`NoSuchFieldError`异常.
- `Field cls.getDeclareField(name)`: 根据字段名获取当前类(不是父类)的某个`field`. 
    - 不存在时, 抛出`NoSuchFieldError`异常.
- `Field cls.getFields()`: 获取所有的`public`的`field`.
- `Field[] cls.getDeclaredFields()`：获取当前类的所有`field`（不包括父类）
- 字段操作:
    - `f.get(object)`: 获取`object`对象字段`f`的值.
    - `f.set(obj, value)`: 设置`obj`对象字段`f`的值.
    - `f.setAccessible(true)`:  对象在使用时取消访问权限检查.

###  3.访问方法

- `Method getMethod(name, Class...)`：获取某个`public`的`Method`(包括父类).  **按声明顺序传入所需参数类型的`Class`**.
    - 不存在时, 抛出`NoSuchMethodException`异常.
- `Method getDeclaredMethod(name, Class...)`：获取当前类的某个`Method`（不包括父类）. **按声明顺序传入所需参数类型的`Class`**.
    - 不存在时, 抛出`NoSuchMethodException`异常.
- `Method[] getMethods()`：获取所有`public`的`Method`（包括父类）
- `Method[] getDeclaredMethods()`：获取当前类的所有`Method`（不包括父类）
- 方法的执行:
    - `m.invoke(obj, 参数)`: 

### 4.构造方法

- `java.lang.reflect.Constructor`: 包括构造方法的所有信息.
    - 通过`cons.newInstance()`创建实例.
- `getConstructor(Class...)`：获取某个`public`的`Constructor`；**按声明顺序传入所需参数类型的`Class`**.
- `getDeclaredConstructor(Class...)`：获取某个`Constructor`；**按声明顺序传入所需参数类型的`Class`**.
- `getConstructors()`：获取所有`public`的`Constructor`；
- `getDeclaredConstructors()`：获取所有`Constructor`。

## 2.泛型

##3.注解

> 放在类, 方法, 字段, 参数前的一种特殊注释.

- 