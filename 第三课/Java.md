## karel和Java

***1）常见的错误***：

*死循环*「infinite loop」

就是字面意思，循环停不下来，而程序总会停下来的，这个问题很经典。

*缺一个*「off-by-one bug」OBOB

程序少执行了一次，但是不容易看出来。在代码层面的逻辑似乎是正确的，但如果少考虑了某些因素，就会导致 *对象* 运行的结果缺少某些东西。

***2）注释***：

`/* 要写的注释 */`

这就是写注释的格式。

另一种格式：`// 要写的注释 `

//只是后面一行的东西变成注释，用一次回车就没了。

***3）细化***：

程序的每一步我们都可以把它细化成**更小**的步骤，这是分解「decomposition」。

把很大的一件事，分解成每一个小的步骤，这就叫 *自顶向下* 「top- down」的设计方法。

**相反的**从最底层的语言和算法开始，向着完整的项目前进，这就是 *自底向上* 「bottom-up」的设计方法。

自底向上的方法一般要经过100小时的编程后，才能逐步转化思考方式为自顶向下。目标自然是能够有「top- down」的**思维方式**。

***

### 算法

解决问题的*方法*「approach」，就是 *算法* 「algorithm」。

例如，将一个格子里的方块**翻倍**。而karel没有计数器，那么就要新的的方法。

*拿起一个方块，移动到另一格，放下两个方块，在返回重复操作。最后把翻倍的方块移回来*

这些操作都是最基础的方法**组合**成的，这就是算法。

`private void DoubleBeeperInPile(){`

​	`while (BeeperPrecent()) {`

​		`pickBeeper();`

​		`PutTwoBeepersNextDoor(); //这是没有定义的方法，等会再定义它`

`}`

​	`MoveNextDoorBack(); //也一样等会再定义，这是一种自顶向下的思维`

`}`

`private void PutTwoBeepersNextDoor() {`

​	`move();`

​	`putBeeper();`

​	`putBeeper(); //这里其实可以用for循环重复两次`

​	`moveBackword();`

`}`

`private void MoveNextDoorBack() {`

​	`move();`

​	`while (BeeperPrecent()) {`

​		`moveOneBeeperBack();`

`}`

​	`moveBackword();`

`}`

`private void moveOneBeeperBack() {`

​	`pickBeeper();`

​	`moveBack();`

​	`putBeeper();`

​	`move();`

`}`

***

### 如何分解要做的一个程序呢？

*原则* ：**一个**方法「method」解决**一个**问题。

   		尽量在1-15行左右，当然可以很多行，不影响。

​			正确的命名（我用的是小驼峰式），自己和别人都能看懂。

​			有注释，简明且关键。

