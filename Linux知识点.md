#使用Linux过程中常见问题及解决方法

##Retext工具栏图标丢失

1.  运行命令

        python3 -c "from gi.repository import Gtk; print(Gtk.Settings.get_default().get_property('gtk-icon-theme-name'))"


1.  设置参数

    *   通过菜单修改。
    
        编辑&rarr;`preferences`中，设置   `Icon theme name`。
    
    *   通过配置文件修改。
       
        编辑  `~/.config/ReText projiect/Retext.conf`，添加一行代码   `iconTheme=Adwaita`（其中`Adwaita`为命令的输出值）


##有序列表重新编序号问题
*   问题：如上例，假如在**运行命令**之后的代码使用` ``` `声明的话，将会导致后一个**设置参数**重新编号。
*   解决方法：使用缩进8个空格的方法，表明为代码区域。