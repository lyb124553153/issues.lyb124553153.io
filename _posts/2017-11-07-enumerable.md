---
layout: default.html
title: 日期操作
date: 2017-11-7
---

# 可枚举类型


## flat_map || collect_concat方法

遍历元素，将运行结果链接为数组

```ruby
[1, 2, 3, 4].flat_map { |e| [e, -e] } #=> [1, -1, 2, -2, 3, -3, 4, -4]

[[1, 2], [3, 4]].flat_map { |e| e + [100] } #=> [1, 2, 100, 3, 4, 100]
```

## inject || reduce 方法


```ruby

# sum some numbers
(5..10).reduce(:+)                             #=> 45
(5..10).inject { |sum, n| sum + n }            #=> 45
(5..10).reduce(1, :*)                          #=> 151200
(5..10).inject(1) { |product, n| product * n } #=> 151200

%w{ cat sheep bear }.inject do |memo, word|
  memo.length > word.length ? memo : word
end                                           #=> ‘sheep’

```
## partition
返回是否满足条件两个数组

```ruby
  (1..6).partition { |v| v.even? }  #=> [[2, 4, 6], [1, 3, 5]]
```



## 条件判断

all? 是否所有元素满足条件
any? 是否所有元素满足条件
one？是否有一个元素满足条件
none？是否没有元素满足条件



## each_with_index 和 each_with_object

### each_with_index
Calls <em>block</em> with two arguments, the item and its index,
 for each item in <i>enum</i>.  Given arguments are passed through
 to #each().
```
hash = Hash.new
%w(cat dog wombat).each_with_index { |item, index|
  hash[item] = index
}
hash   #=> {"cat"=>0, "dog"=>1, "wombat"=>2}
```
### each_with_index
each_with_object does not work on immutable objects like integer.
```
(1..3).each_with_object(0) {|i,sum| sum += i} #=> 0
```
This is because each_with_object iterates over a collection, passing each element and the given object to the block. It does not update the value of object after each iteration and returns the original given object.

It would work with a hash since changing value of a hash key changes it for original object by itself.
```
(1..3).each_with_object({:sum => 0}) {|i,hsh| hsh[:sum] += i}
#=> {:sum => 6}
```
String objects are interesting case. They are mutable so you might expect the following to return "abc"
```
("a".."c").each_with_object("") {|i,str| str += i} # => ""
```
but it does not. This is because str += "a" returns a new object and the original object stays the same. However if we do
```
("a".."c").each_with_object("") {|i,str| str << i} # => "abc"
```
it works because str << "a" modifies the original object.

```
(1..3).inject(0) {|sum,i| sum += i} #=> 6
# or
(1..3).inject(:+) #=> 6
```
