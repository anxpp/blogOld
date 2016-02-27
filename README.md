#地址：http://anxpp.com/ 

```java
public enum SingleEnum{
	ONE,TWO,THREE;
	public static void main(String args[]){
		System.out.println("for循环遍历：");
		for(SingleEnum singleEnum : SingleEnum.values()){
			System.out.println(singleEnum);
		}
		System.out.println("switch的使用：");
		SingleEnum singleEnum = SingleEnum.TWO;
		switch(singleEnum){
		case ONE:System.out.println("这是1");break;
		case TWO:System.out.println("这是2");break;
		case THREE:System.out.println("这是3");break;
		default:System.out.println(singleEnum);break;
		}
	}
}
```
