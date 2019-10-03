#pragma warning(disable : 4996)
// tarea3_AdrianDittelRetana.cpp : Este archivo contiene la función "main". La ejecución del programa comienza y termina ahí.

//Inclusion de librerias
#include <vector>
#include <iostream>
#include <string>
#include <time.h>
#include <iomanip>
using namespace std;

//Constantes Globales
const string tipos_de_arduino[] =
{
	"UNO",
	"TRE",
	"Zero",
	"Zero Pro",
	"BT",
	"Mega",
	"Ethernet",
	"Pro",
	"Pro Mini",
	"Micro",
	"Primo",
	"Nano",
	"Industrial 101",
	"LilyPad",
	"Esplora"
};

//Estructura definida para el tipo y la cantidad de arduinos
struct produccion

{
	string arduino = "";
	int cantidad = 0;

}producto;

//Funcion para imprimir el tiempo
const string currentDateTime()
{
	time_t     now = time(0);
	struct tm  tstruct;
	char       buf[80];
	tstruct = *localtime(&now);
	strftime(buf, sizeof(buf), "%Y/%m/%d - %X", &tstruct);

	return buf;
}

//Funciones definidas para el funcionamiento del programa


/*Entradas: El tipo de arduino, la cantidad de producir, y el vector de tipo produccion.
  Salidas: El vector con un arduino nuevo o modificado.
  Funcionamiento: Recibe el tipo de arduino y si este ya se encuentra en el vector suma la cantidad asignada, de lo contrario lo agrega al final del vector.
  */
void insertarProduccion(string arduino, int cantidad, vector<produccion>& vectorProduccion)
{
	int unidad = 0;
	for (produccion elemento : vectorProduccion)
	{
		if (elemento.arduino == arduino)
		{
			elemento.cantidad += cantidad;
			vectorProduccion[unidad] = elemento;
			cout << "Cantidad sumada" << endl;
			return;
		}
		unidad++;
	}
	produccion producto;
	producto.arduino = arduino;
	producto.cantidad = cantidad;
	vectorProduccion.push_back(producto);
	cout << "Arduino Ingresado" << endl;
}

/*Entradas: El tipo de arduino y el vector de tipo produccion.
  Salidas: Si el arduino es correcto lo lleva a la funcion de ingresar de lo contrario le indica que no existe.
  Funcionamiento: Recibe el tipo de arduino y lo compara en la lista de arduinos para ver si existe.
  */
void validarEntradas(string arduino, vector<produccion>& vectorProduccion)
{
	int cantidad;
	bool cond = false;
	for (int i = 0; i < 15; i++)
	{
		if (arduino == tipos_de_arduino[i])
		{
			cond = true;

		}
	}
	if (cond == true)
	{
		cout << "Indique la cantidad a producir: ";
		cin >> cantidad;
		insertarProduccion(arduino, cantidad, vectorProduccion);
	}
	else
	{
		cout << " El arduino que indico no existe" << endl;
	}
}

/*Entradas: El tipo de arduino y el vector de tipo produccion.
  Salidas: Tipo de arduino a producir y la cantidad, o un mensaje de error.
  Funcionamiento: Si el tipo de arduino que ingreso existe imprime la cantidad y el tipo a producir, de l contrario indica que no existe.
  */
void consultarProduccion(string arduino, vector<produccion>& vectorProduccion)
{
	for (produccion producto : vectorProduccion)
	{
		if (producto.arduino == arduino)
		{
			cout << "El arduino a producir es " << producto.arduino << endl;
			cout << "La cantidad a producir es " << producto.cantidad << endl;
			return;
		}
	}
	{
		cout << "El arduino que indico no existe o no ha comenzado produccion" << endl;
	}

}

/*Entradas: El tipo de arduino, la cantidad de producir, y el vector de tipo produccion.
  Salidas: El vector con un arduino eliminado o modificado.
  Funcionamiento: Recibe el tipo de arduino y lo compara en la lista de arduinos para ver si existe, si es asi valida que la cantidad ingresada no sea mayor a la existente, si cumple la condicion eliminada la cantidad ingresada si el total da 0 se elimina ese tipo de arduino.
  */
void EliminarProduccion(string arduino, int cantidad, vector<produccion>& vectorProduccion)
{
	int unidad = -1;
	producto;
	for (produccion producto : vectorProduccion)
	{
		unidad++;
		if (producto.arduino == arduino)
		{
			if (producto.cantidad >= cantidad)
			{
				producto.cantidad -= cantidad;
				vectorProduccion[unidad] = producto;
				cout << "Arduino modificado" << endl;
				if (producto.cantidad == 0)
				{
					vectorProduccion.erase(vectorProduccion.begin() + unidad);
					cout << "Arduino eliminado" << endl;
				}
				return;
			}
			else
			{
				cout << "La cantidad indicada no puede restarse pues es mayor a la existente" << endl;
				return;
			}


		}
	}

	{
		cout << "El arduino que indico no existe o no ha comenzado produccion" << endl;
	}

}

/*Entradas: El vector de tipo produccion.
  Salidas: Impresion de las unidades por arduino a producir asi como su porcentaje en la produccion, y la cantidad total a producir.
  Funcionamiento: Recorre el vector de produccion e imprime cada tipo de arduino con su cantidad y calcula su porcentaje dentro de la produccion total.
  */
void consultarProduTotal(vector<produccion>& vectorProduccion)
{
	int porcent = 0;
	int total = 0;
	for (produccion producto : vectorProduccion)
	{
		total += producto.cantidad;
	}
	cout << "PRODUCCION TOTAL DE ARDUINOS" << endl;
	cout << "=============================" << endl;
	cout << left << setw(20) << "TIPO" << right << setw(15) << "CANTIDAD" << right << setw(30) << "% PRODUCCION" << endl;
	for (produccion producto : vectorProduccion)
	{
		int porcentaje = producto.cantidad * 100 / total;
		cout << left << setw(20) << producto.arduino << right << setw(10) << producto.cantidad << right << setw(30) << porcentaje << endl;
	}
	cout << "===============================================================================" << endl;
	cout << left << setw(20) << "TOTAL A PRODUCIR" << right << setw(10) << total << right << setw(30) << 100 << endl;
	cout << endl;
}


int main()
{
	vector <produccion> vectorProduccion;
	string arduino;
	int cantidad;
	int opcion;
	int x = 0;
	while (x == 0)
	{
		cout << "===============================================================================" << endl;
		cout << "FABRICA DE ARDUINOS" << "                           " << currentDateTime() << endl;
		cout << "                    " << "PRODUCCION DE ARDUINOS" << endl;
		cout << "                      " << "CONTROL DE PEDIDOS" << endl;
		cout << "1 - Insertar pedido de produccion" << endl;
		cout << "2 - Consultar produccion de un arduino" << endl;
		cout << "3 - Eliminar pedido de produccion" << endl;
		cout << "4 - Consultar tipos de arduinos que puede producir la fabrica" << endl;
		cout << "5 - Consultar produccion total" << endl;
		cout << "0 - Fin" << endl;
		cout << "Opcion seleccionada: ";
		cin >> opcion;
		switch (opcion)

		{
		case 1:

			cout << "Indique el arduino a producir, los disponibles son" << endl;
			cout << endl;
			for (auto arduino : tipos_de_arduino)
			{
				cout << arduino << endl;
			}
			cout << endl;
			cout << "Arduino: ";
			cin.ignore();
			getline(cin, arduino);
			validarEntradas(arduino, vectorProduccion);
			break;

		case 2:
			cout << "Indique el arduino a consultar: ";
			cin.ignore();
			getline(cin, arduino);
			consultarProduccion(arduino, vectorProduccion);
			break;


		case 3:
			cout << "Indique el arduino a eliminar: ";
			cin.ignore();
			getline(cin, arduino);
			cout << "Indique la cantidad a elminar: ";
			cin >> cantidad;
			EliminarProduccion(arduino, cantidad, vectorProduccion);
			break;

		case 4:
			cout << "Los arduinos disponibles son" << endl;
			cout << endl;
			for (auto arduino : tipos_de_arduino)
			{
				cout << arduino << endl;
			}
			cout << endl;
			break;
		case 5:
			consultarProduTotal(vectorProduccion);
			break;
		case 0:
			cout << endl;
			cout << "Gracias por usar el programa" << endl;
			x = 1;
			break;

		}

	}

	return 0;
}

