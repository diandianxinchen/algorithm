### 导出Excel

导出excel报表是一个很常用的功能，在ruoyi的源码中看到了一个封装方式觉得很好这里记录一下。

设计的思想： 导出的Excel只和数据本身有关，我们需要做的只有组装需要导出的数据，其他的处理都不应该由我们自己在写一边（IO的处理等）



使用注解来进行filed值和Excel列名的绑定，包括Excel名字，写入值的转换（如Object中性别用数字表示，导出的Excel需要使用中文），数字精度的处理 等

ExcelUtil 进行通用的处理

最终在需要进行Excel导出的地方只需要

```java
// SysJob 为导出的类的定义
ExcelUtil<SysJob> util = new ExcelUtil<SysJob>(SysJob.class);
// list 为需要导出的数据
util.exportExcel(response, list, "定时任务");
```

代码的冗余比起我自己写的要少很多

具体的实现可以查看ruoyi源码

