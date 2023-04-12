# RTOS
RTOS是一个嵌入式的实时操作系统，

## 官网资源

[freeRTOS官网](https://www.freertos.org/zh-cn-cmn-s/Creating-a-new-FreeRTOS-project.html)

### 下载


## 任务
在裸机系统中，程序的主体是CPU 按照顺序执行的。而在多任务系统中，任务的执行是由系统调度的。系统为了顺利的调度任务，为每个任务都额外定义了一个任务控制块，这个任务控制块就相当于任务的身份证，里面存有任务的所有信息，比如任务的栈指针，任务名称，任务的形参等。