Effective Java
======
对 Effective Java 的总结.

## 创建和销毁对象
- [考虑使用静态工厂方法代替构造器(Constructor)](创建和销毁对象.md#考虑使用静态工厂方法代替构造器Constructor)
- [构造方法参数过多考虑使用构建器(Builder)](创建和销毁对象.md#构造方法参数过多考虑使用构建器Builder)
- [利用私有构造器或Enum强化Singleton](创建和销毁对象.md#利用私有构造器或Enum强化Singleton)
- [使用私有构造器可以强化不可实例化](创建和销毁对象.md#使用私有构造器可以强化不可实例化)
- [避免创建不必要的对象](创建和销毁对象.md#避免创建不必要的对象)
- [清除过期的对象引用](创建和销毁对象.md#清除过期的对象引用)
- [避免使用finalizer方法](创建和销毁对象.md#避免使用finalizer方法)

## 对所有对象都通用的方法
- [覆盖equals需要遵守的约定](对所有对象都通用的方法.md#覆盖equals需要遵守的约定)
- [覆盖equals方法时总要覆盖hashCode方法](对所有对象都通用的方法.md#覆盖equals方法时总要覆盖hashCode方法)
- [覆盖toString便于阅读](对所有对象都通用的方法.md#覆盖toString便于阅读)
- [谨慎覆盖clone方法](对所有对象都通用的方法.md#谨慎覆盖clone方法)
- [考虑实现Comparable接口](对所有对象都通用的方法.md#考虑实现Comparable接口)

## 类和接口
- [类和成员的可访问性最小化](类和接口.md#类和成员的可访问性最小化)
- [public类应使用public访问方法而非public域](类和接口.md#public类应使用public访问方法而非public域)
- [使可变性变小](类和接口.md#使可变性变小)
- [复合优先于继承](类和接口.md#复合优先于继承)