# copy

对于可变的容器类,nsmutableArray,nsmutableDicnary等,调用copy方法,将返回一个不可变得容器类,

对于不可变的容器类,调用mutablCopy返回一个可变的容器类,这两种情况都是深拷贝,

对于不可变的容器类,调用copy只是让这个对象的引用计数+1,浅拷贝

对于可变的容器类,调用mutableCopy也是让这个引用计数+1,浅拷贝

blcok调用copy的原因是将block从栈中copy到堆中,延长他的声明周期.

常见容器类的属性,使用copy修饰的原因是,让这个属性获取在赋值的时候的瞬间值,并不会因为赋值属性的改变而改变

继承自nsobject的对象,调用copy方法必须要先实现nscopying协议