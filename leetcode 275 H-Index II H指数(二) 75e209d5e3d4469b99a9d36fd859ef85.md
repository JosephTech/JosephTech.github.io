# leetcode 275. H-Index II H指数(二)

Tags: 二分查找BS
上传github: No
思路①一句话：: BS  +  初始化ans  (0篇文章被引用超过x次, 则ans=0)  +  贪心(找到了h,  就继续左半拉找更大的h)
手撕代码第①次: No
手撕代码第②次: No
手撕代码第③次: No
提交官方oj: Yes
整理博客: Yes
最后刷题时刻: December 16, 2021
来源/课程: leetcode大宝剑
难度: ⭐ ⭐

- [ ]  lesson
- [ ]  note
- [ ]  code
- [ ]  pseudo
- [ ]  mark

# 课

# 题目：

# ⭐**思路一：BS  +  初始化ans  (0篇文章被引用超过x次, 则ans=0)  +  贪心(找到了h,  就继续左半拉找更大的h)**

**参考资料：**

**手撕：**

**github：**

**提交leetcode:**

![Untitled](leetcode%20275%20H-Index%20II%20H%E6%8C%87%E6%95%B0(%E4%BA%8C)%2075e209d5e3d4469b99a9d36fd859ef85/Untitled.png)

**错误分析:**

由测试用例可知:

0篇文章被引用 ≥ 0次

所以h-index = 0

**所以ans初始化为0**

```cpp
/*
题目:
    H指数(二)
    
    给定一个 整形数组citations
    citations[i]是一个研究员 第i篇文章 被引用数量
    citations是升序排列的
    
    根据h-index的定义:  一个科学家, 如果n篇文章中的h篇, 至少有h次引用,
    就是h-index,
    (其他n-h篇, 每篇都不够h篇引用)
    (这条件能同时满足??? 我咋那么不信呢)
    
    
    如果h有数个 可能的值,  最大的被选为h-index
    
    你必须写一个算法,  log时间的
    
分析:
    log时间,  八成是BS
    升序,  那绝对是BS了
    mid是idx, 可行吗?
        可以, 因为arr[mid]是引文数量c, 
        h = n-mid+1是几篇文章 达到这个引用了
        如果 c>=h:
            更新ans
            左侧继续找,  (贪心, 弹最大的h)
        如果c < h:
            右侧找
    
    (这里, 逻辑挺绕的)
    
    
*/
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int l = 0;
        int n = citations.size()-1;  // ]
        int r = n;
        
        int ans = -1;  // 找最大的h
        
        while(l <= r){  // []
            int mid = l + (r - l)/2;
            int h = n - mid + 1;  // 注意: c++要声明数据类型
            if (citations[mid] >= h){
                ans = max(ans, h);  // 找最大的h,  h是文章数, 所以贪h. (弹citation[i]会错, 试试)
                r = mid - 1;  // 在左侧, 继续找最大的h
            }
            else
                l = mid + 1;  // 在右侧, 找
        }
        //assert(ans != -1);
        return ans;
    }
};
```

![Untitled](leetcode%20275%20H-Index%20II%20H%E6%8C%87%E6%95%B0(%E4%BA%8C)%2075e209d5e3d4469b99a9d36fd859ef85/Untitled%201.png)

(捅穿 如来佛哈哈哈哈)

**注意:**  高亮部分

```cpp
/*
题目:
    H指数(二)
    
    给定一个 整形数组citations
    citations[i]是一个研究员 第i篇文章 被引用数量
    citations是升序排列的
    
    根据h-index的定义:  一个科学家, 如果n篇文章中的h篇, 至少有h次引用, **(注意: 是h次及以上, 所以贪h最大)**
    就是h-index,
    (其他n-h篇, 每篇都不够h篇引用)
		(这么绕的规则,  一定是英国佬tea_cup想出来了)
    (这条件能同时满足??? 我咋那么不信呢)
    
    
    **如果h有 数个可能的值,  最大的被选为h-index**
    
    你必须写一个算法,  log时间的
    
分析:
    log时间,  八成是BS
    升序,  那绝对是BS了
    mid是idx, 可行吗?
        可以, 因为arr[mid]是引文数量c, 
        h = n-mid+1是几篇文章 达到这个引用了
        如果 c>=h:
            更新ans
            左侧继续找,  (贪心, 弹最大的h)
        如果c < h:
            右侧找
    
    (这里, 逻辑挺绕的)
    
    
*/
class Solution {
public:
    int hIndex(vector<int>& citations) {
        int l = 0;
        int n = citations.size()-1;  // ]
        int r = n;
        
        int ans = 0;  // 找最大的h,  边界: 0篇文章被引用超过x次, 则h-idx = 0
        
        while(l <= r){  // []
            int mid = l + (r - l)/2;
            int h = n - mid + 1;  // 注意: [mid, last]是h篇文章
						// 注意: c++要声明数据类型
            if (citations[mid] >= h){
                ans = max(ans, h);  // 找最大的h,  h是文章数, 所以贪h. (贪citation[i]会错, 试试)
                r = mid - 1;  // 在左侧, 继续找最大的h
            }
            else
                l = mid + 1;  // 在右侧, 找
        }
        return ans;
    }
};
```

# **思路二：**

**参考资料：**

**手撕：**

**github：**

**提交leetcode:**

# 思路三：

**参考资料：**

**手撕：**

**github：**

**提交leetcode:**

# 总结：