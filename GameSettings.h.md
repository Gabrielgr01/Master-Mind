

//GameSettings
//Fully documented
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
		//Definition of the variables to be used in this class
		int difficulty;
		bool clock;
		bool timekeeper_play;
		bool timekeeper_game;
		bool element_rep;
		static Image^ picBox_img1_GS;
		static Image^ picBox_img2_GS;
		static Image^ picBox_img3_GS;
		static Image^ picBox_img4_GS;
		static Image^ picBox_img5_GS;
		static Image^ picBox_img6_GS;
	private: System::Windows::Forms::PictureBox^ shapes_hexagon_picBox;
	private: System::Windows::Forms::PictureBox^ shapes_pentagon_picBox;
	private: System::Windows::Forms::PictureBox^ shapes_square_picBox;
	private: System::Windows::Forms::PictureBox^ shapes_doubleTriangle_picBox;
	private: System::Windows::Forms::PictureBox^ shapes_triangle_picBox;
	private: System::Windows::Forms::PictureBox^ shapes_lightning_picBox;
	public:



	public:









	private: System::Windows::Forms::PictureBox^ numbers_5_picBox;

	private: System::Windows::Forms::PictureBox^ numbers_4_picBox;

	private: System::Windows::Forms::PictureBox^ numbers_3_picBox;

	private: System::Windows::Forms::PictureBox^ numbers_2_picBox;

	private: System::Windows::Forms::PictureBox^ numbers_1_picBox;

	private: System::Windows::Forms::PictureBox^ numbers_0_picBox;


	private: System::Windows::Forms::PictureBox^ letters_F_picBox;

	private: System::Windows::Forms::PictureBox^ letters_E_picBox;

	private: System::Windows::Forms::PictureBox^ letters_D_picBox;

	private: System::Windows::Forms::PictureBox^ letters_C_picBox;

	private: System::Windows::Forms::PictureBox^ letters_B_picBox;

	private: System::Windows::Forms::PictureBox^ letters_A_picBox;

	private: System::Windows::Forms::PictureBox^ colors_brown_picBox;

	private: System::Windows::Forms::PictureBox^ colors_pink_picBox;

	private: System::Windows::Forms::PictureBox^ colors_yellow_picBox;

	private: System::Windows::Forms::PictureBox^ colors_green_picBox;

	private: System::Windows::Forms::PictureBox^ colors_blue_picBox;

	private: System::Windows::Forms::PictureBox^ colors_red_picBox;

		   int element_type;

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

	public: System::Windows::Forms::RadioButton^ Element_rep_Disabled;
	public: System::Windows::Forms::RadioButton^ Element_rep_Enabled;

	private: System::Windows::Forms::GroupBox^ groupBox4;
	private: System::Windows::Forms::RadioButton^ elem_type_shapes_rbtn;

	private: System::Windows::Forms::RadioButton^ elem_type_numbers_rbtn;

	private: System::Windows::Forms::RadioButton^ elem_type_letters_rbtn;
	private: System::Windows::Forms::RadioButton^ elem_type_colors_rbtn;


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
			//Definition of the components shown in the form
			System::ComponentModel::ComponentResourceManager^ resources = (gcnew System::ComponentModel::ComponentResourceManager(GameSettings::typeid));
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
			this->shapes_hexagon_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->shapes_pentagon_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->shapes_square_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->shapes_doubleTriangle_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->shapes_triangle_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->shapes_lightning_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->numbers_5_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->numbers_4_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->numbers_3_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->numbers_2_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->numbers_1_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->numbers_0_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->letters_F_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->letters_E_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->letters_D_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->letters_C_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->letters_B_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->letters_A_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->colors_brown_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->colors_pink_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->colors_yellow_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->colors_green_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->colors_blue_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->colors_red_picBox = (gcnew System::Windows::Forms::PictureBox());
			this->elem_type_shapes_rbtn = (gcnew System::Windows::Forms::RadioButton());
			this->elem_type_numbers_rbtn = (gcnew System::Windows::Forms::RadioButton());
			this->elem_type_letters_rbtn = (gcnew System::Windows::Forms::RadioButton());
			this->elem_type_colors_rbtn = (gcnew System::Windows::Forms::RadioButton());
			this->Save_Settings = (gcnew System::Windows::Forms::Button());
			this->button_back = (gcnew System::Windows::Forms::Button());
			this->groupBox1->SuspendLayout();
			this->groupBox2->SuspendLayout();
			this->groupBox3->SuspendLayout();
			this->groupBox4->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_hexagon_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_pentagon_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_square_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_doubleTriangle_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_triangle_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_lightning_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_5_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_4_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_3_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_2_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_1_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_0_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_F_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_E_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_D_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_C_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_B_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_A_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_brown_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_pink_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_yellow_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_green_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_blue_picBox))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_red_picBox))->BeginInit();
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
			this->Difficulty_Hard->Size = System::Drawing::Size(251, 17);
			this->Difficulty_Hard->TabIndex = 2;
			this->Difficulty_Hard->Text = L"Hard (6 plays, combination of 4 from 6 elements)";
			this->Difficulty_Hard->UseVisualStyleBackColor = true;
			this->Difficulty_Hard->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Difficulty_Hard_CheckedChanged);
			// 
			// Difficulty_Medium
			// 
			this->Difficulty_Medium->AutoSize = true;
			this->Difficulty_Medium->Location = System::Drawing::Point(6, 42);
			this->Difficulty_Medium->Name = L"Difficulty_Medium";
			this->Difficulty_Medium->Size = System::Drawing::Size(265, 17);
			this->Difficulty_Medium->TabIndex = 1;
			this->Difficulty_Medium->Text = L"Medium (7 plays, combination of 4 from 6 elements)";
			this->Difficulty_Medium->UseVisualStyleBackColor = true;
			this->Difficulty_Medium->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::Difficulty_Medium_CheckedChanged);
			// 
			// Difficulty_Easy
			// 
			this->Difficulty_Easy->AutoSize = true;
			this->Difficulty_Easy->Checked = true;
			this->Difficulty_Easy->Location = System::Drawing::Point(6, 19);
			this->Difficulty_Easy->Name = L"Difficulty_Easy";
			this->Difficulty_Easy->Size = System::Drawing::Size(251, 17);
			this->Difficulty_Easy->TabIndex = 0;
			this->Difficulty_Easy->TabStop = true;
			this->Difficulty_Easy->Text = L"Easy (8 plays, combination of 4 from 6 elements)";
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
			this->groupBox3->Size = System::Drawing::Size(277, 115);
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
			this->groupBox4->Controls->Add(this->shapes_hexagon_picBox);
			this->groupBox4->Controls->Add(this->shapes_pentagon_picBox);
			this->groupBox4->Controls->Add(this->shapes_square_picBox);
			this->groupBox4->Controls->Add(this->shapes_doubleTriangle_picBox);
			this->groupBox4->Controls->Add(this->shapes_triangle_picBox);
			this->groupBox4->Controls->Add(this->shapes_lightning_picBox);
			this->groupBox4->Controls->Add(this->numbers_5_picBox);
			this->groupBox4->Controls->Add(this->numbers_4_picBox);
			this->groupBox4->Controls->Add(this->numbers_3_picBox);
			this->groupBox4->Controls->Add(this->numbers_2_picBox);
			this->groupBox4->Controls->Add(this->numbers_1_picBox);
			this->groupBox4->Controls->Add(this->numbers_0_picBox);
			this->groupBox4->Controls->Add(this->letters_F_picBox);
			this->groupBox4->Controls->Add(this->letters_E_picBox);
			this->groupBox4->Controls->Add(this->letters_D_picBox);
			this->groupBox4->Controls->Add(this->letters_C_picBox);
			this->groupBox4->Controls->Add(this->letters_B_picBox);
			this->groupBox4->Controls->Add(this->letters_A_picBox);
			this->groupBox4->Controls->Add(this->colors_brown_picBox);
			this->groupBox4->Controls->Add(this->colors_pink_picBox);
			this->groupBox4->Controls->Add(this->colors_yellow_picBox);
			this->groupBox4->Controls->Add(this->colors_green_picBox);
			this->groupBox4->Controls->Add(this->colors_blue_picBox);
			this->groupBox4->Controls->Add(this->colors_red_picBox);
			this->groupBox4->Controls->Add(this->elem_type_shapes_rbtn);
			this->groupBox4->Controls->Add(this->elem_type_numbers_rbtn);
			this->groupBox4->Controls->Add(this->elem_type_letters_rbtn);
			this->groupBox4->Controls->Add(this->elem_type_colors_rbtn);
			this->groupBox4->Location = System::Drawing::Point(295, 12);
			this->groupBox4->Name = L"groupBox4";
			this->groupBox4->Size = System::Drawing::Size(297, 333);
			this->groupBox4->TabIndex = 0;
			this->groupBox4->TabStop = false;
			this->groupBox4->Text = L"Element type to use in combination";
			this->groupBox4->Enter += gcnew System::EventHandler(this, &GameSettings::groupBox4_Enter);
			// 
			// shapes_hexagon_picBox
			// 
			this->shapes_hexagon_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"shapes_hexagon_picBox.BackgroundImage")));
			this->shapes_hexagon_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->shapes_hexagon_picBox->Location = System::Drawing::Point(218, 272);
			this->shapes_hexagon_picBox->Name = L"shapes_hexagon_picBox";
			this->shapes_hexagon_picBox->Size = System::Drawing::Size(45, 40);
			this->shapes_hexagon_picBox->TabIndex = 30;
			this->shapes_hexagon_picBox->TabStop = false;
			// 
			// shapes_pentagon_picBox
			// 
			this->shapes_pentagon_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"shapes_pentagon_picBox.BackgroundImage")));
			this->shapes_pentagon_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->shapes_pentagon_picBox->Location = System::Drawing::Point(218, 226);
			this->shapes_pentagon_picBox->Name = L"shapes_pentagon_picBox";
			this->shapes_pentagon_picBox->Size = System::Drawing::Size(45, 40);
			this->shapes_pentagon_picBox->TabIndex = 29;
			this->shapes_pentagon_picBox->TabStop = false;
			// 
			// shapes_square_picBox
			// 
			this->shapes_square_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"shapes_square_picBox.BackgroundImage")));
			this->shapes_square_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->shapes_square_picBox->Location = System::Drawing::Point(218, 180);
			this->shapes_square_picBox->Name = L"shapes_square_picBox";
			this->shapes_square_picBox->Size = System::Drawing::Size(45, 40);
			this->shapes_square_picBox->TabIndex = 28;
			this->shapes_square_picBox->TabStop = false;
			// 
			// shapes_doubleTriangle_picBox
			// 
			this->shapes_doubleTriangle_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"shapes_doubleTriangle_picBox.BackgroundImage")));
			this->shapes_doubleTriangle_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->shapes_doubleTriangle_picBox->Location = System::Drawing::Point(218, 134);
			this->shapes_doubleTriangle_picBox->Name = L"shapes_doubleTriangle_picBox";
			this->shapes_doubleTriangle_picBox->Size = System::Drawing::Size(45, 40);
			this->shapes_doubleTriangle_picBox->TabIndex = 27;
			this->shapes_doubleTriangle_picBox->TabStop = false;
			// 
			// shapes_triangle_picBox
			// 
			this->shapes_triangle_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"shapes_triangle_picBox.BackgroundImage")));
			this->shapes_triangle_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->shapes_triangle_picBox->Location = System::Drawing::Point(218, 88);
			this->shapes_triangle_picBox->Name = L"shapes_triangle_picBox";
			this->shapes_triangle_picBox->Size = System::Drawing::Size(45, 40);
			this->shapes_triangle_picBox->TabIndex = 26;
			this->shapes_triangle_picBox->TabStop = false;
			// 
			// shapes_lightning_picBox
			// 
			this->shapes_lightning_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"shapes_lightning_picBox.BackgroundImage")));
			this->shapes_lightning_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->shapes_lightning_picBox->Location = System::Drawing::Point(218, 42);
			this->shapes_lightning_picBox->Name = L"shapes_lightning_picBox";
			this->shapes_lightning_picBox->Size = System::Drawing::Size(45, 40);
			this->shapes_lightning_picBox->TabIndex = 25;
			this->shapes_lightning_picBox->TabStop = false;
			// 
			// numbers_5_picBox
			// 
			this->numbers_5_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"numbers_5_picBox.BackgroundImage")));
			this->numbers_5_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->numbers_5_picBox->Location = System::Drawing::Point(151, 272);
			this->numbers_5_picBox->Name = L"numbers_5_picBox";
			this->numbers_5_picBox->Size = System::Drawing::Size(45, 40);
			this->numbers_5_picBox->TabIndex = 24;
			this->numbers_5_picBox->TabStop = false;
			// 
			// numbers_4_picBox
			// 
			this->numbers_4_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"numbers_4_picBox.BackgroundImage")));
			this->numbers_4_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->numbers_4_picBox->Location = System::Drawing::Point(151, 226);
			this->numbers_4_picBox->Name = L"numbers_4_picBox";
			this->numbers_4_picBox->Size = System::Drawing::Size(45, 40);
			this->numbers_4_picBox->TabIndex = 23;
			this->numbers_4_picBox->TabStop = false;
			// 
			// numbers_3_picBox
			// 
			this->numbers_3_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"numbers_3_picBox.BackgroundImage")));
			this->numbers_3_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->numbers_3_picBox->Location = System::Drawing::Point(151, 180);
			this->numbers_3_picBox->Name = L"numbers_3_picBox";
			this->numbers_3_picBox->Size = System::Drawing::Size(45, 40);
			this->numbers_3_picBox->TabIndex = 22;
			this->numbers_3_picBox->TabStop = false;
			// 
			// numbers_2_picBox
			// 
			this->numbers_2_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"numbers_2_picBox.BackgroundImage")));
			this->numbers_2_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->numbers_2_picBox->Location = System::Drawing::Point(151, 134);
			this->numbers_2_picBox->Name = L"numbers_2_picBox";
			this->numbers_2_picBox->Size = System::Drawing::Size(45, 40);
			this->numbers_2_picBox->TabIndex = 21;
			this->numbers_2_picBox->TabStop = false;
			// 
			// numbers_1_picBox
			// 
			this->numbers_1_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"numbers_1_picBox.BackgroundImage")));
			this->numbers_1_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->numbers_1_picBox->Location = System::Drawing::Point(151, 88);
			this->numbers_1_picBox->Name = L"numbers_1_picBox";
			this->numbers_1_picBox->Size = System::Drawing::Size(45, 40);
			this->numbers_1_picBox->TabIndex = 20;
			this->numbers_1_picBox->TabStop = false;
			// 
			// numbers_0_picBox
			// 
			this->numbers_0_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"numbers_0_picBox.BackgroundImage")));
			this->numbers_0_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->numbers_0_picBox->Location = System::Drawing::Point(151, 42);
			this->numbers_0_picBox->Name = L"numbers_0_picBox";
			this->numbers_0_picBox->Size = System::Drawing::Size(45, 40);
			this->numbers_0_picBox->TabIndex = 19;
			this->numbers_0_picBox->TabStop = false;
			// 
			// letters_F_picBox
			// 
			this->letters_F_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"letters_F_picBox.BackgroundImage")));
			this->letters_F_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->letters_F_picBox->Location = System::Drawing::Point(78, 272);
			this->letters_F_picBox->Name = L"letters_F_picBox";
			this->letters_F_picBox->Size = System::Drawing::Size(45, 40);
			this->letters_F_picBox->TabIndex = 18;
			this->letters_F_picBox->TabStop = false;
			// 
			// letters_E_picBox
			// 
			this->letters_E_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"letters_E_picBox.BackgroundImage")));
			this->letters_E_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->letters_E_picBox->Location = System::Drawing::Point(78, 226);
			this->letters_E_picBox->Name = L"letters_E_picBox";
			this->letters_E_picBox->Size = System::Drawing::Size(45, 40);
			this->letters_E_picBox->TabIndex = 17;
			this->letters_E_picBox->TabStop = false;
			// 
			// letters_D_picBox
			// 
			this->letters_D_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"letters_D_picBox.BackgroundImage")));
			this->letters_D_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->letters_D_picBox->Location = System::Drawing::Point(78, 180);
			this->letters_D_picBox->Name = L"letters_D_picBox";
			this->letters_D_picBox->Size = System::Drawing::Size(45, 40);
			this->letters_D_picBox->TabIndex = 16;
			this->letters_D_picBox->TabStop = false;
			// 
			// letters_C_picBox
			// 
			this->letters_C_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"letters_C_picBox.BackgroundImage")));
			this->letters_C_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->letters_C_picBox->Location = System::Drawing::Point(78, 134);
			this->letters_C_picBox->Name = L"letters_C_picBox";
			this->letters_C_picBox->Size = System::Drawing::Size(45, 40);
			this->letters_C_picBox->TabIndex = 15;
			this->letters_C_picBox->TabStop = false;
			// 
			// letters_B_picBox
			// 
			this->letters_B_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"letters_B_picBox.BackgroundImage")));
			this->letters_B_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->letters_B_picBox->Location = System::Drawing::Point(78, 88);
			this->letters_B_picBox->Name = L"letters_B_picBox";
			this->letters_B_picBox->Size = System::Drawing::Size(45, 40);
			this->letters_B_picBox->TabIndex = 14;
			this->letters_B_picBox->TabStop = false;
			// 
			// letters_A_picBox
			// 
			this->letters_A_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"letters_A_picBox.BackgroundImage")));
			this->letters_A_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->letters_A_picBox->Location = System::Drawing::Point(78, 42);
			this->letters_A_picBox->Name = L"letters_A_picBox";
			this->letters_A_picBox->Size = System::Drawing::Size(45, 40);
			this->letters_A_picBox->TabIndex = 13;
			this->letters_A_picBox->TabStop = false;
			// 
			// colors_brown_picBox
			// 
			this->colors_brown_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"colors_brown_picBox.BackgroundImage")));
			this->colors_brown_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->colors_brown_picBox->Location = System::Drawing::Point(15, 272);
			this->colors_brown_picBox->Name = L"colors_brown_picBox";
			this->colors_brown_picBox->Size = System::Drawing::Size(45, 40);
			this->colors_brown_picBox->TabIndex = 12;
			this->colors_brown_picBox->TabStop = false;
			// 
			// colors_pink_picBox
			// 
			this->colors_pink_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"colors_pink_picBox.BackgroundImage")));
			this->colors_pink_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->colors_pink_picBox->Location = System::Drawing::Point(15, 226);
			this->colors_pink_picBox->Name = L"colors_pink_picBox";
			this->colors_pink_picBox->Size = System::Drawing::Size(45, 40);
			this->colors_pink_picBox->TabIndex = 11;
			this->colors_pink_picBox->TabStop = false;
			// 
			// colors_yellow_picBox
			// 
			this->colors_yellow_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"colors_yellow_picBox.BackgroundImage")));
			this->colors_yellow_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->colors_yellow_picBox->Location = System::Drawing::Point(15, 180);
			this->colors_yellow_picBox->Name = L"colors_yellow_picBox";
			this->colors_yellow_picBox->Size = System::Drawing::Size(45, 40);
			this->colors_yellow_picBox->TabIndex = 10;
			this->colors_yellow_picBox->TabStop = false;
			// 
			// colors_green_picBox
			// 
			this->colors_green_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"colors_green_picBox.BackgroundImage")));
			this->colors_green_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->colors_green_picBox->Location = System::Drawing::Point(15, 134);
			this->colors_green_picBox->Name = L"colors_green_picBox";
			this->colors_green_picBox->Size = System::Drawing::Size(45, 40);
			this->colors_green_picBox->TabIndex = 9;
			this->colors_green_picBox->TabStop = false;
			// 
			// colors_blue_picBox
			// 
			this->colors_blue_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"colors_blue_picBox.BackgroundImage")));
			this->colors_blue_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->colors_blue_picBox->Location = System::Drawing::Point(15, 88);
			this->colors_blue_picBox->Name = L"colors_blue_picBox";
			this->colors_blue_picBox->Size = System::Drawing::Size(45, 40);
			this->colors_blue_picBox->TabIndex = 8;
			this->colors_blue_picBox->TabStop = false;
			// 
			// colors_red_picBox
			// 
			this->colors_red_picBox->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"colors_red_picBox.BackgroundImage")));
			this->colors_red_picBox->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->colors_red_picBox->Location = System::Drawing::Point(15, 42);
			this->colors_red_picBox->Name = L"colors_red_picBox";
			this->colors_red_picBox->Size = System::Drawing::Size(45, 40);
			this->colors_red_picBox->TabIndex = 7;
			this->colors_red_picBox->TabStop = false;
			// 
			// elem_type_shapes_rbtn
			// 
			this->elem_type_shapes_rbtn->AutoSize = true;
			this->elem_type_shapes_rbtn->Location = System::Drawing::Point(202, 19);
			this->elem_type_shapes_rbtn->Name = L"elem_type_shapes_rbtn";
			this->elem_type_shapes_rbtn->Size = System::Drawing::Size(61, 17);
			this->elem_type_shapes_rbtn->TabIndex = 3;
			this->elem_type_shapes_rbtn->Text = L"Shapes";
			this->elem_type_shapes_rbtn->UseVisualStyleBackColor = true;
			this->elem_type_shapes_rbtn->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::elem_type_shapes_rbtn_CheckedChanged);
			// 
			// elem_type_numbers_rbtn
			// 
			this->elem_type_numbers_rbtn->AutoSize = true;
			this->elem_type_numbers_rbtn->Location = System::Drawing::Point(129, 19);
			this->elem_type_numbers_rbtn->Name = L"elem_type_numbers_rbtn";
			this->elem_type_numbers_rbtn->Size = System::Drawing::Size(67, 17);
			this->elem_type_numbers_rbtn->TabIndex = 2;
			this->elem_type_numbers_rbtn->Text = L"Numbers";
			this->elem_type_numbers_rbtn->UseVisualStyleBackColor = true;
			this->elem_type_numbers_rbtn->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::elem_type_numbers_rbtn_CheckedChanged);
			// 
			// elem_type_letters_rbtn
			// 
			this->elem_type_letters_rbtn->AutoSize = true;
			this->elem_type_letters_rbtn->Location = System::Drawing::Point(66, 19);
			this->elem_type_letters_rbtn->Name = L"elem_type_letters_rbtn";
			this->elem_type_letters_rbtn->Size = System::Drawing::Size(57, 17);
			this->elem_type_letters_rbtn->TabIndex = 1;
			this->elem_type_letters_rbtn->Text = L"Letters";
			this->elem_type_letters_rbtn->UseVisualStyleBackColor = true;
			this->elem_type_letters_rbtn->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::elem_type_letters_rbtn_CheckedChanged);
			// 
			// elem_type_colors_rbtn
			// 
			this->elem_type_colors_rbtn->AutoSize = true;
			this->elem_type_colors_rbtn->Checked = true;
			this->elem_type_colors_rbtn->Location = System::Drawing::Point(6, 19);
			this->elem_type_colors_rbtn->Name = L"elem_type_colors_rbtn";
			this->elem_type_colors_rbtn->Size = System::Drawing::Size(54, 17);
			this->elem_type_colors_rbtn->TabIndex = 0;
			this->elem_type_colors_rbtn->TabStop = true;
			this->elem_type_colors_rbtn->Text = L"Colors";
			this->elem_type_colors_rbtn->UseVisualStyleBackColor = true;
			this->elem_type_colors_rbtn->CheckedChanged += gcnew System::EventHandler(this, &GameSettings::elem_type_colors_rbtn_CheckedChanged);
			// 
			// Save_Settings
			// 
			this->Save_Settings->Location = System::Drawing::Point(12, 351);
			this->Save_Settings->Name = L"Save_Settings";
			this->Save_Settings->Size = System::Drawing::Size(96, 23);
			this->Save_Settings->TabIndex = 5;
			this->Save_Settings->Text = L"Save and Play!";
			this->Save_Settings->UseVisualStyleBackColor = true;
			this->Save_Settings->Click += gcnew System::EventHandler(this, &GameSettings::Save_Settings_Click);
			// 
			// button_back
			// 
			this->button_back->Location = System::Drawing::Point(517, 351);
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
			this->ClientSize = System::Drawing::Size(604, 386);
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
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_hexagon_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_pentagon_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_square_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_doubleTriangle_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_triangle_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->shapes_lightning_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_5_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_4_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_3_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_2_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_1_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->numbers_0_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_F_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_E_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_D_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_C_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_B_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->letters_A_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_brown_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_pink_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_yellow_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_green_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_blue_picBox))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->colors_red_picBox))->EndInit();
			this->ResumeLayout(false);

		}
#pragma endregion

	private: System::Void button_back_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//This is in charge of closing the tab when you click the back button
		GameSettings::Close();
	}


	private: System::Void Difficulty_Easy_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the difficulty to easy
		difficulty = 1;
		objSettings->setDifficulty(difficulty);
	}
	private: System::Void Difficulty_Medium_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the difficulty to medium
		difficulty = 2;
		objSettings->setDifficulty(difficulty);
	}
	private: System::Void Difficulty_Hard_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the difficulty to hard
		difficulty = 3;
		objSettings->setDifficulty(difficulty);
	}

	private: System::Void Clock_Enabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the timer to function as a clock, making the other options unavailable
		clock = true;
		objSettings->setClock(clock);

		timekeeper_game = false;
		objSettings->setTimekeeperGame(timekeeper_game);

		timekeeper_play = false;
		objSettings->setTimekeeperPlay(timekeeper_play);
	}
	private: System::Void Clock_Disabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This disables the timer and all of the other options
		clock = false;
		objSettings->setClock(clock);

		timekeeper_game = false;
		objSettings->setTimekeeperGame(timekeeper_game);

		timekeeper_play = false;
		objSettings->setTimekeeperPlay(timekeeper_play);
	}
	private: System::Void Timekeeper_Play_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the timer to function as a timekeeper for each of the plays, making the other options unavailable
		clock = false;
		objSettings->setClock(clock);
		timekeeper_game = false;
		objSettings->setTimekeeperGame(timekeeper_game);

		timekeeper_play = true;
		objSettings->setTimekeeperPlay(timekeeper_play);
	}
	private: System::Void Timekeeper_Game_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the timer to function as a timekeeper for the entire game, making the other options unavailable
		clock = false;
		objSettings->setClock(clock);
		timekeeper_play = false;
		objSettings->setTimekeeperPlay(timekeeper_play);

		timekeeper_game = true;
		objSettings->setTimekeeperGame(timekeeper_game);
	}

	private: System::Void Element_rep_Enabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This allows the random combination to be generated with repeated values
		element_rep = true;
		objSettings->setElementRep(element_rep);
	}
	private: System::Void Element_rep_Disabled_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This doesn't allow the random combination to be generated with repeated values
		element_rep = false;
		objSettings->setElementRep(element_rep);
	}

	private: System::Void elem_type_colors_rbtn_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the elements to colors
		element_type = 1;
		objSettings->setElementType(element_type);
	}
	private: System::Void elem_type_letters_rbtn_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the elements to letters
		element_type = 2;
		objSettings->setElementType(element_type);
	}
	private: System::Void elem_type_numbers_rbtn_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the elements to numbers
		element_type = 3;
		objSettings->setElementType(element_type);
	}
	private: System::Void elem_type_shapes_rbtn_CheckedChanged(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the elements to shapes
		element_type = 4;
		objSettings->setElementType(element_type);
	}

	private: System::Void Save_Settings_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//This sets the values of the elements to be played with and sends them to the play tab
		//GameSettings::Close();

		if (objSettings->getElementType() == 1)
		{
			picBox_img1_GS = colors_red_picBox->BackgroundImage;
			picBox_img2_GS = colors_blue_picBox->BackgroundImage;
			picBox_img3_GS = colors_green_picBox->BackgroundImage;
			picBox_img4_GS = colors_yellow_picBox->BackgroundImage;
			picBox_img5_GS = colors_pink_picBox->BackgroundImage;
			picBox_img6_GS = colors_brown_picBox->BackgroundImage;
		}
		else if (objSettings->getElementType() == 2)
		{
			picBox_img1_GS = letters_A_picBox->BackgroundImage;
			picBox_img2_GS = letters_B_picBox->BackgroundImage;
			picBox_img3_GS = letters_C_picBox->BackgroundImage;
			picBox_img4_GS = letters_D_picBox->BackgroundImage;
			picBox_img5_GS = letters_E_picBox->BackgroundImage;
			picBox_img6_GS = letters_F_picBox->BackgroundImage;
		}
		else if (objSettings->getElementType() == 3)
		{
			picBox_img1_GS = numbers_0_picBox->BackgroundImage;
			picBox_img2_GS = numbers_1_picBox->BackgroundImage;
			picBox_img3_GS = numbers_2_picBox->BackgroundImage;
			picBox_img4_GS = numbers_3_picBox->BackgroundImage;
			picBox_img5_GS = numbers_4_picBox->BackgroundImage;
			picBox_img6_GS = numbers_5_picBox->BackgroundImage;
		}
		else if (objSettings->getElementType() == 4)
		{
			picBox_img1_GS = shapes_lightning_picBox->BackgroundImage;
			picBox_img2_GS = shapes_triangle_picBox->BackgroundImage;
			picBox_img3_GS = shapes_doubleTriangle_picBox->BackgroundImage;
			picBox_img4_GS = shapes_square_picBox->BackgroundImage;
			picBox_img5_GS = shapes_pentagon_picBox->BackgroundImage;
			picBox_img6_GS = shapes_hexagon_picBox->BackgroundImage;
		}

		MasterMindProyectoFinal::VentanaPlay::btn_img1_play = picBox_img1_GS;
		MasterMindProyectoFinal::VentanaPlay::btn_img2_play = picBox_img2_GS;
		MasterMindProyectoFinal::VentanaPlay::btn_img3_play = picBox_img3_GS;
		MasterMindProyectoFinal::VentanaPlay::btn_img4_play = picBox_img4_GS;
		MasterMindProyectoFinal::VentanaPlay::btn_img5_play = picBox_img5_GS;
		MasterMindProyectoFinal::VentanaPlay::btn_img6_play = picBox_img6_GS;


		VentanaPlay juego(objSettings);
		juego.ShowDialog();
	}



	private: System::Void groupBox4_Enter(System::Object^ sender, System::EventArgs^ e)
	{
	}

	};
}
