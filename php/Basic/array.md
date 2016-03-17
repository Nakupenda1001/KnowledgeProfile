##### 检查数组中是否包含某个元素
```php
$array = [1, "2", "three"];
in_array(0, $array);
in_array(1, $array);
in_array(2, $array);
```
备忘：array_flip()  
##### 在数组中查找某个元素，并且定位该元素键值
in_array()可以查找数组是否包含某个元素；
arr_search()可以确定元素在数组中的位置，并返回该元素键值；如果该元素不止一次出现，则返回其中一个元素的键值，不一定是第一个元素。或许是取决于查找数据的起始位置？如果未找到匹配，返回false。用===false来测试返回值。

#####根据条件定位数组元素 array_filter
```php
$movies = array(/* ... */);
$flops = array_filter($movies, function ($movie) {
    return ($movie['box_office_gross'] < 5000000) ? 1 : 0;
});
```

##### 找出数组中的最大值，最小值 max() min()
max()如果传多个参数，max返回其中的最大值；如果只传一个数组参数，返回数组中的最大值。
##### 数组排序
sort() rsort() asort() arsort() ksort() krsort() usort() uasort() uksort()
```php
$tests = array('test1.php', 'test10.php', 'test11.php', 'test2.php');
natsort($tests);
```
The elements are now ordered 'test1.php' , 'test2.php' , 'test10.php' , and
'test11.php' .
natcasesort() 不去分大小写
##### 对多个数组或多维数组排序 array_multisort()
