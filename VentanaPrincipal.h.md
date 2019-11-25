# Master-Mind

//VentanaPrincipal.h

#pragma once

#include <Windows.h>

#include "GameSettings.h"
#include "Highscores.h"
#include "HowToPlay.h"
#include "Style.h"
#include <msclr\marshal_cppstd.h>
#include <string>
#include <shellapi.h>

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
	private: System::Windows::Forms::ToolStripMenuItem^ enter_highscoresToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ userManualToolStripMenuItem;





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
			this->enter_highscoresToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->helpToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->howToPlayToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->quitMasterMindToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->textBox_developers = (gcnew System::Windows::Forms::TextBox());
			this->userManualToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->menuStrip1->SuspendLayout();
			this->SuspendLayout();
			// 
			// textBox_titulo
			// 
			this->textBox_titulo->BackColor = System::Drawing::Color::Gainsboro;
			this->textBox_titulo->BorderStyle = System::Windows::Forms::BorderStyle::None;
			this->textBox_titulo->Cursor = System::Windows::Forms::Cursors::Default;
			this->textBox_titulo->Font = (gcnew System::Drawing::Font(L"Modern No. 20", 14.25F, static_cast<System::Drawing::FontStyle>((System::Drawing::FontStyle::Bold | System::Drawing::FontStyle::Italic)),
				System::Drawing::GraphicsUnit::Point, static_cast<System::Byte>(0)));
			this->textBox_titulo->ForeColor = System::Drawing::Color::OrangeRed;
			this->textBox_titulo->Location = System::Drawing::Point(93, 73);
			this->textBox_titulo->Name = L"textBox_titulo";
			this->textBox_titulo->ReadOnly = true;
			this->textBox_titulo->Size = System::Drawing::Size(172, 21);
			this->textBox_titulo->TabIndex = 0;
			this->textBox_titulo->Text = L"MASTERMIND";
			this->textBox_titulo->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_titulo->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox1_TextChanged);
			// 
			// button_play
			// 
			this->button_play->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button_play->Enabled = false;
			this->button_play->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->button_play->Location = System::Drawing::Point(126, 184);
			this->button_play->Name = L"button_play";
			this->button_play->Size = System::Drawing::Size(92, 27);
			this->button_play->TabIndex = 1;
			this->button_play->Text = L"Play";
			this->button_play->UseVisualStyleBackColor = true;
			this->button_play->Click += gcnew System::EventHandler(this, &VentanaPrincipal::button_play_Click);
			// 
			// textBox_enter_username
			// 
			this->textBox_enter_username->Location = System::Drawing::Point(74, 127);
			this->textBox_enter_username->Name = L"textBox_enter_username";
			this->textBox_enter_username->Size = System::Drawing::Size(191, 20);
			this->textBox_enter_username->TabIndex = 2;
			this->textBox_enter_username->Text = L"Enter Username: 2-30 characters";
			this->textBox_enter_username->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_enter_username->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox2_TextChanged);
			// 
			// menuStrip1
			// 
			this->menuStrip1->Items->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(4) {
				this->ayudaToolStripMenuItem,
					this->highscoresToolStripMenuItem, this->helpToolStripMenuItem, this->quitMasterMindToolStripMenuItem
			});
			this->menuStrip1->Location = System::Drawing::Point(0, 0);
			this->menuStrip1->Name = L"menuStrip1";
			this->menuStrip1->Size = System::Drawing::Size(350, 24);
			this->menuStrip1->TabIndex = 3;
			this->menuStrip1->Text = L"menuStrip1";
			// 
			// ayudaToolStripMenuItem
			// 
			this->ayudaToolStripMenuItem->Name = L"ayudaToolStripMenuItem";
			this->ayudaToolStripMenuItem->Size = System::Drawing::Size(37, 20);
			this->ayudaToolStripMenuItem->Text = L"File";
			// 
			// highscoresToolStripMenuItem
			// 
			this->highscoresToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->enter_highscoresToolStripMenuItem });
			this->highscoresToolStripMenuItem->Name = L"highscoresToolStripMenuItem";
			this->highscoresToolStripMenuItem->Size = System::Drawing::Size(78, 20);
			this->highscoresToolStripMenuItem->Text = L"Highscores";
			this->highscoresToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::highscoresToolStripMenuItem_Click);
			// 
			// enter_highscoresToolStripMenuItem
			// 
			this->enter_highscoresToolStripMenuItem->Name = L"enter_highscoresToolStripMenuItem";
			this->enter_highscoresToolStripMenuItem->Size = System::Drawing::Size(133, 22);
			this->enter_highscoresToolStripMenuItem->Text = L"Highscores";
			this->enter_highscoresToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::enter_highscoresToolStripMenuItem_Click);
			// 
			// helpToolStripMenuItem
			// 
			this->helpToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(2) {
				this->howToPlayToolStripMenuItem,
					this->userManualToolStripMenuItem
			});
			this->helpToolStripMenuItem->Name = L"helpToolStripMenuItem";
			this->helpToolStripMenuItem->Size = System::Drawing::Size(44, 20);
			this->helpToolStripMenuItem->Text = L"Help";
			// 
			// howToPlayToolStripMenuItem
			// 
			this->howToPlayToolStripMenuItem->Name = L"howToPlayToolStripMenuItem";
			this->howToPlayToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->howToPlayToolStripMenuItem->Text = L"How to Play";
			this->howToPlayToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::howToPlayToolStripMenuItem_Click);
			// 
			// quitMasterMindToolStripMenuItem
			// 
			this->quitMasterMindToolStripMenuItem->Name = L"quitMasterMindToolStripMenuItem";
			this->quitMasterMindToolStripMenuItem->Size = System::Drawing::Size(76, 20);
			this->quitMasterMindToolStripMenuItem->Text = L"Quit Game";
			this->quitMasterMindToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::quitMasterMindToolStripMenuItem_Click);
			// 
			// textBox_developers
			// 
			this->textBox_developers->BackColor = System::Drawing::Color::Gainsboro;
			this->textBox_developers->BorderStyle = System::Windows::Forms::BorderStyle::None;
			this->textBox_developers->Font = (gcnew System::Drawing::Font(L"Maiandra GD", 8.25F, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->textBox_developers->Location = System::Drawing::Point(221, 219);
			this->textBox_developers->Multiline = true;
			this->textBox_developers->Name = L"textBox_developers";
			this->textBox_developers->ReadOnly = true;
			this->textBox_developers->Size = System::Drawing::Size(117, 51);
			this->textBox_developers->TabIndex = 4;
			this->textBox_developers->Text = L"Developers:\r\nGabriel González\r\nAdrián Dittel";
			this->textBox_developers->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_developers->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox2_TextChanged_1);
			// 
			// userManualToolStripMenuItem
			// 
			this->userManualToolStripMenuItem->Name = L"userManualToolStripMenuItem";
			this->userManualToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->userManualToolStripMenuItem->Text = L"User Manual";
			this->userManualToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPrincipal::userManualToolStripMenuItem_Click);
			// 
			// VentanaPrincipal
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Gainsboro;
			this->ClientSize = System::Drawing::Size(350, 282);
			this->Controls->Add(this->textBox_developers);
			this->Controls->Add(this->textBox_enter_username);
			this->Controls->Add(this->button_play);
			this->Controls->Add(this->textBox_titulo);
			this->Controls->Add(this->menuStrip1);
			this->MainMenuStrip = this->menuStrip1;
			this->Name = L"VentanaPrincipal";
			this->Text = L"Master Mind";
			this->menuStrip1->ResumeLayout(false);
			this->menuStrip1->PerformLayout();
			this->ResumeLayout(false);
			this->PerformLayout();

		}
#pragma endregion
	private: System::Void button_play_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//passes username to VentanaPLay
		userNameBtt = textBox_enter_username->Text;
		MasterMindProyectoFinal::VentanaPlay::userNameBtt = userNameBtt;


		//VentanaPlay
		GameSettings configuration;
		configuration.ShowDialog();
	}

	private: System::Void textBox2_TextChanged(System::Object^ sender, System::EventArgs^ e) 
	{
		//codigo para guardar en una variable el nombre de usuario ingresado

		if ((textBox_enter_username->Text->Length > 2) == (textBox_enter_username->Text->Length < 30))
		{
			using namespace std;
			string textbox_str = msclr::interop::marshal_as<std::string>(textBox_enter_username->Text);
			int size_str_tB = textbox_str.length();
			if (textbox_str.find(" ") > size_str_tB)
				button_play->Enabled = true;

			if (textbox_str.find(" ") <= size_str_tB)
				button_play->Enabled = false;
		}
		if (textBox_enter_username->Text->Length > 30)
			button_play->Enabled = false;
		if (textBox_enter_username->Text->Length < 2)
			button_play->Enabled = false;
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


	private: System::Void enter_highscoresToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Highscores
		Highscores records;
		records.ShowDialog();
	}
	private: System::Void userManualToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e)
	{

		system(".\\PDFs_Docs\\InstruccionesProyectoMASTERMIND.pdf");
		
	}


};
}
