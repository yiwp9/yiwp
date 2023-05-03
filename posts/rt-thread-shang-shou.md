---
title: 'RT-Thread 任务创建'
date: 2021-10-07 14:47:37
tags: [RT-Thread]
published: true
hideInList: false
feature: /post-images/rt-thread-shang-shou.png
isTop: false
---
以 PWM 为例进行说明：

### 静态任务

```c
static uint8_t PWM_Thread_Stack[1024];   //pwm 任务的栈的大小
static void PWM_Thread_Entry(void *para); // pwm 任务的入口函数
static struct rt_thread pwm_thread; //静态任务 pwm 的任务块
```
#### 任务初始化
``` c 
    //初始化 pwm 任务， 启动 pwm 任务
    int Pwm_Thread_Init(void)
    {           
         // 任务块     任务名     任务入口函数    任务参数   任务栈首地址    任务栈大小   优先级    时间片
        rt_thread_init(&pwm_thread, "pwm_thread", PWM_Thread_Entry, RT_NULL, &PWM_Thread_Stack[0], sizeof(PWM_Thread_Stack), 10, 10);                       
        //当两个任务优先级相同时，则按时间片轮流执行，比如 任务 A 时间片为 10个节拍，任务B           的时间片为5 个节拍，则  A 运行 10 个节拍然后B运行 5 个节拍，如此循环
        rt_thread_startup(&pwm_thread);//启动任务
        return 0;
    }
```
#### 任务入口
``` c
    //pwm 任务入口
    static void PWM_Thread_Entry(void *para)
    {
        Pwm_Init();
        while (1)
        {
            /*使 RGB 灯红灯闪烁*/
            for (int var = 0; var < period; var += 10000)
            {
                rt_pwm_set(pwm_dev, PWM_DEV_CHANNEL, period, var);
                rt_thread_mdelay(200);
            }
        }
    }
```

#### 添加任务到终端调试
```c
//将 pwm 任务加入到终端调试，在终端中执行 Pwm_Thread_Init 就会执行 pwm 任务，也可以不添加，直接在 main 里执行  Pwm_Thread_Init 也能执行
INIT_APP_EXPORT(Pwm_Thread_Init);
```
### 动态任务

```c
//创建线程启动函数，用于启动上一步编写的线程主体
static int Thread_RGB(void)
{
    rt_thread_t thread = RT_NULL;
    thread = rt_thread_create("rgb", rgb_thread_entry, RT_NULL, 512, 10, 10);
    if (thread == RT_NULL)
    {
        rt_kprintf("Thread_GRB Init ERROR");
        return RT_ERROR;
    }
    rt_thread_startup(thread);
}
```

### 静态任务与动态任务对比

使用静态线程时，必须先定义静态的线程控制块，并且定义好堆栈空间，然后调用rt_thread_init（） 来完成线程的初始化工作。采用这种方式，线程控制块和堆栈占用的内存会放在 RW/ZI 段，这段空间在编译时就已经确定，它不是可以动态分配的，所以不能被释放，而只能使用 rt_thread_detach() 函数将该线程控制块从对象管理器中脱离。

使用动态定义方式 rt_thread_create() 时， RT-Thread 会动态申请线程控制块和堆栈空间。在编译时， 编译器是不会感知到这段空间的，只有在程序运行时， RT-Thread 才会从系统堆中申请分配这段内存空间，当不需要使用该线程时，调用 rt_thread_delete() 函数就会将这段申请的内存空间重新释放到内存堆中。

这两种方式各有利弊，静态定义方式会占用 RW/ZI 空间，但是不需要动态分配内存，运行时效率较高，实时性较好。 动态方式不会占用额外的 RW/ZI 空间，占用空间小，但是运行时需要动态分配内存，效率没有静态方式高。 总的来说，这两种方式就是空间和时间效率的平衡，可以根据实际环境需求选择采用具体的分配方式。
