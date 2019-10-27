# Master-Mind
#VentanaPrincipal.h

#pragma once

#include <Windows.h>
#include "VentanaPlay.h"

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
	public:
		VentanaPrincipal(void)
		{
			InitializeComponent();

			//
			//TODO: codigo del constructor
			//

		}

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
	private: System::Windows::Forms::TextBox^ textBox1;
	private: System::Windows::Forms::Button^ button_play;
	private: System::Windows::Forms::TextBox^ textBox_enter_username;
	private: System::Windows::Forms::MenuStrip^ menuStrip1;
	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ highscoresToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ settingsToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ changeGameSettingsToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ helpToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ howToPlayToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ quitMasterMindToolStripMenuItem;
	private: System::Windows::Forms::TextBox^ textBox2;



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
			this->textBox1 = (gcnew System::Windows::Forms::TextBox());
			this->button_play = (gcnew System::Windows::Forms::Button());
			this->textBox_enter_username = (gcnew System::Windows::Forms::TextBox());
			this->menuStrip1 = (gcnew System::Windows::Forms::MenuStrip());
			this->ayudaToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->highscoresToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->quitMasterMindToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->settingsToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->changeGameSettingsToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->helpToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->howToPlayToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->textBox2 = (gcnew System::Windows::Forms::TextBox());
			this->menuStrip1->SuspendLayout();
			this->SuspendLayout();
			// 
			// textBox1
			// 
			this->textBox1->BorderStyle = System::Windows::Forms::BorderStyle::None;
			this->textBox1->Location = System::Drawing::Point(117, 47);
			this->textBox1->Name = L"textBox1";
			this->textBox1->ReadOnly = true;
			this->textBox1->Size = System::Drawing::Size(111, 13);
			this->textBox1->TabIndex = 0;
			this->textBox1->Text = L"MASTER MIND";
			this->textBox1->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			// 
			// button_play
			// 
			this->button_play->Location = System::Drawing::Point(126, 170);
			this->button_play->Name = L"button_play";
			this->button_play->Size = System::Drawing::Size(92, 23);
			this->button_play->TabIndex = 1;
			this->button_play->Text = L"Play";
			this->button_play->UseVisualStyleBackColor = true;
			this->button_play->Click += gcnew System::EventHandler(this, &VentanaPrincipal::button1_Click);
			// 
			// textBox_enter_username
			// 
			this->textBox_enter_username->Location = System::Drawing::Point(126, 101);
			this->textBox_enter_username->Name = L"textBox_enter_username";
			this->textBox_enter_username->Size = System::Drawing::Size(92, 20);
			this->textBox_enter_username->TabIndex = 2;
			this->textBox_enter_username->Text = L"Enter Username";
			this->textBox_enter_username->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			this->textBox_enter_username->TextChanged += gcnew System::EventHandler(this, &VentanaPrincipal::textBox2_TextChanged);
			// 
			// menuStrip1
			// 
			this->menuStrip1->Items->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(5) {
				this->ayudaToolStripMenuItem,
					this->highscoresToolStripMenuItem, this->settingsToolStripMenuItem, this->helpToolStripMenuItem, this->quitMasterMindToolStripMenuItem
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
			this->highscoresToolStripMenuItem->Name = L"highscoresToolStripMenuItem";
			this->highscoresToolStripMenuItem->Size = System::Drawing::Size(78, 20);
			this->highscoresToolStripMenuItem->Text = L"Highscores";
			// 
			// quitMasterMindToolStripMenuItem
			// 
			this->quitMasterMindToolStripMenuItem->Name = L"quitMasterMindToolStripMenuItem";
			this->quitMasterMindToolStripMenuItem->Size = System::Drawing::Size(76, 20);
			this->quitMasterMindToolStripMenuItem->Text = L"Quit Game";
			// 
			// settingsToolStripMenuItem
			// 
			this->settingsToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->changeGameSettingsToolStripMenuItem });
			this->settingsToolStripMenuItem->Name = L"settingsToolStripMenuItem";
			this->settingsToolStripMenuItem->Size = System::Drawing::Size(61, 20);
			this->settingsToolStripMenuItem->Text = L"Settings";
			// 
			// changeGameSettingsToolStripMenuItem
			// 
			this->changeGameSettingsToolStripMenuItem->Name = L"changeGameSettingsToolStripMenuItem";
			this->changeGameSettingsToolStripMenuItem->Size = System::Drawing::Size(194, 22);
			this->changeGameSettingsToolStripMenuItem->Text = L"Change Game Settings";
			// 
			// helpToolStripMenuItem
			// 
			this->helpToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->howToPlayToolStripMenuItem });
			this->helpToolStripMenuItem->Name = L"helpToolStripMenuItem";
			this->helpToolStripMenuItem->Size = System::Drawing::Size(44, 20);
			this->helpToolStripMenuItem->Text = L"Help";
			// 
			// howToPlayToolStripMenuItem
			// 
			this->howToPlayToolStripMenuItem->Name = L"howToPlayToolStripMenuItem";
			this->howToPlayToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->howToPlayToolStripMenuItem->Text = L"How to Play";
			// 
			// textBox2
			// 
			this->textBox2->BackColor = System::Drawing::SystemColors::Control;
			this->textBox2->BorderStyle = System::Windows::Forms::BorderStyle::None;
			this->textBox2->Location = System::Drawing::Point(242, 219);
			this->textBox2->Multiline = true;
			this->textBox2->Name = L"textBox2";
			this->textBox2->ReadOnly = true;
			this->textBox2->Size = System::Drawing::Size(96, 51);
			this->textBox2->TabIndex = 4;
			this->textBox2->Text = L"Developers:\r\nGabriel González\r\nAdrián Dittel";
			this->textBox2->TextAlign = System::Windows::Forms::HorizontalAlignment::Center;
			// 
			// VentanaPrincipal
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->ClientSize = System::Drawing::Size(350, 282);
			this->Controls->Add(this->textBox2);
			this->Controls->Add(this->textBox_enter_username);
			this->Controls->Add(this->button_play);
			this->Controls->Add(this->textBox1);
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
	private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e)
	{
		VentanaPlay juego;
		//Application::Run(% juego);
		juego.ShowDialog();
	}
	private: System::Void button2_Click(System::Object^ sender, System::EventArgs^ e) 
	{

	}
	private: System::Void button3_Click(System::Object^ sender, System::EventArgs^ e) 
	{

	}


	private: System::Void textBox2_TextChanged(System::Object^ sender, System::EventArgs^ e) 
	{
		//codigo para guardar en una variable el nombre de usuario ingresado
	}
};
}
