## Golang中for range对struct做出的处理



```
package main

import "fmt"

type student struct {
   Name string
   Age int
   Gender bool
}

func main() {
   m := make(map[string]*student)
   stus := []student {
      {Name: "zhou", Age: 24, Gender: true},
      {Name: "li", Age: 23, Gender: false},
      {Name: "wang", Age: 22, Gender: true},
      {Name: "qin", Age: 21, Gender: false},
      {Name: "liu", Age: 18, Gender: false},

   }
   fmt.Println(&stus[0].Name, &stus[0].Age, &stus[1].Name, &stus[2].Age)
   s := len(stus)
   for i:=0;i<s;i++ {
      m[stus[i].Name] = &stus[i]
      fmt.Printf("%v, %v, %v, %v, %p\n", &stus[i].Name, &stus[i].Age, &stus[i].Gender, stus[i], &stus[i])
   }
   for k, v := range m {
      fmt.Println(k, v.Name, " ", v.Age)
   }

}
```
观察内存地址
```
package main

import "fmt"

type student struct {
   Name string
   Age int
}

func main() {
   m := make(map[string]*student)
   stus := []student {
      {Name: "zhou", Age: 24},
      {Name: "li", Age: 23},
      {Name: "wang", Age: 22},
   }
   for _, stu := range stus {
      m[stu.Name] = &stu
      fmt.Printf("%v, %v, %v, %p\n", stu.Name, stu.Age, stu, &stu)
   }
   for _, v := range m {
      fmt.Println(v.Name, " ", v.Age)
   }

}
```

range对结构体进行了内存分配，同类型字段索引地址相同，根据切片中每个结构体的索引访问结构体内部的元素不会发生内存分配，理论性能更好