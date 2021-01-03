# 算法题库

## 冒泡排序

冒泡排序（Bubble Sort），是一种计算机科学领域的较简单的排序算法。它重复地走访过要排序的元素列，依次比较两个相邻的元素，如果顺序（如从大到小、首字母从Z到A）错误就把他们交换过来。走访元素的工作是重复地进行直到没有相邻元素需要交换，也就是说该元素列已经排序完成。这个算法的名字由来是因为越小的元素会经由交换慢慢“浮”到数列的顶端（升序或降序排列），就如同碳酸饮料中二氧化碳的气泡最终会上浮到顶端一样，故名“冒泡排序”。
图解:
![blockchain](/images/sort/maopao.gif "冒泡")
> 算法步骤：
1. 从第一个元素开始，比较相邻的元素，如果第一个比第二个大，就交换他们两个。
2. 从开始第一对到结尾的最后一对，对每一对相邻元素作同样的工作。比较结束后，最后的元素应该会是最大的数。
3. 对所有的元素重复以上的步骤，除了最后一个。
4. 重复上面的步骤，每次比较的对数会越来越少，直到没有任何一对数字需要比较

```php
// 冒泡排序
function bubble_sort($arr)
{
    $len = count($arr);
    for ($i = 0; $i < $len -1; $i++) {//循环对比的轮数
        for ($j = 0; $j < $len - $i - 1; $j++) {//当前轮相邻元素循环对比
            if ($arr[$j] > $arr[$j + 1]) {//如果前边的大于后边的
                $tmp = $arr[$j];//交换数据
                $arr[$j] = $arr[$j + 1];
                $arr[$j + 1] = $tmp;
            }
        }
    }
    return $arr;
}
$arr = [5,2,4,7,9,4,2,6,8,3];
print_r(bubble_sort($arr));
```

## 快速排序

选择一个基准元素，通常选择第一个元素或者最后一个元素。通过一趟扫描，将待排序列分成两部分，一部分比基准元素小，一部分大于等于基准元素。此时基准元素在其排好序后的正确位置，然后再用同样的方法递归地排序划分的两部分。
图解:
![blockchain](/images/sort/quick.gif "快速")
> 快速排序采用分治法实现排序，具体步骤：
1. 从数列中挑出一个数作为基准元素。通常选择第一个或最后一个元素。
2. 扫描数列，以基准元素为比较对象，把数列分成两个区。规则是：小的移动到基准元素前面，大的移到后面，相等的前后都可以。分区完成之后，基准元素就处于数列的中间位置。
3. 然后再用同样的方法，递归地排序划分的两部分。

```php
function quickSort($arr) {
    //先判断是否需要继续进行
    $length = count($arr);
    if($length <= 1) {
        return $arr;
    }
    //选择第一个元素作为基准
    $base_num = $arr[0];
    //遍历除了标尺外的所有元素，按照大小关系放入两个数组内
    //初始化两个数组
    $left_array = array();  //小于基准的
    $right_array = array();  //大于基准的
    for($i=1; $i<$length; $i++) {
        if($base_num > $arr[$i]) {
            //放入左边数组
            $left_array[] = $arr[$i];
        } else {
            //放入右边
            $right_array[] = $arr[$i];
        }
    }
    //再分别对左边和右边的数组进行相同的排序处理方式递归调用这个函数
    $left_array = quickSort($left_array);
    $right_array = quickSort($right_array);
    //合并
    return array_merge($left_array, array($base_num), $right_array);
}
```

## 插入排序

在要排序的一组数中，假设前面的数已经是排好顺序的，现在要把第 n 个数插到前面的有序数中，使得这 n 个数也是排好顺序的。如此反复循环，直到全部排好顺序。
图解:
![blockchain](/images/sort/insert.gif "插入")
> 算法步骤：
1. 从第一个元素开始，该元素可以认为已经被排序；
2. 取出下一个元素，在已经排序的元素序列中从后向前扫描；
3. 如果以排序的元素大于新元素，将该元素移到下一位置；
4. 重复步骤3，直到找到已排序的元素小于或者等于新元素的位置；
5. 将新元素插入到该位置中；
6. 重复步骤2。

```php
// 方式一(从大到小排)
function quiclySort($arr) {
    $count = count($arr);
    for ($i=1;$i<$count;$i++) {
            $tmp = $arr[$i];
            $j = $i - 1;
            while ($j >= 0 && $tmp > $arr[$j]) {
                    $arr[$j+1] = $arr[$j--];
            }
            $arr[$j+1] = $tmp;
    }
    return $arr;
}
// 方式二(从小到大排)
function insertSort($arr) {
    $len=count($arr);
        for($i=1, $i<$len; $i++)
            $tmp = $arr[$i];
            //内层循环控制，比较并插入
            for($j=$i-1;$j>=0;$j--) {
                if($tmp < $arr[$j]) {
                    //发现插入的元素要大，交换位置，将后边的元素与前面的元素互换
                    $arr[$j+1] = $arr[$j];
                    $arr[$j] = $tmp;
                } else {
                    //如果碰到不需要移动的元素，由于是已经排序好是数组，则前面的就不需要再次比较了。
                    break;
                }
            }
        }
    return $arr;
}
```

## 选择排序

在要排序的一组数中，选出最小的一个数与第一个位置的数交换。然后在剩下的数当中再找最小的与第二个位置的数交换，如此循环到倒数第二个数和最后一个数比较为止。
图解:
![blockchain](/images/sort/choose.gif "选择")
> 算法步骤：
1. 首先，在序列中找到最小元素，存放到排序序列的起始位置；
2. 接着，从剩余未排序元素中继续寻找最小元素，放到已排序序列的末尾。
3. 重复第二步，直到所有元素均排序完毕。

```php
function selectSort($arr) {
//双重循环完成，外层控制轮数，内层控制比较次数
 $len=count($arr);
    for($i=0; $i<$len-1; $i++) {
        //先假设最小的值的位置
        $p = $i;
        for($j=$i+1; $j<$len; $j++) {
            //$arr[$p] 是当前已知的最小值
            if($arr[$p] > $arr[$j]) {
            //比较，发现更小的,记录下最小值的位置；并且在下次比较时采用已知的最小值进行比较。
                $p = $j;
            }
        }
        //已经确定了当前的最小值的位置，保存到$p中。如果发现最小值的位置与当前假设的位置$i不同，则位置互换即可。
        if($p != $i) {
            $tmp = $arr[$p];
            $arr[$p] = $arr[$i];
            $arr[$i] = $tmp;
        }
    }
    //返回最终结果
    return $arr;
}
```

## 归并排序

归并排序是建立在归并操作上的一种有效的排序算法。
归并排序将待排序的序列分成若干组，保证每组都有序，然后再进行合并排序，最终使整个序列有序。
该算法是采用分治法的一个非常典型的应用。
图解:
![blockchain](/images/sort/guibin.gif "归并")
> 算法步骤：
1. 申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列；
2. 设定两个指针，最初位置分别为两个已经排序序列的起始位置
3. 比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置
4. 重复步骤3直到某一指针达到序列尾
5. 将另一序列剩下的所有元素直接复制到合并序列尾

```php
/**
 * 归并排序
 *
 * @param array $lists
 * @return array
 */
function merge_sort(array $lists)
{
    $n = count($lists);
    if ($n <= 1) {
        return $lists;
    }
    $left = merge_sort(array_slice($lists, 0, floor($n / 2)));
    $right = merge_sort(array_slice($lists, floor($n / 2)));
    $lists = merge($left, $right);
    return $lists;
}

function merge(array $left, array $right)
{
    $lists = [];
    $i = $j = 0;
    while ($i < count($left) && $j < count($right)) {
        if ($left[$i] < $right[$j]) {
            $lists[] = $left[$i];
            $i++;
        } else {
            $lists[] = $right[$j];
            $j++;
        }
    }
    $lists = array_merge($lists, array_slice($left, $i));
    $lists = array_merge($lists, array_slice($right, $j));
    return $lists;
}
```

## 堆排序

堆排序是指利用堆这种数据结构所设计的一种排序算法。
堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。
堆排序的平均时间复杂度为Ο(nlogn) 。
图解:
![blockchain](/images/sort/dui.gif "堆")
> 算法步骤：
1. 创建一个堆H[0..n-1]；
2. 把堆首（最大值）和堆尾互换；
3. 把堆的尺寸缩小1，并调用shift_down(0)，目的是把新的数组顶端数据调整到相应位置；
4. 重复步骤2，直到堆的尺寸为1。

```php
/**
 * 堆排序
 *
 * @param array $lists
 * @return array
 */
function heap_sort(array $lists)
{
    $n = count($lists);
    build_heap($lists);
    while (--$n) {
        $val = $lists[0];
        $lists[0] = $lists[$n];
        $lists[$n] = $val;
        heap_adjust($lists, 0, $n);
        //echo "sort: " . $n . "\t" . implode(', ', $lists) . PHP_EOL;
    }
    return $lists;
}

function build_heap(array &$lists)
{
    $n = count($lists) - 1;
    for ($i = floor(($n - 1) / 2); $i >= 0; $i--) {
        heap_adjust($lists, $i, $n + 1);
        //echo "build: " . $i . "\t" . implode(', ', $lists) . PHP_EOL;
    }
    //echo "build ok: " . implode(', ', $lists) . PHP_EOL;
}

function heap_adjust(array &$lists, $i, $num)
{
    if ($i > $num / 2) {
        return;
    }
    $key = $i;
    $leftChild = $i * 2 + 1;
    $rightChild = $i * 2 + 2;

    if ($leftChild < $num && $lists[$leftChild] > $lists[$key]) {
        $key = $leftChild;
    }
    if ($rightChild < $num && $lists[$rightChild] > $lists[$key]) {
        $key = $rightChild;
    }
    if ($key != $i) {
        $val = $lists[$i];
        $lists[$i] = $lists[$key];
        $lists[$key] = $val;
        heap_adjust($lists, $key, $num);
    }
}
```

## 希尔排序

希尔排序，也称递减增量排序算法，是插入排序的一种更高效的改进版本。
但希尔排序是非稳定排序算法。
希尔排序是基于插入排序的以下两点性质而提出改进方法的：
图解:
![blockchain](/images/sort/xier.gif "希尔")
> 算法步骤：
1. 先将整个待排序的记录序列分割成为若干子序列，分别进行直接插入排序
2. 待整个序列中的记录“基本有序”时，再对全体记录进行依次直接插入排序。

```php 
/**
 * 希尔排序 标准
 *
 * @param array $lists
 * @return array
 */
function shell_sort(array $lists)
{
    $n = count($lists);
    $step = 2;
    $gap = intval($n / $step);
    while ($gap > 0) {
        for ($gi = 0; $gi < $gap; $gi++) {
            for ($i = $gi; $i < $n; $i += $gap) {
                $key = $lists[$i];
                for ($j = $i - $gap; $j >= 0 && $lists[$j] > $key; $j -= $gap) {
                    $lists[$j + $gap] = $lists[$j];
                    $lists[$j] = $key;
                }
            }
        }
        $gap = intval($gap / $step);
    }
    return $lists;
}
```

## 基数排序
基数排序是一种非比较型整数排序算法，其原理是将整数按位数切割成不同的数字，然后按每个位数分别比较。
由于整数也可以表达字符串（比如名字或日期）和特定格式的浮点数，所以基数排序也不是只能使用于整数。
图解:
![blockchain](/images/sort/ji.gif "基")
```
说基数排序之前，我们简单介绍桶排序：

桶排序是将阵列分到有限数量的桶子里。

每个桶子再个别排序，有可能再使用别的排序算法，或是以递回方式继续使用桶排序进行排序。

桶排序是鸽巢排序的一种归纳结果。

当要被排序的阵列内的数值是均匀分配的时候，桶排序使用线性时间O(n)。

但桶排序并不是 比较排序，他不受到 O(n log n) 下限的影响。

简单来说，就是把数据分组，放在一个个的桶中，然后对每个桶里面的在进行排序。

例如，要对大小为[1..1000]范围内的n个整数A[1..n]排序

首先，可以把桶设为大小为10的范围，具体而言，设集合B[1]存储[1..10]的整数，集合B[2]存储   (10..20]的整数，……集合B[i]存储(   (i-1)*10,   i*10]的整数，i   =   1,2,..100。总共有  100个桶。

然后，对A[1..n]从头到尾扫描一遍，把每个A[i]放入对应的桶B[j]中。  再对这100个桶中每个桶里的数字排序，这时可用冒泡，选择，乃至快排，一般来说任  何排序法都可以。

最后，依次输出每个桶里面的数字，且每个桶中的数字从小到大输出，这  样就得到所有数字排好序的一个序列了。

假设有n个数字，有m个桶，如果数字是平均分布的，则每个桶里面平均有n/m个数字。

如果对每个桶中的数字采用快速排序，那么整个算法的复杂度是

O(n   +   m   *   n/m*log(n/m))   =   O(n   +   nlogn   –   nlogm)

从上式看出，当m接近n的时候，桶排序复杂度接近O(n)

当然，以上复杂度的计算是基于输入的n个数字是平均分布这个假设的。这个假设是很强的  ，实际应用中效果并没有这么好。如果所有的数字都落在同一个桶中，那就退化成一般的排序了。

前面说的几大排序算法 ，大部分时间复杂度都是O（n2），也有部分排序算法时间复杂度是O(nlogn)。而桶式排序却能实现O（n）的时间复杂度。但桶排序的缺点是：

1）首先是空间复杂度比较高，需要的额外开销大。排序有两个数组的空间开销，一个存放待排序数组，一个就是所谓的桶，比如待排序值是从0到m-1，那就需要m个桶，这个桶数组就要至少m个空间。

2）其次待排序的元素都要在一定的范围内等等。
```

```php
/**
 * 基数排序
 *
 * @param array $lists
 * @return array
 */
function radix_sort(array $lists)
{
    $radix = 10;
    $max = max($lists);
    $k = ceil(log($max, $radix));
    if ($max == pow($radix, $k)) {
        $k++;
    }
    for ($i = 1; $i <= $k; $i++) {
        $newLists = array_fill(0, $radix, []);
        for ($j = 0; $j < count($lists); $j++) {
            $key = $lists[$j] / pow($radix, $i - 1) % $radix;
            $newLists[$key][] = $lists[$j];
        }
        $lists = [];
        for ($j = 0; $j < $radix; $j++) {
            $lists = array_merge($lists, $newLists[$j]);
        }
    }
    return $lists;
}
```

## 各种排序的稳定性，时间复杂度、空间复杂度、稳定性总结如下图：

![blockchain](/images/sort/sort_table.jpg "总结")


> 关于时间复杂度：

(1)平方阶(O(n2))排序
各类简单排序:直接插入、直接选择和冒泡排序；

(2)线性对数阶(O(nlog2n))排序
　　快速排序、堆排序和归并排序；
(3)O(n1+§))排序,§是介于0和1之间的常数。

希尔排序

(4)线性阶(O(n))排序

基数排序，此外还有桶、箱排序。

关于稳定性：

稳定的排序算法：冒泡排序、插入排序、归并排序和基数排序

不是稳定的排序算法：选择排序、快速排序、希尔排序、堆排序