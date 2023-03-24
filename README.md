# Delphi Big Numbers

_**NOTICE:**_ See the [TurboPack branch](https://github.com/TurboPack/DelphiBigNumbers) for the _latest updates_.

----

[Rudy Belthuis](http://rvelthuis.de) is the orignal author of this library. He unfortunately passed away a while back. In an effort to keep this valuable library alive we've done the following:

* Pulled changes from [all the other branches](https://github.com/TurboPack/DelphiBigNumbers/network) into this repository
* Created [Wiki articles](https://github.com/TurboPack/DelphiBigNumbers/wiki) based on his original documentation (with some updates)
* Opened up for [issues](https://github.com/TurboPack/DelphiBigNumbers/issues) 
* Fixed some other issues and updated for Delphi 11.3

***Pull requests welcome.*** If you want to help maintain this library, please let us know.

### BigInteger, BigDecimal and BigRational for Delphi

These are implementations of the multi-precision `BigInteger`, `BigDecimal` and `BigRational` types, built from scratch.

## BigInteger

`BigInteger` is a multi-precision integer. Its size is only limited by available memory.

`BigInteger` is built for ease of use, speed and reliability. It is written in plain Object Pascal and x86-32/x86-64 assembler, but every assembler function has a so called "pure Pascal" equivalent as well. It is modelled after the `BigInteger` type in .NET, but is far more optimized than that and provides an interface that is more in line with Delphi. It uses higher level algorithms like *Burnikel-Ziegler*, *Karatsuba*, *Toom-Cook*, etc. to make things fast even for very large integers. It offers overloaded operators and all the usual functions. More information can be found on the [BigIntegers unit](https://github.com/TurboPack/DelphiBigNumbers/wiki/BigIntegers) wiki page.

## BigDecimal

`BigDecimal` is a multi-precision decimal floating point type. It can have an almost unlimited precision.

`BigDecimal` is equally built for ease of use and reliability. It builds on top of BigInteger: the internal representation is a BigInteger for the significant digits, and a scale to indicate the decimals. It also offers overloaded operators and all the usual functions. This is modelled after the `BigDecimal` type in Java, but the interface is more in line with Delphi. More information about this type can be found on the [BigDecimals unit](https://github.com/TurboPack/DelphiBigNumbers/wiki/BigDecimals) wiki page.

## BigRational

A type that holds a number as fraction (ratio) of two `BigIntegers`, a numerator and a denominator, i.e. `1/7` or `100/3`. 
This type is very good at simple arithmetic (`+`, `-`, `*`, `/`), since it doesn't lose precision or need any rounding. Still a work in progress...

## C++Builder

The newest version of BigIntegers has additional overloaded operators and additional constructors that are compatible
with C++Builder. So now you simply include:

    #include "Velthuis.BigIntegers.hpp"

and then you can do things like:

    BigInteger a = 17;
    BigInteger b = "123";
    BigInteger c = a + b;

## Directory structure

```
BigNumbers
   DataGenerators
      BigDecimals
         BigDecimalTestDataGenerator /...       --- Test data generator in Java; 
	                                            open with NetBeans 8
      BigIntegers
         BigIntegerTestGenerator /...           --- Test data generator in C#; open .sln file with 
                                                    Visual Studio 2010 (Express) or newer
	 Java/BigIntegerTestDataGenerator /...  --- Newer test data generator in Java; 
	                                            open with NetBeans 8
      BigRationals                                   
         BigRationalTestDataGenerator /...      --- Test data generator in Java, using the Apache 
                                                    Commons-Math library.
                                                    Open with NetBeans 8. Might require installation 
                                                    of the Apache libs.
   Source                                       --- Sources for units and for bases.inc generator
   Tests
      BigDecimals /...                          --- Sources for DUnit tests for BigDecimals
      BigIntegers /...                          --- Sources for DUnit tests for BigIntegers
      BigRationals /...                         --- Sources for DUnit tests for BigRationals
   Visualizers                                  --- Sources for IDE debug visualizer DLL and packages for BigInteger 
                                                    and BigDecimal   
```

