# Master-Mind

#pragma once

#include "ConfigurationClass.h"
#include <stdio.h>
#include <stdlib.h>
#include <ctime>


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

	public: ConfigurationClass* objSettings = new ConfigurationClass();


	private: System::Windows::Forms::GroupBox^ play1_groupBox;
	private: System::Windows::Forms::Button^ play1_guess1_button;
	private: System::Windows::Forms::Button^ play1_guess2_button;
	private: System::Windows::Forms::Button^ play1_guess3_button;
	private: System::Windows::Forms::Button^ play1_guess4_button;


	/*
	public: ref struct play
	{
		GroupBox^ play_groupBox = play1_groupBox;
		Button^ guess1_btn = guess1_button;
		Button^ guess2_btn = guess2_button;
		Button^ guess3_btn = guess3_button;
		Button^ guess4_btn = guess4_button;

	} play1, play2, play3, play4, play5, play6, play7, play8;
	*/


	public:
		static int seconds = 0;
		static int minutes = 0;
		static int hours = 0;
		String^ sec;
		String^ min;
		String^ hour;


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
		int actual_play = 1;
		bool win = false;
		int num_rand1 = 0;
		int num_rand2 = 0;
		int num_rand3 = 0;
		int num_rand4 = 0;
		bool quit_game = false;


	private: System::Windows::Forms::Button^ rand_comb4_button;
	private: System::Windows::Forms::Button^ rand_comb3_button;
	private: System::Windows::Forms::Button^ rand_comb2_button;
	private: System::Windows::Forms::Button^ rand_comb1_button;
	private: System::Windows::Forms::GroupBox^ rand_comb_groupBox;
	private: System::Windows::Forms::GroupBox^ win_groupBox;
	private: System::Windows::Forms::Label^ you_win_label;


	private: System::Windows::Forms::Button^ ok_win_button;
	private: System::Windows::Forms::GroupBox^ lose_groupBox;
	private: System::Windows::Forms::Label^ you_lose_label;
	private: System::Windows::Forms::Button^ ok_lose_button;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox4;
	private: System::Windows::Forms::GroupBox^ score_groupBox1;

	private: System::Windows::Forms::PictureBox^ play1_score_picBox4;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox1;
	private: System::Windows::Forms::GroupBox^ play1_pic_groupBox;
	private: System::Windows::Forms::Button^ blank_button;
	private: System::Windows::Forms::GroupBox^ play2_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox4;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox3;
	private: System::Windows::Forms::GroupBox^ play2_score_groupBox;

	private: System::Windows::Forms::PictureBox^ play2_score_picBox4;


	private: System::Windows::Forms::PictureBox^ play2_score_picBox3;

	private: System::Windows::Forms::PictureBox^ play2_score_picBox2;

	private: System::Windows::Forms::PictureBox^ play2_score_picBox1;
	private: System::Windows::Forms::Button^ blank_score_button;
	private: System::Windows::Forms::GroupBox^ play3_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox4;


	private: System::Windows::Forms::PictureBox^ play3_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox3;


	private: System::Windows::Forms::GroupBox^ play4_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox4;


	private: System::Windows::Forms::PictureBox^ play4_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox3;


	private: System::Windows::Forms::GroupBox^ play5_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play5_pictureBox1;

	private: System::Windows::Forms::PictureBox^ play5_pictureBox4;
	private: System::Windows::Forms::PictureBox^ play5_pictureBox2;


	private: System::Windows::Forms::PictureBox^ play5_pictureBox3;

	private: System::Windows::Forms::GroupBox^ play6_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox4;


	private: System::Windows::Forms::PictureBox^ play6_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox3;


	private: System::Windows::Forms::GroupBox^ play7_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox4;


	private: System::Windows::Forms::PictureBox^ play7_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox3;


	private: System::Windows::Forms::GroupBox^ play8_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox4;


	private: System::Windows::Forms::PictureBox^ play8_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox3;


	private: System::Windows::Forms::GroupBox^ play3_score_groupBox;

	private: System::Windows::Forms::PictureBox^ play3_score_picBox4;
	
	private: System::Windows::Forms::PictureBox^ play3_score_picBox3;
	
	private: System::Windows::Forms::PictureBox^ play3_score_picBox2;

	private: System::Windows::Forms::PictureBox^ play3_score_picBox1;
	private: System::Windows::Forms::GroupBox^ play4_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play4_score_picBox4;	
	
	
	private: System::Windows::Forms::PictureBox^ play4_score_picBox3;
	
	private: System::Windows::Forms::PictureBox^ play4_score_picBox2;
	
	private: System::Windows::Forms::PictureBox^ play4_score_picBox1;
	
	private: System::Windows::Forms::GroupBox^ play5_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play5_score_picBox4;
	
	
	private: System::Windows::Forms::PictureBox^ play5_score_picBox3;
	
	private: System::Windows::Forms::PictureBox^ play5_score_picBox2;
	
	private: System::Windows::Forms::PictureBox^ play5_score_picBox1;
	
	private: System::Windows::Forms::GroupBox^ play6_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play6_score_picBox4;
	
	
	private: System::Windows::Forms::PictureBox^ play6_score_picBox3;
	
	private: System::Windows::Forms::PictureBox^ play6_score_picBox2;
	
	private: System::Windows::Forms::PictureBox^ play6_score_picBox1;
	
	private: System::Windows::Forms::GroupBox^ play7_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play7_score_picBox4;
	
	
	private: System::Windows::Forms::PictureBox^ play7_score_picBox3;
	
	private: System::Windows::Forms::PictureBox^ play7_score_picBox2;
	
	private: System::Windows::Forms::PictureBox^ play7_score_picBox1;
	
	private: System::Windows::Forms::GroupBox^ play8_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play8_score_picBox4;
	
	
	private: System::Windows::Forms::PictureBox^ play8_score_picBox3;
	
	private: System::Windows::Forms::PictureBox^ play8_score_picBox2;
	
	private: System::Windows::Forms::PictureBox^ play8_score_picBox1;




	public:
		VentanaPlay(ConfigurationClass* objSettings)
		{
			InitializeComponent();

			this->objSettings = objSettings;

			if (objSettings->getDifficulty() == 1)
			{
				difficulty_label->Text = "Difficulty: Easy";
			}
			else if (objSettings->getDifficulty() == 2)
			{
				difficulty_label->Text = "Difficulty: Medium";
			}
			else if (objSettings->getDifficulty() == 3)
			{
				difficulty_label->Text = "Difficulty: Hard";
			}


			if (objSettings->getElementRep() == true)
			{
				repetition_label->Text = "Element repetition: ON";
			}
			else if (objSettings->getElementRep() == false)
			{
				repetition_label->Text = "Element repetition: OFF";
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
	/*
	private: System::Windows::Forms::Button^ guess1_button;
	private: System::Windows::Forms::Button^ guess2_button;
	private: System::Windows::Forms::Button^ guess3_button;
	private: System::Windows::Forms::Button^ guess4_button;	
	private: System::Windows::Forms::GroupBox^ play1_groupBox;
	*/

	private: System::Windows::Forms::MenuStrip^ menuStrip1;


	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ instruccionesToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ salirToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ archivoToolStripMenuItem;
	private: System::Windows::Forms::Label^ titulo_label;


	private: System::Windows::Forms::ToolStripMenuItem^ saveToolStripMenuItem;
	private: System::Windows::Forms::Label^ Time;


	private: System::ComponentModel::IContainer^ components;
	private: System::Windows::Forms::Button^ play1_score_btn4;


	private: System::Windows::Forms::Button^ play1_score_btn1;
	private: System::Windows::Forms::Button^ play1_score_btn2;
	private: System::Windows::Forms::Button^ play1_score_btn3;



	private: System::Windows::Forms::GroupBox^ play1_score_groupBox;

	private: System::Windows::Forms::Button^ black_button;
	private: System::Windows::Forms::Button^ white_button;
	private: System::Windows::Forms::Label^ color_wbtn_label;
	private: System::Windows::Forms::Label^ color_position_bbtn_label;
	private: System::Windows::Forms::Button^ enter_play_button;



	private: System::Windows::Forms::Label^ difficulty_label;
	private: System::Windows::Forms::Label^ repetition_label;

	private: System::Windows::Forms::GroupBox^ quit_game_groupBox;
	private: System::Windows::Forms::Label^ quit_label;
	private: System::Windows::Forms::Button^ ok_quit_button;
	private: System::Windows::Forms::RadioButton^ quit_yes_radioButton;
	private: System::Windows::Forms::RadioButton^ quit_no_radioButton;


	private: System::Windows::Forms::ToolStripMenuItem^ loadGameToolStripMenuItem;
	private: System::Windows::Forms::Button^ Vent_Play_Start;


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
			this->play1_guess1_button = (gcnew System::Windows::Forms::Button());
			this->play1_guess2_button = (gcnew System::Windows::Forms::Button());
			this->play1_guess3_button = (gcnew System::Windows::Forms::Button());
			this->play1_guess4_button = (gcnew System::Windows::Forms::Button());
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
			this->play1_score_btn4 = (gcnew System::Windows::Forms::Button());
			this->play1_score_btn1 = (gcnew System::Windows::Forms::Button());
			this->play1_score_btn2 = (gcnew System::Windows::Forms::Button());
			this->play1_score_btn3 = (gcnew System::Windows::Forms::Button());
			this->play1_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->black_button = (gcnew System::Windows::Forms::Button());
			this->white_button = (gcnew System::Windows::Forms::Button());
			this->color_wbtn_label = (gcnew System::Windows::Forms::Label());
			this->color_position_bbtn_label = (gcnew System::Windows::Forms::Label());
			this->enter_play_button = (gcnew System::Windows::Forms::Button());
			this->difficulty_label = (gcnew System::Windows::Forms::Label());
			this->repetition_label = (gcnew System::Windows::Forms::Label());
			this->quit_game_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->quit_yes_radioButton = (gcnew System::Windows::Forms::RadioButton());
			this->quit_no_radioButton = (gcnew System::Windows::Forms::RadioButton());
			this->ok_quit_button = (gcnew System::Windows::Forms::Button());
			this->quit_label = (gcnew System::Windows::Forms::Label());
			this->rand_comb4_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb3_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb2_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb1_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->win_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->ok_win_button = (gcnew System::Windows::Forms::Button());
			this->you_win_label = (gcnew System::Windows::Forms::Label());
			this->lose_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->ok_lose_button = (gcnew System::Windows::Forms::Button());
			this->you_lose_label = (gcnew System::Windows::Forms::Label());
			this->play1_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->score_groupBox1 = (gcnew System::Windows::Forms::GroupBox());
			this->play1_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play1_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->blank_button = (gcnew System::Windows::Forms::Button());
			this->play2_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play2_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play2_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play2_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->blank_score_button = (gcnew System::Windows::Forms::Button());
			this->play3_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play3_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play4_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play5_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play6_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play7_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_pic_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play8_pictureBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_pictureBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_pictureBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_pictureBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play3_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play3_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play4_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play4_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play5_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play5_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play6_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play6_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play7_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play7_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_score_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->play8_score_picBox4 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_score_picBox3 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_score_picBox2 = (gcnew System::Windows::Forms::PictureBox());
			this->play8_score_picBox1 = (gcnew System::Windows::Forms::PictureBox());
			this->menuStrip1->SuspendLayout();
			this->play1_groupBox->SuspendLayout();
			this->play1_score_groupBox->SuspendLayout();
			this->quit_game_groupBox->SuspendLayout();
			this->rand_comb_groupBox->SuspendLayout();
			this->win_groupBox->SuspendLayout();
			this->lose_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox4))->BeginInit();
			this->score_groupBox1->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox1))->BeginInit();
			this->play1_pic_groupBox->SuspendLayout();
			this->play2_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox3))->BeginInit();
			this->play2_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox1))->BeginInit();
			this->play3_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox3))->BeginInit();
			this->play4_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox3))->BeginInit();
			this->play5_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox3))->BeginInit();
			this->play6_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox3))->BeginInit();
			this->play7_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox3))->BeginInit();
			this->play8_pic_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox1))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox3))->BeginInit();
			this->play3_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox1))->BeginInit();
			this->play4_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox1))->BeginInit();
			this->play5_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox1))->BeginInit();
			this->play6_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox1))->BeginInit();
			this->play7_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox1))->BeginInit();
			this->play8_score_groupBox->SuspendLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox4))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox3))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox2))->BeginInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox1))->BeginInit();
			this->SuspendLayout();
			// 
			// red_button
			// 
			this->red_button->BackColor = System::Drawing::Color::Transparent;
			this->red_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"red_button.BackgroundImage")));
			this->red_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->red_button->Enabled = false;
			this->red_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->red_button->Location = System::Drawing::Point(582, 255);
			this->red_button->Name = L"red_button";
			this->red_button->Size = System::Drawing::Size(50, 45);
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
			this->blue_button->Location = System::Drawing::Point(582, 306);
			this->blue_button->Name = L"blue_button";
			this->blue_button->Size = System::Drawing::Size(50, 45);
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
			this->green_button->Location = System::Drawing::Point(582, 357);
			this->green_button->Name = L"green_button";
			this->green_button->Size = System::Drawing::Size(50, 45);
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
			this->yellow_button->Location = System::Drawing::Point(582, 408);
			this->yellow_button->Name = L"yellow_button";
			this->yellow_button->Size = System::Drawing::Size(50, 45);
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
			this->pink_button->Location = System::Drawing::Point(582, 458);
			this->pink_button->Name = L"pink_button";
			this->pink_button->Size = System::Drawing::Size(50, 45);
			this->pink_button->TabIndex = 4;
			this->pink_button->Text = L"Pink";
			this->pink_button->UseVisualStyleBackColor = false;
			this->pink_button->Click += gcnew System::EventHandler(this, &VentanaPlay::pink_button_Click);
			// 
			// brown_button
			// 
			this->brown_button->BackColor = System::Drawing::Color::Transparent;
			this->brown_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"brown_button.BackgroundImage")));
			this->brown_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->brown_button->Enabled = false;
			this->brown_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->brown_button->Location = System::Drawing::Point(582, 509);
			this->brown_button->Name = L"brown_button";
			this->brown_button->Size = System::Drawing::Size(50, 45);
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
			// play1_guess1_button
			// 
			this->play1_guess1_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->play1_guess1_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_guess1_button.BackgroundImage")));
			this->play1_guess1_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_guess1_button->Enabled = false;
			this->play1_guess1_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_guess1_button->Location = System::Drawing::Point(6, 19);
			this->play1_guess1_button->Name = L"play1_guess1_button";
			this->play1_guess1_button->Size = System::Drawing::Size(50, 45);
			this->play1_guess1_button->TabIndex = 14;
			this->play1_guess1_button->Text = L"Guess 1";
			this->play1_guess1_button->UseVisualStyleBackColor = false;
			this->play1_guess1_button->Click += gcnew System::EventHandler(this, &VentanaPlay::play1_guess1_button_Click);
			// 
			// play1_guess2_button
			// 
			this->play1_guess2_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->play1_guess2_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_guess2_button.BackgroundImage")));
			this->play1_guess2_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_guess2_button->Enabled = false;
			this->play1_guess2_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_guess2_button->Location = System::Drawing::Point(62, 19);
			this->play1_guess2_button->Name = L"play1_guess2_button";
			this->play1_guess2_button->Size = System::Drawing::Size(50, 45);
			this->play1_guess2_button->TabIndex = 15;
			this->play1_guess2_button->Text = L"Guess 2";
			this->play1_guess2_button->UseVisualStyleBackColor = false;
			this->play1_guess2_button->Click += gcnew System::EventHandler(this, &VentanaPlay::play1_guess2_button_Click);
			// 
			// play1_guess3_button
			// 
			this->play1_guess3_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->play1_guess3_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_guess3_button.BackgroundImage")));
			this->play1_guess3_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_guess3_button->Enabled = false;
			this->play1_guess3_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_guess3_button->Location = System::Drawing::Point(118, 19);
			this->play1_guess3_button->Name = L"play1_guess3_button";
			this->play1_guess3_button->Size = System::Drawing::Size(50, 45);
			this->play1_guess3_button->TabIndex = 16;
			this->play1_guess3_button->Text = L"Guess 3";
			this->play1_guess3_button->UseVisualStyleBackColor = false;
			this->play1_guess3_button->Click += gcnew System::EventHandler(this, &VentanaPlay::play1_guess3_button_Click);
			// 
			// play1_guess4_button
			// 
			this->play1_guess4_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->play1_guess4_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_guess4_button.BackgroundImage")));
			this->play1_guess4_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_guess4_button->Enabled = false;
			this->play1_guess4_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_guess4_button->Location = System::Drawing::Point(174, 19);
			this->play1_guess4_button->Name = L"play1_guess4_button";
			this->play1_guess4_button->Size = System::Drawing::Size(50, 45);
			this->play1_guess4_button->TabIndex = 17;
			this->play1_guess4_button->Text = L"Guess 4";
			this->play1_guess4_button->UseVisualStyleBackColor = false;
			this->play1_guess4_button->Click += gcnew System::EventHandler(this, &VentanaPlay::play1_guess4_button_Click);
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
			this->menuStrip1->Size = System::Drawing::Size(823, 24);
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
			this->salirToolStripMenuItem->Enabled = false;
			this->salirToolStripMenuItem->Name = L"salirToolStripMenuItem";
			this->salirToolStripMenuItem->Size = System::Drawing::Size(75, 20);
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
			this->titulo_label->Location = System::Drawing::Point(12, 33);
			this->titulo_label->Name = L"titulo_label";
			this->titulo_label->Size = System::Drawing::Size(206, 41);
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
			this->Time->Location = System::Drawing::Point(14, 541);
			this->Time->Name = L"Time";
			this->Time->Size = System::Drawing::Size(159, 39);
			this->Time->TabIndex = 21;
			this->Time->Text = L"00:00:00";
			this->Time->Click += gcnew System::EventHandler(this, &VentanaPlay::label2_Click);
			// 
			// Vent_Play_Start
			// 
			this->Vent_Play_Start->AutoSize = true;
			this->Vent_Play_Start->Location = System::Drawing::Point(12, 586);
			this->Vent_Play_Start->Name = L"Vent_Play_Start";
			this->Vent_Play_Start->Size = System::Drawing::Size(161, 54);
			this->Vent_Play_Start->TabIndex = 22;
			this->Vent_Play_Start->Text = L"Start";
			this->Vent_Play_Start->UseVisualStyleBackColor = true;
			this->Vent_Play_Start->Click += gcnew System::EventHandler(this, &VentanaPlay::Vent_Play_Start_Click);
			// 
			// play1_groupBox
			// 
			this->play1_groupBox->Controls->Add(this->play1_guess1_button);
			this->play1_groupBox->Controls->Add(this->play1_guess2_button);
			this->play1_groupBox->Controls->Add(this->play1_guess3_button);
			this->play1_groupBox->Controls->Add(this->play1_guess4_button);
			this->play1_groupBox->Location = System::Drawing::Point(576, 565);
			this->play1_groupBox->Name = L"play1_groupBox";
			this->play1_groupBox->Size = System::Drawing::Size(234, 75);
			this->play1_groupBox->TabIndex = 23;
			this->play1_groupBox->TabStop = false;
			this->play1_groupBox->Text = L"Play 1";
			// 
			// play1_score_btn4
			// 
			this->play1_score_btn4->BackColor = System::Drawing::Color::Transparent;
			this->play1_score_btn4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_btn4.BackgroundImage")));
			this->play1_score_btn4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_btn4->Enabled = false;
			this->play1_score_btn4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_score_btn4->Location = System::Drawing::Point(37, 44);
			this->play1_score_btn4->Name = L"play1_score_btn4";
			this->play1_score_btn4->Size = System::Drawing::Size(25, 25);
			this->play1_score_btn4->TabIndex = 24;
			this->play1_score_btn4->UseVisualStyleBackColor = false;
			// 
			// play1_score_btn1
			// 
			this->play1_score_btn1->BackColor = System::Drawing::Color::Transparent;
			this->play1_score_btn1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_btn1.BackgroundImage")));
			this->play1_score_btn1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_btn1->Enabled = false;
			this->play1_score_btn1->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_score_btn1->Location = System::Drawing::Point(6, 13);
			this->play1_score_btn1->Name = L"play1_score_btn1";
			this->play1_score_btn1->Size = System::Drawing::Size(25, 25);
			this->play1_score_btn1->TabIndex = 25;
			this->play1_score_btn1->UseVisualStyleBackColor = false;
			// 
			// play1_score_btn2
			// 
			this->play1_score_btn2->BackColor = System::Drawing::Color::Transparent;
			this->play1_score_btn2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_btn2.BackgroundImage")));
			this->play1_score_btn2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_btn2->Enabled = false;
			this->play1_score_btn2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_score_btn2->Location = System::Drawing::Point(37, 13);
			this->play1_score_btn2->Name = L"play1_score_btn2";
			this->play1_score_btn2->Size = System::Drawing::Size(25, 25);
			this->play1_score_btn2->TabIndex = 26;
			this->play1_score_btn2->UseVisualStyleBackColor = false;
			// 
			// play1_score_btn3
			// 
			this->play1_score_btn3->BackColor = System::Drawing::Color::Transparent;
			this->play1_score_btn3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_btn3.BackgroundImage")));
			this->play1_score_btn3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_btn3->Enabled = false;
			this->play1_score_btn3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->play1_score_btn3->Location = System::Drawing::Point(6, 44);
			this->play1_score_btn3->Name = L"play1_score_btn3";
			this->play1_score_btn3->Size = System::Drawing::Size(25, 25);
			this->play1_score_btn3->TabIndex = 27;
			this->play1_score_btn3->UseVisualStyleBackColor = false;
			// 
			// play1_score_groupBox
			// 
			this->play1_score_groupBox->Controls->Add(this->play1_score_btn1);
			this->play1_score_groupBox->Controls->Add(this->play1_score_btn4);
			this->play1_score_groupBox->Controls->Add(this->play1_score_btn3);
			this->play1_score_groupBox->Controls->Add(this->play1_score_btn2);
			this->play1_score_groupBox->Location = System::Drawing::Point(694, 392);
			this->play1_score_groupBox->Name = L"play1_score_groupBox";
			this->play1_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play1_score_groupBox->TabIndex = 28;
			this->play1_score_groupBox->TabStop = false;
			this->play1_score_groupBox->Visible = false;
			// 
			// black_button
			// 
			this->black_button->BackColor = System::Drawing::Color::Transparent;
			this->black_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"black_button.BackgroundImage")));
			this->black_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->black_button->Enabled = false;
			this->black_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->black_button->Location = System::Drawing::Point(12, 459);
			this->black_button->Name = L"black_button";
			this->black_button->Size = System::Drawing::Size(25, 25);
			this->black_button->TabIndex = 28;
			this->black_button->UseVisualStyleBackColor = false;
			// 
			// white_button
			// 
			this->white_button->BackColor = System::Drawing::Color::Transparent;
			this->white_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"white_button.BackgroundImage")));
			this->white_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->white_button->Enabled = false;
			this->white_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->white_button->Location = System::Drawing::Point(12, 428);
			this->white_button->Name = L"white_button";
			this->white_button->Size = System::Drawing::Size(25, 25);
			this->white_button->TabIndex = 29;
			this->white_button->UseVisualStyleBackColor = false;
			// 
			// color_wbtn_label
			// 
			this->color_wbtn_label->AutoSize = true;
			this->color_wbtn_label->Location = System::Drawing::Point(43, 434);
			this->color_wbtn_label->Name = L"color_wbtn_label";
			this->color_wbtn_label->Size = System::Drawing::Size(30, 13);
			this->color_wbtn_label->TabIndex = 30;
			this->color_wbtn_label->Text = L"color";
			this->color_wbtn_label->Click += gcnew System::EventHandler(this, &VentanaPlay::color_wbtn_label_Click);
			// 
			// color_position_bbtn_label
			// 
			this->color_position_bbtn_label->AutoSize = true;
			this->color_position_bbtn_label->Location = System::Drawing::Point(43, 465);
			this->color_position_bbtn_label->Name = L"color_position_bbtn_label";
			this->color_position_bbtn_label->Size = System::Drawing::Size(90, 13);
			this->color_position_bbtn_label->TabIndex = 31;
			this->color_position_bbtn_label->Text = L"color and position";
			this->color_position_bbtn_label->Click += gcnew System::EventHandler(this, &VentanaPlay::color_position_bbtn_label_Click);
			// 
			// enter_play_button
			// 
			this->enter_play_button->Enabled = false;
			this->enter_play_button->Location = System::Drawing::Point(687, 531);
			this->enter_play_button->Name = L"enter_play_button";
			this->enter_play_button->Size = System::Drawing::Size(75, 23);
			this->enter_play_button->TabIndex = 32;
			this->enter_play_button->Text = L"Enter Play";
			this->enter_play_button->UseVisualStyleBackColor = true;
			this->enter_play_button->Click += gcnew System::EventHandler(this, &VentanaPlay::enter_play_button_Click);
			// 
			// difficulty_label
			// 
			this->difficulty_label->AutoSize = true;
			this->difficulty_label->Location = System::Drawing::Point(9, 365);
			this->difficulty_label->Name = L"difficulty_label";
			this->difficulty_label->Size = System::Drawing::Size(53, 13);
			this->difficulty_label->TabIndex = 33;
			this->difficulty_label->Text = L"Difficulty: ";
			this->difficulty_label->Click += gcnew System::EventHandler(this, &VentanaPlay::label1_Click);
			// 
			// repetition_label
			// 
			this->repetition_label->AutoSize = true;
			this->repetition_label->Location = System::Drawing::Point(9, 391);
			this->repetition_label->Name = L"repetition_label";
			this->repetition_label->Size = System::Drawing::Size(0, 13);
			this->repetition_label->TabIndex = 34;
			// 
			// quit_game_groupBox
			// 
			this->quit_game_groupBox->BackColor = System::Drawing::SystemColors::ControlDark;
			this->quit_game_groupBox->Controls->Add(this->quit_yes_radioButton);
			this->quit_game_groupBox->Controls->Add(this->quit_no_radioButton);
			this->quit_game_groupBox->Controls->Add(this->ok_quit_button);
			this->quit_game_groupBox->Controls->Add(this->quit_label);
			this->quit_game_groupBox->Enabled = false;
			this->quit_game_groupBox->Location = System::Drawing::Point(180, 117);
			this->quit_game_groupBox->Name = L"quit_game_groupBox";
			this->quit_game_groupBox->Size = System::Drawing::Size(411, 212);
			this->quit_game_groupBox->TabIndex = 35;
			this->quit_game_groupBox->TabStop = false;
			this->quit_game_groupBox->Text = L"Quit Game";
			this->quit_game_groupBox->Visible = false;
			// 
			// quit_yes_radioButton
			// 
			this->quit_yes_radioButton->AutoSize = true;
			this->quit_yes_radioButton->Location = System::Drawing::Point(92, 111);
			this->quit_yes_radioButton->Name = L"quit_yes_radioButton";
			this->quit_yes_radioButton->Size = System::Drawing::Size(43, 17);
			this->quit_yes_radioButton->TabIndex = 37;
			this->quit_yes_radioButton->TabStop = true;
			this->quit_yes_radioButton->Text = L"Yes";
			this->quit_yes_radioButton->UseVisualStyleBackColor = true;
			this->quit_yes_radioButton->CheckedChanged += gcnew System::EventHandler(this, &VentanaPlay::quit_yes_radioButton_CheckedChanged);
			// 
			// quit_no_radioButton
			// 
			this->quit_no_radioButton->AutoSize = true;
			this->quit_no_radioButton->Location = System::Drawing::Point(268, 111);
			this->quit_no_radioButton->Name = L"quit_no_radioButton";
			this->quit_no_radioButton->Size = System::Drawing::Size(39, 17);
			this->quit_no_radioButton->TabIndex = 36;
			this->quit_no_radioButton->TabStop = true;
			this->quit_no_radioButton->Text = L"No";
			this->quit_no_radioButton->UseVisualStyleBackColor = true;
			this->quit_no_radioButton->CheckedChanged += gcnew System::EventHandler(this, &VentanaPlay::quit_no_radioButton_CheckedChanged);
			// 
			// ok_quit_button
			// 
			this->ok_quit_button->Enabled = false;
			this->ok_quit_button->Location = System::Drawing::Point(160, 157);
			this->ok_quit_button->Name = L"ok_quit_button";
			this->ok_quit_button->Size = System::Drawing::Size(75, 23);
			this->ok_quit_button->TabIndex = 21;
			this->ok_quit_button->Text = L"OK";
			this->ok_quit_button->UseVisualStyleBackColor = true;
			this->ok_quit_button->Click += gcnew System::EventHandler(this, &VentanaPlay::ok_quit_button_Click);
			// 
			// quit_label
			// 
			this->quit_label->AutoSize = true;
			this->quit_label->Location = System::Drawing::Point(132, 61);
			this->quit_label->Name = L"quit_label";
			this->quit_label->Size = System::Drawing::Size(150, 13);
			this->quit_label->TabIndex = 20;
			this->quit_label->Text = L"Are you sure you want to quit\?";
			// 
			// rand_comb4_button
			// 
			this->rand_comb4_button->BackColor = System::Drawing::Color::Transparent;
			this->rand_comb4_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->rand_comb4_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->rand_comb4_button->Location = System::Drawing::Point(99, 19);
			this->rand_comb4_button->Name = L"rand_comb4_button";
			this->rand_comb4_button->Size = System::Drawing::Size(25, 25);
			this->rand_comb4_button->TabIndex = 36;
			this->rand_comb4_button->Text = L"4";
			this->rand_comb4_button->UseVisualStyleBackColor = false;
			// 
			// rand_comb3_button
			// 
			this->rand_comb3_button->BackColor = System::Drawing::Color::Transparent;
			this->rand_comb3_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->rand_comb3_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->rand_comb3_button->Location = System::Drawing::Point(68, 19);
			this->rand_comb3_button->Name = L"rand_comb3_button";
			this->rand_comb3_button->Size = System::Drawing::Size(25, 25);
			this->rand_comb3_button->TabIndex = 37;
			this->rand_comb3_button->Text = L"3";
			this->rand_comb3_button->UseVisualStyleBackColor = false;
			// 
			// rand_comb2_button
			// 
			this->rand_comb2_button->BackColor = System::Drawing::Color::Transparent;
			this->rand_comb2_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->rand_comb2_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->rand_comb2_button->Location = System::Drawing::Point(37, 19);
			this->rand_comb2_button->Name = L"rand_comb2_button";
			this->rand_comb2_button->Size = System::Drawing::Size(25, 25);
			this->rand_comb2_button->TabIndex = 38;
			this->rand_comb2_button->Text = L"2";
			this->rand_comb2_button->UseVisualStyleBackColor = false;
			// 
			// rand_comb1_button
			// 
			this->rand_comb1_button->BackColor = System::Drawing::Color::Transparent;
			this->rand_comb1_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->rand_comb1_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->rand_comb1_button->Location = System::Drawing::Point(6, 19);
			this->rand_comb1_button->Name = L"rand_comb1_button";
			this->rand_comb1_button->Size = System::Drawing::Size(25, 25);
			this->rand_comb1_button->TabIndex = 39;
			this->rand_comb1_button->Text = L"1";
			this->rand_comb1_button->UseVisualStyleBackColor = false;
			// 
			// rand_comb_groupBox
			// 
			this->rand_comb_groupBox->Controls->Add(this->rand_comb1_button);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb4_button);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb3_button);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb2_button);
			this->rand_comb_groupBox->Enabled = false;
			this->rand_comb_groupBox->Location = System::Drawing::Point(660, 473);
			this->rand_comb_groupBox->Name = L"rand_comb_groupBox";
			this->rand_comb_groupBox->Size = System::Drawing::Size(132, 52);
			this->rand_comb_groupBox->TabIndex = 40;
			this->rand_comb_groupBox->TabStop = false;
			this->rand_comb_groupBox->Text = L"Random Combination";
			this->rand_comb_groupBox->Visible = false;
			// 
			// win_groupBox
			// 
			this->win_groupBox->BackColor = System::Drawing::Color::DarkGray;
			this->win_groupBox->Controls->Add(this->ok_win_button);
			this->win_groupBox->Controls->Add(this->you_win_label);
			this->win_groupBox->Enabled = false;
			this->win_groupBox->Location = System::Drawing::Point(648, 91);
			this->win_groupBox->Name = L"win_groupBox";
			this->win_groupBox->Size = System::Drawing::Size(144, 100);
			this->win_groupBox->TabIndex = 41;
			this->win_groupBox->TabStop = false;
			this->win_groupBox->Text = L"Win";
			this->win_groupBox->Visible = false;
			// 
			// ok_win_button
			// 
			this->ok_win_button->Location = System::Drawing::Point(33, 65);
			this->ok_win_button->Name = L"ok_win_button";
			this->ok_win_button->Size = System::Drawing::Size(75, 23);
			this->ok_win_button->TabIndex = 1;
			this->ok_win_button->Text = L"OK";
			this->ok_win_button->UseVisualStyleBackColor = true;
			this->ok_win_button->Click += gcnew System::EventHandler(this, &VentanaPlay::ok_win_button_Click);
			// 
			// you_win_label
			// 
			this->you_win_label->AutoSize = true;
			this->you_win_label->Location = System::Drawing::Point(45, 37);
			this->you_win_label->Name = L"you_win_label";
			this->you_win_label->Size = System::Drawing::Size(51, 13);
			this->you_win_label->TabIndex = 0;
			this->you_win_label->Text = L"You Win!";
			this->you_win_label->Click += gcnew System::EventHandler(this, &VentanaPlay::label1_Click_1);
			// 
			// lose_groupBox
			// 
			this->lose_groupBox->BackColor = System::Drawing::Color::DarkGray;
			this->lose_groupBox->Controls->Add(this->ok_lose_button);
			this->lose_groupBox->Controls->Add(this->you_lose_label);
			this->lose_groupBox->Enabled = false;
			this->lose_groupBox->Location = System::Drawing::Point(12, 91);
			this->lose_groupBox->Name = L"lose_groupBox";
			this->lose_groupBox->Size = System::Drawing::Size(144, 100);
			this->lose_groupBox->TabIndex = 42;
			this->lose_groupBox->TabStop = false;
			this->lose_groupBox->Text = L"Lose";
			this->lose_groupBox->Visible = false;
			// 
			// ok_lose_button
			// 
			this->ok_lose_button->Location = System::Drawing::Point(27, 65);
			this->ok_lose_button->Name = L"ok_lose_button";
			this->ok_lose_button->Size = System::Drawing::Size(75, 23);
			this->ok_lose_button->TabIndex = 1;
			this->ok_lose_button->Text = L"OK";
			this->ok_lose_button->UseVisualStyleBackColor = true;
			this->ok_lose_button->Click += gcnew System::EventHandler(this, &VentanaPlay::ok_lose_button_Click);
			// 
			// you_lose_label
			// 
			this->you_lose_label->AutoSize = true;
			this->you_lose_label->Location = System::Drawing::Point(41, 37);
			this->you_lose_label->Name = L"you_lose_label";
			this->you_lose_label->Size = System::Drawing::Size(61, 13);
			this->you_lose_label->TabIndex = 0;
			this->you_lose_label->Text = L"You Lose :(";
			// 
			// play1_pictureBox1
			// 
			this->play1_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play1_pictureBox1->Name = L"play1_pictureBox1";
			this->play1_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox1->TabIndex = 43;
			this->play1_pictureBox1->TabStop = false;
			// 
			// play1_pictureBox2
			// 
			this->play1_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play1_pictureBox2->Name = L"play1_pictureBox2";
			this->play1_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox2->TabIndex = 44;
			this->play1_pictureBox2->TabStop = false;
			// 
			// play1_pictureBox3
			// 
			this->play1_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play1_pictureBox3->Name = L"play1_pictureBox3";
			this->play1_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox3->TabIndex = 45;
			this->play1_pictureBox3->TabStop = false;
			// 
			// play1_pictureBox4
			// 
			this->play1_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play1_pictureBox4->Name = L"play1_pictureBox4";
			this->play1_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox4->TabIndex = 46;
			this->play1_pictureBox4->TabStop = false;
			// 
			// score_groupBox1
			// 
			this->score_groupBox1->Controls->Add(this->play1_score_picBox4);
			this->score_groupBox1->Controls->Add(this->play1_score_picBox3);
			this->score_groupBox1->Controls->Add(this->play1_score_picBox2);
			this->score_groupBox1->Controls->Add(this->play1_score_picBox1);
			this->score_groupBox1->Location = System::Drawing::Point(481, 571);
			this->score_groupBox1->Name = L"score_groupBox1";
			this->score_groupBox1->Size = System::Drawing::Size(68, 75);
			this->score_groupBox1->TabIndex = 30;
			this->score_groupBox1->TabStop = false;
			// 
			// play1_score_picBox4
			// 
			this->play1_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play1_score_picBox4->Name = L"play1_score_picBox4";
			this->play1_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox4->TabIndex = 31;
			this->play1_score_picBox4->TabStop = false;
			// 
			// play1_score_picBox3
			// 
			this->play1_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play1_score_picBox3->Name = L"play1_score_picBox3";
			this->play1_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox3->TabIndex = 30;
			this->play1_score_picBox3->TabStop = false;
			// 
			// play1_score_picBox2
			// 
			this->play1_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play1_score_picBox2->Name = L"play1_score_picBox2";
			this->play1_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox2->TabIndex = 29;
			this->play1_score_picBox2->TabStop = false;
			// 
			// play1_score_picBox1
			// 
			this->play1_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play1_score_picBox1->Name = L"play1_score_picBox1";
			this->play1_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox1->TabIndex = 28;
			this->play1_score_picBox1->TabStop = false;
			// 
			// play1_pic_groupBox
			// 
			this->play1_pic_groupBox->Controls->Add(this->play1_pictureBox1);
			this->play1_pic_groupBox->Controls->Add(this->play1_pictureBox4);
			this->play1_pic_groupBox->Controls->Add(this->play1_pictureBox2);
			this->play1_pic_groupBox->Controls->Add(this->play1_pictureBox3);
			this->play1_pic_groupBox->Location = System::Drawing::Point(241, 571);
			this->play1_pic_groupBox->Name = L"play1_pic_groupBox";
			this->play1_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play1_pic_groupBox->TabIndex = 24;
			this->play1_pic_groupBox->TabStop = false;
			this->play1_pic_groupBox->Text = L"Play 1";
			// 
			// blank_button
			// 
			this->blank_button->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->blank_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"blank_button.BackgroundImage")));
			this->blank_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->blank_button->Enabled = false;
			this->blank_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->blank_button->Location = System::Drawing::Point(123, 490);
			this->blank_button->Name = L"blank_button";
			this->blank_button->Size = System::Drawing::Size(50, 45);
			this->blank_button->TabIndex = 18;
			this->blank_button->Text = L"Blank";
			this->blank_button->UseVisualStyleBackColor = false;
			this->blank_button->Visible = false;
			// 
			// play2_pic_groupBox
			// 
			this->play2_pic_groupBox->Controls->Add(this->play2_pictureBox1);
			this->play2_pic_groupBox->Controls->Add(this->play2_pictureBox4);
			this->play2_pic_groupBox->Controls->Add(this->play2_pictureBox2);
			this->play2_pic_groupBox->Controls->Add(this->play2_pictureBox3);
			this->play2_pic_groupBox->Enabled = false;
			this->play2_pic_groupBox->Location = System::Drawing::Point(241, 490);
			this->play2_pic_groupBox->Name = L"play2_pic_groupBox";
			this->play2_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play2_pic_groupBox->TabIndex = 47;
			this->play2_pic_groupBox->TabStop = false;
			this->play2_pic_groupBox->Text = L"Play 2";
			this->play2_pic_groupBox->Visible = false;
			// 
			// play2_pictureBox1
			// 
			this->play2_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play2_pictureBox1->Name = L"play2_pictureBox1";
			this->play2_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox1->TabIndex = 43;
			this->play2_pictureBox1->TabStop = false;
			// 
			// play2_pictureBox4
			// 
			this->play2_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play2_pictureBox4->Name = L"play2_pictureBox4";
			this->play2_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox4->TabIndex = 46;
			this->play2_pictureBox4->TabStop = false;
			// 
			// play2_pictureBox2
			// 
			this->play2_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play2_pictureBox2->Name = L"play2_pictureBox2";
			this->play2_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox2->TabIndex = 44;
			this->play2_pictureBox2->TabStop = false;
			// 
			// play2_pictureBox3
			// 
			this->play2_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play2_pictureBox3->Name = L"play2_pictureBox3";
			this->play2_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox3->TabIndex = 45;
			this->play2_pictureBox3->TabStop = false;
			// 
			// play2_score_groupBox
			// 
			this->play2_score_groupBox->Controls->Add(this->play2_score_picBox4);
			this->play2_score_groupBox->Controls->Add(this->play2_score_picBox3);
			this->play2_score_groupBox->Controls->Add(this->play2_score_picBox2);
			this->play2_score_groupBox->Controls->Add(this->play2_score_picBox1);
			this->play2_score_groupBox->Enabled = false;
			this->play2_score_groupBox->Location = System::Drawing::Point(481, 490);
			this->play2_score_groupBox->Name = L"play2_score_groupBox";
			this->play2_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play2_score_groupBox->TabIndex = 32;
			this->play2_score_groupBox->TabStop = false;
			this->play2_score_groupBox->Visible = false;
			// 
			// play2_score_picBox4
			// 
			this->play2_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play2_score_picBox4->Name = L"play2_score_picBox4";
			this->play2_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox4->TabIndex = 31;
			this->play2_score_picBox4->TabStop = false;
			// 
			// play2_score_picBox3
			// 
			this->play2_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play2_score_picBox3->Name = L"play2_score_picBox3";
			this->play2_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox3->TabIndex = 30;
			this->play2_score_picBox3->TabStop = false;
			// 
			// play2_score_picBox2
			// 
			this->play2_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play2_score_picBox2->Name = L"play2_score_picBox2";
			this->play2_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox2->TabIndex = 29;
			this->play2_score_picBox2->TabStop = false;
			// 
			// play2_score_picBox1
			// 
			this->play2_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play2_score_picBox1->Name = L"play2_score_picBox1";
			this->play2_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox1->TabIndex = 28;
			this->play2_score_picBox1->TabStop = false;
			// 
			// blank_score_button
			// 
			this->blank_score_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"blank_score_button.BackgroundImage")));
			this->blank_score_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->blank_score_button->Enabled = false;
			this->blank_score_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->blank_score_button->Location = System::Drawing::Point(92, 509);
			this->blank_score_button->Name = L"blank_score_button";
			this->blank_score_button->Size = System::Drawing::Size(25, 25);
			this->blank_score_button->TabIndex = 28;
			this->blank_score_button->UseVisualStyleBackColor = true;
			this->blank_score_button->Visible = false;
			// 
			// play3_pic_groupBox
			// 
			this->play3_pic_groupBox->Controls->Add(this->play3_pictureBox1);
			this->play3_pic_groupBox->Controls->Add(this->play3_pictureBox4);
			this->play3_pic_groupBox->Controls->Add(this->play3_pictureBox2);
			this->play3_pic_groupBox->Controls->Add(this->play3_pictureBox3);
			this->play3_pic_groupBox->Enabled = false;
			this->play3_pic_groupBox->Location = System::Drawing::Point(241, 415);
			this->play3_pic_groupBox->Name = L"play3_pic_groupBox";
			this->play3_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play3_pic_groupBox->TabIndex = 48;
			this->play3_pic_groupBox->TabStop = false;
			this->play3_pic_groupBox->Text = L"Play 3";
			this->play3_pic_groupBox->Visible = false;
			// 
			// play3_pictureBox1
			// 
			this->play3_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play3_pictureBox1->Name = L"play3_pictureBox1";
			this->play3_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox1->TabIndex = 43;
			this->play3_pictureBox1->TabStop = false;
			// 
			// play3_pictureBox4
			// 
			this->play3_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play3_pictureBox4->Name = L"play3_pictureBox4";
			this->play3_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox4->TabIndex = 46;
			this->play3_pictureBox4->TabStop = false;
			// 
			// play3_pictureBox2
			// 
			this->play3_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play3_pictureBox2->Name = L"play3_pictureBox2";
			this->play3_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox2->TabIndex = 44;
			this->play3_pictureBox2->TabStop = false;
			// 
			// play3_pictureBox3
			// 
			this->play3_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play3_pictureBox3->Name = L"play3_pictureBox3";
			this->play3_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox3->TabIndex = 45;
			this->play3_pictureBox3->TabStop = false;
			// 
			// play4_pic_groupBox
			// 
			this->play4_pic_groupBox->Controls->Add(this->play4_pictureBox1);
			this->play4_pic_groupBox->Controls->Add(this->play4_pictureBox4);
			this->play4_pic_groupBox->Controls->Add(this->play4_pictureBox2);
			this->play4_pic_groupBox->Controls->Add(this->play4_pictureBox3);
			this->play4_pic_groupBox->Enabled = false;
			this->play4_pic_groupBox->Location = System::Drawing::Point(241, 340);
			this->play4_pic_groupBox->Name = L"play4_pic_groupBox";
			this->play4_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play4_pic_groupBox->TabIndex = 48;
			this->play4_pic_groupBox->TabStop = false;
			this->play4_pic_groupBox->Text = L"Play 4";
			this->play4_pic_groupBox->Visible = false;
			// 
			// play4_pictureBox1
			// 
			this->play4_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play4_pictureBox1->Name = L"play4_pictureBox1";
			this->play4_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox1->TabIndex = 43;
			this->play4_pictureBox1->TabStop = false;
			// 
			// play4_pictureBox4
			// 
			this->play4_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play4_pictureBox4->Name = L"play4_pictureBox4";
			this->play4_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox4->TabIndex = 46;
			this->play4_pictureBox4->TabStop = false;
			// 
			// play4_pictureBox2
			// 
			this->play4_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play4_pictureBox2->Name = L"play4_pictureBox2";
			this->play4_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox2->TabIndex = 44;
			this->play4_pictureBox2->TabStop = false;
			// 
			// play4_pictureBox3
			// 
			this->play4_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play4_pictureBox3->Name = L"play4_pictureBox3";
			this->play4_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox3->TabIndex = 45;
			this->play4_pictureBox3->TabStop = false;
			// 
			// play5_pic_groupBox
			// 
			this->play5_pic_groupBox->Controls->Add(this->play5_pictureBox1);
			this->play5_pic_groupBox->Controls->Add(this->play5_pictureBox4);
			this->play5_pic_groupBox->Controls->Add(this->play5_pictureBox2);
			this->play5_pic_groupBox->Controls->Add(this->play5_pictureBox3);
			this->play5_pic_groupBox->Enabled = false;
			this->play5_pic_groupBox->Location = System::Drawing::Point(241, 265);
			this->play5_pic_groupBox->Name = L"play5_pic_groupBox";
			this->play5_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play5_pic_groupBox->TabIndex = 49;
			this->play5_pic_groupBox->TabStop = false;
			this->play5_pic_groupBox->Text = L"Play 5";
			this->play5_pic_groupBox->Visible = false;
			// 
			// play5_pictureBox1
			// 
			this->play5_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play5_pictureBox1->Name = L"play5_pictureBox1";
			this->play5_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox1->TabIndex = 43;
			this->play5_pictureBox1->TabStop = false;
			// 
			// play5_pictureBox4
			// 
			this->play5_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play5_pictureBox4->Name = L"play5_pictureBox4";
			this->play5_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox4->TabIndex = 46;
			this->play5_pictureBox4->TabStop = false;
			// 
			// play5_pictureBox2
			// 
			this->play5_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play5_pictureBox2->Name = L"play5_pictureBox2";
			this->play5_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox2->TabIndex = 44;
			this->play5_pictureBox2->TabStop = false;
			// 
			// play5_pictureBox3
			// 
			this->play5_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play5_pictureBox3->Name = L"play5_pictureBox3";
			this->play5_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox3->TabIndex = 45;
			this->play5_pictureBox3->TabStop = false;
			// 
			// play6_pic_groupBox
			// 
			this->play6_pic_groupBox->Controls->Add(this->play6_pictureBox1);
			this->play6_pic_groupBox->Controls->Add(this->play6_pictureBox4);
			this->play6_pic_groupBox->Controls->Add(this->play6_pictureBox2);
			this->play6_pic_groupBox->Controls->Add(this->play6_pictureBox3);
			this->play6_pic_groupBox->Enabled = false;
			this->play6_pic_groupBox->Location = System::Drawing::Point(241, 190);
			this->play6_pic_groupBox->Name = L"play6_pic_groupBox";
			this->play6_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play6_pic_groupBox->TabIndex = 49;
			this->play6_pic_groupBox->TabStop = false;
			this->play6_pic_groupBox->Text = L"Play 6";
			this->play6_pic_groupBox->Visible = false;
			// 
			// play6_pictureBox1
			// 
			this->play6_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play6_pictureBox1->Name = L"play6_pictureBox1";
			this->play6_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox1->TabIndex = 43;
			this->play6_pictureBox1->TabStop = false;
			// 
			// play6_pictureBox4
			// 
			this->play6_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play6_pictureBox4->Name = L"play6_pictureBox4";
			this->play6_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox4->TabIndex = 46;
			this->play6_pictureBox4->TabStop = false;
			// 
			// play6_pictureBox2
			// 
			this->play6_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play6_pictureBox2->Name = L"play6_pictureBox2";
			this->play6_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox2->TabIndex = 44;
			this->play6_pictureBox2->TabStop = false;
			// 
			// play6_pictureBox3
			// 
			this->play6_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play6_pictureBox3->Name = L"play6_pictureBox3";
			this->play6_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox3->TabIndex = 45;
			this->play6_pictureBox3->TabStop = false;
			// 
			// play7_pic_groupBox
			// 
			this->play7_pic_groupBox->Controls->Add(this->play7_pictureBox1);
			this->play7_pic_groupBox->Controls->Add(this->play7_pictureBox4);
			this->play7_pic_groupBox->Controls->Add(this->play7_pictureBox2);
			this->play7_pic_groupBox->Controls->Add(this->play7_pictureBox3);
			this->play7_pic_groupBox->Enabled = false;
			this->play7_pic_groupBox->Location = System::Drawing::Point(241, 115);
			this->play7_pic_groupBox->Name = L"play7_pic_groupBox";
			this->play7_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play7_pic_groupBox->TabIndex = 49;
			this->play7_pic_groupBox->TabStop = false;
			this->play7_pic_groupBox->Text = L"Play 7";
			this->play7_pic_groupBox->Visible = false;
			// 
			// play7_pictureBox1
			// 
			this->play7_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play7_pictureBox1->Name = L"play7_pictureBox1";
			this->play7_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox1->TabIndex = 43;
			this->play7_pictureBox1->TabStop = false;
			// 
			// play7_pictureBox4
			// 
			this->play7_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play7_pictureBox4->Name = L"play7_pictureBox4";
			this->play7_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox4->TabIndex = 46;
			this->play7_pictureBox4->TabStop = false;
			// 
			// play7_pictureBox2
			// 
			this->play7_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play7_pictureBox2->Name = L"play7_pictureBox2";
			this->play7_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox2->TabIndex = 44;
			this->play7_pictureBox2->TabStop = false;
			// 
			// play7_pictureBox3
			// 
			this->play7_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play7_pictureBox3->Name = L"play7_pictureBox3";
			this->play7_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox3->TabIndex = 45;
			this->play7_pictureBox3->TabStop = false;
			// 
			// play8_pic_groupBox
			// 
			this->play8_pic_groupBox->Controls->Add(this->play8_pictureBox1);
			this->play8_pic_groupBox->Controls->Add(this->play8_pictureBox4);
			this->play8_pic_groupBox->Controls->Add(this->play8_pictureBox2);
			this->play8_pic_groupBox->Controls->Add(this->play8_pictureBox3);
			this->play8_pic_groupBox->Enabled = false;
			this->play8_pic_groupBox->Location = System::Drawing::Point(241, 40);
			this->play8_pic_groupBox->Name = L"play8_pic_groupBox";
			this->play8_pic_groupBox->Size = System::Drawing::Size(234, 75);
			this->play8_pic_groupBox->TabIndex = 49;
			this->play8_pic_groupBox->TabStop = false;
			this->play8_pic_groupBox->Text = L"Play 8";
			this->play8_pic_groupBox->Visible = false;
			// 
			// play8_pictureBox1
			// 
			this->play8_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play8_pictureBox1->Name = L"play8_pictureBox1";
			this->play8_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox1->TabIndex = 43;
			this->play8_pictureBox1->TabStop = false;
			// 
			// play8_pictureBox4
			// 
			this->play8_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play8_pictureBox4->Name = L"play8_pictureBox4";
			this->play8_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox4->TabIndex = 46;
			this->play8_pictureBox4->TabStop = false;
			// 
			// play8_pictureBox2
			// 
			this->play8_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play8_pictureBox2->Name = L"play8_pictureBox2";
			this->play8_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox2->TabIndex = 44;
			this->play8_pictureBox2->TabStop = false;
			// 
			// play8_pictureBox3
			// 
			this->play8_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play8_pictureBox3->Name = L"play8_pictureBox3";
			this->play8_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox3->TabIndex = 45;
			this->play8_pictureBox3->TabStop = false;
			// 
			// play3_score_groupBox
			// 
			this->play3_score_groupBox->Controls->Add(this->play3_score_picBox4);
			this->play3_score_groupBox->Controls->Add(this->play3_score_picBox3);
			this->play3_score_groupBox->Controls->Add(this->play3_score_picBox2);
			this->play3_score_groupBox->Controls->Add(this->play3_score_picBox1);
			this->play3_score_groupBox->Enabled = false;
			this->play3_score_groupBox->Location = System::Drawing::Point(481, 415);
			this->play3_score_groupBox->Name = L"play3_score_groupBox";
			this->play3_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play3_score_groupBox->TabIndex = 33;
			this->play3_score_groupBox->TabStop = false;
			this->play3_score_groupBox->Visible = false;
			// 
			// play3_score_picBox4
			// 
			this->play3_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play3_score_picBox4->Name = L"play3_score_picBox4";
			this->play3_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox4->TabIndex = 31;
			this->play3_score_picBox4->TabStop = false;
			// 
			// play3_score_picBox3
			// 
			this->play3_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play3_score_picBox3->Name = L"play3_score_picBox3";
			this->play3_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox3->TabIndex = 30;
			this->play3_score_picBox3->TabStop = false;
			// 
			// play3_score_picBox2
			// 
			this->play3_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play3_score_picBox2->Name = L"play3_score_picBox2";
			this->play3_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox2->TabIndex = 29;
			this->play3_score_picBox2->TabStop = false;
			// 
			// play3_score_picBox1
			// 
			this->play3_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play3_score_picBox1->Name = L"play3_score_picBox1";
			this->play3_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox1->TabIndex = 28;
			this->play3_score_picBox1->TabStop = false;
			// 
			// play4_score_groupBox
			// 
			this->play4_score_groupBox->Controls->Add(this->play4_score_picBox4);
			this->play4_score_groupBox->Controls->Add(this->play4_score_picBox3);
			this->play4_score_groupBox->Controls->Add(this->play4_score_picBox2);
			this->play4_score_groupBox->Controls->Add(this->play4_score_picBox1);
			this->play4_score_groupBox->Enabled = false;
			this->play4_score_groupBox->Location = System::Drawing::Point(481, 340);
			this->play4_score_groupBox->Name = L"play4_score_groupBox";
			this->play4_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play4_score_groupBox->TabIndex = 33;
			this->play4_score_groupBox->TabStop = false;
			this->play4_score_groupBox->Visible = false;
			// 
			// play4_score_picBox4
			// 
			this->play4_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play4_score_picBox4->Name = L"play4_score_picBox4";
			this->play4_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox4->TabIndex = 31;
			this->play4_score_picBox4->TabStop = false;
			// 
			// play4_score_picBox3
			// 
			this->play4_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play4_score_picBox3->Name = L"play4_score_picBox3";
			this->play4_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox3->TabIndex = 30;
			this->play4_score_picBox3->TabStop = false;
			// 
			// play4_score_picBox2
			// 
			this->play4_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play4_score_picBox2->Name = L"play4_score_picBox2";
			this->play4_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox2->TabIndex = 29;
			this->play4_score_picBox2->TabStop = false;
			// 
			// play4_score_picBox1
			// 
			this->play4_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play4_score_picBox1->Name = L"play4_score_picBox1";
			this->play4_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox1->TabIndex = 28;
			this->play4_score_picBox1->TabStop = false;
			// 
			// play5_score_groupBox
			// 
			this->play5_score_groupBox->Controls->Add(this->play5_score_picBox4);
			this->play5_score_groupBox->Controls->Add(this->play5_score_picBox3);
			this->play5_score_groupBox->Controls->Add(this->play5_score_picBox2);
			this->play5_score_groupBox->Controls->Add(this->play5_score_picBox1);
			this->play5_score_groupBox->Enabled = false;
			this->play5_score_groupBox->Location = System::Drawing::Point(481, 265);
			this->play5_score_groupBox->Name = L"play5_score_groupBox";
			this->play5_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play5_score_groupBox->TabIndex = 33;
			this->play5_score_groupBox->TabStop = false;
			this->play5_score_groupBox->Visible = false;
			// 
			// play5_score_picBox4
			// 
			this->play5_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play5_score_picBox4->Name = L"play5_score_picBox4";
			this->play5_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox4->TabIndex = 31;
			this->play5_score_picBox4->TabStop = false;
			// 
			// play5_score_picBox3
			// 
			this->play5_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play5_score_picBox3->Name = L"play5_score_picBox3";
			this->play5_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox3->TabIndex = 30;
			this->play5_score_picBox3->TabStop = false;
			// 
			// play5_score_picBox2
			// 
			this->play5_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play5_score_picBox2->Name = L"play5_score_picBox2";
			this->play5_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox2->TabIndex = 29;
			this->play5_score_picBox2->TabStop = false;
			// 
			// play5_score_picBox1
			// 
			this->play5_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play5_score_picBox1->Name = L"play5_score_picBox1";
			this->play5_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox1->TabIndex = 28;
			this->play5_score_picBox1->TabStop = false;
			// 
			// play6_score_groupBox
			// 
			this->play6_score_groupBox->Controls->Add(this->play6_score_picBox4);
			this->play6_score_groupBox->Controls->Add(this->play6_score_picBox3);
			this->play6_score_groupBox->Controls->Add(this->play6_score_picBox2);
			this->play6_score_groupBox->Controls->Add(this->play6_score_picBox1);
			this->play6_score_groupBox->Enabled = false;
			this->play6_score_groupBox->Location = System::Drawing::Point(481, 190);
			this->play6_score_groupBox->Name = L"play6_score_groupBox";
			this->play6_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play6_score_groupBox->TabIndex = 33;
			this->play6_score_groupBox->TabStop = false;
			this->play6_score_groupBox->Visible = false;
			// 
			// play6_score_picBox4
			// 
			this->play6_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play6_score_picBox4->Name = L"play6_score_picBox4";
			this->play6_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox4->TabIndex = 31;
			this->play6_score_picBox4->TabStop = false;
			// 
			// play6_score_picBox3
			// 
			this->play6_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play6_score_picBox3->Name = L"play6_score_picBox3";
			this->play6_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox3->TabIndex = 30;
			this->play6_score_picBox3->TabStop = false;
			// 
			// play6_score_picBox2
			// 
			this->play6_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play6_score_picBox2->Name = L"play6_score_picBox2";
			this->play6_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox2->TabIndex = 29;
			this->play6_score_picBox2->TabStop = false;
			// 
			// play6_score_picBox1
			// 
			this->play6_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play6_score_picBox1->Name = L"play6_score_picBox1";
			this->play6_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox1->TabIndex = 28;
			this->play6_score_picBox1->TabStop = false;
			// 
			// play7_score_groupBox
			// 
			this->play7_score_groupBox->Controls->Add(this->play7_score_picBox4);
			this->play7_score_groupBox->Controls->Add(this->play7_score_picBox3);
			this->play7_score_groupBox->Controls->Add(this->play7_score_picBox2);
			this->play7_score_groupBox->Controls->Add(this->play7_score_picBox1);
			this->play7_score_groupBox->Enabled = false;
			this->play7_score_groupBox->Location = System::Drawing::Point(481, 115);
			this->play7_score_groupBox->Name = L"play7_score_groupBox";
			this->play7_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play7_score_groupBox->TabIndex = 33;
			this->play7_score_groupBox->TabStop = false;
			this->play7_score_groupBox->Visible = false;
			// 
			// play7_score_picBox4
			// 
			this->play7_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play7_score_picBox4->Name = L"play7_score_picBox4";
			this->play7_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox4->TabIndex = 31;
			this->play7_score_picBox4->TabStop = false;
			// 
			// play7_score_picBox3
			// 
			this->play7_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play7_score_picBox3->Name = L"play7_score_picBox3";
			this->play7_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox3->TabIndex = 30;
			this->play7_score_picBox3->TabStop = false;
			// 
			// play7_score_picBox2
			// 
			this->play7_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play7_score_picBox2->Name = L"play7_score_picBox2";
			this->play7_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox2->TabIndex = 29;
			this->play7_score_picBox2->TabStop = false;
			// 
			// play7_score_picBox1
			// 
			this->play7_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play7_score_picBox1->Name = L"play7_score_picBox1";
			this->play7_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox1->TabIndex = 28;
			this->play7_score_picBox1->TabStop = false;
			// 
			// play8_score_groupBox
			// 
			this->play8_score_groupBox->Controls->Add(this->play8_score_picBox4);
			this->play8_score_groupBox->Controls->Add(this->play8_score_picBox3);
			this->play8_score_groupBox->Controls->Add(this->play8_score_picBox2);
			this->play8_score_groupBox->Controls->Add(this->play8_score_picBox1);
			this->play8_score_groupBox->Enabled = false;
			this->play8_score_groupBox->Location = System::Drawing::Point(481, 40);
			this->play8_score_groupBox->Name = L"play8_score_groupBox";
			this->play8_score_groupBox->Size = System::Drawing::Size(68, 75);
			this->play8_score_groupBox->TabIndex = 33;
			this->play8_score_groupBox->TabStop = false;
			this->play8_score_groupBox->Visible = false;
			// 
			// play8_score_picBox4
			// 
			this->play8_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play8_score_picBox4->Name = L"play8_score_picBox4";
			this->play8_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox4->TabIndex = 31;
			this->play8_score_picBox4->TabStop = false;
			// 
			// play8_score_picBox3
			// 
			this->play8_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play8_score_picBox3->Name = L"play8_score_picBox3";
			this->play8_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox3->TabIndex = 30;
			this->play8_score_picBox3->TabStop = false;
			// 
			// play8_score_picBox2
			// 
			this->play8_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play8_score_picBox2->Name = L"play8_score_picBox2";
			this->play8_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox2->TabIndex = 29;
			this->play8_score_picBox2->TabStop = false;
			// 
			// play8_score_picBox1
			// 
			this->play8_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play8_score_picBox1->Name = L"play8_score_picBox1";
			this->play8_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox1->TabIndex = 28;
			this->play8_score_picBox1->TabStop = false;
			// 
			// VentanaPlay
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Sienna;
			this->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->ClientSize = System::Drawing::Size(823, 652);
			this->Controls->Add(this->play3_pic_groupBox);
			this->Controls->Add(this->play4_pic_groupBox);
			this->Controls->Add(this->rand_comb_groupBox);
			this->Controls->Add(this->yellow_button);
			this->Controls->Add(this->play8_score_groupBox);
			this->Controls->Add(this->quit_game_groupBox);
			this->Controls->Add(this->play7_score_groupBox);
			this->Controls->Add(this->play6_score_groupBox);
			this->Controls->Add(this->play5_score_groupBox);
			this->Controls->Add(this->play4_score_groupBox);
			this->Controls->Add(this->play3_score_groupBox);
			this->Controls->Add(this->play8_pic_groupBox);
			this->Controls->Add(this->play7_pic_groupBox);
			this->Controls->Add(this->play6_pic_groupBox);
			this->Controls->Add(this->play5_pic_groupBox);
			this->Controls->Add(this->blank_score_button);
			this->Controls->Add(this->play2_score_groupBox);
			this->Controls->Add(this->play2_pic_groupBox);
			this->Controls->Add(this->blank_button);
			this->Controls->Add(this->play1_pic_groupBox);
			this->Controls->Add(this->score_groupBox1);
			this->Controls->Add(this->lose_groupBox);
			this->Controls->Add(this->win_groupBox);
			this->Controls->Add(this->repetition_label);
			this->Controls->Add(this->difficulty_label);
			this->Controls->Add(this->titulo_label);
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
			this->play1_groupBox->ResumeLayout(false);
			this->play1_score_groupBox->ResumeLayout(false);
			this->quit_game_groupBox->ResumeLayout(false);
			this->quit_game_groupBox->PerformLayout();
			this->rand_comb_groupBox->ResumeLayout(false);
			this->win_groupBox->ResumeLayout(false);
			this->win_groupBox->PerformLayout();
			this->lose_groupBox->ResumeLayout(false);
			this->lose_groupBox->PerformLayout();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_pictureBox4))->EndInit();
			this->score_groupBox1->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play1_score_picBox1))->EndInit();
			this->play1_pic_groupBox->ResumeLayout(false);
			this->play2_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_pictureBox3))->EndInit();
			this->play2_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play2_score_picBox1))->EndInit();
			this->play3_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_pictureBox3))->EndInit();
			this->play4_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_pictureBox3))->EndInit();
			this->play5_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_pictureBox3))->EndInit();
			this->play6_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_pictureBox3))->EndInit();
			this->play7_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_pictureBox3))->EndInit();
			this->play8_pic_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox1))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_pictureBox3))->EndInit();
			this->play3_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play3_score_picBox1))->EndInit();
			this->play4_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play4_score_picBox1))->EndInit();
			this->play5_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play5_score_picBox1))->EndInit();
			this->play6_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play6_score_picBox1))->EndInit();
			this->play7_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play7_score_picBox1))->EndInit();
			this->play8_score_groupBox->ResumeLayout(false);
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox4))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox3))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox2))->EndInit();
			(cli::safe_cast<System::ComponentModel::ISupportInitialize^>(this->play8_score_picBox1))->EndInit();
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
		
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;
		
		//code for focusing the buttons

		bool_red_button = true;

	}
	private: System::Void blue_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_blue_button = true;
	}
	private: System::Void green_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_green_button = true;
	}
	private: System::Void yellow_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_yellow_button = true;
	}
	private: System::Void pink_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;

		//code for focusing the buttons

		bool_pink_button = true;
	}
	private: System::Void brown_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;

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
		quit_game_groupBox->Visible = true;
		quit_game_groupBox->Enabled = true;
	}


	private: System::Void play1_guess1_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{

		if (bool_red_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess1_button->BackgroundImage = red_button->BackgroundImage;
				play1_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
				play1_guess1_button->BackColor = red_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((red_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess1_button->BackgroundImage = red_button->BackgroundImage;
					play1_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
					play1_guess1_button->BackColor = red_button->BackColor;
				}
			}

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess1_button->BackgroundImage = blue_button->BackgroundImage;
				play1_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
				play1_guess1_button->BackColor = blue_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((blue_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess1_button->BackgroundImage = blue_button->BackgroundImage;
					play1_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
					play1_guess1_button->BackColor = blue_button->BackColor;
				}
			}

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess1_button->BackgroundImage = green_button->BackgroundImage;
				play1_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
				play1_guess1_button->BackColor = green_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((green_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess1_button->BackgroundImage = green_button->BackgroundImage;
					play1_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
					play1_guess1_button->BackColor = green_button->BackColor;
				}
			}

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
				play1_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
				play1_guess1_button->BackColor = yellow_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((yellow_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
					play1_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
					play1_guess1_button->BackColor = yellow_button->BackColor;
				}
			}

			bool_yellow_button= false;
		}
		if (bool_pink_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess1_button->BackgroundImage = pink_button->BackgroundImage;
				play1_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
				play1_guess1_button->BackColor = pink_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((pink_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess1_button->BackgroundImage = pink_button->BackgroundImage;
					play1_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
					play1_guess1_button->BackColor = pink_button->BackColor;
				}
			}

			bool_pink_button = false;
		}
		if (bool_brown_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess1_button->BackgroundImage = brown_button->BackgroundImage;
				play1_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
				play1_guess1_button->BackColor = brown_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((brown_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess1_button->BackgroundImage = brown_button->BackgroundImage;
					play1_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
					play1_guess1_button->BackColor = brown_button->BackColor;
				}
			}

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play1_guess2_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (bool_red_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess2_button->BackgroundImage = red_button->BackgroundImage;
				play1_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
				play1_guess2_button->BackColor = red_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((red_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess2_button->BackgroundImage = red_button->BackgroundImage;
					play1_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
					play1_guess2_button->BackColor = red_button->BackColor;
				}
			}

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess2_button->BackgroundImage = blue_button->BackgroundImage;
				play1_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
				play1_guess2_button->BackColor = blue_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((blue_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess2_button->BackgroundImage = blue_button->BackgroundImage;
					play1_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
					play1_guess2_button->BackColor = blue_button->BackColor;
				}
			}

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess2_button->BackgroundImage = green_button->BackgroundImage;
				play1_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
				play1_guess2_button->BackColor = green_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((green_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess2_button->BackgroundImage = green_button->BackgroundImage;
					play1_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
					play1_guess2_button->BackColor = green_button->BackColor;
				}
			}

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
				play1_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
				play1_guess2_button->BackColor = yellow_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((yellow_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
					play1_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
					play1_guess2_button->BackColor = yellow_button->BackColor;
				}
			}

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess2_button->BackgroundImage = pink_button->BackgroundImage;
				play1_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
				play1_guess2_button->BackColor = pink_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((pink_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess2_button->BackgroundImage = pink_button->BackgroundImage;
					play1_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
					play1_guess2_button->BackColor = pink_button->BackColor;
				}
			}

			bool_pink_button = false;
		}
		if (bool_brown_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess2_button->BackgroundImage = brown_button->BackgroundImage;
				play1_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
				play1_guess2_button->BackColor = brown_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((brown_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess3_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess2_button->BackgroundImage = brown_button->BackgroundImage;
					play1_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
					play1_guess2_button->BackColor = brown_button->BackColor;
				}
			}

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play1_guess3_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (bool_red_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess3_button->BackgroundImage = red_button->BackgroundImage;
				play1_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
				play1_guess3_button->BackColor = red_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((red_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess3_button->BackgroundImage = red_button->BackgroundImage;
					play1_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
					play1_guess3_button->BackColor = red_button->BackColor;
				}
			}

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess3_button->BackgroundImage = blue_button->BackgroundImage;
				play1_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
				play1_guess3_button->BackColor = blue_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((blue_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess3_button->BackgroundImage = blue_button->BackgroundImage;
					play1_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
					play1_guess3_button->BackColor = blue_button->BackColor;
				}
			}

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess3_button->BackgroundImage = green_button->BackgroundImage;
				play1_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
				play1_guess3_button->BackColor = red_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((green_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess3_button->BackgroundImage = green_button->BackgroundImage;
					play1_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
					play1_guess3_button->BackColor = green_button->BackColor;
				}
			}

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
				play1_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
				play1_guess3_button->BackColor = yellow_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((yellow_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
					play1_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
					play1_guess3_button->BackColor = yellow_button->BackColor;
				}
			}

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess3_button->BackgroundImage = pink_button->BackgroundImage;
				play1_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
				play1_guess3_button->BackColor = pink_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((pink_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess3_button->BackgroundImage = pink_button->BackgroundImage;
					play1_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
					play1_guess3_button->BackColor = pink_button->BackColor;
				}
			}

			bool_pink_button = false;
		}
		if (bool_brown_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess3_button->BackgroundImage = brown_button->BackgroundImage;
				play1_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
				play1_guess3_button->BackColor = brown_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((brown_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess4_button->BackgroundImage))
				{
					play1_guess3_button->BackgroundImage = brown_button->BackgroundImage;
					play1_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
					play1_guess3_button->BackColor = brown_button->BackColor;
				}
			}

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play1_guess4_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (bool_red_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess4_button->BackgroundImage = red_button->BackgroundImage;
				play1_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
				play1_guess4_button->BackColor = red_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((red_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (red_button->BackgroundImage != play1_guess3_button->BackgroundImage))
				{
					play1_guess4_button->BackgroundImage = red_button->BackgroundImage;
					play1_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
					play1_guess4_button->BackColor = red_button->BackColor;
				}
			}

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess4_button->BackgroundImage = blue_button->BackgroundImage;
				play1_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
				play1_guess4_button->BackColor = blue_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((blue_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (blue_button->BackgroundImage != play1_guess3_button->BackgroundImage))
				{
					play1_guess4_button->BackgroundImage = blue_button->BackgroundImage;
					play1_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
					play1_guess4_button->BackColor = blue_button->BackColor;
				}
			}

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess4_button->BackgroundImage = green_button->BackgroundImage;
				play1_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
				play1_guess4_button->BackColor = green_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((green_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (green_button->BackgroundImage != play1_guess3_button->BackgroundImage))
				{
					play1_guess4_button->BackgroundImage = green_button->BackgroundImage;
					play1_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
					play1_guess4_button->BackColor = red_button->BackColor;
				}
			}

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
				play1_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
				play1_guess4_button->BackColor = yellow_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((yellow_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (yellow_button->BackgroundImage != play1_guess3_button->BackgroundImage))
				{
					play1_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
					play1_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
					play1_guess4_button->BackColor = yellow_button->BackColor;
				}
			}

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess4_button->BackgroundImage = pink_button->BackgroundImage;
				play1_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
				play1_guess4_button->BackColor = pink_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((pink_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (pink_button->BackgroundImage != play1_guess3_button->BackgroundImage))
				{
					play1_guess4_button->BackgroundImage = pink_button->BackgroundImage;
					play1_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
					play1_guess4_button->BackColor = pink_button->BackColor;
				}
			}

			bool_pink_button = false;
		}
		if (bool_brown_button == true)
		{
			if (objSettings->getElementRep() == true)
			{
				play1_guess4_button->BackgroundImage = brown_button->BackgroundImage;
				play1_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
				play1_guess4_button->BackColor = brown_button->BackColor;
			}
			else if (objSettings->getElementRep() == false)
			{
				if ((brown_button->BackgroundImage != play1_guess1_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess2_button->BackgroundImage) && (brown_button->BackgroundImage != play1_guess3_button->BackgroundImage))
				{
					play1_guess4_button->BackgroundImage = brown_button->BackgroundImage;
					play1_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
					play1_guess4_button->BackColor = brown_button->BackColor;
				}
			}

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}

	/*
	private: System::Void play2_guess1_button_Click(System::Object^ sender, System::EventArgs^ e)
	{

		if (bool_red_button == true)
		{
			play2_guess1_button->BackgroundImage = red_button->BackgroundImage;
			play2_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play2_guess1_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play2_guess1_button->BackgroundImage = blue_button->BackgroundImage;
			play2_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play2_guess1_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play2_guess1_button->BackgroundImage = green_button->BackgroundImage;
			play2_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play2_guess1_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
			play2_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play2_guess1_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play2_guess1_button->BackgroundImage = pink_button->BackgroundImage;
			play2_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play2_guess1_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess1_button->BackgroundImage = brown_button->BackgroundImage;
			play2_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play2_guess1_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play2_guess2_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play2_guess2_button->BackgroundImage = red_button->BackgroundImage;
			play2_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play2_guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play2_guess2_button->BackgroundImage = blue_button->BackgroundImage;
			play2_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play2_guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play2_guess2_button->BackgroundImage = green_button->BackgroundImage;
			play2_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play2_guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			play2_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play2_guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play2_guess2_button->BackgroundImage = pink_button->BackgroundImage;
			play2_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play2_guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess2_button->BackgroundImage = brown_button->BackgroundImage;
			play2_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play2_guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play2_guess3_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play2_guess3_button->BackgroundImage = red_button->BackgroundImage;
			play2_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play2_guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play2_guess3_button->BackgroundImage = blue_button->BackgroundImage;
			play2_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play2_guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play2_guess3_button->BackgroundImage = green_button->BackgroundImage;
			play2_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play2_guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			play2_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play2_guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play2_guess3_button->BackgroundImage = pink_button->BackgroundImage;
			play2_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play2_guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess3_button->BackgroundImage = brown_button->BackgroundImage;
			play2_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play2_guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play2_guess4_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play2_guess4_button->BackgroundImage = red_button->BackgroundImage;
			play2_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play2_guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play2_guess4_button->BackgroundImage = blue_button->BackgroundImage;
			play2_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play2_guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play2_guess4_button->BackgroundImage = green_button->BackgroundImage;
			play2_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play2_guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			play2_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play2_guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play2_guess4_button->BackgroundImage = pink_button->BackgroundImage;
			play2_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play2_guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play2_guess4_button->BackgroundImage = brown_button->BackgroundImage;
			play2_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play2_guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	
	private: System::Void play3_guess1_button_Click(System::Object^ sender, System::EventArgs^ e)
	{

		if (bool_red_button == true)
		{
			play3_guess1_button->BackgroundImage = red_button->BackgroundImage;
			play3_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play3_guess1_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play3_guess1_button->BackgroundImage = blue_button->BackgroundImage;
			play3_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play3_guess1_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play3_guess1_button->BackgroundImage = green_button->BackgroundImage;
			play3_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play3_guess1_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
			play3_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play3_guess1_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play3_guess1_button->BackgroundImage = pink_button->BackgroundImage;
			play3_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play3_guess1_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess1_button->BackgroundImage = brown_button->BackgroundImage;
			play3_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play3_guess1_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play3_guess2_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play3_guess2_button->BackgroundImage = red_button->BackgroundImage;
			play3_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play3_guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play3_guess2_button->BackgroundImage = blue_button->BackgroundImage;
			play3_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play3_guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play3_guess2_button->BackgroundImage = green_button->BackgroundImage;
			play3_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play3_guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			play3_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play3_guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play3_guess2_button->BackgroundImage = pink_button->BackgroundImage;
			play3_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play3_guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess2_button->BackgroundImage = brown_button->BackgroundImage;
			play3_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play3_guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play3_guess3_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play3_guess3_button->BackgroundImage = red_button->BackgroundImage;
			play3_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play3_guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play3_guess3_button->BackgroundImage = blue_button->BackgroundImage;
			play3_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play3_guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play3_guess3_button->BackgroundImage = green_button->BackgroundImage;
			play3_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play3_guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			play3_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play3_guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play3_guess3_button->BackgroundImage = pink_button->BackgroundImage;
			play3_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play3_guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess3_button->BackgroundImage = brown_button->BackgroundImage;
			play3_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play3_guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play3_guess4_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play3_guess4_button->BackgroundImage = red_button->BackgroundImage;
			play3_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play3_guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play3_guess4_button->BackgroundImage = blue_button->BackgroundImage;
			play3_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play3_guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play3_guess4_button->BackgroundImage = green_button->BackgroundImage;
			play3_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play3_guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			play3_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play3_guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play3_guess4_button->BackgroundImage = pink_button->BackgroundImage;
			play3_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play3_guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play3_guess4_button->BackgroundImage = brown_button->BackgroundImage;
			play3_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play3_guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	


	private: System::Void play4_guess1_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{

		if (bool_red_button == true)
		{
			play1_guess1_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess1_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess1_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess1_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess1_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play4_guess2_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess2_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess2_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess2_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess2_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play4_guess3_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess3_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess3_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess3_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess3_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play4_guess4_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess4_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess4_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess4_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess4_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}

	private: System::Void play5_guess1_button_Click1(System::Object^ sender, System::EventArgs^ e)
{

	if (bool_red_button == true)
	{
		play1_guess1_button->BackgroundImage = red_button->BackgroundImage;
		play1_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
		play1_guess1_button->BackColor = red_button->BackColor;

		bool_red_button = false;
	}
	if (bool_blue_button == true)
	{
		play1_guess1_button->BackgroundImage = blue_button->BackgroundImage;
		play1_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
		play1_guess1_button->BackColor = blue_button->BackColor;

		bool_blue_button = false;
	}
	if (bool_green_button == true)
	{
		play1_guess1_button->BackgroundImage = green_button->BackgroundImage;
		play1_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
		play1_guess1_button->BackColor = green_button->BackColor;

		bool_green_button = false;
	}
	if (bool_yellow_button == true)
	{
		play1_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
		play1_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
		play1_guess1_button->BackColor = yellow_button->BackColor;

		bool_yellow_button = false;
	}
	if (bool_pink_button == true)
	{
		play1_guess1_button->BackgroundImage = pink_button->BackgroundImage;
		play1_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
		play1_guess1_button->BackColor = pink_button->BackColor;

		bool_pink_button = false;
	}
	if (bool_yellow_button == true)
	{
		play1_guess1_button->BackgroundImage = brown_button->BackgroundImage;
		play1_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
		play1_guess1_button->BackColor = brown_button->BackColor;

		bool_brown_button = false;
	}

	//Enter button 
	enter_play_ready++;
	if (enter_play_ready >= 4)
	{
		enter_play_button->Enabled = true;
	}
}
	private: System::Void play5_guess2_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess2_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess2_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess2_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess2_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play5_guess3_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess3_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess3_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess3_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess3_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play5_guess4_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess4_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess4_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess4_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess4_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}

	private: System::Void play6_guess1_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{

		if (bool_red_button == true)
		{
			play1_guess1_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess1_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess1_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess1_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess1_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play6_guess2_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess2_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess2_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess2_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess2_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play6_guess3_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess3_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess3_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess3_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess3_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play6_guess4_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess4_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess4_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess4_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess4_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}

	private: System::Void play7_guess1_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{

		if (bool_red_button == true)
		{
			play1_guess1_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess1_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess1_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess1_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess1_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess1_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess1_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess1_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play7_guess2_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess2_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess2_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess2_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess2_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess2_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess2_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess2_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play7_guess3_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess3_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess3_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess3_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess3_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess3_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess3_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess3_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	private: System::Void play7_guess4_button_Click1(System::Object^ sender, System::EventArgs^ e)
	{
		if (bool_red_button == true)
		{
			play1_guess4_button->BackgroundImage = red_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = red_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = red_button->BackColor;

			bool_red_button = false;
		}
		if (bool_blue_button == true)
		{
			play1_guess4_button->BackgroundImage = blue_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = blue_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = blue_button->BackColor;

			bool_blue_button = false;
		}
		if (bool_green_button == true)
		{
			play1_guess4_button->BackgroundImage = green_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = green_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = green_button->BackColor;

			bool_green_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = yellow_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = yellow_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = yellow_button->BackColor;

			bool_yellow_button = false;
		}
		if (bool_pink_button == true)
		{
			play1_guess4_button->BackgroundImage = pink_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = pink_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = pink_button->BackColor;

			bool_pink_button = false;
		}
		if (bool_yellow_button == true)
		{
			play1_guess4_button->BackgroundImage = brown_button->BackgroundImage;
			play1_guess4_button->BackgroundImageLayout = brown_button->BackgroundImageLayout;
			play1_guess4_button->BackColor = brown_button->BackColor;

			bool_brown_button = false;
		}

		//Enter button 
		enter_play_ready++;
		if (enter_play_ready >= 4)
		{
			enter_play_button->Enabled = true;
		}
	}
	*/


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
		//random_combination_rep();

		//1 = red
		//2 = blue
		//3 = green
		//4 = yellow
		//5 = pink
		//6 = brown

		if (objSettings->getElementRep() == true)
		{
			objSettings->setRandomNum1();
			objSettings->setRandomNum2();
			objSettings->setRandomNum3();
			objSettings->setRandomNum4();
		}
		else if (objSettings->getElementRep() == false)
		{
			objSettings->setRandomNum1();

			objSettings->setRandomNum2();
			while (objSettings->getRandomNum2() == objSettings->getRandomNum1())
			{
				objSettings->setRandomNum2();
			}

			objSettings->setRandomNum3();
			while ((objSettings->getRandomNum3() == objSettings->getRandomNum1()) || (objSettings->getRandomNum3() == objSettings->getRandomNum2()))
			{
				objSettings->setRandomNum3();
			}

			objSettings->setRandomNum4();
			while ((objSettings->getRandomNum4() == objSettings->getRandomNum1()) || (objSettings->getRandomNum4() == objSettings->getRandomNum2()) || (objSettings->getRandomNum4() == objSettings->getRandomNum3()))
			{
				objSettings->setRandomNum4();
			}
		}



		if (objSettings->getRandomNum1() == 1)
			rand_comb1_button->BackgroundImage = red_button->BackgroundImage;
		if (objSettings->getRandomNum1() == 2)
			rand_comb1_button->BackgroundImage = blue_button->BackgroundImage;
		if (objSettings->getRandomNum1() == 3)
			rand_comb1_button->BackgroundImage = green_button->BackgroundImage;
		if (objSettings->getRandomNum1() == 4)
			rand_comb1_button->BackgroundImage = yellow_button->BackgroundImage;
		if (objSettings->getRandomNum1() == 5)
			rand_comb1_button->BackgroundImage = pink_button->BackgroundImage;
		if (objSettings->getRandomNum1() == 6)
			rand_comb1_button->BackgroundImage = brown_button->BackgroundImage;

		if (objSettings->getRandomNum2() == 1)
			rand_comb2_button->BackgroundImage = red_button->BackgroundImage;
		if (objSettings->getRandomNum2() == 2)
			rand_comb2_button->BackgroundImage = blue_button->BackgroundImage;
		if (objSettings->getRandomNum2() == 3)
			rand_comb2_button->BackgroundImage = green_button->BackgroundImage;
		if (objSettings->getRandomNum2() == 4)
			rand_comb2_button->BackgroundImage = yellow_button->BackgroundImage;
		if (objSettings->getRandomNum2() == 5)
			rand_comb2_button->BackgroundImage = pink_button->BackgroundImage;
		if (objSettings->getRandomNum2() == 6)
			rand_comb2_button->BackgroundImage = brown_button->BackgroundImage;

		if (objSettings->getRandomNum3() == 1)
			rand_comb3_button->BackgroundImage = red_button->BackgroundImage;
		if (objSettings->getRandomNum3() == 2)
			rand_comb3_button->BackgroundImage = blue_button->BackgroundImage;
		if (objSettings->getRandomNum3() == 3)
			rand_comb3_button->BackgroundImage = green_button->BackgroundImage;
		if (objSettings->getRandomNum3() == 4)
			rand_comb3_button->BackgroundImage = yellow_button->BackgroundImage;
		if (objSettings->getRandomNum3() == 5)
			rand_comb3_button->BackgroundImage = pink_button->BackgroundImage;
		if (objSettings->getRandomNum3() == 6)
			rand_comb3_button->BackgroundImage = brown_button->BackgroundImage;

		if (objSettings->getRandomNum4() == 1)
			rand_comb4_button->BackgroundImage = red_button->BackgroundImage;
		if (objSettings->getRandomNum4() == 2)
			rand_comb4_button->BackgroundImage = blue_button->BackgroundImage;
		if (objSettings->getRandomNum4() == 3)
			rand_comb4_button->BackgroundImage = green_button->BackgroundImage;
		if (objSettings->getRandomNum4() == 4)
			rand_comb4_button->BackgroundImage = yellow_button->BackgroundImage;
		if (objSettings->getRandomNum4() == 5)
			rand_comb4_button->BackgroundImage = pink_button->BackgroundImage;
		if (objSettings->getRandomNum4() == 6)
			rand_comb4_button->BackgroundImage = brown_button->BackgroundImage;

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

		salirToolStripMenuItem->Enabled = true;

		actual_play = 1;
	}

	private: System::Void enter_play_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		srand(time(0));

		//calificacion negra
		if (play1_guess1_button->BackgroundImage == rand_comb1_button->BackgroundImage)
		{
			objSettings->setRandomNUM();
			num_rand1 = objSettings->getRandomNUM();

			if (num_rand1 == 1)
			{
				play1_score_btn1->BackgroundImage = black_button->BackgroundImage;
				//play1_score_btn1->BackgroundImageLayout = Stretch;
			}
			else if (num_rand1 == 2)
			{
				play1_score_btn2->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand1 == 3)
			{
				play1_score_btn3->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand1 == 4)
			{
				play1_score_btn4->BackgroundImage = black_button->BackgroundImage;
			}

		}

		if (play1_guess2_button->BackgroundImage == rand_comb2_button->BackgroundImage)
		{
			objSettings->setRandomNUM();
			num_rand2 = objSettings->getRandomNUM();

			while (num_rand2 == num_rand1)
			{
				objSettings->setRandomNUM();
				num_rand2 = objSettings->getRandomNUM();
			}

			if (num_rand2 == 1)
			{
				play1_score_btn1->BackgroundImage = black_button->BackgroundImage;
				//play1_score_btn1->BackgroundImageLayout = Stretch;
			}
			else if (num_rand2 == 2)
			{
				play1_score_btn2->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand2 == 3)
			{
				play1_score_btn3->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand2 == 4)
			{
				play1_score_btn4->BackgroundImage = black_button->BackgroundImage;
			}
		}

		if (play1_guess3_button->BackgroundImage == rand_comb3_button->BackgroundImage)
		{
			objSettings->setRandomNUM();
			num_rand3 = objSettings->getRandomNUM();

			while ((num_rand3 == num_rand1) || (num_rand3 == num_rand2))
			{
				objSettings->setRandomNUM();
				num_rand3 = objSettings->getRandomNUM();
			}

			if (num_rand3 == 1)
			{
				play1_score_btn1->BackgroundImage = black_button->BackgroundImage;
				//play1_score_btn1->BackgroundImageLayout = Stretch;
			}
			else if (num_rand3 == 2)
			{
				play1_score_btn2->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand3 == 3)
			{
				play1_score_btn3->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand3 == 4)
			{
				play1_score_btn4->BackgroundImage = black_button->BackgroundImage;
			}
		}

		if (play1_guess4_button->BackgroundImage == rand_comb4_button->BackgroundImage)
		{
			objSettings->setRandomNUM();
			num_rand4 = objSettings->getRandomNUM();


			while ((num_rand4 == num_rand1) || (num_rand4 == num_rand2) || (num_rand4 == num3))
			{
				objSettings->setRandomNUM();
				num_rand4 = objSettings->getRandomNUM();
			}

			if (num_rand4 == 1)
			{
				play1_score_btn1->BackgroundImage = black_button->BackgroundImage;
				//play1_score_btn1->BackgroundImageLayout = Stretch;
			}
			else if (num_rand4 == 2)
			{
				play1_score_btn2->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand4 == 3)
			{
				play1_score_btn3->BackgroundImage = black_button->BackgroundImage;
			}
			else if (num_rand4 == 4)
			{
				play1_score_btn4->BackgroundImage = black_button->BackgroundImage;
			}
		}

		//calificacion blanca
		if (objSettings->getElementRep() == true)
		{

		}
		else if (objSettings->getElementRep() == false)
		{
			if ((play1_guess1_button->BackgroundImage == rand_comb2_button->BackgroundImage) || (play1_guess1_button->BackgroundImage == rand_comb3_button->BackgroundImage) || (play1_guess1_button->BackgroundImage == rand_comb4_button->BackgroundImage))
			{
				if ((play1_score_btn1->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn1->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn1->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn2->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn2->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn2->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn3->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn3->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn3->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn4->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn4->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn4->BackgroundImage = white_button->BackgroundImage;
				}
			}
			if ((play1_guess2_button->BackgroundImage == rand_comb1_button->BackgroundImage) || (play1_guess2_button->BackgroundImage == rand_comb3_button->BackgroundImage) || (play1_guess2_button->BackgroundImage == rand_comb4_button->BackgroundImage))
			{
				if ((play1_score_btn1->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn1->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn1->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn2->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn2->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn2->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn3->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn3->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn3->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn4->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn4->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn4->BackgroundImage = white_button->BackgroundImage;
				}
			}
			if ((play1_guess3_button->BackgroundImage == rand_comb1_button->BackgroundImage) || (play1_guess3_button->BackgroundImage == rand_comb2_button->BackgroundImage) || (play1_guess3_button->BackgroundImage == rand_comb4_button->BackgroundImage))
			{
				if ((play1_score_btn1->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn1->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn1->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn2->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn2->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn2->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn3->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn3->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn3->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn4->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn4->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn4->BackgroundImage = white_button->BackgroundImage;
				}
			}
			if ((play1_guess4_button->BackgroundImage == rand_comb1_button->BackgroundImage) || (play1_guess4_button->BackgroundImage == rand_comb2_button->BackgroundImage) || (play1_guess4_button->BackgroundImage == rand_comb3_button->BackgroundImage))
			{
				if ((play1_score_btn1->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn1->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn1->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn2->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn2->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn2->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn3->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn3->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn3->BackgroundImage = white_button->BackgroundImage;
				}
				else if ((play1_score_btn4->BackgroundImage != black_button->BackgroundImage) && (play1_score_btn4->BackgroundImage != white_button->BackgroundImage))
				{
					play1_score_btn4->BackgroundImage = white_button->BackgroundImage;
				}
			}
		}

		//ganar juego / perder juego
		if ((play1_score_btn1->BackgroundImage == black_button->BackgroundImage) && (play1_score_btn2->BackgroundImage == black_button->BackgroundImage) && (play1_score_btn3->BackgroundImage == black_button->BackgroundImage) && (play1_score_btn4->BackgroundImage == black_button->BackgroundImage))
		{
			win_groupBox->Visible = true;
			win_groupBox->Enabled = true;

			rand_comb_groupBox->Visible = true;
			win = true;
		}
		
		else
		{
			if ((objSettings->getDifficulty() == 1) && (win == false))
			{
				if (actual_play == 8)
				{
					enter_play_button->Enabled = false;

					//codigo para terminar el juego
					lose_groupBox->Visible = true;
					lose_groupBox->Enabled = true;

					rand_comb_groupBox->Visible = true;
				}
			}
			else if ((objSettings->getDifficulty() == 2) && (win == false))
			{
				if (actual_play == 7)
				{
					enter_play_button->Enabled = false;

					//codigo para terminar el juego
					lose_groupBox->Visible = true;
					lose_groupBox->Enabled = true;

					rand_comb_groupBox->Visible = true;
				}
			}
			else if ((objSettings->getDifficulty() == 3) && (win == false))
			{
				if (actual_play == 6)
				{
					enter_play_button->Enabled = false;

					//codigo para terminar el juego
					lose_groupBox->Visible = true;
					lose_groupBox->Enabled = true;

					rand_comb_groupBox->Visible = true;
				}
			}
		}


		//jugadas

		if (actual_play == 1)
		{
			/*
			play1_groupBox->Enabled = false;
			play2_groupBox->Enabled = true;

			play2_groupBox->Visible = true;

			play2_guess1_button->Enabled = true;
			play2_guess2_button->Enabled = true;
			play2_guess3_button->Enabled = true;
			play2_guess4_button->Enabled = true;
			*/



			//picture boxes
			play1_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play1_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play1_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play1_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;

			play1_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play1_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play1_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play1_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;

			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;


			play2_pic_groupBox->Visible = true;
			play2_pic_groupBox->Enabled = true;
			play2_score_groupBox->Visible = true;
			play2_score_groupBox->Enabled = true;
		}
		
		else if (actual_play == 2)
		{
			/*
			play2_groupBox->Enabled = false;
			play3_groupBox->Enabled = true;

			play3_groupBox->Visible = true;

			play3_guess1_button->Enabled = true;
			play3_guess2_button->Enabled = true;
			play3_guess3_button->Enabled = true;
			play3_guess4_button->Enabled = true;

			
			//codigo para calificar jugada 2
			if (play2_guess1_button->BackgroundImage == rand_comb1_button->BackgroundImage)
			{
				objSettings->setRandomNUM();
				num_rand1 = objSettings->getRandomNUM();

				if (num_rand1 == 1)
				{
					play2_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand1 == 2)
				{
					play2_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand1 == 3)
				{
					play2_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand1 == 4)
				{
					play2_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}

			if (play2_guess2_button->BackgroundImage == rand_comb2_button->BackgroundImage)
			{
				objSettings->setRandomNUM();
				num_rand2 = objSettings->getRandomNUM();

				while (num_rand2 == num_rand1)
				{
					objSettings->setRandomNUM();
					num_rand2 = objSettings->getRandomNUM();
				}

				if (num_rand2 == 1)
				{
					play2_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand2 == 2)
				{
					play2_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand2 == 3)
				{
					play2_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand2 == 4)
				{
					play2_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}

			if (play2_guess3_button->BackgroundImage == rand_comb3_button->BackgroundImage)
			{
				objSettings->setRandomNUM();
				num_rand3 = objSettings->getRandomNUM();

				while ((num_rand3 == num_rand1) || (num_rand3 == num_rand2))
				{
					objSettings->setRandomNUM();
					num_rand3 = objSettings->getRandomNUM();
				}

				if (num_rand3 == 1)
				{
					play2_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand3 == 2)
				{
					play2_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand3 == 3)
				{
					play2_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand3 == 4)
				{
					play2_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}

			if (play2_guess4_button->BackgroundImage == rand_comb4_button->BackgroundImage)
			{
				objSettings->setRandomNUM();
				num_rand4 = objSettings->getRandomNUM();

				while ((num_rand4 == num_rand1) || (num_rand4 == num_rand2) || (num_rand4 == num3))
				{
					objSettings->setRandomNUM();
					num_rand4 = objSettings->getRandomNUM();
				}

				if (num_rand4 == 1)
				{
					play2_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand4 == 2)
				{
					play2_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand4 == 3)
				{
					play2_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand4 == 4)
				{
					play2_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}
			*/

			//picture boxes
			play2_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play2_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play2_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play2_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;
				
			play2_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play2_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play2_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play2_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;
				
			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;


			play3_pic_groupBox->Visible = true;
			play3_pic_groupBox->Enabled = true;
			play3_score_groupBox->Visible = true;
			play3_score_groupBox->Enabled = true;
		}

		else if (actual_play == 3)
		{
			
			/*
			play3_groupBox->Enabled = false;
			play4_groupBox->Enabled = true;

			play4_groupBox->Visible = true;

			play4_guess1_button->Enabled = true;
			play4_guess2_button->Enabled = true;
			play4_guess3_button->Enabled = true;
			play4_guess4_button->Enabled = true;

			//codigo para calificar jugada 3
			if (play3_guess1_button->BackgroundImage == rand_comb1_button->BackgroundImage)
			{
				num_rand1 = objSettings->getRandomNUM();

				if (num_rand1 == 1)
				{
					play3_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand1 == 2)
				{
					play3_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand1 == 3)
				{
					play3_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand1 == 4)
				{
					play3_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}

			if (play3_guess2_button->BackgroundImage == rand_comb2_button->BackgroundImage)
			{
				num_rand2 = objSettings->getRandomNUM();

				if (num_rand2 == num_rand1)
				{
					while (num_rand2 == num_rand1)
					{
						num_rand2 = objSettings->getRandomNUM();
					}
				}

				if (num_rand2 == 1)
				{
					play3_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand2 == 2)
				{
					play3_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand2 == 3)
				{
					play3_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand2 == 4)
				{
					play3_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}

			if (play3_guess3_button->BackgroundImage == rand_comb3_button->BackgroundImage)
			{
				num_rand3 = objSettings->getRandomNUM();

				if (num_rand3 == num_rand1 || num_rand3 == num_rand2)
				{
					while (num_rand3 == num_rand1 || num_rand3 == num_rand2)
					{
						num_rand3 = objSettings->getRandomNUM();
					}
				}

				if (num_rand3 == 1)
				{
					play3_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand3 == 2)
				{
					play3_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand3 == 3)
				{
					play3_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand3 == 4)
				{
					play3_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}

			if (play3_guess4_button->BackgroundImage == rand_comb4_button->BackgroundImage)
			{
				num_rand4 = objSettings->getRandomNUM();

				if (num_rand4 == num_rand1 || num_rand4 == num_rand2 || num_rand4 == num_rand3)
				{
					while (num_rand3 == num_rand1 || num_rand3 == num_rand2 || num_rand4 == num3)
					{
						num_rand4 = objSettings->getRandomNUM();
					}
				}

				if (num_rand4 == 1)
				{
					play3_score_btn1->BackgroundImage = black_button->BackgroundImage;
					//play1_score_btn1->BackgroundImageLayout = Stretch;
				}
				else if (num_rand4 == 2)
				{
					play3_score_btn2->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand4 == 3)
				{
					play3_score_btn3->BackgroundImage = black_button->BackgroundImage;
				}
				else if (num_rand4 == 4)
				{
					play3_score_btn4->BackgroundImage = black_button->BackgroundImage;
				}
			}
			*/
			
			//picture boxes
			play3_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play3_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play3_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play3_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;
			
			play3_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play3_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play3_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play3_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;
			
			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;
				
			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;

			play4_pic_groupBox->Visible = true;
			play4_pic_groupBox->Enabled = true;
			play4_score_groupBox->Visible = true;
			play4_score_groupBox->Enabled = true;
		}
	
		else if (actual_play == 4)
		{
			/*
			play4_groupBox->Enabled = false;
			play5_groupBox->Enabled = true;

			play5_groupBox->Visible = true;

			play5_guess1_button->Enabled = true;
			play5_guess2_button->Enabled = true;
			play5_guess3_button->Enabled = true;
			play5_guess4_button->Enabled = true;

			//codigo para calificar jugada 4
			*/

			//picture boxes
			play4_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play4_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play4_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play4_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;

			play4_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play4_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play4_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play4_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;

			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;

			play5_pic_groupBox->Visible = true;
			play5_pic_groupBox->Enabled = true;
			play5_score_groupBox->Visible = true;
			play5_score_groupBox->Enabled = true;
		}
		
		else if (actual_play == 5)
		{
			/*
			play5_groupBox->Enabled = false;
			play6_groupBox->Enabled = true;

			play6_groupBox->Visible = true;

			play6_guess1_button->Enabled = true;
			play6_guess2_button->Enabled = true;
			play6_guess3_button->Enabled = true;
			play6_guess4_button->Enabled = true;

			//codigo para calificar jugada 5
			*/

			//picture boxes
			play5_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play5_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play5_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play5_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;

			play5_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play5_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play5_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play5_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;

			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;

			play6_pic_groupBox->Visible = true;
			play6_pic_groupBox->Enabled = true;
			play6_score_groupBox->Visible = true;
			play6_score_groupBox->Enabled = true;
		}
		
		else if (actual_play == 6)
		{
			/*
			play6_groupBox->Enabled = false;
			play7_groupBox->Enabled = true;

			play7_groupBox->Visible = true;

			play7_guess1_button->Enabled = true;
			play7_guess2_button->Enabled = true;
			play7_guess3_button->Enabled = true;
			play7_guess4_button->Enabled = true;

			//codigo para calificar jugada 6
			*/

			//picture boxes
			play6_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play6_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play6_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play6_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;

			play6_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play6_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play6_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play6_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;

			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;

			play7_pic_groupBox->Visible = true;
			play7_pic_groupBox->Enabled = true;
			play7_score_groupBox->Visible = true;
			play7_score_groupBox->Enabled = true;
		}
		
		else if (actual_play == 7)
		{
			/*
			play7_groupBox->Enabled = false;
			play8_groupBox->Enabled = true;

			play8_groupBox->Visible = true;

			play8_guess1_button->Enabled = true;
			play8_guess2_button->Enabled = true;
			play8_guess3_button->Enabled = true;
			play8_guess4_button->Enabled = true;

			//codigo para calificar jugada 7
			*/

			//picture boxes
			play7_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play7_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play7_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play7_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;

			play7_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play7_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play7_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play7_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;

			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;

			play8_pic_groupBox->Visible = true;
			play8_pic_groupBox->Enabled = true;
			play8_score_groupBox->Visible = true;
			play8_score_groupBox->Enabled = true;
		}
		
		else if (actual_play == 8)
		{
			/*
			play8_groupBox->Enabled = false;

			//codigo para calificar jugada 8
			*/

			//picture boxes
			play8_pictureBox1->BackgroundImage = play1_guess1_button->BackgroundImage;
			play8_pictureBox2->BackgroundImage = play1_guess2_button->BackgroundImage;
			play8_pictureBox3->BackgroundImage = play1_guess3_button->BackgroundImage;
			play8_pictureBox4->BackgroundImage = play1_guess4_button->BackgroundImage;

			play8_score_picBox1->BackgroundImage = play1_score_btn1->BackgroundImage;
			play8_score_picBox2->BackgroundImage = play1_score_btn2->BackgroundImage;
			play8_score_picBox3->BackgroundImage = play1_score_btn3->BackgroundImage;
			play8_score_picBox4->BackgroundImage = play1_score_btn4->BackgroundImage;

			//guess button back to blank
			play1_guess1_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess1_button->BackColor = blank_button->BackColor;
			play1_guess2_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess2_button->BackColor = blank_button->BackColor;
			play1_guess3_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess3_button->BackColor = blank_button->BackColor;
			play1_guess4_button->BackgroundImage = blank_button->BackgroundImage;
			play1_guess4_button->BackColor = blank_button->BackColor;

			//score button back to blank
			play1_score_btn1->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn1->BackColor = blank_score_button->BackColor;
			play1_score_btn2->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn2->BackColor = blank_score_button->BackColor;
			play1_score_btn3->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn3->BackColor = blank_score_button->BackColor;
			play1_score_btn4->BackgroundImage = blank_score_button->BackgroundImage;
			play1_score_btn4->BackColor = blank_score_button->BackColor;

		}



		actual_play++;
	
		enter_play_button->Enabled = false;
	}


	private: System::Void color_position_bbtn_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void color_wbtn_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}



	private: System::Void play7_groupBox_Enter(System::Object^ sender, System::EventArgs^ e) 
	{
		
	}

	private: System::Void label1_Click(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void ok_quit_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		if (quit_game == true)
		{
			VentanaPlay::Close();

			//devuleve los valores del reloj/cronometro a 0
			seconds = 0;
			minutes = 0;
			hours = 0;
		}
		else if (quit_game == false)
		{
			quit_game_groupBox->Enabled = false;
			quit_game_groupBox->Visible = false;
		}
	}
	private: System::Void quit_yes_radioButton_CheckedChanged(System::Object^ sender, System::EventArgs^ e) 
	{
		quit_game = true;
	
		ok_quit_button->Enabled = true;
	}
	private: System::Void quit_no_radioButton_CheckedChanged(System::Object^ sender, System::EventArgs^ e) 
	{
		quit_game = false;

		ok_quit_button->Enabled = true;
	}
	

	private: System::Void label1_Click_1(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void ok_win_button_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//codigo para guardar el highscore del jugador

		VentanaPlay::Close();

		//devuleve los valores del reloj/cronometro a 0
		seconds = 0;
		minutes = 0;
		hours = 0;
	}
	private: System::Void ok_lose_button_Click(System::Object^ sender, System::EventArgs^ e)	
	{
		VentanaPlay::Close();

		//devuleve los valores del reloj/cronometro a 0
		seconds = 0;
		minutes = 0;
		hours = 0;
	}




	};
}
