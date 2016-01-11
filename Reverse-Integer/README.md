# Reverse-Integer
LeetCodeOJ Algorithms Question7 Reverse Integer

Question Name: Reverse Integer

Reverse digits of an integer.

````
Example1: x = 123, return 321
Example2: x = -123, return -321
````
Spoilers:

	Have you thought about this?
	Here are some good questions to ask before coding. Bonus points for you if you have already thought through this!
	
	If the integer's last digit is 0, what should the output be? ie, cases such as 10, 100.

	Did you notice that the reversed integer might overflow? Assume the input is a 32-bit integer, then the reverse of 1000000003 overflows. How should you handle such cases?

	For the purpose of this problem, assume that your function returns 0 when the reversed integer overflows.

	Update (2014-11-10):
	Test cases had been added to test the overflow behavior.

thinking:

	看了一下题目觉得还挺简单的，但是看了"剧透"，发现还是有点坑的。但整体的编码异常简单。
	
	
code:
	
	public class Solution {
    public int reverse(int x) {
        int result = 0;
        String tempResult = "";
        Boolean isPositive = true;
        //判断正负
        if(x<0){
            x = -x;
            isPositive = false;
        }
        //转换成String，并用String进行反转
        tempResult = String.valueOf(x);
        tempResult = new StringBuffer(tempResult).reverse().toString();
        //String转成int，并注意溢出
        try{
            result = Integer.parseInt(tempResult);
            if(!isPositive){
                result = -result;
            }
        }catch(Exception e){
        //溢出则返回0
            result = 0;
        }
        //返回结果
        return result;
    }
	}
