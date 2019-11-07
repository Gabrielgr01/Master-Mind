# Master-Mind

//GameSettings

#pragma once

#include "ConfigurationClass.h"
#include "VentanaPlay.h"

namespace MasterMindProyectoFinal {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;
	
	/// <summary>
	/// Resumen de GameSettings
	/// </summary>
	public ref class GameSettings : public System::Windows::Forms::Form
	{
	public:
		ConfigurationClass* objSettings = new ConfigurationClass();

		int difficulty;
		bool clock;
		bool timekeeper_play;
		bool timekeeper_game;
		bool element_rep;

	public:

		GameSettings(void)
		{
			InitializeComponent();
			//
			//TODO: agregar código de constructor aquí
			//
		}
		
	protected:
		/// <summary>
		/// Limpiar los recursos que se estén usando.
		/// </summary>
		~GameSettings()
		{
			if (components)
			{
				delete components;
			}
		}

	private: System::Windows::Forms::GroupBox^ groupBox1;
	private: System::Windows::Forms::RadioButton^ Difficulty_Hard;
	protected:

	private: System::Windows::Forms::RadioButton^ Difficulty_Medium;

	private: System::Windows::Forms::RadioButton^ Difficulty_Easy;

	private: System::Windows::Forms::GroupBox^ groupBox2;
	private: System::Windows::Forms::RadioButton^ Timekeeper_Game;

	private: System::Windows::Forms::RadioButton^ Timekeeper_Play;

	private: System::Windows::Forms::RadioButton^ Clock_Disabled;

	private: System::Windows::Forms::RadioButton^ Clock_Enabled;

	private: System::Windows::Forms::GroupBox^ groupBox3;
	private: System::Windows::Forms::RadioButton^ Element_rep_Disabled;

	private: System::Windows::Forms::RadioButton^ Element_rep_Enabled;

	private: System::Windows::Forms::GroupBox^ groupBox4;
	private: System::Windows::Forms::RadioButton^ radioButton13;
	private: System::Windows::Forms::RadioButton^ radioButton12;
	private: System::Windows::Forms::RadioButton^ radioButton11;
	private: System::Windows::Forms::RadioButton^ radioButton10;
	private: System::Windows::Forms::Button^ Save_Settings;
	private: System::Windows::Forms::Button^ button_back;



	protected:

	private:
		/// <summary>
		/// Variable del diseñador necesaria.
		/// </summary>
		System::ComponentModel::Container^ components;



#pragma region Windows Form Designer generated code
		/// <summary>
		/// Método necesario para admitir el Diseñador. No se puede modificar
		/// el contenido de este método con el editor de código.
		/// </summary>
		void InitializeComponent(void)
		{
			this->groupBox1 = (gcnew System::Windows::Forms::GroupBox());
			this->Difficulty_Hard = (gcnew System::Windows::Forms::RadioButton());
			this->Difficulty_Medium = (gcnew System::Windows::Forms::RadioButton());
			this->Difficulty_Easy = (gcnew System::Windows::Forms::RadioButton());
			this->groupBox2 = (gcnew System::Windows::Forms::GroupBox());
			this->Timekeeper_Game = (gcnew System::Windows::Forms::RadioButton());
			this->Timekeeper_Play = (gcnew System::Windows::Forms::RadioButton());
			this->Clock_Disabled = (gcnew System::Windows::Forms::RadioButton());
			this->Clock_Enabled = (gcnew System::Windows::Forms::RadioButton());
			this->groupBox3 = (gcnew System::Windows::Forms::GroupBox());
			this->Element_rep_Disabled = (gcnew System::Windows::Forms::RadioButton());
			this->Element_rep_Enabled = (gcnew System::Windows::Forms::RadioButton());
			this->groupBox4 = (gcnew System::Windows::Forms::GroupBox());
			this->radioButton13 = (gcnew System::Windows::Forms::RadioButton());
			this->radioButton12 = (gcnew System::Windows::Forms::RadioButton());
			this->radioButton11 = (gcnew System::Windows::Forms::RadioButton());
			this->radioButton10 = (gcnew System::Windows::Forms::RadioButton());
			this->Save_Settings = (gcnew System::Windows::Forms::Button());
			this->button_back = (gcnew System::Windows::Forms::Button());
			this->groupBox1->SuspendLayout();
			this->groupBox2->SuspendLayout();
			this->groupBox3->SuspendLayout();
			this->groupBox4->SuspendLayout();
			this->SuspendLayout();
			// 
			// groupBox1
			// 
			this->groupBox1->Controls->Add(this->Difficulty_Hard);
			this->groupBox1->Controls->Add(this->Difficulty_Medium);
			this->groupBox1->Controls->Add(this->Difficulty_Easy);
			this->groupBox1->Location = System::Drawing::Point(12, 12);
			this->groupBox1->Name = L"groupBox1";
			this->groupBox1->Size = System::Drawing::Size(277, 88);
			this->groupBox1->TabIndex = 3;
			this->groupBox1->TabStop = false;
			this->groupBox1->Text = L"Difficulty";
			// 
			// Difficulty_Hard
			// 
			this->Difficulty_Hard->AutoSize = true;
			this->Difficulty_Hard->Location = System::Drawing::Point(6, 65);
			this->Difficulty_Hard->Name = L"Difficulty_Hard";
			this->Difficulty_Hard->Size = System::Drawing::Size(240, 17);
			this->Difficulty_Hard->TabIndex = 2;
			this->Difficulty_Hard->Text = L"Hard (6 plays, combination of 4 to 6 elements)";
			this->Difficulty_Hard->UseVisualStyleBackColor = true;
			this->Difficulty_Hard->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Difficulty_Hard_CheckedChanged);
			// 
			// Difficulty_Medium
			// 
			this->Difficulty_Medium->AutoSize = true;
			this->Difficulty_Medium->Location = System::Drawing::Point(6, 42);
			this->Difficulty_Medium->Name = L"Difficulty_Medium";
			this->Difficulty_Medium->Size = System::Drawing::Size(254, 17);
			this->Difficulty_Medium->TabIndex = 1;
			this->Difficulty_Medium->Text = L"Medium (7 plays, combination of 4 to 6 elements)";
			this->Difficulty_Medium->UseVisualStyleBackColor = true;
			this->Difficulty_Medium->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Difficulty_Medium_CheckedChanged);
			// 
			// Difficulty_Easy
			// 
			this->Difficulty_Easy->AutoSize = true;
			this->Difficulty_Easy->Checked = true;
			this->Difficulty_Easy->Location = System::Drawing::Point(6, 19);
			this->Difficulty_Easy->Name = L"Difficulty_Easy";
			this->Difficulty_Easy->Size = System::Drawing::Size(240, 17);
			this->Difficulty_Easy->TabIndex = 0;
			this->Difficulty_Easy->TabStop = true;
			this->Difficulty_Easy->Text = L"Easy (8 plays, combination of 4 to 6 elements)";
			this->Difficulty_Easy->UseVisualStyleBackColor = true;
			this->Difficulty_Easy->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Difficulty_Easy_CheckedChanged);
			// 
			// groupBox2
			// 
			this->groupBox2->Controls->Add(this->Timekeeper_Game);
			this->groupBox2->Controls->Add(this->Timekeeper_Play);
			this->groupBox2->Controls->Add(this->Clock_Disabled);
			this->groupBox2->Controls->Add(this->Clock_Enabled);
			this->groupBox2->Location = System::Drawing::Point(12, 106);
			this->groupBox2->Name = L"groupBox2";
			this->groupBox2->Size = System::Drawing::Size(277, 118);
			this->groupBox2->TabIndex = 4;
			this->groupBox2->TabStop = false;
			this->groupBox2->Text = L"Clock";
			// 
			// Timekeeper_Game
			// 
			this->Timekeeper_Game->AutoSize = true;
			this->Timekeeper_Game->Location = System::Drawing::Point(6, 88);
			this->Timekeeper_Game->Name = L"Timekeeper_Game";
			this->Timekeeper_Game->Size = System::Drawing::Size(125, 17);
			this->Timekeeper_Game->TabIndex = 3;
			this->Timekeeper_Game->Text = L"Timekeeper for game";
			this->Timekeeper_Game->UseVisualStyleBackColor = true;
			this->Timekeeper_Game->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Timekeeper_Game_CheckedChanged);
			// 
			// Timekeeper_Play
			// 
			this->Timekeeper_Play->AutoSize = true;
			this->Timekeeper_Play->Location = System::Drawing::Point(6, 65);
			this->Timekeeper_Play->Name = L"Timekeeper_Play";
			this->Timekeeper_Play->Size = System::Drawing::Size(118, 17);
			this->Timekeeper_Play->TabIndex = 2;
			this->Timekeeper_Play->Text = L"Timekeeper for play";
			this->Timekeeper_Play->UseVisualStyleBackColor = true;
			this->Timekeeper_Play->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Timekeeper_Play_CheckedChanged);
			// 
			// Clock_Disabled
			// 
			this->Clock_Disabled->AutoSize = true;
			this->Clock_Disabled->Location = System::Drawing::Point(6, 42);
			this->Clock_Disabled->Name = L"Clock_Disabled";
			this->Clock_Disabled->Size = System::Drawing::Size(66, 17);
			this->Clock_Disabled->TabIndex = 1;
			this->Clock_Disabled->Text = L"Disabled";
			this->Clock_Disabled->UseVisualStyleBackColor = true;
			this->Clock_Disabled->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Clock_Disabled_CheckedChanged);
			// 
			// Clock_Enabled
			// 
			this->Clock_Enabled->AutoSize = true;
			this->Clock_Enabled->Checked = true;
			this->Clock_Enabled->Location = System::Drawing::Point(6, 19);
			this->Clock_Enabled->Name = L"Clock_Enabled";
			this->Clock_Enabled->Size = System::Drawing::Size(64, 17);
			this->Clock_Enabled->TabIndex = 0;
			this->Clock_Enabled->TabStop = true;
			this->Clock_Enabled->Text = L"Enabled";
			this->Clock_Enabled->UseVisualStyleBackColor = true;
			this->Clock_Enabled->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Clock_Enabled_CheckedChanged);
			// 
			// groupBox3
			// 
			this->groupBox3->Controls->Add(this->Element_rep_Disabled);
			this->groupBox3->Controls->Add(this->Element_rep_Enabled);
			this->groupBox3->Location = System::Drawing::Point(12, 230);
			this->groupBox3->Name = L"groupBox3";
			this->groupBox3->Size = System::Drawing::Size(277, 88);
			this->groupBox3->TabIndex = 4;
			this->groupBox3->TabStop = false;
			this->groupBox3->Text = L"Element repetition in combination";
			// 
			// Element_rep_Disabled
			// 
			this->Element_rep_Disabled->AutoSize = true;
			this->Element_rep_Disabled->Location = System::Drawing::Point(6, 42);
			this->Element_rep_Disabled->Name = L"Element_rep_Disabled";
			this->Element_rep_Disabled->Size = System::Drawing::Size(66, 17);
			this->Element_rep_Disabled->TabIndex = 1;
			this->Element_rep_Disabled->Text = L"Disabled";
			this->Element_rep_Disabled->UseVisualStyleBackColor = true;
			this->Element_rep_Disabled->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Element_rep_Disabled_CheckedChanged);
			// 
			// Element_rep_Enabled
			// 
			this->Element_rep_Enabled->AutoSize = true;
			this->Element_rep_Enabled->Checked = true;
			this->Element_rep_Enabled->Location = System::Drawing::Point(6, 19);
			this->Element_rep_Enabled->Name = L"Element_rep_Enabled";
			this->Element_rep_Enabled->Size = System::Drawing::Size(64, 17);
			this->Element_rep_Enabled->TabIndex = 0;
			this->Element_rep_Enabled->TabStop = true;
			this->Element_rep_Enabled->Text = L"Enabled";
			this->Element_rep_Enabled->UseVisualStyleBackColor = true;
			this->Element_rep_Enabled->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Element_rep_Enabled_CheckedChanged);
			// 
			// groupBox4
			// 
			this->groupBox4->Controls->Add(this->radioButton13);
			this->groupBox4->Controls->Add(this->radioButton12);
			this->groupBox4->Controls->Add(this->radioButton11);
			this->groupBox4->Controls->Add(this->radioButton10);
			this->groupBox4->Location = System::Drawing::Point(295, 12);
			this->groupBox4->Name = L"groupBox4";
			this->groupBox4->Size = System::Drawing::Size(307, 306);
			this->groupBox4->TabIndex = 0;
			this->groupBox4->TabStop = false;
			this->groupBox4->Text = L"Element type to use in combination";
			this->groupBox4->Enter += gcnew System::EventHandler(this, &GameSettings::groupBox4_Enter);
			// 
			// radioButton13
			// 
			this->radioButton13->AutoSize = true;
			this->radioButton13->Location = System::Drawing::Point(202, 19);
			this->radioButton13->Name = L"radioButton13";
			this->radioButton13->Size = System::Drawing::Size(97, 17);
			this->radioButton13->TabIndex = 3;
			this->radioButton13->Text = L"(Undefined yet)";
			this->radioButton13->UseVisualStyleBackColor = true;
			// 
			// radioButton12
			// 
			this->radioButton12->AutoSize = true;
			this->radioButton12->Location = System::Drawing::Point(129, 19);
			this->radioButton12->Name = L"radioButton12";
			this->radioButton12->Size = System::Drawing::Size(67, 17);
			this->radioButton12->TabIndex = 2;
			this->radioButton12->Text = L"Numbers";
			this->radioButton12->UseVisualStyleBackColor = true;
			// 
			// radioButton11
			// 
			this->radioButton11->AutoSize = true;
			this->radioButton11->Location = System::Drawing::Point(66, 19);
			this->radioButton11->Name = L"radioButton11";
			this->radioButton11->Size = System::Drawing::Size(57, 17);
			this->radioButton11->TabIndex = 1;
			this->radioButton11->Text = L"Letters";
			this->radioButton11->UseVisualStyleBackColor = true;
			this->radioButton11->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::radioButton11_CheckedChanged);
			// 
			// radioButton10
			// 
			this->radioButton10->AutoSize = true;
			this->radioButton10->Checked = true;
			this->radioButton10->Location = System::Drawing::Point(6, 19);
			this->radioButton10->Name = L"radioButton10";
			this->radioButton10->Size = System::Drawing::Size(54, 17);
			this->radioButton10->TabIndex = 0;
			this->radioButton10->TabStop = true;
			this->radioButton10->Text = L"Colors";
			this->radioButton10->UseVisualStyleBackColor = true;
			this->radioButton10->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::radioButton10_CheckedChanged);
			// 
			// Save_Settings
			// 
			this->Save_Settings->Location = System::Drawing::Point(12, 330);
			this->Save_Settings->Name = L"Save_Settings";
			this->Save_Settings->Size = System::Drawing::Size(75, 23);
			this->Save_Settings->TabIndex = 5;
			this->Save_Settings->Text = L"Save";
			this->Save_Settings->UseVisualStyleBackColor = true;
			this->Save_Settings->Click += gcnew System::EventHandler(this, &GameSettings::Save_Settings_Click);
			// 
			// button_back
			// 
			this->button_back->Location = System::Drawing::Point(527, 330);
			this->button_back->Name = L"button_back";
			this->button_back->Size = System::Drawing::Size(75, 23);
			this->button_back->TabIndex = 6;
			this->button_back->Text = L"Back";
			this->button_back->UseVisualStyleBackColor = true;
			this->button_back->Click += gcnew System::EventHandler(this, &GameSettings::button_back_Click);
			// 
			// GameSettings
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->ClientSize = System::Drawing::Size(614, 365);
			this->Controls->Add(this->button_back);
			this->Controls->Add(this->Save_Settings);
			this->Controls->Add(this->groupBox4);
			this->Controls->Add(this->groupBox3);
			this->Controls->Add(this->groupBox2);
			this->Controls->Add(this->groupBox1);
			this->Name = L"GameSettings";
			this->Text = L"GameSettings";
			this->groupBox1->ResumeLayout(false);
			this->groupBox1->PerformLayout();
			this->groupBox2->ResumeLayout(false);
			this->groupBox2->PerformLayout();
			this->groupBox3->ResumeLayout(false);
			this->groupBox3->PerformLayout();
			this->groupBox4->ResumeLayout(false);
			this->groupBox4->PerformLayout();
			this->ResumeLayout(false);

		}
#pragma endregion
	private: System::Void radioButton10_CheckedChanged(System::Object^ sender, System::EventArgs^ e) 
	{

	}
	private: System::Void radioButton11_CheckedChanged(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void button_back_Click(System::Object^ sender, System::EventArgs^ e)
	{
		GameSettings::Close();
	}


	private: System::Void Difficulty_Easy_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		difficulty = 1;
		objSettings->setDifficulty(difficulty);
	}
	private: System::Void Difficulty_Medium_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		difficulty = 2;
		objSettings->setDifficulty(difficulty);
	}

	private: System::Void Difficulty_Hard_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		difficulty = 3;
		objSettings->setDifficulty(difficulty);
	}

	private: System::Void Clock_Enabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		clock = true;
		objSettings->setClock(clock);
	}
	private: System::Void Clock_Disabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		clock = false;
		objSettings->setClock(clock);
	}
	private: System::Void Timekeeper_Play_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		clock = false;
		objSettings->setClock(clock);
		timekeeper_game = false;
		objSettings->setTimekeeperGame(timekeeper_game);

		timekeeper_play = true;
		objSettings->setTimekeeperPlay(timekeeper_play);
	}
	private: System::Void Timekeeper_Game_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		clock = false;
		objSettings->setClock(clock);
		timekeeper_play = false;
		objSettings->setTimekeeperPlay(timekeeper_play);

		timekeeper_game = true;
		objSettings->setTimekeeperGame(timekeeper_game);
	}
	private: System::Void Element_rep_Enabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		element_rep = true;
		objSettings->setElementRep(element_rep);
	}
	private: System::Void Element_rep_Disabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e) 
	{
		element_rep = false;
		objSettings->setElementRep(element_rep);
	}
	private: System::Void Save_Settings_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//GameSettings::Close();

		VentanaPlay juego(objSettings);
		juego.ShowDialog();
	}



	private: System::Void groupBox4_Enter(System::Object^ sender, System::EventArgs^ e) 
	{
	}
};
}
