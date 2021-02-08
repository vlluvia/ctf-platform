

# Guess-the-Number

* 下载文件是jar文件，用jd-gui-0.3.6.windows打开，得到java代码
``` 
import java.io.PrintStream;

public class guess
{
  static String XOR(String _str_one, String _str_two)
  {
    java.math.BigInteger i1 = new java.math.BigInteger(_str_one, 16);
    java.math.BigInteger i2 = new java.math.BigInteger(_str_two, 16);
    java.math.BigInteger res = i1.xor(i2);
    String result = res.toString(16);
    return result;
  }
  
  public static void main(String[] args) {
    int guess_number = 0;
    int my_num = 349763335;
    int my_number = 1545686892;
    int flag = 345736730;
    
    if (args.length > 0) {
      try {
        guess_number = Integer.parseInt(args[0]);
        if (my_number / 5 == guess_number) {
          String str_one = "4b64ca12ace755516c178f72d05d7061";
          String str_two = "ecd44646cfe5994ebeb35bf922e25dba";
          my_num += flag;
          String answer = XOR(str_one, str_two);
          
          System.out.println("your flag is: " + answer);
        } else {
          System.err.println("wrong guess!");
          System.exit(1);
        }
      } catch (NumberFormatException e) {
        System.err.println("please enter an integer \nexample: java -jar guess 12");
        System.exit(1);
      }
    } else {
      System.err.println("wrong guess!");
      int num = 1000000;
      num++;
      System.exit(1);
    }
  }
}

```

* 分析代码，得到解密代码
``` 
class Untitled {
static String XOR(String _str_one, String _str_two)
  {
    java.math.BigInteger i1 = new java.math.BigInteger(_str_one, 16);
    java.math.BigInteger i2 = new java.math.BigInteger(_str_two, 16);
    java.math.BigInteger res = i1.xor(i2);
    String result = res.toString(16);
    return result;
  }
	public static void main(String[] args) {
		String str_one = "4b64ca12ace755516c178f72d05d7061";
          String str_two = "ecd44646cfe5994ebeb35bf922e25dba";
		String answer = XOR(str_one, str_two);
          
          System.out.println("your flag is: " + answer);
		System.out.println("hello https://tool.lu/");
	}
}
```

* 运行之后，得到flag
> your flag is: a7b08c546302cc1fd2a4d48bf2bf2ddb


