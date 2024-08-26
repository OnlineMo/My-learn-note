# 方法一
[autojs判断app是否运行](https://juejin.cn/s/autojs%E5%88%A4%E6%96%ADapp%E6%98%AF%E5%90%A6%E8%BF%90%E8%A1%8C)
代码：

```
function isAppRunning(packageName) {
    
    var activityManager = context.getSystemService(android.content.Context.ACTIVITY_SERVICE);

    var runningTasks = activityManager.getRunningTasks(1);

    for (var i in runningTasks) {

        var task = runningTasks[i];

        console.log(task.baseActivity.getPackageName());

        if (task.baseActivity.getPackageName() === packageName) {

            return true;

        }

    }

    return false;

}

if (isAppRunning(getPackageName(""))) {

    console.log("App is running");

} else {

    console.log("App is not running");

}
```

注：
1.[使用ActivityManager类的`getRunningTasks()`方法来获取当前正在运行的任务列表，然后遍历该列表以检查每个任务的包名是否与需要检查的应用程序的包名相同。但是，从Android 5.0开始，该方法已被弃用，并且在Android 11中已被删除。因此，如果您的应用程序针对Android 5.0或更高版本，请改用其他方法，例如使用`UsageStatsManager`类](https://cloud.tencent.com/developer/article/1731867)[1](https://cloud.tencent.com/developer/article/1731867)。
2.activityManage定义代码：`var activityManager = context.getSystemService(android.content.Context.ACTIVITY_SERVICE);`


# 方法二
