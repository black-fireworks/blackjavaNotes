# 数组
概念
```
数组是相同数据类型的多个数据的容器.
这些元素按线性排列.

什么是线性排列？
    线性排列就是除第一个元素外,都有一个前驱元素。
    除最后一个元素外,每个元素都有一个后继元素。
```

语法格式
```
常用格式1:    数组名[] 数组名称 = new 数据类型[长度];
常用格式2:    数组名[] 数组名称 = {元素1,元素2,元素3};

示例:
    int[] nums = new int[2];
    int[] nums = {1,2,3,4,5,6};
```

为数组的某个索引进行赋值操作
```java
// 数组名[索引]  = 值;
// 示例
nums[0] = 1;
nums[1] = 2;
```

从数组中进行取值操作
```java
// 数组名[索引];
// 示例
int[] nums = {1,2,3,4,5,6};
// 这样就从数组中将2号索引位中的数值取出了
int num = nums[2];
```

获取数组的长度
```java
// 数组名.length
// 示例
int[] nums = {1,2,3,4,5,6};
System.out.print(nums.length);
```


## 数组练习案例
### 从当前数组中获取最大与最小值;
```java
public static void main(String[] args) {
	// 先创建一个数组
	int[] nums = {10,20,20,30,5,30,90,65,35,55};
	// 我们以上面数组为例子。分别获取中间最大与最小值
	int max = nums[0];
	int min = nums[0];
	for(int i=0;i<nums.length;i++) {
		max = max<nums[i]?nums[i]:max;
		min = min>nums[i]?nums[i]:min;
	}
	System.out.println("数组中最大值是:"+max);
	System.out.println("数组中最小值是:"+min);
}
```
### 将一个乱序的数组进行排序操作
将数组进行升序排序操作
```java
public static void main(String[] args) {
	// 先创建一个数组
	int[] nums = {10,20,20,30,5,30,90,65,35,55};
	// 对上面数组进行冒泡排序
	int temp;
	// 控制循环轮数
	for(int i=0; i<nums.length-1; i++) {
		for(int j=0; j<nums.length-i-1; j++) {
			if(nums[j]>nums[j+1]) {
				temp = nums[j];
				nums[j] = nums[j+1];
				nums[j+1] =temp;
			}
		}
	}
	for(int i=0;i<nums.length;i++) {
		System.out.println(nums[i]);
	}
}
```
将数组进行降序排序操作
```java
public static void main(String[] args) {
	// 先创建一个数组
	int[] nums = {10,20,20,30,5,30,90,65,35,55};
	// 对上面数组进行冒泡排序
	int temp;
	// 控制循环轮数
	for(int i=0; i<nums.length-1; i++) {
		for(int j=0; j<nums.length-i-1; j++) {
			if(nums[j]<nums[j+1]) {
				temp = nums[j];
				nums[j] = nums[j+1];
				nums[j+1] =temp;
			}
		}
	}
	for(int i=0;i<nums.length;i++) {
		System.out.println(nums[i]);
	}
}
```

### 快速在一组有序数据中进行查找某个数据
```java
// 二分查找 必须是采用顺序存储结构有序排列
public static void main(String[] args) {
	int[] nums = {10,20,30,40,50,60,70,80,90};
	// 说明要查找的变量
	int num = 50;

	int maxIndex = nums.length-1;
	int minIndex = 0;
	int centerIndex = (maxIndex+minIndex)/2;

	// 为什么使用while循环？  因为我们不确定到底要循环几次,所以我们使用while循环
	while(true) {
		if(nums[centerIndex]>num) {
			// 因为中间数值较大 所以 中间索引值之后的数值都不是 所以将最大索引值 变为 中间索引值-1
			maxIndex = centerIndex-1;
		}else if(nums[centerIndex]<num) {
			// 因为中间数值较小 所以 中间索引值之前的数值都不是 所以将最小索引值 变为 中间索引值+1
			minIndex = centerIndex+1;
		}else {
			break;
		}

		// 如果最小索引值大于了最大索引值 那么 说明此数值不在数组中
		if(minIndex>maxIndex) {
			break;
		}

		// 因为大小边界发生了改变 所以我们需要中间索引值重新计算
		centerIndex = (maxIndex+minIndex)/2;
	}
	System.out.println(num+"所在的位置是"+centerIndex);
}
```