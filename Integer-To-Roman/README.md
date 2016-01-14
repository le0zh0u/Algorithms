#Integer to Roman
LeetCodeOJ Algorithms Question8 Integer to Roman

Question Name: Integer to Roman

Description:
	
	
	Given an integer, convert it to a roman numeral.

	Input is guaranteed to be within the range from 1 to 3999.
	

Spoilers:
	
	罗马数字共有七个，即I(1)，V(5)，X(10)，L(50)，C(100)，D(500)，M(1000)。按照下面的规则可以表示任意正整数。
	
	重复数次：一个罗马数字重复几次，就表示这个数的几倍。 

	右加左减：在一个较大的罗马数字的右边记上一个较小的罗马数字，表示大数字加小数字。在一个较大的数字的左边记上一个较小的罗马数字，表示大数字减小数字。但是，左减不能跨越等级。比如，99不可以用IC表示，用XCIX表示。 

	加线乘千：在一个罗马数字的上方加上一条横线或者在右下方写M，表示将这个数字乘以1000，即是原数的1000倍。同理，如果上方有两条横线，即是原数的1000000倍。 

	单位限制：同样单位只能出现3次，如40不能表示为XXXX，而要表示为XL。
[显示1~1000的罗马数字连接](http://www.360doc.com/content/12/1128/19/803452_250820485.shtml "链接")

Thinking:
	
	使用map，分别装入1~10，10，20~90，100，200~900，1000，2000，3000等对应的罗马数字，经传入的数字进行解析，根据数字分别从map中进行获取对应的值。从而拼凑成对应的罗马数字。
	
coding:

	