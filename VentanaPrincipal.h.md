//VentanaPrincipal.h

#pragma once

#include <Windows.h>

#include "GameSettings.h"
#include "Highscores.h"
#include "HowToPlay.h"
#include "Style.h"

namespace MasterMindProyectoFinal {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;

	/// <summary>
	/// Resumen de VentanaPrincipal
	/// </summary>
	public ref class VentanaPrincipal : public System::Windows::Forms::Form
	{
	public: static String^ userNameBtt;
	public:
		
		VentanaPrincipal(void)
		{
			InitializeComponent();
			//
			//TODO: codigo del constructor
			//
		}
		/*
		VentanaPrincipal(ConfigurationClass *objSettings)
		{
			InitializeComponent();

			this->objSettings = objSettings;
			//
			//TODO: codigo del constructor
			//

		}
		*/
	protected:
		/// <summary>
		/// Limpiar los recursos que se estén usando.
		/// </summary>
		~VentanaPrincipal()
		{
			if (components)
			{
				delete components;
			}
		}
	private: System::Windows::Forms::TextBox^ textBox_titulo;
	protected:

	protected:

	private: System::Windows::Forms::Button^ button_play;
	private: System::Windows::Forms::TextBox^ textBox_enter_username;
	private: System::Windows::Forms::MenuStrip^ menuStrip1;
	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ highscoresToolStripMenuItem;


	private: System::Windows::Forms::ToolStripMenuItem^ helpToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ howToPlayToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ quitMasterMindToolStripMenuItem;
	private: System::Windows::Forms::TextBox^ textBox_developers;





	protected:




	private:
		/// <summary>
		/// Variable del diseñador necesaria.
		/// </summary>
		System::ComponentModel::Container ^components;

#pragma region Windows Form Designer generated code
		/// <summary>
		/// Método necesario para admitir el Diseñador. No se puede modificar
		/// el contenido de este método con el editor de código.
		/// </summary>
		void InitializeComponent(void)
		{
			this->textBox_titulo = (gcnew System::Windows::Forms::TextBox());
			this->button_play = (gcnew System::Windows::Forms::Button());
			this->textBox_enter_username = (gcnew System::Windows::Forms::TextBox());
			this->menuStrip1 = (gcnew System::Windows::Forms::MenuStrip());
			this->ayudaToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->highscoresToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->helpToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->howToPlayToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->quitMasterMindToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->textBox_developers = (gcnew System::Windows::Forms::TextBox());
			this->menuStrip1->SuspendLayout();
			this->SuspendLayout();
			// 
			// textBox_titulo
			// 
			this->textBox_titulo->BorderStyle = System::Windows::Forms::BorderStyle::None;
			this->textBox_titulo->Cursor = System::Windows::Forms::Cursors::Default;
			this->textBox_titulo->Location = System::Drawing::Point(156, 91);
			this->textBox_titulo->Margin = System::Windows::Forms::Padding(4, 4, 4, 4);
			this->textBox_titulo->Name = L"textBox_titulo";
			this->textBox_titulo->ReadOnly = true;
			this->textBox_titulo->Size = System::Drawing::Size(148, 15);
			this->textBox_titulo->TabIndex = 0;
			this->textBox_titulo->Text = L"MASTER MIND";
			this->textBox_titulo->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_titulo->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox1_TextChanged);
			// 
			// button_play
			// 
			this->button_play->Location = System::Drawing::Point(168, 226);
			this->button_play->Margin = System::Windows::Forms::Padding(4, 4, 4, 4);
			this->button_play->Name = L"button_play";
			this->button_play->Size = System::Drawing::Size(123, 28);
			this->button_play->TabIndex = 1;
			this->button_play->Text = L"Play";
			this->button_play->UseVisualStyleBackColor = true;
			this->button_play->Click += gcnew System::EventHandler(this, &VentanaPrincipal::button1_Click);
			// 
			// textBox_enter_username
			// 
			this->textBox_enter_username->Location = System::Drawing::Point(168, 153);
			this->textBox_enter_username->Margin = System::Windows::Forms::Padding(4, 4, 4, 4);
			this->textBox_enter_username->MaxLength = 12;
			this->textBox_enter_username->Name = L"textBox_enter_username";
			this->textBox_enter_username->Size = System::Drawing::Size(121, 22);
			this->textBox_enter_username->TabIndex = 2;
			this->textBox_enter_username->Text = L"Enter Username";
			this->textBox_enter_username->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_enter_username->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox2_TextChanged);
			// 
			// menuStrip1
			// 
			this->menuStrip1->ImageScalingSize = System::Drawing::Size(20, 20);
			this->menuStrip1->Items->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(4) {
				this->ayudaToolStripMenuItem,
					this->highscoresToolStripMenuItem, this->helpToolStripMenuItem, this->quitMasterMindToolStripMenuItem
			});
			this->menuStrip1->Location = System::Drawing::Point(0, 0);
			this->menuStrip1->Name = L"menuStrip1";
			this->menuStrip1->Padding = System::Windows::Forms::Padding(8, 2, 0, 2);
			this->menuStrip1->Size = System::Drawing::Size(467, 28);
			this->menuStrip1->TabIndex = 3;
			this->menuStrip1->Text = L"menuStrip1";
			// 
			// ayudaToolStripMenuItem
			// 
			this->ayudaToolStripMenuItem->Name = L"ayudaToolStripMenuItem";
			this->ayudaToolStripMenuItem->Size = System::Drawing::Size(46, 24);
			this->ayudaToolStripMenuItem->Text = L"File";
			// 
			// highscoresToolStripMenuItem
			// 
			this->highscoresToolStripMenuItem->Name = L"highscoresToolStripMenuItem";
			this->highscoresToolStripMenuItem->Size = System::Drawing::Size(96, 24);
			this->highscoresToolStripMenuItem->Text = L"Highscores";
			this->highscoresToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::highscoresToolStripMenuItem_Click);
			// 
			// helpToolStripMenuItem
			// 
			this->helpToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->howToPlayToolStripMenuItem });
			this->helpToolStripMenuItem->Name = L"helpToolStripMenuItem";
			this->helpToolStripMenuItem->Size = System::Drawing::Size(55, 24);
			this->helpToolStripMenuItem->Text = L"Help";
			// 
			// howToPlayToolStripMenuItem
			// 
			this->howToPlayToolStripMenuItem->Name = L"howToPlayToolStripMenuItem";
			this->howToPlayToolStripMenuItem->Size = System::Drawing::Size(172, 26);
			this->howToPlayToolStripMenuItem->Text = L"How to Play";
			this->howToPlayToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::howToPlayToolStripMenuItem_Click);
			// 
			// quitMasterMindToolStripMenuItem
			// 
			this->quitMasterMindToolStripMenuItem->Name = L"quitMasterMindToolStripMenuItem";
			this->quitMasterMindToolStripMenuItem->Size = System::Drawing::Size(94, 24);
			this->quitMasterMindToolStripMenuItem->Text = L"Quit Game";
			this->quitMasterMindToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::quitMasterMindToolStripMenuItem_Click);
			// 
			// textBox_developers
			// 
			this->textBox_developers->BackColor = System::Drawing::SystemColors::Control;
			this->textBox_developers->BorderStyle = System::Windows::Forms::BorderStyle::None;
			this->textBox_developers->Location = System::Drawing::Point(323, 270);
			this->textBox_developers->Margin = System::Windows::Forms::Padding(4, 4, 4, 4);
			this->textBox_developers->Multiline = true;
			this->textBox_developers->Name = L"textBox_developers";
			this->textBox_developers->ReadOnly = true;
			this->textBox_developers->Size = System::Drawing::Size(128, 63);
			this->textBox_developers->TabIndex = 4;
			this->textBox_developers->Text = L"Developers:\r\nGabriel González\r\nAdrián Dittel";
			this->textBox_developers->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_developers->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox2_TextChanged_1);
			// 
			// VentanaPrincipal
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(8, 16);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->ClientSize = System::Drawing::Size(467, 347);
			this->Controls->Add(this->textBox_developers);
			this->Controls->Add(this->textBox_enter_username);
			this->Controls->Add(this->button_play);
			this->Controls->Add(this->textBox_titulo);
			this->Controls->Add(this->menuStrip1);
			this->MainMenuStrip = this->menuStrip1;
			this->Margin = System::Windows::Forms::Padding(4, 4, 4, 4);
			this->Name = L"VentanaPrincipal";
			this->Text = L"Master Mind";
			this->menuStrip1->ResumeLayout(false);
			this->menuStrip1->PerformLayout();
			this->ResumeLayout(false);
			this->PerformLayout();

		}
#pragma endregion
	private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//VentanaPlay
		GameSettings configuration;
		configuration.ShowDialog();
	}

	private: System::Void textBox2_TextChanged(System::Object^ sender, System::EventArgs^ e)
	{
		userNameBtt = textBox_enter_username->Text;
		MasterMindProyectoFinal::VentanaPlay::userNameBtt = userNameBtt;
	}
	/*
	private: System::Void changeGameSettingsToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Game settings
	}
	*/
	private: System::Void textBox1_TextChanged(System::Object^ sender, System::EventArgs^ e) 
	{
		//Titulo (Master Mind)
	}
	private: System::Void textBox2_TextChanged_1(System::Object^ sender, System::EventArgs^ e) 
	{
		//Texto Developers
	}
	private: System::Void quitMasterMindToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Quit Game
		VentanaPrincipal::Close();
	}
	private: System::Void highscoresToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Highscores
		Highscores records;
		records.ShowDialog();
	}
	private: System::Void changeStyleToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Style
		Style diseño_juego;
		diseño_juego.ShowDialog();
	}
	private: System::Void howToPlayToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//How to Play
		HowToPlay instrucciones;
		instrucciones.ShowDialog();
	}


	};
}
