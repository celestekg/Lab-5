# Lab-5: This program reads data 3 values at a time from the input file, sorts the values in order from lowest to highest, prints the data onto another output file, rereads the data from that file back into memory, and then prints the values displaying lowest to highest.

#include <iostream>
#include <fstream>

using namespace std;

int main()

{
	ifstream fin("file1.txt");
	ofstream fout("file2.txt");

	int a, b, c;

	fin >> a >> b >> c;
	while (a != -1 && b != -1 && c != -1)

	{
		if (a <= b && a <= c)
		{
			if (b <= c)
				fout << a << " " << b << " " << c << endl;
			else
				fout << a << " " << c << " " << b << endl;
		}

		else if (b <= a && b <= c)
		{
			if (a <= c)
				fout << b << " " << a << " " << c << endl;
			else
				fout << b << " " << c << " " << a << endl;
		}

		else
		{
			if (a <= b)
				fout << c << " " << a << " " << b << endl;
			else
				fout << c << " " << b << " " << a << endl;
		}

		fin >> a >> b >> c;
	}

	fin.close();
	fout.close();

	ifstream finl("file2.txt");
	finl >> a >> b >> c;
	while (!finl.eof())

	{
		cout << a << "\t" << b << "\t" << c << endl;
		finl >> a >> b >> c;
	}

	cout << endl;
	system("PAUSE");
	return 0;
}
