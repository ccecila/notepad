# notepad
首先，因为给的项目版本较旧，先将build.gradle文件修改为下图：
![image](https://github.com/ccecila/notepad/blob/main/images/%E4%BF%AE%E6%94%B9(build.gradle%E6%96%87%E4%BB%B6).png)

接下来为notepad添加时间戳：
1.在notelist_item.xml布局文件中添加一个：
![image](https://github.com/ccecila/notepad/blob/main/images/%E4%BF%AE%E6%94%B9%EF%BC%88notelist_item.xml%E6%96%87%E4%BB%B6%EF%BC%89.png)


2.在PROJECTION中加入我们要显示的时间：
![image](https://github.com/ccecila/notepad/blob/main/images/%E4%BF%AE%E6%94%B92.png)


3.相应的，添加要装配的数据：
![image](https://github.com/ccecila/notepad/blob/main/images/%E4%BF%AE%E6%94%B93.png)


4.先import所需要的包：
import java.text.SimpleDateFormat;
import java.util.Date;


5.修改NotePadProvider.java:
		// Gets the current system time in milliseconds
        Long now = Long.valueOf(System.currentTimeMillis());
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String time = sdf.format(new Date(Long.parseLong(String.valueOf(now))));
        
        
6.修改NoteEditor.java：
// Sets up a map to contain values to be updated in the provider.
        ContentValues values = new ContentValues();
        Long now = Long.valueOf(System.currentTimeMillis());
        SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss");
        String time = sdf.format(new Date(Long.parseLong(String.valueOf(now))));
        values.put(NotePad.Notes.COLUMN_NAME_MODIFICATION_DATE, time);

7.运行结果截图：
![image](https://github.com/ccecila/notepad/blob/main/images/%24%5B%5B105FR5UU%7D9XSWV0Z95YL.png)
