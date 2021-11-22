## 冒泡排序

```
func Maopao(nums []int) []int {
	n := len(nums)
	if n < 2 {
		return nums
	}

	for i := 0; i < n; i++ {
		flag := false
		//n-i 表示已排序
		//n-i-1表示最后一个不需要排序
		for j := 0; j < n-i-1; j++ {
			if nums[j] > nums[j+1] {
				nums[j], nums[j+1] = nums[j+1], nums[j]
				flag = true
			}
		}

		if !flag {
			break
		}
	}

	return nums
}
```

## 插入排序

```
//InsertionSort 左边为已排序，后面不停往前找,找到左边排序号的数据中合适的位置
func InsertionSort(nums []int) []int {
	n := len(nums)
	if n < 2 {
		return nums
	}

	for i := 0; i < n; i++ {
		val := nums[i]
		j := i - 1
		for ; j >= 0; j-- {
			if val > nums[j] {
				break
			}

			//移动nums[j]的数据往后移一位
			nums[j+1] = nums[j] //移动数据
		}

		nums[j+1] = val
	}
	return nums
}
```

## 选择排序

```
//SelectionSort 左边为已排序，从未排序中找到最小的元素，然后交换到左边的最后面
func SelectionSort(nums []int) []int {
	n := len(nums)
	if n < 2 {
		return nums
	}

	for i := 0; i < n; i++ {
		min := i //最小值的位置
		for j := i + 1; j < n; j++ {
			if nums[j] < nums[min] {
				min = j //交换最小值
			}
		}

		//当前i就是最小情况
		if min == i {
			continue
		}

		nums[i], nums[min] = nums[min], nums[i]
	}

	return nums
}
```

## 归并排序

```
func MergeSort(arr []int) {
	l := len(arr)
	if l <= 1 {
		return
	}

	executeMerge(arr, 0, l-1)
}

func executeMerge(arr []int, start, end int) {
	//终止
	if start >= end {
		return
	}

	//取中位数，防止溢出
	mid := start + (end-start)>>1
	executeMerge(arr, start, mid)
	executeMerge(arr, mid+1, end)

	merge(arr, start, mid, end)
}

func merge(arr []int, start, mid, end int) {
	tmp := make([]int, end-start+1)
	i := start   //左边数组指针
	j := mid + 1 //右边数组指针
	k := 0       //tmp指针
	for ; i <= mid && j <= end; k++ {
		if arr[i] <= arr[j] {
			tmp[k] = arr[i]
			i++ //左边指针移动
		} else {
			tmp[k] = arr[j]
			j++
		}
	}

	//检查那个有富余
	for ; i <= mid; i++ {
		tmp[k] = arr[i]
		k++
	}
	for ; j <= end; j++ {
		tmp[k] = arr[j]
		k++
	}

	//移动
	copy(arr[start:end+1], tmp)
}
```

## 快速排序

```
func Quicksort(nums []int) {
	n := len(nums)
	if n < 2 {
		return
	}
	quicksortc(nums, 0, n-1)
}

func quicksortc(nums []int, p, r int) {
	if p >= r {
		return
	}

	q := partition(nums, p, r) //找分区点

	quicksortc(nums, p, q-1)
	quicksortc(nums, q+1, r)
}

func partition(nums []int, p, r int) int {
	pivot := nums[r]
	i := p
	for j := p; j < r; j++ {
		if nums[j] < pivot {
			nums[i], nums[j] = nums[j], nums[i]
			i++
		}
	}

	nums[i], nums[r] = nums[r], nums[i]
	return i
}

```



**原地排序算法**  就是特指空间复杂度是 O(1) 的排序算法

**稳定性** 如果待排序的序列中存在值相等的元素，经过排序之后，相等元素之间原有的先后顺序不变

