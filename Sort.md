## 直接插入排序

### 思想

思想：

#### 1.给我一个序列，我需要一个哨兵A[0]，初始值为第一个元素

#### 2.从第二个元素遍历序列

#### 3.如果第i个元素比第i-1个元素的值（也就是前面有序序列的最大值）小：

我就要把它往前插，并且把此值赋值给哨兵A[0]

往前插就是从第i-1个元素起向前遍历,如果值比哨兵的值小，我就把它向后移一位。

#### 4.否则的话我就继续遍历第i+1个元素

#### 5.遍历整个序列，排序结束

### 代码

```c
void directInsert(int n)//直接插入
{
    int i;
    int j;
    for(i=2;i<=n;i++)
    {
        if(list[i].key<list[i-1].key)
        {
            shaobing=list[i];
            for(j=i-1;list[j].key>shaobing.key;--j)
            {
                list[j+1]=list[j];
            }
            list[j+1]=shaobing;
        }
    }
    return;
}

```

### 优化点

#### 当我们插入list[i]时，查找它的位置可以使用二分查找，这样就变成了折半插入排序





## 冒泡排序

### 思想：

1.首先是一个无序的序列,循环对序列操作n-1次遍历

2.遍历的思想是比较相邻的两个元素，把值小的那个交换到前面

3.这样每一次循环的结果就是把后面的无序序列中的最小元素冒泡到了序列的最后面

### 代码：

```c
void bubblesort(int n)
{
    int i,j;
    node temp;
    for(i=0;i<n-1;i++)
    {
        //优化思想，在某一次循环中，假设没有出现交换，证明整个序列已经有序
        // int flag=false;
        for(j=n-1;j>i;j--)
        {
            //flag=false;
            if(list[j-1].key>list[j].key)
            {
                //flag=true;
                temp=list[j];
                list[j]=list[j-1];
                list[j-1]=temp;
            }
           /* if(!flag)
            {
                return;
            }*/
        }
    }
    return ;
    
}
```



## 快速排序

### 思想：

1.给我一个序列，首先，我确定一个中枢pivot

2.然后进行第一次排序，保证pivot前面的元素都比它小，后面的都比它大







## 简单选择排序

### 思想

1.一个无序序列，循环n-1次

2.第i次循环，把min设为无序序列的第一个值的位置即i+1，然后向下找，如果有值比min位置的值小，把min的值替换成这个位置，这样每一次循环找到的都是无序序列中最小的那个。找完以后如果min不是初始值了，那就交换这两个位置的值。

### 代码

```c
void choosesort(int n)//简单选择排序
{
    int i,j;
    int min;
    node temp;
    for(i=0;i<n-1;i++)
    {
        min=i;
        for(j=i+1;j<n;j++)
        {
            if(list[j].key<list[min].key)
                min=j;
        }
        if(min!=i)
        {
            temp=list[i];
            list[i]=list[min];
            list[min]=temp;
        }
    }
}

```

