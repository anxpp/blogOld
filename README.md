#地址：http://anxpp.com/ 

```java
public enum SingleEnum{
	ONE(1),THREE(3){
		@Override
		public boolean isEven() {
			return false;
		}
	},TWO(2){
		@Override
		public boolean isEven() {
			return true;
		}
	};
	private int value;
	private SingleEnum(){}
	private SingleEnum(int value){
		this.value = value;
	}
	public int getValue(){
		return value;
	}
	public boolean isEven(){
		return false;
	}
	public static void main(String args[]){
		for(SingleEnum singleEnum : SingleEnum.values()){
			System.out.println(singleEnum + ":" + singleEnum.isEven() + singleEnum.getValue());
		}
	}
}
/*输出：
ONE:false1
THREE:false3
TWO:true2
*/
```
