## Golang中for range对slice做出的处理



```
rst := "hello Golang!"
	fmt.Println(&rst)
	for z := range rst {
		fmt.Println(&z, z)
		if z == 'a' {
			z = 's'
		}
		fmt.Println(&z, z)
	}
	fmt.Println("______________________________________________")
	for z := range []rune(rst) {
		fmt.Println(&z, z)
		if z == 'a' {
			z = 's'
		}
		fmt.Println(&z, z)
	}

	rst_l := len(rst)
	for k := 0; k < rst_l; k++ {
		fmt.Printf("%d %v %p\n", k, rst[k], rst[k])
	}
	fmt.Println("----------------------------------------------")
	brst := []byte(rst)
	fmt.Println(&rst, &brst)
	brst_l := len(brst)
	for k := 0; k < brst_l; k++ {
		fmt.Printf("%d %v %p \n", k, brst[k], brst[k])
		if brst[k] == 'a' {
			brst[k] = 's'
		}
		fmt.Printf("%d %v %p \n", k, brst[k], brst[k])
	}
	nrst := string(brst)
	fmt.Println(&rst, rst, &brst[0], &brst[1], &brst[2], brst, &nrst, nrst)
```
range对字符串也进行了内存复制，所以对range循环中的变量操作不影响原始字符串

