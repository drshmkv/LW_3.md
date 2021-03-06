# Общая информатика

## Лабораторная работа №3
## Шмыкова Дарья 2105-240502D

### Содержание:

1. Условие задачи
2. Блок-схема
3. Код
4. Описание программы

### 1. Задание:

Сделать программу, вычисляющую длину вектора, координаты которого находятся в файле input.txt и сохраняющую результат в файл output.txt.

### 2. Блок-схема алгоритма:

![image](https://user-images.githubusercontent.com/100388979/172998600-13f125c4-2456-4931-a6d9-9d8a3d682327.png)


### 3. Текст и результат работы программы:

#### Текст программы:

```c++

#include <fstream>  //библиотека для ввода в файл и вывода из файла
#include <iostream> //подключение библиотеки для ввода и вывода

using namespace std;

int main() //головная программа
{
	cout << "IDEU" << endl;			//объявляем данные о себе и о задаче
	cout << "ShmykovaDarya" << endl;   
	cout << "Group 2105" << endl;
	cout << "LW number 1" << endl << endl; 
	
	double a, b, c, Vector; //объявляем переменные типа double
	int n = 0; //счётчик, который посчитает сколько координат указано в файле: 1, 2 или 3

	ifstream ifile("C:/Users/User/Desktop/input.txt"); //открыфваем поток ввода из файла

	if (ifile) {					// если файл удалось открыть и он нормальный, то
		while (!ifile.eof() && n < 3) {		//цикл while пока не конецй файла и пока счётчик < 3, то // eof() - если файл закончился то возвращает 1 истину; && - логическоке и
			ifile >> a;			//считываем число , то есть это проверка сколько значимых координат имеется  в файле
			++n; //				//прибавляем +1 к счётчику
		}
	}
	ifile.close();				//закрываем поток ввода

	ofstream ofile("C:/Users/User/Desktop/output.txt");	//открываем поток вывода

	if (ofile) {				//проверим, возможно ли открыть файл для ввода
		if (n < 2) ofile << "error. malo dannih" << endl;	//если у нас меньше двух координат, то выводим В ФАЙЛ сообщение об ошибке 
		else {				//иначе
			ifstream ifile("C:/Users/User/Desktop/input.txt");	//открываем поток ввода 
			if (n == 2) {					//проверяем, если счётчик равен двум, то у нас вектор состоит из 2 элементов, то
				ifile >> a >> b;									
				Vector = sqrt(a * a + b * b);	//и тогда вычисляем его длину по следующей формуле
			
			else {				//иначе счётчик равен 3 и считаем длину вектора из 3 элементов
				ifile >> a >> b >> c;
				Vector = sqrt(a * a + b * b + c * c);		//считаем длину вектора (формула)
			}
			ifile.close();					//закрываем поток ввода
			ofile << "Vector = " << Vector;			//в поток вывода записывается значение посчитанной длины вектора
		}
	}

	ofile.close();		//закрываем поток вывода

	cout << "Check the output file" << endl;

	return 0; //означает нормальное завершение работы головной программы
}

```

#### Результат работы программы:

![image](https://user-images.githubusercontent.com/100388979/172994152-f2502677-f0bf-42b3-aa9f-c545c9c190ac.png)


Если n=1:


![image](https://user-images.githubusercontent.com/100388979/172995256-72492651-5a6a-459c-ae81-5544d1a67bd6.png)
![image](https://user-images.githubusercontent.com/100388979/172994956-c5b9ffa4-72c8-40a1-9a48-d73817018c70.png)


Если n=2:

![image](https://user-images.githubusercontent.com/100388979/172995008-57bd3b73-4746-4ff8-83a6-b3e912f922ac.png)
![image](https://user-images.githubusercontent.com/100388979/172995074-19ecf61f-828f-42d4-b3eb-30b30e5d0330.png)


Если n=3:

![image](https://user-images.githubusercontent.com/100388979/172995126-0540ba60-c400-403e-b2fd-78e02dafe6ef.png)
![image](https://user-images.githubusercontent.com/100388979/172995161-5d5d38c1-f26f-4014-bdbd-4cf0ce34fc9d.png)



Вот что выводится на экран после запуска программы:

![image](https://user-images.githubusercontent.com/100388979/172994735-52e62a99-5d00-41b1-a5a8-263e4fda2a87.png)


### 4. Описание работы программы:

Программа выполняется в Visual Studio 2022. Для считывания данных из файла и для записи в файл использована библиотека fstream, взаимодействие с пользователем реализовывается посредством файла ввода данных, куда пользователь вводит нужные значения, и файла вывода данных, куда записывается результат программы. Сначала пользователь вводит координаты в файл input.txt через пробел и сохраняет файл. Затем запускает программу. Она выполняется, не выводя ничего на экран. Она открывает файл input.txt, считывает из него координаты вектора, одновременно считая их количество (если оно равно единице, то в текстовом документе output.txt говорится, что произошла ошибка, так как мало данных) и закрывает его. Далее открывается файл output.txt, программа сравнивает, соответствует ли количество координат заданным условиям. Если да, то производится вычисление длины вектора и результат выводится в файл. Файл закрывается и программма завершает свое выполнение. Затем пользователь может посмотреть результат работы программы в файле output.txt.
