#地址：http://anxpp.com/ 

```java
package com.anxpp.demo;
import java.util.regex.Matcher;
import java.util.regex.Pattern;
public class RegexExamples {
	public static void main(String[] args) {
		//创建一个带有标志的Pattern对象(此处为不区分大小写)
		Pattern pattern = Pattern.compile("ab", Pattern.CASE_INSENSITIVE);
		//源字符串
		Matcher matcher = pattern.matcher("ABcabdAb");
		//使用Matcher find(),group(),start()和 end()方法
		while (matcher.find()) {
			System.out.println("Found the text \"" + matcher.group()+"\" starting at "+matcher.start()+" index and ending at index "+matcher.end());
		}
		//\W表示非英文字母
		pattern = Pattern.compile("\\W");
		//分割字符串
		String[] words = pattern.split("one@two#three:four$five");
		//遍历并输出结果
		for (String s : words) {
			System.out.println("Split using Pattern.split(): " + s);
		}
		//使用Matcher.replaceFirst()、replaceAll()方法
		//*表示零次或多次匹配前面的字符或子表达式
		pattern = Pattern.compile("1*2");
		//源字符串
		matcher = pattern.matcher("11234512678");
		//替换全部匹配的字符串为_
		System.out.println("Using replaceAll: " + matcher.replaceAll("_"));
		//替换首个匹配的字符串为_
		System.out.println("Using replaceFirst: " + matcher.replaceFirst("_"));
		//Pattern与String的matches方法
		String str = "bbb";
		System.out.println("Using String matches method: "+str.matches(".bb"));
		System.out.println("Using Pattern matches method: "+Pattern.matches(".bb", str));
		// 按指定模式在字符串查找（下面的例子说明如何从一个给定的字符串中找到数字串）
		//源字符串
		String line = "This order was placed for QT3000! OK?";
		//.*表示任意个任意字符，\d+表示连续至少一个数字
		Matcher m = Pattern.compile("(.*)(\\d+)(.*)").matcher(line);
		if (m.find()) {
			//分别输出组0到2匹配的字符串
			System.out.println("Found value: " + m.group(0));
			System.out.println("Found value: " + m.group(1));
			System.out.println("Found value: " + m.group(2));
		} else {
			System.out.println("NO MATCH");
		}
		//\w为字母，\d为数字，\1(\num)就是组1的引用，这里意思就是又一个(\w\d)且这个(\w\d)与前面的相同，整个表达式意思就是(\w\d)(\w\d)并且两个(\w\d)内容一样
		System.out.println(Pattern.matches("(\\w\\d)\\1", "a2a2")); //true
	    System.out.println(Pattern.matches("(\\w\\d)\\1", "a2b2")); //false
	    //\2就是组2的引用，这里的组2就是(B\\d)
	    System.out.println(Pattern.matches("(AB)(B\\d)\\2\\1", "ABB2B2AB")); //true
	    System.out.println(Pattern.matches("(AB)(B\\d)\\2\\1", "ABB2B3AB")); //false
	}
}
/*输出如下：
Found the text "AB" starting at 0 index and ending at index 2
Found the text "ab" starting at 3 index and ending at index 5
Found the text "Ab" starting at 6 index and ending at index 8
Split using Pattern.split(): one
Split using Pattern.split(): two
Split using Pattern.split(): three
Split using Pattern.split(): four
Split using Pattern.split(): five
Using replaceAll: _345_678
Using replaceFirst: _34512678
Using String matches method: true
Using Pattern matches method: true
Found value: This order was placed for QT3000! OK?
Found value: This order was placed for QT300
Found value: 0
true
false
true
false
*/
```
