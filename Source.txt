#include <iostream>
using namespace std;
class Rational
{
public:
	Rational(int num = 0, int den = 1);
	double addition(Rational c);
	double subtraction(Rational c);
	double multiplication(Rational c);
	double division(Rational c);
	void printRational();
	void printRationalAsDouble();
private:
	int numerator;	// initializes numerator
	int denominator;	// initializes denominator
	double d;	// initializes d
	double x;	// initializes x 
private:
	double reduction();
};
Rational::Rational(int num, int den) : numerator(num), denominator(den)
{

}

double Rational::addition(Rational c)
{
	numerator = numerator + c.numerator; // adds numerator
	denominator = denominator + c.denominator; // add denominator
	return reduction();
}


double Rational::subtraction(Rational c)
{
	numerator = numerator - c.numerator; // subtracts numerator
	denominator = denominator - c.denominator; // subtracts denominator
	return reduction();
}

double Rational::multiplication(Rational c)
{
	numerator = numerator * c.numerator; // multiplies numerator
	denominator = denominator * c.denominator; // multiplies denominator
	return reduction();
}

double Rational::division(Rational c)
{
	numerator = numerator * c.denominator; // divides numerator and denominator
	denominator = denominator * c.numerator; // divdes denominator and numerator
	return reduction();
}

void Rational::printRational()
{
	cout << numerator << "/" << denominator; // prints fraction
}

void Rational::printRationalAsDouble()
{
	cout << d / static_cast<float>(x); // prints as a double number
}

double Rational::reduction()
{
	int largest; // initializes largest
	largest = numerator > denominator ? numerator : denominator;

	int gcd = 0; // greatest common divisor

	for (int loop = 2; loop <= largest; loop++) // initializes loop to 2, if loop is less that or equal to the largest, then increment the loop counter.

		if (numerator % loop == 0 && denominator % loop == 0) //if the loop's remainder equals 0 and the denominator's remainder equals 0,
			gcd = loop; // then the greatest common denominator is assigned the value of the loop.

	if (gcd != 0)
	{					// if the greatest common denominator does not equal 0, the divide both the numerator and the denominator by the greatest common denominator.
		numerator /= gcd;
		denominator /= gcd;
	} // end if 

	return gcd;
} // end function reduction
int main()
{
	Rational c; // instantiates objects c of class Rational
	cout << "The result of the calculation is:"<<endl;
	c.printRational();
	cout <<endl<< "The result of the calculation is:"<<endl;
	c.printRationalAsDouble();
	cout << endl;
	/*ush(stdin);
	cin.get();*/
	system("pause");
	return 0;
}

