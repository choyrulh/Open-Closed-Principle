# Open Closed Principle
Sebagai gambaran yang jelas tentang apa yang di maksud dengan OCP. Setiap entitas software, baik itu (Class, module, fungsi) terbuka untuk perluasan, namun tertutup untuk modifikasi.

## Purpose
Untuk menghindari keretakan software dikarenakan perubahan secara langsung terhadap sebuah class, module, ataupun function.

## About Program
- Pada Source Code ini terdapat 2 program, yakni CouponWithOCP dan CouponWithoutOCP.
- Pada bagian Coupon With OCP, karena menggunakan Abstraction kita dapat mengubah object menjadi object lain tanpa harus meninggalkan fungsi sesungguhnya.
- Sedangkan pada bagian CouponWithoutOCP, jika kalian mengubah salah satu fungsi maka akan memengaruhi fungsi lain.
- Program ini berjalan pada console, sehingga jalankan dengan Run Without Debug.

# Coupon Without OCP.
- Class Coupon
``` C#
class Coupon
    {
        public double discNominal = 0;
        public double priceNett(double originPrice)
        {
            double net = 0;
            net = (100 - discPercentage) * originPrice / 100;
            return net;
        }
    }
  ``` 
  - Class Program
  ```csharp
  class Program
    {
        static void Main(string[] args)
        {


            Coupon coupon1 = new Coupon();
            coupon1.discNominal = 2000;
            Console.WriteLine(coupon1.priceNett(10000));
        }
    }
  ```
  # Coupon With OCP.
  - abstract class Coupon.cs
  ```C#
  public abstract class Coupon
    {
        public abstract double calculate(double originPrice);
    }
  ```
-  class CouponWithNominal.cs
```C#
class CouponWithNominal : Coupon
    {
        public double discNominal;

        public CouponWithNominal(double discNominal)
        {
            this.discNominal = discNominal;
        }

        public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
    }
```
- class Program.cs
```C#
class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello Bro !");
            Coupon coupon1 = new CouponWithNominal(2000);
            Console.WriteLine(coupon1.calculate(10000));
        }
    }
```
Kemudian di explorasi lagi 
