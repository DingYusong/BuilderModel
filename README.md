# BuilderModel

建造者模式又叫生成器模式是一种创建型设计模式，它把对象的创建步骤抽象成生成器，并且可以通过指导类（director）对所有生成步骤的先后顺序进行控制。客户端使用指导类并传入相应的生成器，通过指导类的接口便可以得到相应的对象。



属于创建者模式。

场景：画人，人有胖瘦之分（头，身子，左胳膊，右胳膊，左腿，右腿）六个元素不能少。

 

分析：画人可以分为画（头，身子，左胳膊，右胳膊，左腿，右腿）六部分，这个流程是确定的，每个部分因人的胖瘦是有差异的

 

实现：一个抽象创建类，确定创建六个部分，胖人创建类和瘦人创建类继承创建类，复写创建部分。一个流程控制类，确定创建流程的每一步，完成创建。（这种场景可使用建造者模式）

 

创建者模式：一个复杂对象的创建和他的表示分离，同样的创建过程可以创建不同的表示。

 

新增一种类型的人，只需要增加一个创建类，符合开闭原则。

```objective-c
int main(int argc, const char * argv[]) {
    @autoreleasepool {
        
        DYSPersonBuilderDirector *director = [DYSPersonBuilderDirector new];
        DYSPersonBuilder *builder = [DYSThinPersonBuilder new];
        director.personBuilder = builder;
        [director createPerson];
        
        builder = [DYSFatPersonBuilder new];
        director.personBuilder = builder;
        [director createPerson];
        
    }
    return 0;
}
```

