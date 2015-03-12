---
layout: post
title: 可能造成内存泄漏的Handler
---
当Activity里的自定义handler不是内部类时，会警告有可能造成内存泄漏， 原因是这样的：

1 当在主线程中初始化Handler时，会建立一个主线程的Looper对象，Looper实现了一个简单的消息队列，一个一个的处理里面的Message对象。主线程Looper对象在整个应用的生命周期中存在。

2  处理某个消息时需要调用相对应的handler，所以会一直保持消息相对应的handler引用

3 handler作为内部类又持有外部类的引用，当外部类是Activity时，会导致Activity销毁不了，造成内存泄露

4解决办法是把handler定义成静态内部类，这样就不会持有外部类的对象。如下所示

private static class MyHandler extends Handler{

private final WeakReference<Activity> mActivity;

public MyHandler(Activity activity){

mActivity = new WeakReference<Activity>(activity);

}
@Override

public void handleMessage(Message msg) {

if(mActivity.get()==null){

return;

}
}
}
