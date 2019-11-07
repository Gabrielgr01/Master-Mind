# Master-Mind

//VentanaPlay.h

#pragma once

#include "ConfigurationClass.h"
#include <vector>

namespace MasterMindProyectoFinal {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;

	/// <summary>
	/// Resumen de MyForm
	/// </summary>
	public ref class VentanaPlay : public System::Windows::Forms::Form
	{

		static int seconds = 0;
		static int minutes = 0;
		static int hours = 0;
		String^ sec;
		String^ min;
		String^ hour;
	private: System::Windows::Forms::ToolStripMenuItem^ loadGameToolStripMenuItem;
	private: System::Windows::Forms::Button^ Vent_Play_Start;
	private: System::Windows::Forms::GroupBox^ play_groupBox;

	public:
		bool bool_red_button = false;
		bool bool_blue_button = false;
		bool bool_green_button = false;
		bool bool_yellow_button = false;
		bool bool_pink_button = false;
		bool bool_brown_button = false;
		int enter_play_ready = 0;
		int num1;
		int num2;
		int num3;
		int num4;

	private: System::Windows::Forms::Button^ play_score_btn4;
	private: System::Windows::Forms::Button^ play_score_btn1;
	private: System::Windows::Forms::Button^ play_score_btn2;
	private: System::Windows::Forms::Button^ play_score_btn3;
	private: System::Windows::Forms::GroupBox^ play_score_groupBox;
	private: System::Windows::Forms::Button^ black_button;
	private: System::Windows::Forms::Button^ white_button;
	private: System::Windows::Forms::Label^ color_wbtn_label;
	private: System::Windows::Forms::Label^ color_position_bbtn_label;
	private: System::Windows::Forms::Button^ enter_play_button;




	public: ConfigurationClass* objSettings = new ConfigurationClass();

	public:
		VentanaPlay(ConfigurationClass* objSettings)
		{
			InitializeComponent();

			this->objSettings = objSettings;
			//
			//TODO: agregar código de constructor aquí
			//
		}

	protected:
		/// <summary>
		/// Limpiar los recursos que se estén usando.
		/// </summary>
		~VentanaPlay()
		{
			if (components)
			{
				delete components;
			}
		}


	private: System::Windows::Forms::Button^ red_button;
	private: System::Windows::Forms::Button^ blue_button;
	private: System::Windows::Forms::Button^ green_button;
	private: System::Windows::Forms::Button^ yellow_button;
	private: System::Windows::Forms::Button^ pink_button;
	private: System::Windows::Forms::Button^ brown_button;


	private: System::Windows::Forms::Timer^ Clock;
	private: System::Windows::Forms::Button^ guess1_button;
	private: System::Windows::Forms::Button^ guess2_button;
	private: System::Windows::Forms::Button^ guess3_button;
	private: System::Windows::Forms::Button^ guess4_button;


	private: System::Windows::Forms::MenuStrip^ menuStrip1;


	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ instruccionesToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ salirToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ archivoToolStripMenuItem;
	private: System::Windows::Forms::Label^ titulo_label;


	private: System::Windows::Forms::ToolStripMenuItem^ saveToolStripMenuItem;
	private: System::Windows::Forms::Label^ Time;


	private: System::ComponentModel::IContainer^ components;


	private:
		/// <summary>
		/// Variable del diseñador necesaria.
		/// </summary>


#pragma region Windows Form Designer generated code
		/// <summary>
		/// Método necesario para admitir el Diseñador. No se puede modificar
		/// el contenido de este método con el editor de código.
		/// </summary>
		void InitializeComponent(void)
		{
			this->components = (gcnew System::ComponentModel::Container());
			System::ComponentModel::ComponentResourceManager^ resources = (gcnew System::ComponentModel::ComponentResourceManager(VentanaPlay::typeid));
			this->red_button = (gcnew System::Windows::Forms::Button());
			this->blue_button = (gcnew System::Windows::Forms::Button());
			this->green_button = (gcnew System::Windows::Forms::Button());
			this->yellow_button = (gcnew System::Windows::Forms::Button());
			this->pink_button = (gcnew System::Windows::Forms::Button());
			this->brown_button = (gcnew System::Windows::Forms::Button());
			this->Clock = (gcnew System::Windows::Forms::Timer(this->components));
			this->guess1_button = (gcnew System::Windows::Forms::Button());
			this->guess2_button = (gcnew System::Windows::Forms::Button());
			this->guess3_button = (gcnew System::Windows::Forms::Button());
			this->guess4_button = (gcnew System::Windows::Forms::Button());
			this->menuStrip1 = (gcnew System::Windows::Forms::MenuStrip());
			this->archivoToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->saveToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->loadGameToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->ayudaToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->instruccionesToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->salirToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->titulo_label = (gcnew System::Windows::Forms::Label());
			this->Time = (gcnew System::Windows::Forms::Label());
			this->Vent_Play_Start = (gcnew System::Windows::Forms::Button());
			this->play_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play_score_btn4 = (gcnew System::Windows::Forms::Button());
			this->play_score_btn1 = (gcnew System::Windows::Forms::Button());
			this->play_score_btn2 = (gcnew System::Windows::Forms::Button());
			this->play_score_btn3 = (gcnew System::Windows::Forms::Button());
			this->play_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->black_button = (gcnew System::Windows::Forms::Button());
			this->white_button = (gcnew System::Windows::Forms::Button());
			this->color_wbtn_label = (gcnew System::Windows::Forms::Label());
			this->color_position_bbtn_label = (gcnew System::Windows::Forms::Label());
			this->enter_play_button = (gcnew System::Windows::Forms::Button());
			this->menuStrip1->SuspendLayout();
			this->play_groupBox->SuspendLayout();
			this->play_score_groupBox->SuspendLayout();
			this->SuspendLayout();
			// 
			// red_button
			// 
			this->red_button->BackColor = System::Drawing::Color::Transparent;
			this->red_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"red_button.BackgroundImage")));
			this->red_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->red_button->Enabled = false;
			this->red_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->red_button->Location = System::Drawing::Point(689, 135);
			this->red_button->Name = L"red_button";
			this->red_button->Size = System::Drawing::Size(69, 60);
			this->red_button->TabIndex = 0;
			this->red_button->Text = L"Red";
			this->red_button->UseVisualStyleBackColor = false;
			this->red_button->Click += gcnew System::EventHandler(this, &VentanaPlay::red_button_Click_1);
			// 
			// blue_button
			// 
			this->blue_button->BackColor = System::Drawing::Color::Transparent;
			this->blue_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"blue_button.BackgroundImage")));
			this->blue_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->blue_button->Enabled = false;
			this->blue_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->blue_button->Location = System::Drawing::Point(689, 201);
			this->blue_button->Name = L"blue_button";
			this->blue_button->Size = System::Drawing::Size(69, 65);
			this->blue_button->TabIndex = 1;
			this->blue_button->Text = L"Blue";
			this->blue_button->UseVisualStyleBackColor = false;
			this->blue_button->Click += gcnew System::EventHandler(this, &VentanaPlay::blue_button_Click);
			// 
			// green_button
			// 
			this->green_button->BackColor = System::Drawing::Color::Transparent;
			this->green_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"green_button.BackgroundImage")));
			this->green_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->green_button->Enabled = false;
			this->green_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->green_button->Location = System::Drawing::Point(689, 272);
			this->green_button->Name = L"green_button";
			this->green_button->Size = System::Drawing::Size(69, 63);
			this->green_button->TabIndex = 2;
			this->green_button->Text = L"Green";
			this->green_button->UseVisualStyleBackColor = false;
			this->green_button->Click += gcnew System::EventHandler(this, &VentanaPlay::green_button_Click);
			// 
			// yellow_button
			// 
			this->yellow_button->BackColor = System::Drawing::Color::Transparent;
			this->yellow_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"yellow_button.BackgroundImage")));
			this->yellow_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->yellow_button->Enabled = false;
			this->yellow_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->yellow_button->Location = System::Drawing::Point(689, 341);
			this->yellow_button->Name = L"yellow_button";
			this->yellow_button->Size = System::Drawing::Size(69, 63);
			this->yellow_button->TabIndex = 3;
			this->yellow_button->Text = L"Yellow";
			this->yellow_button->UseVisualStyleBackColor = false;
			this->yellow_button->Click += gcnew System::EventHandler(this, &VentanaPlay::yellow_button_Click);
			// 
			// pink_button
			// 
			this->pink_button->BackColor = System::Drawing::Color::Transparent;
			this->pink_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"pink_button.BackgroundImage")));
			this->pink_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->pink_button->Enabled = false;
			this->pink_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->pink_button->Location = System::Drawing::Point(689, 410);
			this->pink_button->Name = L"pink_button";
			this->pink_button->Size = System::Drawing::Size(69, 63);
			this->pink_button->TabIndex = 4;
			this->pink_button->Text = L"Pink";
			this->pink_button->UseVisualStyleBackColor = false;
			this->pink_button->Click += gcnew System::EventHandler(this, &VentanaPlay::pink_button_Click);
			// 
			// brown_button
			// 
			this->brown_button->BackColor = System::Drawing::Color::SaddleBrown;
			this->brown_button->Enabled = false;
			this->brown_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->brown_button->Location = System::Drawing::Point(689, 479);
			this->brown_button->Name = L"brown_button";
			this->brown_button->Size = System::Drawing::Size(69, 63);
			this->brown_button->TabIndex = 5;
			this->brown_button->Text = L"Brown";
			this->brown_button->UseVisualStyleBackColor = false;
			this->brown_button->Click += gcnew System::EventHandler(this, &VentanaPlay::brown_button_Click);
			// 
			// Clock
			// 
			this->Clock->Interval = 1000;
			this->Clock->Tick += gcnew System::EventHandler(this, &VentanaPlay::Clock_Tick);
			// 
			// guess1_button
			// 
			this->guess1_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess1_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"guess1_button.BackgroundImage")));
			this->guess1_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess1_button->Enabled = false;
			this->guess1_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess1_button->Location = System::Drawing::Point(6, 19);
			this->guess1_button->Name = L"guess1_button";
			this->guess1_button->Size = System::Drawing::Size(72, 63);
			this->guess1_button->TabIndex = 14;
			this->guess1_button->Text = L"Guess 1";
			this->guess1_button->UseVisualStyleBackColor = false;
			this->guess1_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess1_button_Click);
			// 
			// guess2_button
			// 
			this->guess2_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess2_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"guess2_button.BackgroundImage")));
			this->guess2_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess2_button->Enabled = false;
			this->guess2_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess2_button->Location = System::Drawing::Point(84, 19);
			this->guess2_button->Name = L"guess2_button";
			this->guess2_button->Size = System::Drawing::Size(72, 63);
			this->guess2_button->TabIndex = 15;
			this->guess2_button->Text = L"Guess 2";
			this->guess2_button->UseVisualStyleBackColor = false;
			this->guess2_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess2_button_Click);
			// 
			// guess3_button
			// 
			this->guess3_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess3_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"guess3_button.BackgroundImage")));
			this->guess3_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess3_button->Enabled = false;
			this->guess3_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess3_button->Location = System::Drawing::Point(162, 19);
			this->guess3_button->Name = L"guess3_button";
			this->guess3_button->Size = System::Drawing::Size(72, 63);
			this->guess3_button->TabIndex = 16;
			this->guess3_button->Text = L"Guess 3";
			this->guess3_button->UseVisualStyleBackColor = false;
			this->guess3_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess3_button_Click);
			// 
			// guess4_button
			// 
			this->guess4_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess4_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"guess4_button.BackgroundImage")));
			this->guess4_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess4_button->Enabled = false;
			this->guess4_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess4_button->Location = System::Drawing::Point(240, 19);
			this->guess4_button->Name = L"guess4_button";
			this->guess4_button->Size = System::Drawing::Size(72, 63);
			this->guess4_button->TabIndex = 17;
			this->guess4_button->Text = L"Guess 4";
			this->guess4_button->UseVisualStyleBackColor = false;
			this->guess4_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess4_button_Click);
			// 
			// menuStrip1
			// 
			this->menuStrip1->ImageScalingSize = System::Drawing::Size(20, 20);
			this->menuStrip1->Items->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(3) {
				this->archivoToolStripMenuItem,
					this->ayudaToolStripMenuItem, this->salirToolStripMenuItem
			});
			this->menuStrip1->Location = System::Drawing::Point(0, 0);
			this->menuStrip1->Name = L"menuStrip1";
			this->menuStrip1->Padding = System::Windows::Forms::Padding(4, 2, 0, 2);
			this->menuStrip1->Size = System::Drawing::Size(780, 24);
			this->menuStrip1->TabIndex = 19;
			this->menuStrip1->Text = L"menuStrip1";
			this->menuStrip1->ItemClicked += gcnew System::Windows::Forms::ToolStripItemClickedEventHandler(this, &VentanaPlay::menuStrip1_ItemClicked);
			// 
			// archivoToolStripMenuItem
			// 
			this->archivoToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(2) {
				this->saveToolStripMenuItem,
					this->loadGameToolStripMenuItem
			});
			this->archivoToolStripMenuItem->Name = L"archivoToolStripMenuItem";
			this->archivoToolStripMenuItem->Size = System::Drawing::Size(37, 20);
			this->archivoToolStripMenuItem->Text = L"File";
			this->archivoToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::archivoToolStripMenuItem_Click);
			// 
			// saveToolStripMenuItem
			// 
			this->saveToolStripMenuItem->Name = L"saveToolStripMenuItem";
			this->saveToolStripMenuItem->Size = System::Drawing::Size(134, 22);
			this->saveToolStripMenuItem->Text = L"Save Game";
			// 
			// loadGameToolStripMenuItem
			// 
			this->loadGameToolStripMenuItem->Name = L"loadGameToolStripMenuItem";
			this->loadGameToolStripMenuItem->Size = System::Drawing::Size(134, 22);
			this->loadGameToolStripMenuItem->Text = L"Load Game";
			// 
			// ayudaToolStripMenuItem
			// 
			this->ayudaToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->instruccionesToolStripMenuItem });
			this->ayudaToolStripMenuItem->Name = L"ayudaToolStripMenuItem";
			this->ayudaToolStripMenuItem->Size = System::Drawing::Size(44, 20);
			this->ayudaToolStripMenuItem->Text = L"Help";
			// 
			// instruccionesToolStripMenuItem
			// 
			this->instruccionesToolStripMenuItem->Name = L"instruccionesToolStripMenuItem";
			this->instruccionesToolStripMenuItem->Size = System::Drawing::Size(138, 22);
			this->instruccionesToolStripMenuItem->Text = L"How to play";
			// 
			// salirToolStripMenuItem
			// 
			this->salirToolStripMenuItem->Name = L"salirToolStripMenuItem";
			this->salirToolStripMenuItem->Size = System::Drawing::Size(75, 20);
			this->salirToolStripMenuItem->Text = L"Quit game";
			this->salirToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::salirToolStripMenuItem_Click);
			// 
			// titulo_label
			// 
			this->titulo_label->AutoSize = true;
			this->titulo_label->BackColor = System::Drawing::Color::OrangeRed;
			this->titulo_label->BorderStyle = System::Windows::Forms::BorderStyle::FixedSingle;
			this->titulo_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 48, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->titulo_label->ForeColor = System::Drawing::Color::Yellow;
			this->titulo_label->Location = System::Drawing::Point(204, 45);
			this->titulo_label->Name = L"titulo_label";
			this->titulo_label->Size = System::Drawing::Size(369, 75);
			this->titulo_label->TabIndex = 20;
			this->titulo_label->Text = L"MasterMind";
			this->titulo_label->Click += gcnew System::EventHandler(this, &VentanaPlay::titulo_label_Click);
			// 
			// Time
			// 
			this->Time->AutoSize = true;
			this->Time->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->Time->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 26.25F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->Time->Location = System::Drawing::Point(35, 565);
			this->Time->Name = L"Time";
			this->Time->Size = System::Drawing::Size(159, 39);
			this->Time->TabIndex = 21;
			this->Time->Text = L"00:00:00";
			this->Time->Click += gcnew System::EventHandler(this, &VentanaPlay::label2_Click);
			// 
			// Vent_Play_Start
			// 
			this->Vent_Play_Start->AutoSize = true;
			this->Vent_Play_Start->Location = System::Drawing::Point(264, 565);
			this->Vent_Play_Start->Name = L"Vent_Play_Start";
			this->Vent_Play_Start->Size = System::Drawing::Size(257, 54);
			this->Vent_Play_Start->TabIndex = 22;
			this->Vent_Play_Start->Text = L"Start";
			this->Vent_Play_Start->UseVisualStyleBackColor = true;
			this->Vent_Play_Start->Click += gcnew System::EventHandler(this, &VentanaPlay::Vent_Play_Start_Click);
			// 
			// play_groupBox
			// 
			this->play_groupBox->Controls->Add(this->guess1_button);
			this->play_groupBox->Controls->Add(this->guess2_button);
			this->play_groupBox->Controls->Add(this->guess3_button);
			this->play_groupBox->Controls->Add(this->guess4_button);
			this->play_groupBox->Location = System::Drawing::Point(204, 452);
			this->play_groupBox->Name = L"play_groupBox";
			this->play_groupBox->Size = System::Drawing::Size(317, 90);
			this->play_groupBox->TabIndex = 23;
			this->play_groupBox->TabStop = false;
			this->play_groupBox->Text = L"Play 1";
			// 
			// play_score_btn4
			// 
			this->play_score_btn4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play_score_btn4.BackgroundImage")));
			this->play_score_btn4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn4->Enabled = false;
			this->play_score_btn4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn4->Location = System::Drawing::Point(37, 50);
			this->play_score_btn4->Name = L"play_score_btn4";
			this->play_score_btn4->Size = System::Drawing::Size(25, 25);
			this->play_score_btn4->TabIndex = 24;
			this->play_score_btn4->UseVisualStyleBackColor = true;
			// 
			// play_score_btn1
			// 
			this->play_score_btn1->BackColor = System::Drawing::Color::Sienna;
			this->play_score_btn1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play_score_btn1.BackgroundImage")));
			this->play_score_btn1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn1->Enabled = false;
			this->play_score_btn1->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn1->Location = System::Drawing::Point(6, 19);
			this->play_score_btn1->Name = L"play_score_btn1";
			this->play_score_btn1->Size = System::Drawing::Size(25, 25);
			this->play_score_btn1->TabIndex = 25;
			this->play_score_btn1->UseVisualStyleBackColor = false;
			// 
			// play_score_btn2
			// 
			this->play_score_btn2->BackColor = System::Drawing::Color::Sienna;
			this->play_score_btn2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play_score_btn2.BackgroundImage")));
			this->play_score_btn2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn2->Enabled = false;
			this->play_score_btn2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn2->Location = System::Drawing::Point(37, 19);
			this->play_score_btn2->Name = L"play_score_btn2";
			this->play_score_btn2->Size = System::Drawing::Size(25, 25);
			this->play_score_btn2->TabIndex = 26;
			this->play_score_btn2->UseVisualStyleBackColor = false;
			// 
			// play_score_btn3
			// 
			this->play_score_btn3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play_score_btn3.BackgroundImage")));
			this->play_score_btn3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn3->Enabled = false;
			this->play_score_btn3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn3->Location = System::Drawing::Point(6, 50);
			this->play_score_btn3->Name = L"play_score_btn3";
			this->play_score_btn3->Size = System::Drawing::Size(25, 25);
			this->play_score_btn3->TabIndex = 27;
			this->play_score_btn3->UseVisualStyleBackColor = true;
			// 
			// play_score_groupBox
			// 
			this->play_score_groupBox->Controls->Add(this->play_score_btn1);
			this->play_score_groupBox->Controls->Add(this->play_score_btn4);
			this->play_score_groupBox->Controls->Add(this->play_score_btn3);
			this->play_score_groupBox->Controls->Add(this->play_score_btn2);
			this->play_score_groupBox->Location = System::Drawing::Point(527, 452);
			this->play_score_groupBox->Name = L"play_score_groupBox";
			this->play_score_groupBox->Size = System::Drawing::Size(68, 90);
			this->play_score_groupBox->TabIndex = 28;
			this->play_score_groupBox->TabStop = false;
			// 
			// black_button
			// 
			this->black_button->BackColor = System::Drawing::Color::Sienna;
			this->black_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"black_button.BackgroundImage")));
			this->black_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->black_button->Enabled = false;
			this->black_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->black_button->Location = System::Drawing::Point(533, 594);
			this->black_button->Name = L"black_button";
			this->black_button->Size = System::Drawing::Size(25, 25);
			this->black_button->TabIndex = 28;
			this->black_button->UseVisualStyleBackColor = false;
			// 
			// white_button
			// 
			this->white_button->BackColor = System::Drawing::Color::Sienna;
			this->white_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"white_button.BackgroundImage")));
			this->white_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->white_button->Enabled = false;
			this->white_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->white_button->Location = System::Drawing::Point(533, 563);
			this->white_button->Name = L"white_button";
			this->white_button->Size = System::Drawing::Size(25, 25);
			this->white_button->TabIndex = 29;
			this->white_button->UseVisualStyleBackColor = false;
			// 
			// color_wbtn_label
			// 
			this->color_wbtn_label->AutoSize = true;
			this->color_wbtn_label->Location = System::Drawing::Point(564, 569);
			this->color_wbtn_label->Name = L"color_wbtn_label";
			this->color_wbtn_label->Size = System::Drawing::Size(30, 13);
			this->color_wbtn_label->TabIndex = 30;
			this->color_wbtn_label->Text = L"color";
			this->color_wbtn_label->Click += gcnew System::EventHandler(this, &VentanaPlay::color_wbtn_label_Click);
			// 
			// color_position_bbtn_label
			// 
			this->color_position_bbtn_label->AutoSize = true;
			this->color_position_bbtn_label->Location = System::Drawing::Point(564, 600);
			this->color_position_bbtn_label->Name = L"color_position_bbtn_label";
			this->color_position_bbtn_label->Size = System::Drawing::Size(90, 13);
			this->color_position_bbtn_label->TabIndex = 31;
			this->color_position_bbtn_label->Text = L"color and position";
			this->color_position_bbtn_label->Click += gcnew System::EventHandler(this, &VentanaPlay::color_position_bbtn_label_Click);
			// 
			// enter_play_button
			// 
			this->enter_play_button->Enabled = false;
			this->enter_play_button->Location = System::Drawing::Point(77, 491);
			this->enter_play_button->Name = L"enter_play_button";
			this->enter_play_button->Size = System::Drawing::Size(75, 23);
			this->enter_play_button->TabIndex = 32;
			this->enter_play_button->Text = L"Enter";
			this->enter_play_button->UseVisualStyleBackColor = true;
			this->enter_play_button->Click += gcnew System::EventHandler(this, &VentanaPlay::enter_play_button_Click);
			// 
			// VentanaPlay
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Sienna;
			this->ClientSize = System::Drawing::Size(780, 640);
			this->Controls->Add(this->enter_play_button);
			this->Controls->Add(this->color_position_bbtn_label);
			this->Controls->Add(this->color_wbtn_label);
			this->Controls->Add(this->white_button);
			this->Controls->Add(this->black_button);
			this->Controls->Add(this->play_score_groupBox);
			this->Controls->Add(this->play_groupBox);
			this->Controls->Add(this->Vent_Play_Start);
			this->Controls->Add(this->Time);
			this->Controls->Add(this->titulo_label);
			this->Controls->Add(this->brown_button);
			this->Controls->Add(this->pink_button);
			this->Controls->Add(this->yellow_button);
			this->Controls->Add(this->green_button);
			this->Controls->Add(this->blue_button);
			this->Controls->Add(this->red_button);
			this->Controls->Add(this->menuStrip1);
			this->FormBorderStyle = System::Windows::Forms::FormBorderStyle::FixedDialog;
			this->MainMenuStrip = this->menuStrip1;
			this->Name = L"VentanaPlay";
			this->Text = L"Master Mind";
			this->Load += gcnew System::EventHandler(this, &VentanaPlay::MyForm_Load);
			this->menuStrip1->ResumeLayout(false);
			this->menuStrip1->PerformLayout();
			this->play_groupBox->ResumeLayout(false);
			this->play_score_groupBox->ResumeLayout(false);
			this->ResumeLayout(false);
			this->PerformLayout();

		}
#pragma endregion

	private: System::Void MyForm_Load(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void titulo_label_Click(System::Object^ sender, System::EventArgs^ e){
	}
	private: System::Void label2_Click(System::Object^ sender, System::EventArgs^ e){
	}

	private: System::Void score_random()
	{

	}
	private: System::Void random_combination_rep()
	{
		num1 = rand() % 6 + 1;
		num2 = rand() % 6 + 1;
		num3 = rand() % 6 + 1;
		num4 = rand() % 6 + 1;
	}

	private: System::Void red_button_Click_1(System::Object^ sender, System::EventArgs^ e) 
	{

		//Enables the guess buttons
		
		guess1_button->Enabled = true;
		guess2_button->Enabled = true;
		guess3_button->Enabled = true;
		guess4_button->Enabled = true;
		
		//code for focusing the buttons

		bool_red_button = true;

	}
	private: System::Void blue_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		guess1_button->Enabled = true;
		guess2_button->Enabled = true;
		guess3_button->Enabled = true;
		guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_blue_button = true;
	}
	private: System::Void green_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		guess1_button->Enabled = true;
		guess2_button->Enabled = true;
		guess3_button->Enabled = true;
		guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_green_button = true;
	}
	private: System::Void yellow_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		guess1_button->Enabled = true;
		guess2_button->Enabled = true;
		guess3_button->Enabled = true;
		guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_yellow_button = true;
	}
	private: System::Void pink_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		guess1_button->Enabled = true;
		guess2_button->Enabled = true;
		guess3_button->Enabled = true;
		guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_pink_button = true;
	}
	private: System::Void brown_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		guess1_button->Enabled = true;
		guess2_button->Enabled = true;
		guess3_button->Enabled = true;
		guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_brown_button = true;
	}


	private: System::Void menuStrip1_ItemClicked(System::Object^ sender, System::Windows::Forms::ToolStripItemClickedEventArgs^ e) 
	{

	}
	private: System::Void archivoToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) 
	{

	}
	private: System::Void salirToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e)
	{
		VentanaPlay::Close();

		//devuleve los valores del reloj/cronometro a 0
		seconds = 0;
		minutes = 0;
		hours = 0;
	}


	private: System::Void guess1_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{

		if (bool_red_button == true)
		{
			guess1_button->BackgroundImage = red_button->BackgroundImage;
			guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			guess1_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			guess1_button->BackgroundImage = blue_button->BackgroundImage;
			guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			guess1_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			guess1_button->BackgroundImage = green_button->BackgroundImage;
			guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			guess1_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess1_button->BackgroundImage = yellow_button->BackgroundImage;
			guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			guess1_button->BackColor = yellow_button->BackColor;

			bool_yellow_button= false;
		}
		if (bool_pink_button == true)
		{
			guess1_button->BackgroundImage = pink_button->BackgroundImage;
			guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			guess1_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess1_button->BackgroundImage = brown_button->BackgroundImage;
			guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			guess1_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void guess2_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (bool_red_button == true)
		{
			guess2_button->BackgroundImage = red_button->BackgroundImage;
			guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			guess2_button->BackgroundImage = blue_button->BackgroundImage;
			guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			guess2_button->BackgroundImage = green_button->BackgroundImage;
			guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			guess2_button->BackgroundImage = pink_button->BackgroundImage;
			guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess2_button->BackgroundImage = brown_button->BackgroundImage;
			guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void guess3_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (bool_red_button == true)
		{
			guess3_button->BackgroundImage = red_button->BackgroundImage;
			guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			guess3_button->BackgroundImage = blue_button->BackgroundImage;
			guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			guess3_button->BackgroundImage = green_button->BackgroundImage;
			guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			guess3_button->BackgroundImage = pink_button->BackgroundImage;
			guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess3_button->BackgroundImage = brown_button->BackgroundImage;
			guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void guess4_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (bool_red_button == true)
		{
			guess4_button->BackgroundImage = red_button->BackgroundImage;
			guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			guess4_button->BackgroundImage = blue_button->BackgroundImage;
			guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			guess4_button->BackgroundImage = green_button->BackgroundImage;
			guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			guess4_button->BackgroundImage = pink_button->BackgroundImage;
			guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			guess4_button->BackgroundImage = brown_button->BackgroundImage;
			guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}


	private: System::Void Clock_Tick(System::Object^ sender, System::EventArgs^ e)
	{

		if (objSettings->getClock() == true)
		{
			seconds++;
			if (seconds == 60)
			{
				seconds = 0;
				minutes++;
			}
			if (minutes == 60)
			{
				minutes = 0;
				hours++;
			}
			if (hours == 2)
			{
				seconds = 0;
				minutes = 0;
				hours = 0;
			}
			sec = Convert::ToString(seconds);
			min = Convert::ToString(minutes);
			hour = Convert::ToString(hours);

			if (hours < 10)
			{
				if (minutes < 10)
				{
					if (seconds < 10)
					{
						Time->Text = "0" + hour + ":0" + min + ":0" + sec;
					}
					else if (seconds >= 10)
					{
						Time->Text = "0" + hour + ":0" + min + ":" + sec;
					}
				}
				else if (minutes >= 10)
				{
					if (seconds < 10)
					{
						Time->Text = "0" + hour + ":" + min + ":0" + sec;
					}
					else if (seconds >= 10)
					{
						Time->Text = "0" + hour + ":" + min + ":" + sec;
					}
				}
			}
			else if (hours >= 10)
			{
				if (minutes < 10)
				{
					if (seconds < 10)
					{
						Time->Text = hour + ":0" + min + ":0" + sec;
					}
					else if (seconds >= 10)
					{
						Time->Text = hour + ":0" + min + ":" + sec;
					}
				}
				else if (minutes >= 10)
				{
					if (seconds < 10)
					{
						Time->Text = hour + ":" + min + ":0" + sec;
					}
					else if (seconds >= 10)
					{
						Time->Text = hour + ":" + min + ":" + sec;
					}
				}
			}

			else if (objSettings->getTimekeeperPlay() == true)
			{
				//CODIGO TIMEKEEPER POR JUGADA
			}

			else if (objSettings->getTimekeeperGame() == true)
			{
				//CODIGO TIMEKEEPER POR JUEGO
			}
		}
	}

	private: System::Void Vent_Play_Start_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//combination
		random_combination_rep();

		//Enables the colors buttons
		VentanaPlay::red_button->Enabled = true;
		VentanaPlay::blue_button->Enabled = true;
		VentanaPlay::green_button->Enabled  = true;
		VentanaPlay::yellow_button->Enabled = true;
		VentanaPlay::pink_button->Enabled = true;
		VentanaPlay::brown_button->Enabled = true;


		//Clock starts
		if (objSettings->getClock() == true)
		{
			Clock->Enabled = true;
		}
		else if (objSettings->getClock() == false)
		{
			if (objSettings->getTimekeeperPlay() == true)
			{
				Clock->Enabled = true;
			}
			else if (objSettings->getTimekeeperGame() == true)
			{
				Clock->Enabled = true;
			}
			else
			{
				Clock->Enabled = false;
			}
		}


		Vent_Play_Start->Enabled = false;
	}

	private: System::Void enter_play_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//codigo para calificar

		//codigo para habilitar otra jugada
	}


	private: System::Void color_position_bbtn_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void color_wbtn_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}



};
}
