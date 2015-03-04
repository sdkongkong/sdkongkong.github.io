---
layout: post
title: 摇摇美（摇一摇）开发过程中的注意事项
---
在开发摇一摇过程中使用了传感器，发现了几个使用传感器需要注意的地方：
1 使用之前要检测手机有没有配置传感器，防止没有传感器的手机出现异常。
2 因为传感器比较耗电，在不使用的传感器的时候要取消注册，使用的时候再重新注册。
取消注册protected void onPause() {
  super.onPause();
  mSensorManager.unregisterListener(this);
}
注册 if (mSensorManager.getDefaultSensor(Sensor.TYPE_ACCELEROMETER) != null) {
            mSensorManager.registerListener(mSensorListener,
                    mSensorManager.getDefaultSensor(Sensor.TYPE_ACCELEROMETER), SensorManager.SENSOR_DELAY_UI);
        } else {
            CommonUtility.showMiddleToast(ShakeHomeActivity.this, "", "你的设备不支持摇一摇，请点击马尾巴参与摇奖");
        }
3 模拟器不支持关于传感器功能的测试，需要在真机上测试。
4 onSensorChanged()的执行频率很高， 不要再里面执行耗时耗性能的工作，尤其是创建对象等。
5 注册传感器要尽可能的晚 ，因为早注册早费电。

