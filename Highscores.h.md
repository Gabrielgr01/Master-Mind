# Master-Mind

//Highscores.h

#pragma once

#include <stdio.h>
#include <stdlib.h>
#include <fstream>
#include <string>
#include <msclr\marshal_cppstd.h>

namespace MasterMindProyectoFinal {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;

	/// <summary>
	/// Resumen de Highscores
	/// </summary>
	public ref class Highscores : public System::Windows::Forms::Form
	{

	public:
		Highscores(void)
		{
			InitializeComponent();


			compare_players_time(); //updates the top3 list


			//
			//TODO: agregar código de constructor aquí
			//
		}

	protected:
		/// <summary>
		/// Limpiar los recursos que se estén usando.
		/// </summary>
		~Highscores()
		{
			if (components)
			{
				delete components;
			}
		}
	private: System::Windows::Forms::Button^ button1;
	private: System::Windows::Forms::Label^ top3_hard_label;
	private: System::Windows::Forms::Label^ player1_hard_label;
	private: System::Windows::Forms::Label^ player2_hard_label;
	private: System::Windows::Forms::Label^ player3_hard_label;
	private: System::Windows::Forms::Label^ top3_medium_label;
	private: System::Windows::Forms::Label^ top3_easy_label;
	private: System::Windows::Forms::Label^ player1_medium_label;
	private: System::Windows::Forms::Label^ player2_easy_label;


	private: System::Windows::Forms::Label^ player3_medium_label;
	private: System::Windows::Forms::Label^ player1_easy_label;
	private: System::Windows::Forms::Label^ player2_medium_label;

	private: System::Windows::Forms::Label^ player3_easy_label;
private: System::Windows::Forms::Label^ num_p1_h_label;
private: System::Windows::Forms::Label^ num_p2_h_label;
private: System::Windows::Forms::Label^ num_p3_h_label;
private: System::Windows::Forms::Label^ num_p1_m_label;
private: System::Windows::Forms::Label^ num_p2_m_label;
private: System::Windows::Forms::Label^ num_p3_m_label;
private: System::Windows::Forms::Label^ num_p1_e_label;
private: System::Windows::Forms::Label^ num_p2_e_label;
private: System::Windows::Forms::Label^ num_p3_e_label;





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
			this->button1 = (gcnew System::Windows::Forms::Button());
			this->top3_hard_label = (gcnew System::Windows::Forms::Label());
			this->player1_hard_label = (gcnew System::Windows::Forms::Label());
			this->player2_hard_label = (gcnew System::Windows::Forms::Label());
			this->player3_hard_label = (gcnew System::Windows::Forms::Label());
			this->top3_medium_label = (gcnew System::Windows::Forms::Label());
			this->top3_easy_label = (gcnew System::Windows::Forms::Label());
			this->player1_medium_label = (gcnew System::Windows::Forms::Label());
			this->player2_easy_label = (gcnew System::Windows::Forms::Label());
			this->player3_medium_label = (gcnew System::Windows::Forms::Label());
			this->player1_easy_label = (gcnew System::Windows::Forms::Label());
			this->player2_medium_label = (gcnew System::Windows::Forms::Label());
			this->player3_easy_label = (gcnew System::Windows::Forms::Label());
			this->num_p1_h_label = (gcnew System::Windows::Forms::Label());
			this->num_p2_h_label = (gcnew System::Windows::Forms::Label());
			this->num_p3_h_label = (gcnew System::Windows::Forms::Label());
			this->num_p1_m_label = (gcnew System::Windows::Forms::Label());
			this->num_p2_m_label = (gcnew System::Windows::Forms::Label());
			this->num_p3_m_label = (gcnew System::Windows::Forms::Label());
			this->num_p1_e_label = (gcnew System::Windows::Forms::Label());
			this->num_p2_e_label = (gcnew System::Windows::Forms::Label());
			this->num_p3_e_label = (gcnew System::Windows::Forms::Label());
			this->SuspendLayout();
			// 
			// button1
			// 
			this->button1->Location = System::Drawing::Point(12, 312);
			this->button1->Name = L"button1";
			this->button1->Size = System::Drawing::Size(75, 23);
			this->button1->TabIndex = 0;
			this->button1->Text = L"Back";
			this->button1->UseVisualStyleBackColor = true;
			this->button1->Click += gcnew System::EventHandler(this, &Highscores::button1_Click);
			// 
			// top3_hard_label
			// 
			this->top3_hard_label->AutoSize = true;
			this->top3_hard_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->top3_hard_label->Location = System::Drawing::Point(77, 9);
			this->top3_hard_label->Name = L"top3_hard_label";
			this->top3_hard_label->Size = System::Drawing::Size(153, 16);
			this->top3_hard_label->TabIndex = 1;
			this->top3_hard_label->Text = L"Top 3 Players (Hard)";
			// 
			// player1_hard_label
			// 
			this->player1_hard_label->AutoSize = true;
			this->player1_hard_label->Location = System::Drawing::Point(96, 31);
			this->player1_hard_label->Name = L"player1_hard_label";
			this->player1_hard_label->Size = System::Drawing::Size(48, 13);
			this->player1_hard_label->TabIndex = 2;
			this->player1_hard_label->Text = L"(Player1)";
			// 
			// player2_hard_label
			// 
			this->player2_hard_label->AutoSize = true;
			this->player2_hard_label->Location = System::Drawing::Point(96, 54);
			this->player2_hard_label->Name = L"player2_hard_label";
			this->player2_hard_label->Size = System::Drawing::Size(48, 13);
			this->player2_hard_label->TabIndex = 3;
			this->player2_hard_label->Text = L"(Player2)";
			// 
			// player3_hard_label
			// 
			this->player3_hard_label->AutoSize = true;
			this->player3_hard_label->Location = System::Drawing::Point(96, 79);
			this->player3_hard_label->Name = L"player3_hard_label";
			this->player3_hard_label->Size = System::Drawing::Size(48, 13);
			this->player3_hard_label->TabIndex = 4;
			this->player3_hard_label->Text = L"(Player3)";
			// 
			// top3_medium_label
			// 
			this->top3_medium_label->AutoSize = true;
			this->top3_medium_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->top3_medium_label->Location = System::Drawing::Point(67, 104);
			this->top3_medium_label->Name = L"top3_medium_label";
			this->top3_medium_label->Size = System::Drawing::Size(173, 16);
			this->top3_medium_label->TabIndex = 5;
			this->top3_medium_label->Text = L"Top 3 Players (Medium)";
			// 
			// top3_easy_label
			// 
			this->top3_easy_label->AutoSize = true;
			this->top3_easy_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->top3_easy_label->Location = System::Drawing::Point(77, 204);
			this->top3_easy_label->Name = L"top3_easy_label";
			this->top3_easy_label->Size = System::Drawing::Size(154, 16);
			this->top3_easy_label->TabIndex = 6;
			this->top3_easy_label->Text = L"Top 3 Players (Easy)";
			// 
			// player1_medium_label
			// 
			this->player1_medium_label->AutoSize = true;
			this->player1_medium_label->Location = System::Drawing::Point(96, 130);
			this->player1_medium_label->Name = L"player1_medium_label";
			this->player1_medium_label->Size = System::Drawing::Size(48, 13);
			this->player1_medium_label->TabIndex = 7;
			this->player1_medium_label->Text = L"(Player1)";
			// 
			// player2_easy_label
			// 
			this->player2_easy_label->AutoSize = true;
			this->player2_easy_label->Location = System::Drawing::Point(96, 255);
			this->player2_easy_label->Name = L"player2_easy_label";
			this->player2_easy_label->Size = System::Drawing::Size(48, 13);
			this->player2_easy_label->TabIndex = 8;
			this->player2_easy_label->Text = L"(Player2)";
			// 
			// player3_medium_label
			// 
			this->player3_medium_label->AutoSize = true;
			this->player3_medium_label->Location = System::Drawing::Point(96, 177);
			this->player3_medium_label->Name = L"player3_medium_label";
			this->player3_medium_label->Size = System::Drawing::Size(48, 13);
			this->player3_medium_label->TabIndex = 9;
			this->player3_medium_label->Text = L"(Player3)";
			// 
			// player1_easy_label
			// 
			this->player1_easy_label->AutoSize = true;
			this->player1_easy_label->Location = System::Drawing::Point(96, 231);
			this->player1_easy_label->Name = L"player1_easy_label";
			this->player1_easy_label->Size = System::Drawing::Size(48, 13);
			this->player1_easy_label->TabIndex = 10;
			this->player1_easy_label->Text = L"(Player1)";
			// 
			// player2_medium_label
			// 
			this->player2_medium_label->AutoSize = true;
			this->player2_medium_label->Location = System::Drawing::Point(96, 153);
			this->player2_medium_label->Name = L"player2_medium_label";
			this->player2_medium_label->Size = System::Drawing::Size(48, 13);
			this->player2_medium_label->TabIndex = 11;
			this->player2_medium_label->Text = L"(Player2)";
			// 
			// player3_easy_label
			// 
			this->player3_easy_label->AutoSize = true;
			this->player3_easy_label->Location = System::Drawing::Point(96, 277);
			this->player3_easy_label->Name = L"player3_easy_label";
			this->player3_easy_label->Size = System::Drawing::Size(48, 13);
			this->player3_easy_label->TabIndex = 12;
			this->player3_easy_label->Text = L"(Player3)";
			// 
			// num_p1_h_label
			// 
			this->num_p1_h_label->AutoSize = true;
			this->num_p1_h_label->Location = System::Drawing::Point(257, 31);
			this->num_p1_h_label->Name = L"num_p1_h_label";
			this->num_p1_h_label->Size = System::Drawing::Size(43, 13);
			this->num_p1_h_label->TabIndex = 13;
			this->num_p1_h_label->Text = L"020000";
			this->num_p1_h_label->Visible = false;
			// 
			// num_p2_h_label
			// 
			this->num_p2_h_label->AutoSize = true;
			this->num_p2_h_label->Location = System::Drawing::Point(257, 54);
			this->num_p2_h_label->Name = L"num_p2_h_label";
			this->num_p2_h_label->Size = System::Drawing::Size(43, 13);
			this->num_p2_h_label->TabIndex = 14;
			this->num_p2_h_label->Text = L"020000";
			this->num_p2_h_label->Visible = false;
			// 
			// num_p3_h_label
			// 
			this->num_p3_h_label->AutoSize = true;
			this->num_p3_h_label->Location = System::Drawing::Point(257, 79);
			this->num_p3_h_label->Name = L"num_p3_h_label";
			this->num_p3_h_label->Size = System::Drawing::Size(43, 13);
			this->num_p3_h_label->TabIndex = 15;
			this->num_p3_h_label->Text = L"020000";
			this->num_p3_h_label->Visible = false;
			// 
			// num_p1_m_label
			// 
			this->num_p1_m_label->AutoSize = true;
			this->num_p1_m_label->Location = System::Drawing::Point(257, 130);
			this->num_p1_m_label->Name = L"num_p1_m_label";
			this->num_p1_m_label->Size = System::Drawing::Size(43, 13);
			this->num_p1_m_label->TabIndex = 16;
			this->num_p1_m_label->Text = L"020000";
			this->num_p1_m_label->Visible = false;
			// 
			// num_p2_m_label
			// 
			this->num_p2_m_label->AutoSize = true;
			this->num_p2_m_label->Location = System::Drawing::Point(257, 153);
			this->num_p2_m_label->Name = L"num_p2_m_label";
			this->num_p2_m_label->Size = System::Drawing::Size(43, 13);
			this->num_p2_m_label->TabIndex = 17;
			this->num_p2_m_label->Text = L"020000";
			this->num_p2_m_label->Visible = false;
			// 
			// num_p3_m_label
			// 
			this->num_p3_m_label->AutoSize = true;
			this->num_p3_m_label->Location = System::Drawing::Point(257, 177);
			this->num_p3_m_label->Name = L"num_p3_m_label";
			this->num_p3_m_label->Size = System::Drawing::Size(43, 13);
			this->num_p3_m_label->TabIndex = 18;
			this->num_p3_m_label->Text = L"020000";
			this->num_p3_m_label->Visible = false;
			// 
			// num_p1_e_label
			// 
			this->num_p1_e_label->AutoSize = true;
			this->num_p1_e_label->Location = System::Drawing::Point(257, 231);
			this->num_p1_e_label->Name = L"num_p1_e_label";
			this->num_p1_e_label->Size = System::Drawing::Size(43, 13);
			this->num_p1_e_label->TabIndex = 19;
			this->num_p1_e_label->Text = L"020000";
			this->num_p1_e_label->Visible = false;
			// 
			// num_p2_e_label
			// 
			this->num_p2_e_label->AutoSize = true;
			this->num_p2_e_label->Location = System::Drawing::Point(257, 255);
			this->num_p2_e_label->Name = L"num_p2_e_label";
			this->num_p2_e_label->Size = System::Drawing::Size(43, 13);
			this->num_p2_e_label->TabIndex = 20;
			this->num_p2_e_label->Text = L"020000";
			this->num_p2_e_label->Visible = false;
			// 
			// num_p3_e_label
			// 
			this->num_p3_e_label->AutoSize = true;
			this->num_p3_e_label->Location = System::Drawing::Point(257, 277);
			this->num_p3_e_label->Name = L"num_p3_e_label";
			this->num_p3_e_label->Size = System::Drawing::Size(43, 13);
			this->num_p3_e_label->TabIndex = 21;
			this->num_p3_e_label->Text = L"020000";
			this->num_p3_e_label->Visible = false;
			// 
			// Highscores
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->ClientSize = System::Drawing::Size(312, 347);
			this->Controls->Add(this->num_p3_e_label);
			this->Controls->Add(this->num_p2_e_label);
			this->Controls->Add(this->num_p1_e_label);
			this->Controls->Add(this->num_p3_m_label);
			this->Controls->Add(this->num_p2_m_label);
			this->Controls->Add(this->num_p1_m_label);
			this->Controls->Add(this->num_p3_h_label);
			this->Controls->Add(this->num_p2_h_label);
			this->Controls->Add(this->num_p1_h_label);
			this->Controls->Add(this->player3_easy_label);
			this->Controls->Add(this->player2_medium_label);
			this->Controls->Add(this->player1_easy_label);
			this->Controls->Add(this->player3_medium_label);
			this->Controls->Add(this->player2_easy_label);
			this->Controls->Add(this->player1_medium_label);
			this->Controls->Add(this->top3_easy_label);
			this->Controls->Add(this->top3_medium_label);
			this->Controls->Add(this->player3_hard_label);
			this->Controls->Add(this->player2_hard_label);
			this->Controls->Add(this->player1_hard_label);
			this->Controls->Add(this->top3_hard_label);
			this->Controls->Add(this->button1);
			this->Name = L"Highscores";
			this->Text = L"Highscores";
			this->Load += gcnew System::EventHandler(this, &Highscores::Highscores_Load);
			this->ResumeLayout(false);
			this->PerformLayout();

		}
#pragma endregion
	private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		Highscores::Close();
	}

	private: System::Void Highscores_Load(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void compare_players_time()
	{
		using namespace std;

		string title;
		string data;
		String^ data_STR;

		ifstream winnersFile;
		winnersFile.open("SavedWinners.txt", ios::in);

		while (!winnersFile.eof())
		{
			winnersFile >> title;
			winnersFile >> data;

			if (data == "Hard")
			{
				winnersFile >> title;
				winnersFile >> data;
				
				string p1_label_str = msclr::interop::marshal_as<std::string>(num_p1_h_label->Text);
				int p1_label_int = stoi(p1_label_str);
				string p2_label_str = msclr::interop::marshal_as<std::string>(num_p2_h_label->Text);
				int p2_label_int = stoi(p2_label_str);
				string p3_label_str = msclr::interop::marshal_as<std::string>(num_p3_h_label->Text);
				int p3_label_int = stoi(p3_label_str);

				int data_time_int = stoi(data);
				data_STR = gcnew String(data.c_str());

				if (data_time_int < p1_label_int)
				{
					num_p1_h_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player1_hard_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player1_hard_label->Text = player1_hard_label->Text + " " + data_STR;
				}
				else if (data_time_int < p2_label_int)
				{
					num_p2_h_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player2_hard_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player2_hard_label->Text = player2_hard_label->Text + " " + data_STR;
				}
				else if (data_time_int < p3_label_int)
				{
					num_p3_h_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player3_hard_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player3_hard_label->Text = player3_hard_label->Text + " " + data_STR;
				}

				winnersFile >> title;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> title;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;

			}
			else if (data == "Medium")
			{
				winnersFile >> title;
				winnersFile >> data;

				string p1_label_str = msclr::interop::marshal_as<std::string>(num_p1_m_label->Text);
				int p1_label_int = stoi(p1_label_str);
				string p2_label_str = msclr::interop::marshal_as<std::string>(num_p2_m_label->Text);
				int p2_label_int = stoi(p2_label_str);
				string p3_label_str = msclr::interop::marshal_as<std::string>(num_p3_m_label->Text);
				int p3_label_int = stoi(p3_label_str);

				int data_time_int = stoi(data);
				data_STR = gcnew String(data.c_str());

				if (data_time_int < p1_label_int)
				{
					num_p1_m_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player1_medium_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player1_medium_label->Text = player1_medium_label->Text + " " + data_STR;

				}
				else if (data_time_int < p2_label_int)
				{
					num_p2_m_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player2_medium_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player2_medium_label->Text = player2_medium_label->Text + " " + data_STR;
				}
				else if (data_time_int < p3_label_int)
				{
					num_p3_m_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player3_medium_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player3_medium_label->Text = player3_medium_label->Text + " " + data_STR;
				}

				winnersFile >> title;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> title;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
			}
			else if (data == "Easy")
			{
				winnersFile >> title;
				winnersFile >> data;
					
				string p1_label_str = msclr::interop::marshal_as<std::string>(num_p1_e_label->Text);
				int p1_label_int = stoi(p1_label_str);
				string p2_label_str = msclr::interop::marshal_as<std::string>(num_p2_e_label->Text);
				int p2_label_int = stoi(p2_label_str);
				string p3_label_str = msclr::interop::marshal_as<std::string>(num_p3_e_label->Text);
				int p3_label_int = stoi(p3_label_str);
					
				int data_time_int = stoi(data);
				data_STR = gcnew String(data.c_str());

				if (data_time_int < p1_label_int)
				{
					num_p1_e_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player1_easy_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player1_easy_label->Text = player1_easy_label->Text + " " + data_STR;

				}
				else if (data_time_int < p2_label_int)
				{
					num_p2_e_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player2_easy_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player2_easy_label->Text = player2_easy_label->Text + " " + data_STR;
				}
				else if (data_time_int < p3_label_int)
				{
					num_p3_e_label->Text = data_STR;

					//guardar username y tiempo en modo ver
					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player3_easy_label->Text = data_STR;

					winnersFile >> title;
					winnersFile >> data;
					data_STR = gcnew String(data.c_str());
					player3_easy_label->Text = player3_easy_label->Text + " " + data_STR;
				}

				winnersFile >> title;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> title;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
				winnersFile >> data;
			}
		}

		winnersFile.close();

	}



	};
}

