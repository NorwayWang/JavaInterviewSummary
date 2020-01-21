[interrupt(),interrupted() 和 isinterrupted() 的区别](#top)</br>
[1.关于线程终止方法interrupt()](#one)</br>
[2.interrupted() 和 isInterrupted() 的区别](#two)</br>

+ [2.1. Thread.interrupted()](#two-one)</br>
+ [2.2.this.isInterrupted()](#two-two)</br>

[总结](#total)</br>

---

## <span id="top">interrupt(),interrupted() 和 isinterrupted() 的区别</span>

+ interrupt()：将调用该方法的对象所表示的线程标记一个停止标记，并不是真的停止该线程。
+ interrupted()：获取当前线程的中断状态，并且会清除线程的状态标记。是一个是静态方法。
+ isInterrupted()：获取调用该方法的对象所表示的线程，不会清除线程的状态标记。是一个实例方法。

### <span id="one">1.关于线程终止方法interrupt()</span>

&emsp;&emsp;由于`stop()`方法已经过时和废弃，是之前JDK设计有缺陷的方法，所以我们一般使用`interrupt()`方法来终止线程，但是`interrupt()`方法并不像`stop()`方法那样暴力终止线程，通俗的说使用效果并没有for+break语句那样，马上就终止循环。调用`interrupt()`方法仅仅是在当前线程中打了一个停止的标记，并不是真正意义上的停止线程。我们先来看一个简单的示例：
```
public class TestThread {
	public static void main(String[] args) {
		try {
	           MyThread01 myThread = new MyThread01();
	           myThread.start();
	           Thread.sleep(2000);
	           myThread.interrupt();
	       } catch (Exception e) {
	           System.out.println("main catch");
	           e.printStackTrace();
	       }
	   }
	}

class MyThread01 extends Thread {
	@Override
	public void run() {
		super.run();
		for (int i = 0; i < 500; i++) {
			System.out.println("i= " + (i+1));
		}
	}
}
```
结果：
```
i= 1
i= 2
i= 3
···
i= 498
i= 499
i= 500
```
&emsp;&emsp;从运行结果来看，`interrupt()`方法并没有终止线程，所以我们需要java提供的2个方法`interrupted()`和`isInterrupted()`来判断它停止的标志从而能正确的终止线程。但是这2个方法是很容易混淆的，下面我们通过源码解读+测试小例子来把它们的区别和用法彻底搞清楚。

### <span id="two">2.interrupted() 和 isInterrupted() 的区别</span>
&emsp;&emsp;判断线程是否是停止状态，java中的JDK提供了两种方法：

+ Thread.interrupted():测试当前线程是否已经中断
+ this.isInterrupted():测试线程是否已经中断

&emsp;&emsp;这两个方法有什么差别呢？我们先看下JDK源码：
```
public static boolean interrupted() {
    return currentThread().isInterrupted(true);
}

public boolean isInterrupted() {
    return isInterrupted(false);
}
```
&emsp;&emsp;首先我们发现这个2个方法都调用了`isInterrupted(boolean ClearInterrupted)`这个方法，我们看这个方法的注解，它的意思是说如果一个线程已经被终止了，中断状态是否被重置取决于`ClearInterrupted`的值，即`ClearInterrupted`为`true`时，中断状态会被重置，为`false`则不会被重置。

&emsp;&emsp;然后我们比较这2个方法的差别，结果就很明显了，可以看出，`interrupted()`是静态方法，所以我们用`Thread.interrupted()`方法表示，它调用的是`currentThread().isInterrupted(true)`方法，即说明是返回当前线程的是否已经中断的状态值，而且有清理中断状态的机制。而`isInterrupted()`是一个实例方法，所以我们用`this.isInterrupted()`方法表示，它调用的是`isInterrupted(false)`方法，意思是返回线程是否已经中断的状态值，与`Thread.interrupted()`方法相反，它没有清理中断状态的机制。（PS：这里看不懂没关系，后面会用例子验证）

#### <span id="two-one">2.1. Thread.interrupted()</span>
&emsp;&emsp;下面我们先研究一下Thread.interrupted()方法，请看下面的一个例子：
```
public class TestThread extends Thread {
    @Override
    public void run() {
        super.run();
        for (int i = 0; i < 50000; i++) {
            System.out.println("i= " + (i+1));
        }
    }

	public static void main(String[] args) {
        TestThread thread=new TestThread();
        thread.start();
        try {
            Thread.sleep(1000);
            thread.interrupt();
            System.out.println("是否已经停止 1？="+Thread.interrupted());
            System.out.println("是否已经停止 2？="+Thread.interrupted());
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end!");
	}
}
```
结果：
```
i= 1
i= 2
i= 3
···
···
i= 6129
i= 6130
是否已经停止 1？=false
是否已经停止 2？=false
end!
i= 6131
i= 6132
···
···
i= 49999
i= 50000
```

&emsp;&emsp;从执行的结果来看，线程并未终止，这也就证明了`interrupted()方法`的解释：测试当前线程是否已经中断，这个“当前线程”是main，它从未中断过，所以2个结果都是false。

&emsp;&emsp;哪如何让main线程终止呢？
```
public class TestThread {
    public static void main(String[] args) {
        Thread.currentThread().interrupt();
        System.out.println("是否停止 1？="+Thread.interrupted());
        System.out.println("是否停止 2？="+Thread.interrupted());
        System.out.println("end!");
    }
}
```
结果：
```
是否停止 1？=true
是否停止 2？=false
end!
```
&emsp;&emsp;从执行结果来看，方法`interrupted()`的确能判断出当前线程是否是中断（停止）状态。第二个false是什么意思呢，这就验证了我们上面所说的中断状态清除的情况，就是说`interrupted()`会清除中断状态，如果连续2次调用该方法，则第二次会返回false值（在第一次调用已清除了中断状态之后，且第二次调用检验完中断状态之前，当前线程再次中断的情况除外）。

#### <span id="two-two">2.2.this.isInterrupted()</span>
&emsp;&emsp;分析完Thread.interrupted()方法之后，我们下面再来分析this.isInterrupted()方法：
```
public class TestThread extends Thread {
    @Override
    public void run() {
        super.run();
        for (int i = 0; i < 50000; i++) {
            System.out.println("i= " + (i+1));
        }
    }

	public static void main(String[] args) {
        TestThread thread=new TestThread();
        thread.start();
        try {
            Thread.sleep(1000);
            thread.interrupt();
            System.out.println("是否已经停止 1？="+thread.interrupted());
            System.out.println("是否已经停止 2？="+thread.interrupted());
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("end!");
	}
}
```
结果：
```
i= 1
i= 2
i= 3
···
···
i= 6580
是否已经停止 1？=false
是否已经停止 2？=false
end!
i= 6581
i= 6582
···
···
i= 49999
i= 50000
```
&emsp;&emsp;从结果看，2个值都为true，说明方法isInterrupted()并没有清除中断状态标志，和我们之前分析源码的结果一致。

### <span id="total">总结</span>

+ interrupted()是static方法，调用的时候要用Thread.interrupted()，而isInterrupted()是实例方法，调用时要用线程的实例调用；
+ Thread.interrupted()：测试当前线程是否已经是中断状态，执行后具有将状态标志清除为false的功能；
+ this.isInterrupted()：测试线程Thread对象是否已经是中断状态，但不清除状态标志。

[返回顶端](#top)
