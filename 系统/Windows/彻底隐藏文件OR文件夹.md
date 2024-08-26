## 第一步
在属性中隐藏文件夹

## 第二步
修改文件夹内容为系统隐藏的文件/文件夹

打开cmd
键入 attrib +h +s "文件/文件夹" 
（隐藏文件夹内容还需多一步：cd 到文件夹，然后 attrib +h +s * /s /d ）


## 第三步
修改注册表禁止显示隐藏的文件

1.新建reg，键入```
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced\Folder\Hidden\SHOWALL]

"CheckedValue"=dword:00000000
```
2.保存
3.双击运行

还可以配合禁止修改注册表使用

1. 打开“运行”对话框，输入“gpedit.msc”命令，打开组策略编辑器；
    
2. 在左侧导航栏中，依次展开“用户配置”、“管理模板”、“系统”；
    
3. 在右侧窗口中，找到并双击“阻止访问注册表编辑工具”策略；
    
4. 在弹出的对话框中，选择“已禁用”选项，然后点击“应用”和“确定”按钮；
    
5. 重启计算机，使设置生效。

 （取消反之）

## 恢复
首先允许显示隐藏的文件
```Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Advanced\Folder\Hidden\SHOWALL]

"CheckedValue"=dword:00000001
```
然后恢复文件状态
cmd键入attrib -h -s "文件/文件夹"（ attrib -h -s * /s /d ）