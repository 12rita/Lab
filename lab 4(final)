// lab4.cpp : Defines the entry point for the console application.
//

#include <stdlib.h>
#include <iostream>
#include <iomanip>
#define WIN32_LEAN_AND_MEAN



#include <stdio.h>
#include <tchar.h>
#include <string>
#include <stdlib.h>
#include <iostream>
#include <fstream>
#include <sstream>
#include <iomanip>
#include <conio.h>
#include <time.h>

using namespace std;
int modal;


class Element
{ protected:
int a;
const static int modal =1000;
public:
    Element(int d = 0)
	{
		a = d%modal;
	}
	friend Element operator+(const Element& sk, const Element& sb);
	friend Element operator*(const Element& sk, const Element& sb);
	friend ostream& operator << (ostream& out, Element const& a);
	friend istream& operator >> (istream& in, Element& a);
};



	Element operator+(const Element& sk, const Element& sb)
	{
		int g=sk.a+sb.a;
		Element d(g);
		return d;
	}
	Element operator*(const Element& sk, const Element& sb)
	{
		int g=sk.a*sb.a;
		Element d(g);
		return d;
	}

	ostream& operator << (ostream& out, Element const& d)
{
	out << d.a;
	return out;
}
istream& operator >> (istream& in, Element& d)
{
	string el;
	in >> el;
	stringstream stsr;
	ss << el;
	ss >> d.a;
	return in;
}


class Matrix
{protected:
	Element** d;
	int stroki, stolbcu;
public:
	Matrix(int sk, int sb, Element** dv = 0)
	{
		d = new Element*[sk];
		for (int i = 0;i < sk; i++)
		{
			d[i] = new Element[sb];
		}
		for (int i = 0;i < sk; i++)
		{
			for (int j = 0;j < sb; j++)
			{
				if (dv != 0)
				{
					d[i][j] = dv[i][j];
				}
				else d[i][j] = 0;
			}
		}
		stroki = sk;
		stolbcu = sb;
	}
	Element poluch(int c, int b)//получение элемента по индексу
	{
		return d[c][b];
	}
	void vstav(int c, int b, Element m)//вставка элемента по индексу
	{
		d[c][b] = m;
		return;
	}
	Matrix operator |(const Matrix& m)//конкатенация
	{
		Matrix q(stroki, (stolbcu+m.stolbcu));
		for (int i = 0;i < stroki; i++)
		{
			for (int j = 0;j < (stolbcu + m.stolbcu); j++)
			{
				if (j < stolbcu)
				{
					q.d[i][j] = d[i][j];
				}
				else q.d[i][j] = m.d[i][j-stolbcu];
			}
		}
		return q;
	}

	Matrix operator +(const Matrix& m)//сложение
	{
		if ((stolbcu != m.stolbcu) || (stroki != m.stroki))
		throw "ne ravn razmer";
		Matrix q(stroki, stolbcu);
		for (int i = 0;i < stroki; i++)
		{
			for (int j = 0;j < stolbcu; j++)
			{
				q.d[i][j] = d[i][j] + m.d[i][j];
			}
		}
		return q;
	}
	Matrix turn(void)
	{
		Matrix q(stolbcu, stroki);
		for (int i = 0; i<stroki;i++)
		{
			for (int j = 0; j < stolbcu;j++)
			{
				q.d[j][stroki-1-i] = d[i][j];
			}
		}
		return q;
	}

	friend ostream& operator << (ostream& out, Matrix const& d);
	friend istream& operator >> (istream& in, Matrix& d);

};



ostream& operator << (ostream& out, Matrix const& d)
{
	for (int i = 0;i < d.stroki; i++)
	{
		for (int j = 0;j < d.stolbcu; j++)
		{
			out << setw(4) << d.d[i][j];
		}
		out << endl;
	}
	return out;
}
istream& operator >> (istream& in, Matrix& d)
{
	string el;
	//in >> el;
	//stringstream stsr;
	//ss << el;
	for (int i = 0;i < d.stroki; i++)
	{
		for (int j = 0;j < d.stolbcu; j++)
		{
			in >> el;
			stringstream stsr;
			ss << el;
			ss >> d.d[i][j];
		}
	}
	return in;
}


int main()
{
     int a1,b1;
srand(time(NULL));
	fstream m1("m1.txt");
	fstream m2("m2.txt");
/*
cout << "vvedite pervoe chislo ";
cin >>a1;
cout << "vvedite vtoroe chislo ";
cin>>b1;
Element a(a1);
Element b(b1);
Element *pp;
pp=&a;
cout<<"a=";
pp->print();
cout << endl;
cout<<"a+b=";(a+b).print();
cout << endl;
cout<<"a*b=";(a*b).print();
cout<<endl;*/
Element** a;
	a = new Element*[5];
	for (int i = 0;i < 5; i++)
	{
		a[i] = new Element[5];
	}
	for (int i = 0;i < 5; i++)
	{
		for (int j = 0;j < 5; j++)
		{
				a[i][j] = rand();
		}
	}

	Matrix b(5, 5, a);
	cout << "prost" << endl << b;
	m1 << b;

	b = b + b;
	cout << "plus" << endl << b;

	b = b | b;
	cout << "konuktinaciya" << endl << b;

	b = b.turn();
	cout << "turn" << endl << b;

	Matrix c(5, 5);
	m2 >> c;
	cout << "from file" << endl << c;

	cout << "enter new matrix 2x2" << endl;
	Matrix d(2, 2);
	cin >> d;
	cout << "new d" << endl << d;

	try
	{
		c = c + d;
		cout << b;
	}
	catch (char*& a)
	{
		cout << "iskluch " << a << endl;
	}

system("pause");
return 0;
}



