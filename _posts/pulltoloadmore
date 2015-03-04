---
layout: post
title: 我们项目中下拉加载更多的实现方式
---
我国美的客户端里面有很多列表， 不免要用到下拉加载更多的方式。
在我们项目中一般的实现方式是：

1  根据currentpage 和  pagesize 去服务器上取数据 ，如果取回来的数据 == pagesize 表明还有下一页 或者正好平分 （ 例如  每页10条而总共正好有10条））

2 listview添加loading view 做footerview  

3 在listview的onScrollStateChanged (view.getLastVisiblePosition() == view.getCount() - 1) && footview的数量>1 

4 判断是否正在加载，设置bool类型变量，防止加载多次
