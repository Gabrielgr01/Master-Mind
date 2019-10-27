# Master-Mind

//VentanaPlay.cpp
//CONFIGURACION DEFAULT

#include "pch.h"
#include "VentanaPlay.h"

#include <Windows.h>

using namespace MasterMindProyectoFinal ; // Project name

int WINAPI WinMain(HINSTANCE, HINSTANCE, LPSTR, int)

	{

	Application::EnableVisualStyles();

	Application::SetCompatibleTextRenderingDefault(false);

	Application::Run(gcnew VentanaPlay());

	return 0;

	}
