# Coupon with ocp
merupakan program sederhana yang melakukan perhitungan coupon ditambah dengan potongan diskon dan cashback, program ini menerapkan `Open closed Principle`.

## How does it work
Kunci keberhasilan dari ocp yaitu dengan membuat abstraksi terlebih dahulu
```csharp
public abstract class Coupon
    {
        public abstract double calculate(double originPrice);
    }
```
kemudian proses perhitungan terdapat 4 macam yaitu `CouponWithCashback`, `CouponWithMaxNominal`, `CouponWithPercentage` dan `CouponWithNominal`.

-CouponWithCashback
```
public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
```
dilakukan dengan cara melakukan pengurangan pada harga real dengan discNominal.

- CouponWithMaxNominal
 
  dilakukan perhitungan seperti pada method dibawah ini
```csharp
  public override double calculate(double originPrice)
        {
            double discPercentageInRupiah = discPercentage * originPrice / 100;
            double finalPrice = 0;
            if (discPercentageInRupiah > discNominal)
            {
                finalPrice = originPrice - discNominal;
            }
            else
            {
                finalPrice = originPrice - discPercentageInRupiah;
            }
            return finalPrice;
        }
```
- CouponWithNominal
hampir sama seperti perhitungan cashback
```csharp
  public override double calculate(double originPrice)
        {
            return originPrice - discNominal;
        }
```
-CouponWithPercentage
perhitungannya dilakukan seperti pada method dibawah ini
```csharp
 public override double calculate(double originPrice)
        {
            return (100 - discPercentage) * originPrice / 100;
        }
```


