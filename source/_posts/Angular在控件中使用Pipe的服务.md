---
title: Angular在控件中使用Pipe的服务
date: 2018-01-16 10:17:22
tags: 
 - Angular
 - TypeScript
categories: 
- 前端开发
---
# 管道 (Pipe)

每个应用开始的时候差不多都是一些简单任务：获取数据、转换它们，然后把它们显示给用户。获取数据可能简单到创建一个局部变量就行，也可能复杂到从WebSocket中获取数据流。

我们经常在html中这样使用Pipe

```bash
<p>消费总金额：{{ offerItems|number:'1.2-2' }}</p>`
```

但是在我们实际应用中有时候因为计算，我们也需要在Component的Ts中去调用管道提供的方法进行计算、转换，这样保持数据一致。

首先import你需要的用到的管道。可以查看自带有哪些Pipe的API [@angular/common](https://angular.cn/api)

```bash
import { DecimalPipe } from '@angular/common';
```

在Component中注入服务

```bash
@Component({
    selector: 'app-pipe',
    templateUrl: 'pipe.component.html',
    styleUrls: ['./pipe.component.scss'],
    providers: [DecimalPipe]
})
```

调用 ``transform`` 方法

```bash
export class PipeComponent {
    constructor(private decimalPipe: DecimalPipe) {
        const offerItem = decimalPipe.transform(21.556, '1.2-2');
        console.log(offerItem);
    }
}
```