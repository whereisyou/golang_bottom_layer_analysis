## Golang中for range对slice做出的处理



```
	kk := make([]int, 5, 10)
	fmt.Println(&kk[0], &kk[1], &kk[2], &kk[3], &kk[4], kk)
	for i := range kk {
		fmt.Println(&i, i)
		i = 8
		fmt.Println(&i, i)
	}
	fmt.Println("______________________________________________")
	kk_l := len(kk)
	for j := 0; j < kk_l; j++ {

		fmt.Println(&kk[j], kk[j])
		kk[j] = 8
		fmt.Println(&kk[j], kk[j])
	}
	fmt.Println(&kk[0], &kk[1], &kk[2], &kk[3], &kk[4], &kk)
```
range对切片也进行了内存复制，所以对range循环中的变量操作不影响原始切片

