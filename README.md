# 最大公因數與最小公倍數
找出最大公因數及其最小公倍數:
 ex:輸入2
    輸入3

    輸出:最大公因數=1,最小公倍數=6
#作法
-主函式
```
using System;
namespace LCM_GCD
{
    class Program
    {
        static void Main(string[] args)
        {
            int num1, num2;
            Console.Write("請輸入第一個數:");
            num1 = int.Parse(Console.ReadLine());
            Console.Write("請輸入第一個數:");
            num2 = Convert.ToInt32(Console.ReadLine());
            int Product = num1 * num2;//先將原兩數相乘,以利後續計算最小公倍數
            for(int K=0; K<=1; ++K)
            {
                if (num1 == 0 || num2 == 0)
                {
                    K = 0;
                }
                //只要有0的存在,程式不跳出for迴圈
                else
                {
                    break;
                }
                Console.WriteLine("請輸入至少一數不為0!");
                Console.Write("請輸入第一個數:");
                num1 = int.Parse(Console.ReadLine());
                Console.Write("請輸入第一個數:");
                num2 = Convert.ToInt32(Console.ReadLine());
            }
            //只要有0的存在,程式便不執行公因數公倍數判斷
            if (num1<=num2)
            {
                int box;
                box = num1;
                num1 = num2;
                num2 = box;
            }
            //排序,讓num1必大於等於num2
            int num3 = num1 % num2;
            int box1;
            box1 = num3;
            num3 = num1;
            num1 = num2;
            num2 = box1;
            //第一次輾轉相除法
            while (num1!=0 && num2 !=0)
            {
                num3 = num1 % num2;
                box1 = num3;
                num3 = num1;
                num1 = num2;
                num2 = box1;
            }
            //輾轉相除法,且每做完一輪,先將餘數挪至除數,再將原除數挪至被除數,依照此規則循環
            int Lcm = Product / num1;//由最大公因數*最小公倍數=原兩數相乘            
            Console.WriteLine("最大公因數為={0},最小公倍數為={1}",num1, Lcm);//Lcm是最小公倍數之縮寫
            Console.ReadKey();//讀取任意鍵繼續

        }
    }
}
```
