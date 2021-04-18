# 递归

递归：

- 本质是循环
- 通过函数体来进行的循环

递归模板：

1. 终结语句

2. 递归前处理

3. 调用递归

4. 递归后处理

```java
// Java
public void recur(int level, int param) {
  // terminator
  if (level > MAX_LEVEL)
  {
    // process result
    return;
  }
  // process current logic
  process(level, param);
  // drill down
  recur( level: level + 1, newParam);
  // restore current status
}
```





# 递归状态树

![image-20210418141627327](http://img.newtrekwang.me/img/20210418141627.png)

 

# 分治代码模板

![image-20210418141911076](http://img.newtrekwang.me/img/20210418141911.png)

```java
public Result divideConquer(problem, param1, param2, ...){
  # recursion termanator 终止条件
    if(problem is None){
      return result;
    }
  # prepare data
    data = prepareData(problem);
  	subProblems = split_problem(problem, data);
  # conquer subproblemas
    subResult1 = divideConquer(subProblems[0], p1, ...);
    subResult2 = divideConquer(subProblems[1], p1, ...);
    subResult3 = divideConquer(subProblems[2], p1, ...);
   ...
  # process and generate the final result
     result = processResult(sbuResult1, sbuResult2, sbuResult3, ...);
  # revert the current level states
    ...
  return result; 
}
```

# 回溯

回溯法通常用最简单的递归方法实现，在反复重复上述的步骤后可能出现的两种情况：

- 找到一个可能存在的正确的答案
- 在尝试了所有可能的分布方法后宣告该问题没有答案

在最坏的情况下，回溯法会导致一次复杂度为指数时间的计算

