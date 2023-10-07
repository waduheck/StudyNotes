## SLLists
### 改进：中介，避免直接操纵裸数据

IntList——>SLList
SLList就像中介一样，可以帮助我们操纵裸递归数据结构
![两者关系][IntListandSLList.png]

### 改进:使用静态内部类(Nested Classes)
1. 静态内部类不能访问不能访问非静态的方法和属性
2. 静态内部类可以声明普通成员变量和方法，而普通内部类不能声明static成员变量和方法。
3. 静态内部类可以单独初始化:`Inner i = new Outer.Inner();`
静态内部类使用场景一般是**当外部类需要使用内部类，而内部类无需外部类资源，并且内部类可以单独创建的时候**

### 改进:添加缓存
### 改进:添加头节点(Sentinel Nodes)

## DLLists
### 改进1:添加last
