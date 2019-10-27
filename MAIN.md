#include "pch.h"
#include <Windows.h>

#include "VentanaPrincipal.h"
#include "VentanaPlay.h"

using namespace System;
using namespace System::ComponentModel;
using namespace System::Collections;
using namespace System::Windows::Forms;
using namespace System::Data;
using namespace System::Drawing;

using namespace MasterMindProyectoFinal;

int main(array<System::String^>^ args)
{
	Application::EnableVisualStyles();
	Application::SetCompatibleTextRenderingDefault(false);
	VentanaPrincipal vent_principal;
	Application::Run(% vent_principal);

	//juego.Show();
	//system("pause");

    return 0;
}
