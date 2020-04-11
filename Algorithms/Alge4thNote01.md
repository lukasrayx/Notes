# 第二张：排序

```java
public class hello {
	public static void main(String[] args) {
		int[] arr = new int[] {2, 4, 5, 7, 2, 1};
		selectSort(arr);
		for( int i = 0; i < arr.length; i++ ) {
			System.out.print(arr[i] + " ");
		}
	}
		
	public static void selectSort(int[] arr) {
		int N = arr.length;
		for (int i = 0; i < N; i++) {	
			int min = i;
			
			for (int j = i + 1; j < N; j++) {
				if (arr[j] < arr[min]) { min = j; }
			}
			
			if (min != i) {
				int temp = arr[i];
				arr[i] = arr[min];
				arr[min] = temp;
			}
		}		
	}
}
```

