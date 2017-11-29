# 2017涂鸦工厂-最长不重复子串

给定一字符串只包含数字，请写一个算法，找出该字符串中的最长不重复子串（不重复是指子串中每一元素不同于子串中其他元素）

如： “120135435”最长不重复子串为"201354"

```java
public int max_substring(char[] str){  
        int length = str.length;  
        int begin = 0;    //记录最长子串的起点  以便输出最长串  
        int end = 0;    //记录最长子串的终点  以便输出最长串  
        int maxlen = 0;        //最长不重复字符串长度  
        int j = 0;          //记录当前不重复字符串的起点  
        int i = 0;          //记录当前不重复字符串的终点  
        int hs[] = new int[128];   //用数组代替哈希表map  
        int k =0;  
          
        /* 将模拟hashmap的数组初始化*/  
        while(k < 128){  
            hs[k] = -1;  
            k++;  
        }  
        //遍历字符数组  
        while(i < length){       
            if(hs[str[i]-0] >= j){   //如果当前维护的不重复子串中出现了str[i]  
                j = hs[str[i]-0]+1;  //更新j  
            }else{                  //如果当前维护的不重复子串没有出现str[i]  
                if(i-j+1 > maxlen){  
                    maxlen = i-j+1;   /*更新结果取较大者*/  
                    begin = j;        /*  并记录当前较大子串的起点*/  
                    end = i;         /*  并记录当前较大子串的终点*/  
                }  
            }  
            hs[str[i]-0] = i;        //更新map(实际上是更新模拟map的数组)  
            i++;  
        }  
        //打印输出最长串  
        for(int m = begin; m <= end; ++m){  
            System.out.print(str[m]);  
        }  
        return maxlen;  
    }  
    ```

见[java-leetcode/note/003](https://github.com/simifun/java-leetcode/tree/master/leetcode/note/003)

