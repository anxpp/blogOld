#地址：http://anxpp.com/ 

```java
package com.anxpp.phyg.utils;
import android.content.Context;
import android.content.SharedPreferences;
/**
 * Created by anxpp on 2015/10/29.
 *
 */
public class MySharedPrerences {
    /**
     * 存储或修改值
     * @param context   上下文
     * @param flag      存储标志
     * @param valueName 存储字段名
     * @param value     要保存的值
     */
    public static void save(Context context,String flag,String valueName,String value){
        SharedPreferences sp =context.getSharedPreferences(flag, Context.MODE_PRIVATE);
        SharedPreferences.Editor editor=sp.edit();
        editor.putString(valueName, value);
        editor.apply();
    }
    /**
     * 获取值
     * @param context   上下文
     * @param flag      存储标志
     * @param valueName 要获取的字段名
     * @return          要获取的值
     //@param default   默认值
     */
    public static String getString(Context context,String flag,String valueName){
        SharedPreferences sp =context.getSharedPreferences(flag, Context.MODE_PRIVATE);
        return sp.getString(valueName, "");
    }
    public static String getString(Context context,String flag,String valueName,String defaultStr){
        SharedPreferences sp =context.getSharedPreferences(flag, Context.MODE_PRIVATE);
        return sp.getString(valueName, defaultStr);
    }
    public static int getInt(Context context,String flag,String valueName){
        SharedPreferences sp =context.getSharedPreferences(flag, Context.MODE_PRIVATE);
        return sp.getInt(valueName, 0);
    }
    public static int getInt(Context context,String flag,String valueName,int defaultInt){
        SharedPreferences sp =context.getSharedPreferences(flag, Context.MODE_PRIVATE);
        return sp.getInt(valueName, defaultInt);
    }
}
```
