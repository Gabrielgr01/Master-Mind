

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
	private: System::Windows::Forms::GroupBox^ play1_groupBox;
	public: static String^ userNameBtt;
	public: System::Windows::Forms::Label^ Username;
	public: System::Windows::Forms::Label^ UserNamePlay;



	



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
	private: System::Windows::Forms::GroupBox^ play1_score_groupBox;

	private: System::Windows::Forms::Button^ black_button;
	private: System::Windows::Forms::Button^ white_button;
	private: System::Windows::Forms::Label^ color_wbtn_label;
	private: System::Windows::Forms::Label^ color_position_bbtn_label;
	private: System::Windows::Forms::Button^ enter_play_button;
	private: System::Windows::Forms::GroupBox^ play2_groupBox;

	private: System::Windows::Forms::Button^ button25;
	private: System::Windows::Forms::Button^ button26;
	private: System::Windows::Forms::Button^ button27;
	private: System::Windows::Forms::Button^ button28;
	private: System::Windows::Forms::GroupBox^ play3_groupBox;

	private: System::Windows::Forms::Button^ button1;
	private: System::Windows::Forms::Button^ button2;
	private: System::Windows::Forms::Button^ button3;
	private: System::Windows::Forms::Button^ button4;
	private: System::Windows::Forms::GroupBox^ play4_groupBox;

	private: System::Windows::Forms::Button^ button5;
	private: System::Windows::Forms::Button^ button6;
	private: System::Windows::Forms::Button^ button7;
	private: System::Windows::Forms::Button^ button8;
	private: System::Windows::Forms::GroupBox^ play5_groupBox;

	private: System::Windows::Forms::Button^ button9;
	private: System::Windows::Forms::Button^ button10;
	private: System::Windows::Forms::Button^ button11;
	private: System::Windows::Forms::Button^ button12;
	private: System::Windows::Forms::GroupBox^ play6_groupBox;

	private: System::Windows::Forms::Button^ button13;
	private: System::Windows::Forms::Button^ button14;
	private: System::Windows::Forms::Button^ button15;
	private: System::Windows::Forms::Button^ button16;
	private: System::Windows::Forms::GroupBox^ play7_groupBox;

	private: System::Windows::Forms::Button^ button29;
	private: System::Windows::Forms::Button^ button30;
	private: System::Windows::Forms::Button^ button31;
	private: System::Windows::Forms::Button^ button32;
	private: System::Windows::Forms::GroupBox^ play2_score_groupBox;


	private: System::Windows::Forms::Button^ button17;
	private: System::Windows::Forms::Button^ button18;
	private: System::Windows::Forms::Button^ button19;
	private: System::Windows::Forms::Button^ button20;
	private: System::Windows::Forms::GroupBox^ play3_score_groupBox;

	private: System::Windows::Forms::Button^ button21;
	private: System::Windows::Forms::Button^ button22;
	private: System::Windows::Forms::Button^ button23;
	private: System::Windows::Forms::Button^ button24;
	private: System::Windows::Forms::GroupBox^ play4_score_groupBox;

	private: System::Windows::Forms::Button^ button33;
	private: System::Windows::Forms::Button^ button34;
	private: System::Windows::Forms::Button^ button35;
	private: System::Windows::Forms::Button^ button36;
	private: System::Windows::Forms::GroupBox^ play5_score_groupBox;

	private: System::Windows::Forms::Button^ button37;
	private: System::Windows::Forms::Button^ button38;
	private: System::Windows::Forms::Button^ button39;
	private: System::Windows::Forms::Button^ button40;
	private: System::Windows::Forms::GroupBox^ play6_score_groupBox;

	private: System::Windows::Forms::Button^ button41;
	private: System::Windows::Forms::Button^ button42;
	private: System::Windows::Forms::Button^ button43;
	private: System::Windows::Forms::Button^ button44;
	private: System::Windows::Forms::GroupBox^ play7_score_groupBox;

	private: System::Windows::Forms::Button^ button45;
	private: System::Windows::Forms::Button^ button46;
	private: System::Windows::Forms::Button^ button47;
	private: System::Windows::Forms::Button^ button48;
	private: System::Windows::Forms::GroupBox^ play8_groupBox;
	private: System::Windows::Forms::Button^ button49;
	private: System::Windows::Forms::Button^ button50;
	private: System::Windows::Forms::Button^ button51;
	private: System::Windows::Forms::Button^ button52;
	private: System::Windows::Forms::GroupBox^ play8_score_groupBox;
	private: System::Windows::Forms::Button^ button53;
	private: System::Windows::Forms::Button^ button54;
	private: System::Windows::Forms::Button^ button55;
	private: System::Windows::Forms::Button^ button56;



public:
	VentanaPlay(void)
	{
		InitializeComponent();
		//
		//TODO: agregar código de constructor aquí
		//
	}

	protected:


















	public: ConfigurationClass* objSettings = new ConfigurationClass();

	public:
		VentanaPlay(ConfigurationClass* objSettings)
		{
			InitializeComponent();

			this->objSettings = objSettings;

			if (objSettings->getDifficulty() == 1)
			{
				play7_groupBox->Visible = true;
				play7_groupBox->Enabled = true;
				play7_score_groupBox->Visible = true;
				play7_score_groupBox->Enabled = true;

				play8_groupBox->Visible = true;
				play8_groupBox->Enabled = true;
				play8_score_groupBox->Visible = true;
				play8_score_groupBox->Enabled = true;
			}
			else if (objSettings->getDifficulty() == 2)
			{
				play7_groupBox->Visible = true;
				play7_groupBox->Enabled = true;
				play7_score_groupBox->Visible = true;
				play7_score_groupBox->Enabled = true;
			}

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
			this->play1_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play_score_btn4 = (gcnew System::Windows::Forms::Button());
			this->play_score_btn1 = (gcnew System::Windows::Forms::Button());
			this->play_score_btn2 = (gcnew System::Windows::Forms::Button());
			this->play_score_btn3 = (gcnew System::Windows::Forms::Button());
			this->play1_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->black_button = (gcnew System::Windows::Forms::Button());
			this->white_button = (gcnew System::Windows::Forms::Button());
			this->color_wbtn_label = (gcnew System::Windows::Forms::Label());
			this->color_position_bbtn_label = (gcnew System::Windows::Forms::Label());
			this->enter_play_button = (gcnew System::Windows::Forms::Button());
			this->play2_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button25 = (gcnew System::Windows::Forms::Button());
			this->button26 = (gcnew System::Windows::Forms::Button());
			this->button27 = (gcnew System::Windows::Forms::Button());
			this->button28 = (gcnew System::Windows::Forms::Button());
			this->play3_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button1 = (gcnew System::Windows::Forms::Button());
			this->button2 = (gcnew System::Windows::Forms::Button());
			this->button3 = (gcnew System::Windows::Forms::Button());
			this->button4 = (gcnew System::Windows::Forms::Button());
			this->play4_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button5 = (gcnew System::Windows::Forms::Button());
			this->button6 = (gcnew System::Windows::Forms::Button());
			this->button7 = (gcnew System::Windows::Forms::Button());
			this->button8 = (gcnew System::Windows::Forms::Button());
			this->play5_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button9 = (gcnew System::Windows::Forms::Button());
			this->button10 = (gcnew System::Windows::Forms::Button());
			this->button11 = (gcnew System::Windows::Forms::Button());
			this->button12 = (gcnew System::Windows::Forms::Button());
			this->play6_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button13 = (gcnew System::Windows::Forms::Button());
			this->button14 = (gcnew System::Windows::Forms::Button());
			this->button15 = (gcnew System::Windows::Forms::Button());
			this->button16 = (gcnew System::Windows::Forms::Button());
			this->play7_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button29 = (gcnew System::Windows::Forms::Button());
			this->button30 = (gcnew System::Windows::Forms::Button());
			this->button31 = (gcnew System::Windows::Forms::Button());
			this->button32 = (gcnew System::Windows::Forms::Button());
			this->play2_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button17 = (gcnew System::Windows::Forms::Button());
			this->button18 = (gcnew System::Windows::Forms::Button());
			this->button19 = (gcnew System::Windows::Forms::Button());
			this->button20 = (gcnew System::Windows::Forms::Button());
			this->play3_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button21 = (gcnew System::Windows::Forms::Button());
			this->button22 = (gcnew System::Windows::Forms::Button());
			this->button23 = (gcnew System::Windows::Forms::Button());
			this->button24 = (gcnew System::Windows::Forms::Button());
			this->play4_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button33 = (gcnew System::Windows::Forms::Button());
			this->button34 = (gcnew System::Windows::Forms::Button());
			this->button35 = (gcnew System::Windows::Forms::Button());
			this->button36 = (gcnew System::Windows::Forms::Button());
			this->play5_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button37 = (gcnew System::Windows::Forms::Button());
			this->button38 = (gcnew System::Windows::Forms::Button());
			this->button39 = (gcnew System::Windows::Forms::Button());
			this->button40 = (gcnew System::Windows::Forms::Button());
			this->play6_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button41 = (gcnew System::Windows::Forms::Button());
			this->button42 = (gcnew System::Windows::Forms::Button());
			this->button43 = (gcnew System::Windows::Forms::Button());
			this->button44 = (gcnew System::Windows::Forms::Button());
			this->play7_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button45 = (gcnew System::Windows::Forms::Button());
			this->button46 = (gcnew System::Windows::Forms::Button());
			this->button47 = (gcnew System::Windows::Forms::Button());
			this->button48 = (gcnew System::Windows::Forms::Button());
			this->play8_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button49 = (gcnew System::Windows::Forms::Button());
			this->button50 = (gcnew System::Windows::Forms::Button());
			this->button51 = (gcnew System::Windows::Forms::Button());
			this->button52 = (gcnew System::Windows::Forms::Button());
			this->play8_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->button53 = (gcnew System::Windows::Forms::Button());
			this->button54 = (gcnew System::Windows::Forms::Button());
			this->button55 = (gcnew System::Windows::Forms::Button());
			this->button56 = (gcnew System::Windows::Forms::Button());
			this->UserNamePlay = (gcnew System::Windows::Forms::Label());
			this->menuStrip1->SuspendLayout();
			this->play1_groupBox->SuspendLayout();
			this->play1_score_groupBox->SuspendLayout();
			this->play2_groupBox->SuspendLayout();
			this->play3_groupBox->SuspendLayout();
			this->play4_groupBox->SuspendLayout();
			this->play5_groupBox->SuspendLayout();
			this->play6_groupBox->SuspendLayout();
			this->play7_groupBox->SuspendLayout();
			this->play2_score_groupBox->SuspendLayout();
			this->play3_score_groupBox->SuspendLayout();
			this->play4_score_groupBox->SuspendLayout();
			this->play5_score_groupBox->SuspendLayout();
			this->play6_score_groupBox->SuspendLayout();
			this->play7_score_groupBox->SuspendLayout();
			this->play8_groupBox->SuspendLayout();
			this->play8_score_groupBox->SuspendLayout();
			this->SuspendLayout();
			// 
			// red_button
			// 
			this->red_button->BackColor = System::Drawing::Color::Transparent;
			this->red_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->red_button->Enabled = false;
			this->red_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->red_button->Location = System::Drawing::Point(783, 214);
			this->red_button->Margin = System::Windows::Forms::Padding(4);
			this->red_button->Name = L"red_button";
			this->red_button->Size = System::Drawing::Size(67, 55);
			this->red_button->TabIndex = 0;
			this->red_button->Text = L"Red";
			this->red_button->UseVisualStyleBackColor = false;
			this->red_button->Click += gcnew System::EventHandler(this, &VentanaPlay::red_button_Click_1);
			// 
			// blue_button
			// 
			this->blue_button->BackColor = System::Drawing::Color::Transparent;
			this->blue_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->blue_button->Enabled = false;
			this->blue_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->blue_button->Location = System::Drawing::Point(783, 277);
			this->blue_button->Margin = System::Windows::Forms::Padding(4);
			this->blue_button->Name = L"blue_button";
			this->blue_button->Size = System::Drawing::Size(67, 55);
			this->blue_button->TabIndex = 1;
			this->blue_button->Text = L"Blue";
			this->blue_button->UseVisualStyleBackColor = false;
			this->blue_button->Click += gcnew System::EventHandler(this, &VentanaPlay::blue_button_Click);
			// 
			// green_button
			// 
			this->green_button->BackColor = System::Drawing::Color::Transparent;
			this->green_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->green_button->Enabled = false;
			this->green_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->green_button->Location = System::Drawing::Point(783, 340);
			this->green_button->Margin = System::Windows::Forms::Padding(4);
			this->green_button->Name = L"green_button";
			this->green_button->Size = System::Drawing::Size(67, 55);
			this->green_button->TabIndex = 2;
			this->green_button->Text = L"Green";
			this->green_button->UseVisualStyleBackColor = false;
			this->green_button->Click += gcnew System::EventHandler(this, &VentanaPlay::green_button_Click);
			// 
			// yellow_button
			// 
			this->yellow_button->BackColor = System::Drawing::Color::Transparent;
			this->yellow_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->yellow_button->Enabled = false;
			this->yellow_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->yellow_button->Location = System::Drawing::Point(783, 402);
			this->yellow_button->Margin = System::Windows::Forms::Padding(4);
			this->yellow_button->Name = L"yellow_button";
			this->yellow_button->Size = System::Drawing::Size(67, 55);
			this->yellow_button->TabIndex = 3;
			this->yellow_button->Text = L"Yellow";
			this->yellow_button->UseVisualStyleBackColor = false;
			this->yellow_button->Click += gcnew System::EventHandler(this, &VentanaPlay::yellow_button_Click);
			// 
			// pink_button
			// 
			this->pink_button->BackColor = System::Drawing::Color::Transparent;
			this->pink_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->pink_button->Enabled = false;
			this->pink_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->pink_button->Location = System::Drawing::Point(783, 465);
			this->pink_button->Margin = System::Windows::Forms::Padding(4);
			this->pink_button->Name = L"pink_button";
			this->pink_button->Size = System::Drawing::Size(67, 55);
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
			this->brown_button->Location = System::Drawing::Point(783, 528);
			this->brown_button->Margin = System::Windows::Forms::Padding(4);
			this->brown_button->Name = L"brown_button";
			this->brown_button->Size = System::Drawing::Size(67, 55);
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
			this->guess1_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess1_button->Enabled = false;
			this->guess1_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess1_button->Location = System::Drawing::Point(8, 23);
			this->guess1_button->Margin = System::Windows::Forms::Padding(4);
			this->guess1_button->Name = L"guess1_button";
			this->guess1_button->Size = System::Drawing::Size(67, 55);
			this->guess1_button->TabIndex = 14;
			this->guess1_button->Text = L"Guess 1";
			this->guess1_button->UseVisualStyleBackColor = false;
			this->guess1_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess1_button_Click);
			// 
			// guess2_button
			// 
			this->guess2_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess2_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess2_button->Enabled = false;
			this->guess2_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess2_button->Location = System::Drawing::Point(83, 23);
			this->guess2_button->Margin = System::Windows::Forms::Padding(4);
			this->guess2_button->Name = L"guess2_button";
			this->guess2_button->Size = System::Drawing::Size(67, 55);
			this->guess2_button->TabIndex = 15;
			this->guess2_button->Text = L"Guess 2";
			this->guess2_button->UseVisualStyleBackColor = false;
			this->guess2_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess2_button_Click);
			// 
			// guess3_button
			// 
			this->guess3_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess3_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess3_button->Enabled = false;
			this->guess3_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess3_button->Location = System::Drawing::Point(157, 23);
			this->guess3_button->Margin = System::Windows::Forms::Padding(4);
			this->guess3_button->Name = L"guess3_button";
			this->guess3_button->Size = System::Drawing::Size(67, 55);
			this->guess3_button->TabIndex = 16;
			this->guess3_button->Text = L"Guess 3";
			this->guess3_button->UseVisualStyleBackColor = false;
			this->guess3_button->Click += gcnew System::EventHandler(this, &VentanaPlay::guess3_button_Click);
			// 
			// guess4_button
			// 
			this->guess4_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->guess4_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->guess4_button->Enabled = false;
			this->guess4_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->guess4_button->Location = System::Drawing::Point(232, 23);
			this->guess4_button->Margin = System::Windows::Forms::Padding(4);
			this->guess4_button->Name = L"guess4_button";
			this->guess4_button->Size = System::Drawing::Size(67, 55);
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
			this->menuStrip1->Padding = System::Windows::Forms::Padding(5, 2, 0, 2);
			this->menuStrip1->Size = System::Drawing::Size(952, 28);
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
			this->archivoToolStripMenuItem->Size = System::Drawing::Size(46, 24);
			this->archivoToolStripMenuItem->Text = L"File";
			this->archivoToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::archivoToolStripMenuItem_Click);
			// 
			// saveToolStripMenuItem
			// 
			this->saveToolStripMenuItem->Name = L"saveToolStripMenuItem";
			this->saveToolStripMenuItem->Size = System::Drawing::Size(168, 26);
			this->saveToolStripMenuItem->Text = L"Save Game";
			// 
			// loadGameToolStripMenuItem
			// 
			this->loadGameToolStripMenuItem->Name = L"loadGameToolStripMenuItem";
			this->loadGameToolStripMenuItem->Size = System::Drawing::Size(168, 26);
			this->loadGameToolStripMenuItem->Text = L"Load Game";
			// 
			// ayudaToolStripMenuItem
			// 
			this->ayudaToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->instruccionesToolStripMenuItem });
			this->ayudaToolStripMenuItem->Name = L"ayudaToolStripMenuItem";
			this->ayudaToolStripMenuItem->Size = System::Drawing::Size(55, 24);
			this->ayudaToolStripMenuItem->Text = L"Help";
			// 
			// instruccionesToolStripMenuItem
			// 
			this->instruccionesToolStripMenuItem->Name = L"instruccionesToolStripMenuItem";
			this->instruccionesToolStripMenuItem->Size = System::Drawing::Size(173, 26);
			this->instruccionesToolStripMenuItem->Text = L"How to play";
			// 
			// salirToolStripMenuItem
			// 
			this->salirToolStripMenuItem->Name = L"salirToolStripMenuItem";
			this->salirToolStripMenuItem->Size = System::Drawing::Size(93, 24);
			this->salirToolStripMenuItem->Text = L"Quit game";
			this->salirToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::salirToolStripMenuItem_Click);
			// 
			// titulo_label
			// 
			this->titulo_label->BackColor = System::Drawing::Color::OrangeRed;
			this->titulo_label->BorderStyle = System::Windows::Forms::BorderStyle::FixedSingle;
			this->titulo_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 26.25F, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->titulo_label->ForeColor = System::Drawing::Color::Yellow;
			this->titulo_label->Location = System::Drawing::Point(16, 41);
			this->titulo_label->Margin = System::Windows::Forms::Padding(4, 0, 4, 0);
			this->titulo_label->Name = L"titulo_label";
			this->titulo_label->Size = System::Drawing::Size(274, 50);
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
			this->Time->Location = System::Drawing::Point(19, 666);
			this->Time->Margin = System::Windows::Forms::Padding(4, 0, 4, 0);
			this->Time->Name = L"Time";
			this->Time->Size = System::Drawing::Size(199, 52);
			this->Time->TabIndex = 21;
			this->Time->Text = L"00:00:00";
			this->Time->Click += gcnew System::EventHandler(this, &VentanaPlay::label2_Click);
			// 
			// Vent_Play_Start
			// 
			this->Vent_Play_Start->AutoSize = true;
			this->Vent_Play_Start->Location = System::Drawing::Point(16, 721);
			this->Vent_Play_Start->Margin = System::Windows::Forms::Padding(4);
			this->Vent_Play_Start->Name = L"Vent_Play_Start";
			this->Vent_Play_Start->Size = System::Drawing::Size(215, 66);
			this->Vent_Play_Start->TabIndex = 22;
			this->Vent_Play_Start->Text = L"Start";
			this->Vent_Play_Start->UseVisualStyleBackColor = true;
			this->Vent_Play_Start->Click += gcnew System::EventHandler(this, &VentanaPlay::Vent_Play_Start_Click);
			// 
			// play1_groupBox
			// 
			this->play1_groupBox->Controls->Add(this->guess1_button);
			this->play1_groupBox->Controls->Add(this->guess2_button);
			this->play1_groupBox->Controls->Add(this->guess3_button);
			this->play1_groupBox->Controls->Add(this->guess4_button);
			this->play1_groupBox->Location = System::Drawing::Point(321, 695);
			this->play1_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play1_groupBox->Name = L"play1_groupBox";
			this->play1_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play1_groupBox->Size = System::Drawing::Size(312, 92);
			this->play1_groupBox->TabIndex = 23;
			this->play1_groupBox->TabStop = false;
			this->play1_groupBox->Text = L"Play 1";
			// 
			// play_score_btn4
			// 
			this->play_score_btn4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn4->Enabled = false;
			this->play_score_btn4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn4->Location = System::Drawing::Point(49, 54);
			this->play_score_btn4->Margin = System::Windows::Forms::Padding(4);
			this->play_score_btn4->Name = L"play_score_btn4";
			this->play_score_btn4->Size = System::Drawing::Size(33, 31);
			this->play_score_btn4->TabIndex = 24;
			this->play_score_btn4->UseVisualStyleBackColor = true;
			// 
			// play_score_btn1
			// 
			this->play_score_btn1->BackColor = System::Drawing::Color::Sienna;
			this->play_score_btn1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn1->Enabled = false;
			this->play_score_btn1->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn1->Location = System::Drawing::Point(8, 16);
			this->play_score_btn1->Margin = System::Windows::Forms::Padding(4);
			this->play_score_btn1->Name = L"play_score_btn1";
			this->play_score_btn1->Size = System::Drawing::Size(33, 31);
			this->play_score_btn1->TabIndex = 25;
			this->play_score_btn1->UseVisualStyleBackColor = false;
			// 
			// play_score_btn2
			// 
			this->play_score_btn2->BackColor = System::Drawing::Color::Sienna;
			this->play_score_btn2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn2->Enabled = false;
			this->play_score_btn2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn2->Location = System::Drawing::Point(49, 16);
			this->play_score_btn2->Margin = System::Windows::Forms::Padding(4);
			this->play_score_btn2->Name = L"play_score_btn2";
			this->play_score_btn2->Size = System::Drawing::Size(33, 31);
			this->play_score_btn2->TabIndex = 26;
			this->play_score_btn2->UseVisualStyleBackColor = false;
			// 
			// play_score_btn3
			// 
			this->play_score_btn3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play_score_btn3->Enabled = false;
			this->play_score_btn3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play_score_btn3->Location = System::Drawing::Point(8, 54);
			this->play_score_btn3->Margin = System::Windows::Forms::Padding(4);
			this->play_score_btn3->Name = L"play_score_btn3";
			this->play_score_btn3->Size = System::Drawing::Size(33, 31);
			this->play_score_btn3->TabIndex = 27;
			this->play_score_btn3->UseVisualStyleBackColor = true;
			// 
			// play1_score_groupBox
			// 
			this->play1_score_groupBox->Controls->Add(this->play_score_btn1);
			this->play1_score_groupBox->Controls->Add(this->play_score_btn4);
			this->play1_score_groupBox->Controls->Add(this->play_score_btn3);
			this->play1_score_groupBox->Controls->Add(this->play_score_btn2);
			this->play1_score_groupBox->Location = System::Drawing::Point(641, 695);
			this->play1_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play1_score_groupBox->Name = L"play1_score_groupBox";
			this->play1_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play1_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play1_score_groupBox->TabIndex = 28;
			this->play1_score_groupBox->TabStop = false;
			// 
			// black_button
			// 
			this->black_button->BackColor = System::Drawing::Color::Sienna;
			this->black_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->black_button->Enabled = false;
			this->black_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->black_button->Location = System::Drawing::Point(768, 750);
			this->black_button->Margin = System::Windows::Forms::Padding(4);
			this->black_button->Name = L"black_button";
			this->black_button->Size = System::Drawing::Size(33, 31);
			this->black_button->TabIndex = 28;
			this->black_button->UseVisualStyleBackColor = false;
			// 
			// white_button
			// 
			this->white_button->BackColor = System::Drawing::Color::Sienna;
			this->white_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->white_button->Enabled = false;
			this->white_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->white_button->Location = System::Drawing::Point(768, 711);
			this->white_button->Margin = System::Windows::Forms::Padding(4);
			this->white_button->Name = L"white_button";
			this->white_button->Size = System::Drawing::Size(33, 31);
			this->white_button->TabIndex = 29;
			this->white_button->UseVisualStyleBackColor = false;
			// 
			// color_wbtn_label
			// 
			this->color_wbtn_label->AutoSize = true;
			this->color_wbtn_label->Location = System::Drawing::Point(809, 719);
			this->color_wbtn_label->Margin = System::Windows::Forms::Padding(4, 0, 4, 0);
			this->color_wbtn_label->Name = L"color_wbtn_label";
			this->color_wbtn_label->Size = System::Drawing::Size(39, 17);
			this->color_wbtn_label->TabIndex = 30;
			this->color_wbtn_label->Text = L"color";
			this->color_wbtn_label->Click += gcnew System::EventHandler(this, &VentanaPlay::color_wbtn_label_Click);
			// 
			// color_position_bbtn_label
			// 
			this->color_position_bbtn_label->AutoSize = true;
			this->color_position_bbtn_label->Location = System::Drawing::Point(809, 757);
			this->color_position_bbtn_label->Margin = System::Windows::Forms::Padding(4, 0, 4, 0);
			this->color_position_bbtn_label->Name = L"color_position_bbtn_label";
			this->color_position_bbtn_label->Size = System::Drawing::Size(120, 17);
			this->color_position_bbtn_label->TabIndex = 31;
			this->color_position_bbtn_label->Text = L"color and position";
			this->color_position_bbtn_label->Click += gcnew System::EventHandler(this, &VentanaPlay::color_position_bbtn_label_Click);
			// 
			// enter_play_button
			// 
			this->enter_play_button->Enabled = false;
			this->enter_play_button->Location = System::Drawing::Point(79, 612);
			this->enter_play_button->Margin = System::Windows::Forms::Padding(4);
			this->enter_play_button->Name = L"enter_play_button";
			this->enter_play_button->Size = System::Drawing::Size(100, 28);
			this->enter_play_button->TabIndex = 32;
			this->enter_play_button->Text = L"Enter Play";
			this->enter_play_button->UseVisualStyleBackColor = true;
			this->enter_play_button->Click += gcnew System::EventHandler(this, &VentanaPlay::enter_play_button_Click);
			// 
			// play2_groupBox
			// 
			this->play2_groupBox->Controls->Add(this->button25);
			this->play2_groupBox->Controls->Add(this->button26);
			this->play2_groupBox->Controls->Add(this->button27);
			this->play2_groupBox->Controls->Add(this->button28);
			this->play2_groupBox->Location = System::Drawing::Point(321, 603);
			this->play2_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play2_groupBox->Name = L"play2_groupBox";
			this->play2_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play2_groupBox->Size = System::Drawing::Size(312, 92);
			this->play2_groupBox->TabIndex = 24;
			this->play2_groupBox->TabStop = false;
			this->play2_groupBox->Text = L"Play 2";
			// 
			// button25
			// 
			this->button25->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button25->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button25->Enabled = false;
			this->button25->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button25->Location = System::Drawing::Point(8, 23);
			this->button25->Margin = System::Windows::Forms::Padding(4);
			this->button25->Name = L"button25";
			this->button25->Size = System::Drawing::Size(67, 55);
			this->button25->TabIndex = 14;
			this->button25->Text = L"Guess 1";
			this->button25->UseVisualStyleBackColor = false;
			// 
			// button26
			// 
			this->button26->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button26->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button26->Enabled = false;
			this->button26->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button26->Location = System::Drawing::Point(83, 23);
			this->button26->Margin = System::Windows::Forms::Padding(4);
			this->button26->Name = L"button26";
			this->button26->Size = System::Drawing::Size(67, 55);
			this->button26->TabIndex = 15;
			this->button26->Text = L"Guess 2";
			this->button26->UseVisualStyleBackColor = false;
			// 
			// button27
			// 
			this->button27->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button27->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button27->Enabled = false;
			this->button27->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button27->Location = System::Drawing::Point(157, 23);
			this->button27->Margin = System::Windows::Forms::Padding(4);
			this->button27->Name = L"button27";
			this->button27->Size = System::Drawing::Size(67, 55);
			this->button27->TabIndex = 16;
			this->button27->Text = L"Guess 3";
			this->button27->UseVisualStyleBackColor = false;
			// 
			// button28
			// 
			this->button28->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button28->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button28->Enabled = false;
			this->button28->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button28->Location = System::Drawing::Point(232, 23);
			this->button28->Margin = System::Windows::Forms::Padding(4);
			this->button28->Name = L"button28";
			this->button28->Size = System::Drawing::Size(67, 55);
			this->button28->TabIndex = 17;
			this->button28->Text = L"Guess 4";
			this->button28->UseVisualStyleBackColor = false;
			// 
			// play3_groupBox
			// 
			this->play3_groupBox->Controls->Add(this->button1);
			this->play3_groupBox->Controls->Add(this->button2);
			this->play3_groupBox->Controls->Add(this->button3);
			this->play3_groupBox->Controls->Add(this->button4);
			this->play3_groupBox->Location = System::Drawing::Point(321, 511);
			this->play3_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play3_groupBox->Name = L"play3_groupBox";
			this->play3_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play3_groupBox->Size = System::Drawing::Size(312, 92);
			this->play3_groupBox->TabIndex = 24;
			this->play3_groupBox->TabStop = false;
			this->play3_groupBox->Text = L"Play 3";
			// 
			// button1
			// 
			this->button1->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button1->Enabled = false;
			this->button1->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button1->Location = System::Drawing::Point(8, 23);
			this->button1->Margin = System::Windows::Forms::Padding(4);
			this->button1->Name = L"button1";
			this->button1->Size = System::Drawing::Size(67, 55);
			this->button1->TabIndex = 14;
			this->button1->Text = L"Guess 1";
			this->button1->UseVisualStyleBackColor = false;
			// 
			// button2
			// 
			this->button2->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button2->Enabled = false;
			this->button2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button2->Location = System::Drawing::Point(83, 23);
			this->button2->Margin = System::Windows::Forms::Padding(4);
			this->button2->Name = L"button2";
			this->button2->Size = System::Drawing::Size(67, 55);
			this->button2->TabIndex = 15;
			this->button2->Text = L"Guess 2";
			this->button2->UseVisualStyleBackColor = false;
			// 
			// button3
			// 
			this->button3->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button3->Enabled = false;
			this->button3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button3->Location = System::Drawing::Point(157, 23);
			this->button3->Margin = System::Windows::Forms::Padding(4);
			this->button3->Name = L"button3";
			this->button3->Size = System::Drawing::Size(67, 55);
			this->button3->TabIndex = 16;
			this->button3->Text = L"Guess 3";
			this->button3->UseVisualStyleBackColor = false;
			// 
			// button4
			// 
			this->button4->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button4->Enabled = false;
			this->button4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button4->Location = System::Drawing::Point(232, 23);
			this->button4->Margin = System::Windows::Forms::Padding(4);
			this->button4->Name = L"button4";
			this->button4->Size = System::Drawing::Size(67, 55);
			this->button4->TabIndex = 17;
			this->button4->Text = L"Guess 4";
			this->button4->UseVisualStyleBackColor = false;
			// 
			// play4_groupBox
			// 
			this->play4_groupBox->Controls->Add(this->button5);
			this->play4_groupBox->Controls->Add(this->button6);
			this->play4_groupBox->Controls->Add(this->button7);
			this->play4_groupBox->Controls->Add(this->button8);
			this->play4_groupBox->Location = System::Drawing::Point(321, 418);
			this->play4_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play4_groupBox->Name = L"play4_groupBox";
			this->play4_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play4_groupBox->Size = System::Drawing::Size(312, 92);
			this->play4_groupBox->TabIndex = 25;
			this->play4_groupBox->TabStop = false;
			this->play4_groupBox->Text = L"Play 4";
			// 
			// button5
			// 
			this->button5->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button5->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button5->Enabled = false;
			this->button5->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button5->Location = System::Drawing::Point(8, 23);
			this->button5->Margin = System::Windows::Forms::Padding(4);
			this->button5->Name = L"button5";
			this->button5->Size = System::Drawing::Size(67, 55);
			this->button5->TabIndex = 14;
			this->button5->Text = L"Guess 1";
			this->button5->UseVisualStyleBackColor = false;
			// 
			// button6
			// 
			this->button6->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button6->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button6->Enabled = false;
			this->button6->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button6->Location = System::Drawing::Point(83, 23);
			this->button6->Margin = System::Windows::Forms::Padding(4);
			this->button6->Name = L"button6";
			this->button6->Size = System::Drawing::Size(67, 55);
			this->button6->TabIndex = 15;
			this->button6->Text = L"Guess 2";
			this->button6->UseVisualStyleBackColor = false;
			// 
			// button7
			// 
			this->button7->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button7->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button7->Enabled = false;
			this->button7->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button7->Location = System::Drawing::Point(157, 23);
			this->button7->Margin = System::Windows::Forms::Padding(4);
			this->button7->Name = L"button7";
			this->button7->Size = System::Drawing::Size(67, 55);
			this->button7->TabIndex = 16;
			this->button7->Text = L"Guess 3";
			this->button7->UseVisualStyleBackColor = false;
			// 
			// button8
			// 
			this->button8->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button8->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button8->Enabled = false;
			this->button8->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button8->Location = System::Drawing::Point(232, 23);
			this->button8->Margin = System::Windows::Forms::Padding(4);
			this->button8->Name = L"button8";
			this->button8->Size = System::Drawing::Size(67, 55);
			this->button8->TabIndex = 17;
			this->button8->Text = L"Guess 4";
			this->button8->UseVisualStyleBackColor = false;
			// 
			// play5_groupBox
			// 
			this->play5_groupBox->Controls->Add(this->button9);
			this->play5_groupBox->Controls->Add(this->button10);
			this->play5_groupBox->Controls->Add(this->button11);
			this->play5_groupBox->Controls->Add(this->button12);
			this->play5_groupBox->Location = System::Drawing::Point(321, 326);
			this->play5_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play5_groupBox->Name = L"play5_groupBox";
			this->play5_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play5_groupBox->Size = System::Drawing::Size(312, 92);
			this->play5_groupBox->TabIndex = 26;
			this->play5_groupBox->TabStop = false;
			this->play5_groupBox->Text = L"Play 5";
			// 
			// button9
			// 
			this->button9->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button9->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button9->Enabled = false;
			this->button9->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button9->Location = System::Drawing::Point(8, 23);
			this->button9->Margin = System::Windows::Forms::Padding(4);
			this->button9->Name = L"button9";
			this->button9->Size = System::Drawing::Size(67, 55);
			this->button9->TabIndex = 14;
			this->button9->Text = L"Guess 1";
			this->button9->UseVisualStyleBackColor = false;
			// 
			// button10
			// 
			this->button10->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button10->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button10->Enabled = false;
			this->button10->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button10->Location = System::Drawing::Point(83, 23);
			this->button10->Margin = System::Windows::Forms::Padding(4);
			this->button10->Name = L"button10";
			this->button10->Size = System::Drawing::Size(67, 55);
			this->button10->TabIndex = 15;
			this->button10->Text = L"Guess 2";
			this->button10->UseVisualStyleBackColor = false;
			// 
			// button11
			// 
			this->button11->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button11->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button11->Enabled = false;
			this->button11->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button11->Location = System::Drawing::Point(157, 23);
			this->button11->Margin = System::Windows::Forms::Padding(4);
			this->button11->Name = L"button11";
			this->button11->Size = System::Drawing::Size(67, 55);
			this->button11->TabIndex = 16;
			this->button11->Text = L"Guess 3";
			this->button11->UseVisualStyleBackColor = false;
			// 
			// button12
			// 
			this->button12->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button12->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button12->Enabled = false;
			this->button12->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button12->Location = System::Drawing::Point(232, 23);
			this->button12->Margin = System::Windows::Forms::Padding(4);
			this->button12->Name = L"button12";
			this->button12->Size = System::Drawing::Size(67, 55);
			this->button12->TabIndex = 17;
			this->button12->Text = L"Guess 4";
			this->button12->UseVisualStyleBackColor = false;
			// 
			// play6_groupBox
			// 
			this->play6_groupBox->Controls->Add(this->button13);
			this->play6_groupBox->Controls->Add(this->button14);
			this->play6_groupBox->Controls->Add(this->button15);
			this->play6_groupBox->Controls->Add(this->button16);
			this->play6_groupBox->Location = System::Drawing::Point(321, 234);
			this->play6_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play6_groupBox->Name = L"play6_groupBox";
			this->play6_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play6_groupBox->Size = System::Drawing::Size(312, 92);
			this->play6_groupBox->TabIndex = 27;
			this->play6_groupBox->TabStop = false;
			this->play6_groupBox->Text = L"Play 6";
			// 
			// button13
			// 
			this->button13->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button13->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button13->Enabled = false;
			this->button13->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button13->Location = System::Drawing::Point(8, 23);
			this->button13->Margin = System::Windows::Forms::Padding(4);
			this->button13->Name = L"button13";
			this->button13->Size = System::Drawing::Size(67, 55);
			this->button13->TabIndex = 14;
			this->button13->Text = L"Guess 1";
			this->button13->UseVisualStyleBackColor = false;
			// 
			// button14
			// 
			this->button14->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button14->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button14->Enabled = false;
			this->button14->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button14->Location = System::Drawing::Point(83, 23);
			this->button14->Margin = System::Windows::Forms::Padding(4);
			this->button14->Name = L"button14";
			this->button14->Size = System::Drawing::Size(67, 55);
			this->button14->TabIndex = 15;
			this->button14->Text = L"Guess 2";
			this->button14->UseVisualStyleBackColor = false;
			// 
			// button15
			// 
			this->button15->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button15->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button15->Enabled = false;
			this->button15->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button15->Location = System::Drawing::Point(157, 23);
			this->button15->Margin = System::Windows::Forms::Padding(4);
			this->button15->Name = L"button15";
			this->button15->Size = System::Drawing::Size(67, 55);
			this->button15->TabIndex = 16;
			this->button15->Text = L"Guess 3";
			this->button15->UseVisualStyleBackColor = false;
			// 
			// button16
			// 
			this->button16->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button16->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button16->Enabled = false;
			this->button16->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button16->Location = System::Drawing::Point(232, 23);
			this->button16->Margin = System::Windows::Forms::Padding(4);
			this->button16->Name = L"button16";
			this->button16->Size = System::Drawing::Size(67, 55);
			this->button16->TabIndex = 17;
			this->button16->Text = L"Guess 4";
			this->button16->UseVisualStyleBackColor = false;
			// 
			// play7_groupBox
			// 
			this->play7_groupBox->Controls->Add(this->button29);
			this->play7_groupBox->Controls->Add(this->button30);
			this->play7_groupBox->Controls->Add(this->button31);
			this->play7_groupBox->Controls->Add(this->button32);
			this->play7_groupBox->Enabled = false;
			this->play7_groupBox->Location = System::Drawing::Point(321, 142);
			this->play7_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play7_groupBox->Name = L"play7_groupBox";
			this->play7_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play7_groupBox->Size = System::Drawing::Size(312, 92);
			this->play7_groupBox->TabIndex = 28;
			this->play7_groupBox->TabStop = false;
			this->play7_groupBox->Text = L"Play 7";
			this->play7_groupBox->Visible = false;
			this->play7_groupBox->Enter += gcnew System::EventHandler(this, &VentanaPlay::play7_groupBox_Enter);
			// 
			// button29
			// 
			this->button29->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button29->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button29->Enabled = false;
			this->button29->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button29->Location = System::Drawing::Point(8, 23);
			this->button29->Margin = System::Windows::Forms::Padding(4);
			this->button29->Name = L"button29";
			this->button29->Size = System::Drawing::Size(67, 55);
			this->button29->TabIndex = 14;
			this->button29->Text = L"Guess 1";
			this->button29->UseVisualStyleBackColor = false;
			// 
			// button30
			// 
			this->button30->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button30->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button30->Enabled = false;
			this->button30->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button30->Location = System::Drawing::Point(83, 23);
			this->button30->Margin = System::Windows::Forms::Padding(4);
			this->button30->Name = L"button30";
			this->button30->Size = System::Drawing::Size(67, 55);
			this->button30->TabIndex = 15;
			this->button30->Text = L"Guess 2";
			this->button30->UseVisualStyleBackColor = false;
			// 
			// button31
			// 
			this->button31->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button31->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button31->Enabled = false;
			this->button31->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button31->Location = System::Drawing::Point(157, 23);
			this->button31->Margin = System::Windows::Forms::Padding(4);
			this->button31->Name = L"button31";
			this->button31->Size = System::Drawing::Size(67, 55);
			this->button31->TabIndex = 16;
			this->button31->Text = L"Guess 3";
			this->button31->UseVisualStyleBackColor = false;
			// 
			// button32
			// 
			this->button32->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button32->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button32->Enabled = false;
			this->button32->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button32->Location = System::Drawing::Point(232, 23);
			this->button32->Margin = System::Windows::Forms::Padding(4);
			this->button32->Name = L"button32";
			this->button32->Size = System::Drawing::Size(67, 55);
			this->button32->TabIndex = 17;
			this->button32->Text = L"Guess 4";
			this->button32->UseVisualStyleBackColor = false;
			// 
			// play2_score_groupBox
			// 
			this->play2_score_groupBox->Controls->Add(this->button17);
			this->play2_score_groupBox->Controls->Add(this->button18);
			this->play2_score_groupBox->Controls->Add(this->button19);
			this->play2_score_groupBox->Controls->Add(this->button20);
			this->play2_score_groupBox->Location = System::Drawing::Point(641, 603);
			this->play2_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play2_score_groupBox->Name = L"play2_score_groupBox";
			this->play2_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play2_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play2_score_groupBox->TabIndex = 29;
			this->play2_score_groupBox->TabStop = false;
			// 
			// button17
			// 
			this->button17->BackColor = System::Drawing::Color::Sienna;
			this->button17->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button17->Enabled = false;
			this->button17->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button17->Location = System::Drawing::Point(8, 16);
			this->button17->Margin = System::Windows::Forms::Padding(4);
			this->button17->Name = L"button17";
			this->button17->Size = System::Drawing::Size(33, 31);
			this->button17->TabIndex = 25;
			this->button17->UseVisualStyleBackColor = false;
			// 
			// button18
			// 
			this->button18->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button18->Enabled = false;
			this->button18->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button18->Location = System::Drawing::Point(49, 54);
			this->button18->Margin = System::Windows::Forms::Padding(4);
			this->button18->Name = L"button18";
			this->button18->Size = System::Drawing::Size(33, 31);
			this->button18->TabIndex = 24;
			this->button18->UseVisualStyleBackColor = true;
			// 
			// button19
			// 
			this->button19->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button19->Enabled = false;
			this->button19->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button19->Location = System::Drawing::Point(8, 54);
			this->button19->Margin = System::Windows::Forms::Padding(4);
			this->button19->Name = L"button19";
			this->button19->Size = System::Drawing::Size(33, 31);
			this->button19->TabIndex = 27;
			this->button19->UseVisualStyleBackColor = true;
			// 
			// button20
			// 
			this->button20->BackColor = System::Drawing::Color::Sienna;
			this->button20->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button20->Enabled = false;
			this->button20->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button20->Location = System::Drawing::Point(49, 16);
			this->button20->Margin = System::Windows::Forms::Padding(4);
			this->button20->Name = L"button20";
			this->button20->Size = System::Drawing::Size(33, 31);
			this->button20->TabIndex = 26;
			this->button20->UseVisualStyleBackColor = false;
			// 
			// play3_score_groupBox
			// 
			this->play3_score_groupBox->Controls->Add(this->button21);
			this->play3_score_groupBox->Controls->Add(this->button22);
			this->play3_score_groupBox->Controls->Add(this->button23);
			this->play3_score_groupBox->Controls->Add(this->button24);
			this->play3_score_groupBox->Location = System::Drawing::Point(641, 511);
			this->play3_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play3_score_groupBox->Name = L"play3_score_groupBox";
			this->play3_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play3_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play3_score_groupBox->TabIndex = 29;
			this->play3_score_groupBox->TabStop = false;
			// 
			// button21
			// 
			this->button21->BackColor = System::Drawing::Color::Sienna;
			this->button21->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button21->Enabled = false;
			this->button21->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button21->Location = System::Drawing::Point(8, 16);
			this->button21->Margin = System::Windows::Forms::Padding(4);
			this->button21->Name = L"button21";
			this->button21->Size = System::Drawing::Size(33, 31);
			this->button21->TabIndex = 25;
			this->button21->UseVisualStyleBackColor = false;
			// 
			// button22
			// 
			this->button22->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button22->Enabled = false;
			this->button22->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button22->Location = System::Drawing::Point(49, 54);
			this->button22->Margin = System::Windows::Forms::Padding(4);
			this->button22->Name = L"button22";
			this->button22->Size = System::Drawing::Size(33, 31);
			this->button22->TabIndex = 24;
			this->button22->UseVisualStyleBackColor = true;
			// 
			// button23
			// 
			this->button23->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button23->Enabled = false;
			this->button23->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button23->Location = System::Drawing::Point(8, 54);
			this->button23->Margin = System::Windows::Forms::Padding(4);
			this->button23->Name = L"button23";
			this->button23->Size = System::Drawing::Size(33, 31);
			this->button23->TabIndex = 27;
			this->button23->UseVisualStyleBackColor = true;
			// 
			// button24
			// 
			this->button24->BackColor = System::Drawing::Color::Sienna;
			this->button24->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button24->Enabled = false;
			this->button24->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button24->Location = System::Drawing::Point(49, 16);
			this->button24->Margin = System::Windows::Forms::Padding(4);
			this->button24->Name = L"button24";
			this->button24->Size = System::Drawing::Size(33, 31);
			this->button24->TabIndex = 26;
			this->button24->UseVisualStyleBackColor = false;
			// 
			// play4_score_groupBox
			// 
			this->play4_score_groupBox->Controls->Add(this->button33);
			this->play4_score_groupBox->Controls->Add(this->button34);
			this->play4_score_groupBox->Controls->Add(this->button35);
			this->play4_score_groupBox->Controls->Add(this->button36);
			this->play4_score_groupBox->Location = System::Drawing::Point(641, 418);
			this->play4_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play4_score_groupBox->Name = L"play4_score_groupBox";
			this->play4_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play4_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play4_score_groupBox->TabIndex = 29;
			this->play4_score_groupBox->TabStop = false;
			// 
			// button33
			// 
			this->button33->BackColor = System::Drawing::Color::Sienna;
			this->button33->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button33->Enabled = false;
			this->button33->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button33->Location = System::Drawing::Point(8, 16);
			this->button33->Margin = System::Windows::Forms::Padding(4);
			this->button33->Name = L"button33";
			this->button33->Size = System::Drawing::Size(33, 31);
			this->button33->TabIndex = 25;
			this->button33->UseVisualStyleBackColor = false;
			// 
			// button34
			// 
			this->button34->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button34->Enabled = false;
			this->button34->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button34->Location = System::Drawing::Point(49, 54);
			this->button34->Margin = System::Windows::Forms::Padding(4);
			this->button34->Name = L"button34";
			this->button34->Size = System::Drawing::Size(33, 31);
			this->button34->TabIndex = 24;
			this->button34->UseVisualStyleBackColor = true;
			// 
			// button35
			// 
			this->button35->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button35->Enabled = false;
			this->button35->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button35->Location = System::Drawing::Point(8, 54);
			this->button35->Margin = System::Windows::Forms::Padding(4);
			this->button35->Name = L"button35";
			this->button35->Size = System::Drawing::Size(33, 31);
			this->button35->TabIndex = 27;
			this->button35->UseVisualStyleBackColor = true;
			// 
			// button36
			// 
			this->button36->BackColor = System::Drawing::Color::Sienna;
			this->button36->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button36->Enabled = false;
			this->button36->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button36->Location = System::Drawing::Point(49, 16);
			this->button36->Margin = System::Windows::Forms::Padding(4);
			this->button36->Name = L"button36";
			this->button36->Size = System::Drawing::Size(33, 31);
			this->button36->TabIndex = 26;
			this->button36->UseVisualStyleBackColor = false;
			// 
			// play5_score_groupBox
			// 
			this->play5_score_groupBox->Controls->Add(this->button37);
			this->play5_score_groupBox->Controls->Add(this->button38);
			this->play5_score_groupBox->Controls->Add(this->button39);
			this->play5_score_groupBox->Controls->Add(this->button40);
			this->play5_score_groupBox->Location = System::Drawing::Point(641, 326);
			this->play5_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play5_score_groupBox->Name = L"play5_score_groupBox";
			this->play5_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play5_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play5_score_groupBox->TabIndex = 29;
			this->play5_score_groupBox->TabStop = false;
			// 
			// button37
			// 
			this->button37->BackColor = System::Drawing::Color::Sienna;
			this->button37->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button37->Enabled = false;
			this->button37->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button37->Location = System::Drawing::Point(8, 16);
			this->button37->Margin = System::Windows::Forms::Padding(4);
			this->button37->Name = L"button37";
			this->button37->Size = System::Drawing::Size(33, 31);
			this->button37->TabIndex = 25;
			this->button37->UseVisualStyleBackColor = false;
			// 
			// button38
			// 
			this->button38->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button38->Enabled = false;
			this->button38->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button38->Location = System::Drawing::Point(49, 54);
			this->button38->Margin = System::Windows::Forms::Padding(4);
			this->button38->Name = L"button38";
			this->button38->Size = System::Drawing::Size(33, 31);
			this->button38->TabIndex = 24;
			this->button38->UseVisualStyleBackColor = true;
			// 
			// button39
			// 
			this->button39->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button39->Enabled = false;
			this->button39->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button39->Location = System::Drawing::Point(8, 54);
			this->button39->Margin = System::Windows::Forms::Padding(4);
			this->button39->Name = L"button39";
			this->button39->Size = System::Drawing::Size(33, 31);
			this->button39->TabIndex = 27;
			this->button39->UseVisualStyleBackColor = true;
			// 
			// button40
			// 
			this->button40->BackColor = System::Drawing::Color::Sienna;
			this->button40->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button40->Enabled = false;
			this->button40->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button40->Location = System::Drawing::Point(49, 16);
			this->button40->Margin = System::Windows::Forms::Padding(4);
			this->button40->Name = L"button40";
			this->button40->Size = System::Drawing::Size(33, 31);
			this->button40->TabIndex = 26;
			this->button40->UseVisualStyleBackColor = false;
			// 
			// play6_score_groupBox
			// 
			this->play6_score_groupBox->Controls->Add(this->button41);
			this->play6_score_groupBox->Controls->Add(this->button42);
			this->play6_score_groupBox->Controls->Add(this->button43);
			this->play6_score_groupBox->Controls->Add(this->button44);
			this->play6_score_groupBox->Location = System::Drawing::Point(641, 234);
			this->play6_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play6_score_groupBox->Name = L"play6_score_groupBox";
			this->play6_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play6_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play6_score_groupBox->TabIndex = 29;
			this->play6_score_groupBox->TabStop = false;
			// 
			// button41
			// 
			this->button41->BackColor = System::Drawing::Color::Sienna;
			this->button41->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button41->Enabled = false;
			this->button41->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button41->Location = System::Drawing::Point(8, 16);
			this->button41->Margin = System::Windows::Forms::Padding(4);
			this->button41->Name = L"button41";
			this->button41->Size = System::Drawing::Size(33, 31);
			this->button41->TabIndex = 25;
			this->button41->UseVisualStyleBackColor = false;
			// 
			// button42
			// 
			this->button42->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button42->Enabled = false;
			this->button42->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button42->Location = System::Drawing::Point(49, 54);
			this->button42->Margin = System::Windows::Forms::Padding(4);
			this->button42->Name = L"button42";
			this->button42->Size = System::Drawing::Size(33, 31);
			this->button42->TabIndex = 24;
			this->button42->UseVisualStyleBackColor = true;
			// 
			// button43
			// 
			this->button43->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button43->Enabled = false;
			this->button43->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button43->Location = System::Drawing::Point(8, 54);
			this->button43->Margin = System::Windows::Forms::Padding(4);
			this->button43->Name = L"button43";
			this->button43->Size = System::Drawing::Size(33, 31);
			this->button43->TabIndex = 27;
			this->button43->UseVisualStyleBackColor = true;
			// 
			// button44
			// 
			this->button44->BackColor = System::Drawing::Color::Sienna;
			this->button44->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button44->Enabled = false;
			this->button44->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button44->Location = System::Drawing::Point(49, 16);
			this->button44->Margin = System::Windows::Forms::Padding(4);
			this->button44->Name = L"button44";
			this->button44->Size = System::Drawing::Size(33, 31);
			this->button44->TabIndex = 26;
			this->button44->UseVisualStyleBackColor = false;
			// 
			// play7_score_groupBox
			// 
			this->play7_score_groupBox->Controls->Add(this->button45);
			this->play7_score_groupBox->Controls->Add(this->button46);
			this->play7_score_groupBox->Controls->Add(this->button47);
			this->play7_score_groupBox->Controls->Add(this->button48);
			this->play7_score_groupBox->Enabled = false;
			this->play7_score_groupBox->Location = System::Drawing::Point(641, 142);
			this->play7_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play7_score_groupBox->Name = L"play7_score_groupBox";
			this->play7_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play7_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play7_score_groupBox->TabIndex = 29;
			this->play7_score_groupBox->TabStop = false;
			this->play7_score_groupBox->Visible = false;
			// 
			// button45
			// 
			this->button45->BackColor = System::Drawing::Color::Sienna;
			this->button45->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button45->Enabled = false;
			this->button45->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button45->Location = System::Drawing::Point(8, 16);
			this->button45->Margin = System::Windows::Forms::Padding(4);
			this->button45->Name = L"button45";
			this->button45->Size = System::Drawing::Size(33, 31);
			this->button45->TabIndex = 25;
			this->button45->UseVisualStyleBackColor = false;
			// 
			// button46
			// 
			this->button46->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button46->Enabled = false;
			this->button46->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button46->Location = System::Drawing::Point(49, 54);
			this->button46->Margin = System::Windows::Forms::Padding(4);
			this->button46->Name = L"button46";
			this->button46->Size = System::Drawing::Size(33, 31);
			this->button46->TabIndex = 24;
			this->button46->UseVisualStyleBackColor = true;
			// 
			// button47
			// 
			this->button47->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button47->Enabled = false;
			this->button47->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button47->Location = System::Drawing::Point(8, 54);
			this->button47->Margin = System::Windows::Forms::Padding(4);
			this->button47->Name = L"button47";
			this->button47->Size = System::Drawing::Size(33, 31);
			this->button47->TabIndex = 27;
			this->button47->UseVisualStyleBackColor = true;
			// 
			// button48
			// 
			this->button48->BackColor = System::Drawing::Color::Sienna;
			this->button48->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button48->Enabled = false;
			this->button48->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button48->Location = System::Drawing::Point(49, 16);
			this->button48->Margin = System::Windows::Forms::Padding(4);
			this->button48->Name = L"button48";
			this->button48->Size = System::Drawing::Size(33, 31);
			this->button48->TabIndex = 26;
			this->button48->UseVisualStyleBackColor = false;
			// 
			// play8_groupBox
			// 
			this->play8_groupBox->Controls->Add(this->button49);
			this->play8_groupBox->Controls->Add(this->button50);
			this->play8_groupBox->Controls->Add(this->button51);
			this->play8_groupBox->Controls->Add(this->button52);
			this->play8_groupBox->Enabled = false;
			this->play8_groupBox->Location = System::Drawing::Point(321, 49);
			this->play8_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play8_groupBox->Name = L"play8_groupBox";
			this->play8_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play8_groupBox->Size = System::Drawing::Size(312, 92);
			this->play8_groupBox->TabIndex = 29;
			this->play8_groupBox->TabStop = false;
			this->play8_groupBox->Text = L"Play 8";
			this->play8_groupBox->Visible = false;
			// 
			// button49
			// 
			this->button49->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button49->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button49->Enabled = false;
			this->button49->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button49->Location = System::Drawing::Point(8, 23);
			this->button49->Margin = System::Windows::Forms::Padding(4);
			this->button49->Name = L"button49";
			this->button49->Size = System::Drawing::Size(67, 55);
			this->button49->TabIndex = 14;
			this->button49->Text = L"Guess 1";
			this->button49->UseVisualStyleBackColor = false;
			// 
			// button50
			// 
			this->button50->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button50->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button50->Enabled = false;
			this->button50->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button50->Location = System::Drawing::Point(83, 23);
			this->button50->Margin = System::Windows::Forms::Padding(4);
			this->button50->Name = L"button50";
			this->button50->Size = System::Drawing::Size(67, 55);
			this->button50->TabIndex = 15;
			this->button50->Text = L"Guess 2";
			this->button50->UseVisualStyleBackColor = false;
			// 
			// button51
			// 
			this->button51->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button51->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button51->Enabled = false;
			this->button51->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button51->Location = System::Drawing::Point(157, 23);
			this->button51->Margin = System::Windows::Forms::Padding(4);
			this->button51->Name = L"button51";
			this->button51->Size = System::Drawing::Size(67, 55);
			this->button51->TabIndex = 16;
			this->button51->Text = L"Guess 3";
			this->button51->UseVisualStyleBackColor = false;
			// 
			// button52
			// 
			this->button52->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button52->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button52->Enabled = false;
			this->button52->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button52->Location = System::Drawing::Point(232, 23);
			this->button52->Margin = System::Windows::Forms::Padding(4);
			this->button52->Name = L"button52";
			this->button52->Size = System::Drawing::Size(67, 55);
			this->button52->TabIndex = 17;
			this->button52->Text = L"Guess 4";
			this->button52->UseVisualStyleBackColor = false;
			// 
			// play8_score_groupBox
			// 
			this->play8_score_groupBox->Controls->Add(this->button53);
			this->play8_score_groupBox->Controls->Add(this->button54);
			this->play8_score_groupBox->Controls->Add(this->button55);
			this->play8_score_groupBox->Controls->Add(this->button56);
			this->play8_score_groupBox->Enabled = false;
			this->play8_score_groupBox->Location = System::Drawing::Point(641, 49);
			this->play8_score_groupBox->Margin = System::Windows::Forms::Padding(4);
			this->play8_score_groupBox->Name = L"play8_score_groupBox";
			this->play8_score_groupBox->Padding = System::Windows::Forms::Padding(4);
			this->play8_score_groupBox->Size = System::Drawing::Size(91, 92);
			this->play8_score_groupBox->TabIndex = 30;
			this->play8_score_groupBox->TabStop = false;
			this->play8_score_groupBox->Visible = false;
			// 
			// button53
			// 
			this->button53->BackColor = System::Drawing::Color::Sienna;
			this->button53->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button53->Enabled = false;
			this->button53->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button53->Location = System::Drawing::Point(8, 16);
			this->button53->Margin = System::Windows::Forms::Padding(4);
			this->button53->Name = L"button53";
			this->button53->Size = System::Drawing::Size(33, 31);
			this->button53->TabIndex = 25;
			this->button53->UseVisualStyleBackColor = false;
			// 
			// button54
			// 
			this->button54->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button54->Enabled = false;
			this->button54->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button54->Location = System::Drawing::Point(49, 54);
			this->button54->Margin = System::Windows::Forms::Padding(4);
			this->button54->Name = L"button54";
			this->button54->Size = System::Drawing::Size(33, 31);
			this->button54->TabIndex = 24;
			this->button54->UseVisualStyleBackColor = true;
			// 
			// button55
			// 
			this->button55->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button55->Enabled = false;
			this->button55->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button55->Location = System::Drawing::Point(8, 54);
			this->button55->Margin = System::Windows::Forms::Padding(4);
			this->button55->Name = L"button55";
			this->button55->Size = System::Drawing::Size(33, 31);
			this->button55->TabIndex = 27;
			this->button55->UseVisualStyleBackColor = true;
			// 
			// button56
			// 
			this->button56->BackColor = System::Drawing::Color::Sienna;
			this->button56->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->button56->Enabled = false;
			this->button56->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button56->Location = System::Drawing::Point(49, 16);
			this->button56->Margin = System::Windows::Forms::Padding(4);
			this->button56->Name = L"button56";
			this->button56->Size = System::Drawing::Size(33, 31);
			this->button56->TabIndex = 26;
			this->button56->UseVisualStyleBackColor = false;
			// 
			// UserNamePlay
			// 
			this->UserNamePlay->AutoSize = true;
			this->UserNamePlay->BackColor = System::Drawing::Color::DimGray;
			this->UserNamePlay->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 19.8F, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->UserNamePlay->ForeColor = System::Drawing::Color::Black;
			this->UserNamePlay->Location = System::Drawing::Point(15, 114);
			this->UserNamePlay->Name = L"UserNamePlay";
			this->UserNamePlay->Size = System::Drawing::Size(0, 38);
			this->UserNamePlay->TabIndex = 34;
			this->UserNamePlay->Text = userNameBtt;
			this->UserNamePlay->Click += gcnew System::EventHandler(this, &VentanaPlay::UserNamePlay_Click);
			// 
			// VentanaPlay
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(8, 16);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Sienna;
			this->ClientSize = System::Drawing::Size(952, 802);
			this->Controls->Add(this->UserNamePlay);
			this->Controls->Add(this->play8_score_groupBox);
			this->Controls->Add(this->play8_groupBox);
			this->Controls->Add(this->play7_score_groupBox);
			this->Controls->Add(this->play6_score_groupBox);
			this->Controls->Add(this->play5_score_groupBox);
			this->Controls->Add(this->play4_score_groupBox);
			this->Controls->Add(this->play3_score_groupBox);
			this->Controls->Add(this->play2_score_groupBox);
			this->Controls->Add(this->play7_groupBox);
			this->Controls->Add(this->play6_groupBox);
			this->Controls->Add(this->play5_groupBox);
			this->Controls->Add(this->play4_groupBox);
			this->Controls->Add(this->play3_groupBox);
			this->Controls->Add(this->titulo_label);
			this->Controls->Add(this->play2_groupBox);
			this->Controls->Add(this->enter_play_button);
			this->Controls->Add(this->color_position_bbtn_label);
			this->Controls->Add(this->color_wbtn_label);
			this->Controls->Add(this->white_button);
			this->Controls->Add(this->black_button);
			this->Controls->Add(this->play1_score_groupBox);
			this->Controls->Add(this->play1_groupBox);
			this->Controls->Add(this->Vent_Play_Start);
			this->Controls->Add(this->Time);
			this->Controls->Add(this->brown_button);
			this->Controls->Add(this->pink_button);
			this->Controls->Add(this->yellow_button);
			this->Controls->Add(this->green_button);
			this->Controls->Add(this->blue_button);
			this->Controls->Add(this->red_button);
			this->Controls->Add(this->menuStrip1);
			this->FormBorderStyle = System::Windows::Forms::FormBorderStyle::FixedDialog;
			this->MainMenuStrip = this->menuStrip1;
			this->Margin = System::Windows::Forms::Padding(4);
			this->Name = L"VentanaPlay";
			this->Text = L"Master Mind";
			this->Load += gcnew System::EventHandler(this, &VentanaPlay::MyForm_Load);
			this->menuStrip1->ResumeLayout(false);
			this->menuStrip1->PerformLayout();
			this->play1_groupBox->ResumeLayout(false);
			this->play1_score_groupBox->ResumeLayout(false);
			this->play2_groupBox->ResumeLayout(false);
			this->play3_groupBox->ResumeLayout(false);
			this->play4_groupBox->ResumeLayout(false);
			this->play5_groupBox->ResumeLayout(false);
			this->play6_groupBox->ResumeLayout(false);
			this->play7_groupBox->ResumeLayout(false);
			this->play2_score_groupBox->ResumeLayout(false);
			this->play3_score_groupBox->ResumeLayout(false);
			this->play4_score_groupBox->ResumeLayout(false);
			this->play5_score_groupBox->ResumeLayout(false);
			this->play6_score_groupBox->ResumeLayout(false);
			this->play7_score_groupBox->ResumeLayout(false);
			this->play8_groupBox->ResumeLayout(false);
			this->play8_score_groupBox->ResumeLayout(false);
			this->ResumeLayout(false);
			this->PerformLayout();

		}
#pragma endregion

	private: System::Void MyForm_Load(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void titulo_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void label2_Click(System::Object^ sender, System::EventArgs^ e) {
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

			bool_yellow_button = false;
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
		VentanaPlay::green_button->Enabled = true;
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



	private: System::Void play7_groupBox_Enter(System::Object^ sender, System::EventArgs^ e)
	{

	}
	private: System::Void UserNamePlay_Click(System::Object^ sender, System::EventArgs^ e) {
	}
};
}
