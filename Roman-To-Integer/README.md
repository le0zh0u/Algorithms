#Roman to Integer
LeetCodeOJ Algorithms Question8 Roman to Integer

Question Name: Roman to Integer

Description:
	
	
	Given a roman numeral, convert it to an integer.

	Input is guaranteed to be within the range from 1 to 3999.
	

Spoilers:
	
	罗马数字共有七个，即I(1)，V(5)，X(10)，L(50)，C(100)，D(500)，M(1000)。按照下面的规则可以表示任意正整数。
	
	重复数次：一个罗马数字重复几次，就表示这个数的几倍。 

	右加左减：在一个较大的罗马数字的右边记上一个较小的罗马数字，表示大数字加小数字。在一个较大的数字的左边记上一个较小的罗马数字，表示大数字减小数字。但是，左减不能跨越等级。比如，99不可以用IC表示，用XCIX表示。 

	加线乘千：在一个罗马数字的上方加上一条横线或者在右下方写M，表示将这个数字乘以1000，即是原数的1000倍。同理，如果上方有两条横线，即是原数的1000000倍。 

	单位限制：同样单位只能出现3次，如40不能表示为XXXX，而要表示为XL。
[显示1~1000的罗马数字连接](http://www.360doc.com/content/12/1128/19/803452_250820485.shtml "链接")

Thinking:
	
	想法与Integer to Roman 相类似，增加一个map，然后遍历map，String去匹配map中的罗马数字，选择最大的值
	
coding:

	public class Solution {
    public static int romanToInt(String s) {
        int result = 0;
        Map<String, String> map = new HashMap<String, String>();
        map.put("1", "I");
        map.put("2", "II");
        map.put("3", "III");
        map.put("4", "IV");
        map.put("5", "V");
        map.put("6", "VI");
        map.put("7", "VII");
        map.put("8", "VIII");
        map.put("9", "IX");
        map.put("10", "X");
        map.put("20", "XX");
        map.put("30", "XXX");
        map.put("40", "XL");
        map.put("50", "L");
        map.put("60", "LX");
        map.put("70", "LXX");
        map.put("80", "LXXX");
        map.put("90", "XC");
        map.put("100", "C");
        map.put("200", "CC");
        map.put("300", "CCC");
        map.put("400", "CD");
        map.put("500", "D");
        map.put("600", "DC");
        map.put("700", "DCC");
        map.put("800", "DCCC");
        map.put("900", "CM");
        map.put("1000", "M");
        map.put("2000", "MM");
        map.put("3000", "MMM");

        Integer m=0;
        Integer c=0;
        Integer x=0;
        Integer i=0;
        Integer temp = 0;
        Iterator<Map.Entry<String, String>> entries = map.entrySet().iterator();
        while (entries.hasNext()) {
            Map.Entry<String, String> entry = entries.next();
            if(s.contains(entry.getValue())){
                if(entry.getKey().length()==4){
                    //包含CM,M,MM,MMM
                    if(entry.getValue().equals("M")&&s.contains("CM")&&!s.contains("MC")){
                        //排除CM
                        continue;
                    }
                    temp = Integer.parseInt(entry.getKey());
                    if(temp>m){
                        m=temp;
                    }
                }else if(entry.getKey().length() == 3){
                    //包含90 - 900
                    if(entry.getValue().equals("C")&&s.contains("XC")&&!s.contains("CX")){
                        //排除90
                        continue;
                    }
                    temp = Integer.parseInt(entry.getKey());
                    if(temp>c){
                        if(temp.equals(500)){
                            if(s.contains("CD")){
                                temp = 400;
                            }
                        }
                        c = temp;
                    }
                }else if(entry.getKey().length()==2){
                    //包含 9 - 90
                    if(entry.getValue().equals("X")&&s.contains("IX")&&!s.contains("XI")){
                        continue;
                    }
                    temp = Integer.parseInt(entry.getKey());
                    if(temp>x){
                        if(temp.equals(50)){
                            if(s.contains("XL")){
                                temp = 40;
                            }
                        }
                        x = temp;
                    }
                }else{
                    temp = Integer.parseInt(entry.getKey());
                    if(temp>i){
                        if(temp.equals(5)){
                            if(s.contains("IV")){
                                temp = 4;
                            }
                        }
                        i = temp;
                    }
                }
            }
        }
        result = m+c+x+i;


        return result;
    }
	}
	
ending:
	
	虽然说做出来了，但并不满意，因为在提交过程中，发现自己漏考虑了很多东西，这个答案是提交提出来的，诶。
	卧槽，点金more detail，显示"You are here! Your runtime beats 0.84% of java submissions"。击败了百分之零点八四，我是有多水额。智商不够咋办。