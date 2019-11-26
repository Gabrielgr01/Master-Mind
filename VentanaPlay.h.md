#Master-Mind

//VentanaPlay.h
//Fully Documented

#pragma once

#include "ConfigurationClass.h"
#include "HowToPlay.h"
#include <iostream>
#include <stdio.h>
#include <stdlib.h>
#include <ctime>
#include <chrono>
#include <thread>
#include <fstream>
#include <string>
#include <msclr\marshal_cppstd.h>
#include <time.h>


namespace MasterMindProyectoFinal {

	using namespace System;
	using namespace System::ComponentModel;
	using namespace System::Collections;
	using namespace System::Windows::Forms;
	using namespace System::Data;
	using namespace System::Drawing;
	using namespace System::Media;
	using namespace std::this_thread;
	using namespace std::chrono;

	/// <summary>
	/// Resumen de MyForm
	/// </summary>
	public ref class VentanaPlay : public System::Windows::Forms::Form
	{

	public: ConfigurationClass* objSettings = new ConfigurationClass();



	public:
		//variables para guardar valores del cronómetro/temporizador
		static int seconds = 0; //para el reloj
		static int minutes = 0; //para el reloj
		static int hours = 0; //para el reloj
		static int secondsP = 60; //por jugada - P de Play
		static int minutesP = 0;  //por jugada - P de Play
		static int secondsG = 60; //por juego - G de Game
		static int minutesG = 29; //por juego - G de Game
		static int hoursG = 1; //por juego - G de Game
		static int secondsTimer = 0; //para el timer del tiempo total por juego
		static int minutesTimer = 0; //para el timer del tiempo total por juego
		static int hoursTimer = 0;  //para el timer del tiempo total por juego
		int game_timer_int;

		String^ sec;
		String^ min;
		String^ hour;
		String^ secP;
		String^ minP;
		String^ secG;
		String^ minG;
		String^ hourG;

		static String^ userNameBtt; //username

		//color/letter/number/shape buttons
		bool bool_red_button = false;
		bool bool_blue_button = false;
		bool bool_green_button = false;
		bool bool_yellow_button = false;
		bool bool_pink_button = false;
		bool bool_brown_button = false;

		//random numbers
		int num1;
		int num2;
		int num3;
		int num4;
		int num_rand1 = 0;
		int num_rand2 = 0;
		int num_rand3 = 0;
		int num_rand4 = 0;

		bool quit_game = false;
		bool en_partida = false; //dice si se está en una partida

		int actual_play = 1; //marca la jugada actual
		bool win = false; //marca si se ganó o no

		//variables para saber si el juego se guardó o se cargó
		int saved_plays = 0;
		bool saved_game = false;
		bool loaded_game = false;
		
		//imagenes de los seis botones de color/letter/number/shape
		static Image^ btn_img1_play;
		static Image^ btn_img2_play;
		static Image^ btn_img3_play;
		static Image^ btn_img4_play;
		static Image^ btn_img5_play;
		static Image^ btn_img6_play;

		//variables conteniendo los archivo de audio
		SoundPlayer^ backg = gcnew SoundPlayer(".//SoundFx//Jazz.wav");
		SoundPlayer^ applause = gcnew SoundPlayer(".//SoundFx//Applause.wav");
		SoundPlayer^ disappointment = gcnew SoundPlayer(".//SoundFx//Disappointment.wav");



	public:
		VentanaPlay(ConfigurationClass* objSettings)
		{
			//CODIGO DEL CONSTRUCTOR:
			InitializeComponent();

			backg->PlayLooping(); //backg starts looping

			this->objSettings = objSettings; //asigna al objeto objSettings el valor del objeto obtenido por parámetro

			//difficulty labels
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

			//Element repetition labels
			if (objSettings->getElementRep() == true)
			{
				repetition_label->Text = "Element repetition: ON";
			}
			else if (objSettings->getElementRep() == false)
			{
				repetition_label->Text = "Element repetition: OFF";
			}

			//determina si se seleccionó Clock Disabled en la configuración y le quita la visibilidad al texto del reloj
			if ((objSettings->getClock() == false) && (objSettings->getTimekeeperGame() == false) && (objSettings->getTimekeeperPlay() == false))
			{
				Time->Visible = false;
			}

			Username_label->Text = userNameBtt; //el nombre de usuario ingresado en la VentanaPrincipal se lo asigna al label correspondiente de la VentanaPlay


			//Element Type: le asigna a los botones de color/letter/number/shape la opción seleccionada en la configuración			
			red_button->BackgroundImage = btn_img1_play;
			blue_button->BackgroundImage = btn_img2_play;
			green_button->BackgroundImage = btn_img3_play;
			yellow_button->BackgroundImage = btn_img4_play;
			pink_button->BackgroundImage = btn_img5_play;
			brown_button->BackgroundImage = btn_img6_play;

			//pone o quita texto dependiendo de la opción seleccionada en la configuración
			if (objSettings->getElementType() == 1)
			{
				red_button->Text = "Red";
				blue_button-> Text = "Blue";
				green_button->Text = "Green";
				yellow_button->Text = "Yellow";
				pink_button->Text = "Pink";
				brown_button->Text = "Brown";
			}
			else if ((objSettings->getElementType() == 2) || (objSettings->getElementType() == 3) || (objSettings->getElementType() == 4))
			{
				red_button->Text = "";
				blue_button->Text = "";
				green_button->Text = "";
				yellow_button->Text = "";
				pink_button->Text = "";
				brown_button->Text = "";
			}
			
			//busca en el archivo donde se guarda el juego si se ha guardado algun juego o no 
			using namespace std;
			string titulo;
			string dato;
			ifstream saved_game_file;
			saved_game_file.open("SavedGameData.txt", ios::in); //opens file, in read-only mode
			saved_game_file >> titulo;
			saved_game_file >> dato;
			if (dato == "true")
				saved_game = true;
			else if (dato == "false")
				saved_game = false;
			saved_game_file.close(); //closes file
			

			//guess button backg image set to blank
			play1_guess1_button->BackgroundImage == blank_button->BackgroundImage;
			play1_guess2_button->BackgroundImage == blank_button->BackgroundImage;
			play1_guess3_button->BackgroundImage == blank_button->BackgroundImage;
			play1_guess4_button->BackgroundImage == blank_button->BackgroundImage;
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


	private: System::ComponentModel::IContainer^ components;

	private: System::Windows::Forms::Label^ titulo_label;
	private: System::Windows::Forms::Label^ Username_label;
	private: System::Windows::Forms::Label^ Time;

	private: System::Windows::Forms::Timer^ you_lose_timer;
	private: System::Windows::Forms::Timer^ Clock;
	private: System::Windows::Forms::Timer^ game_timer;
	private: System::Windows::Forms::Label^ gameTimer_label;
	private: System::Windows::Forms::Label^ num_gameTimer_label;

	private: System::Windows::Forms::Label^ color_wbtn_label;
	private: System::Windows::Forms::Label^ color_position_bbtn_label;

	private: System::Windows::Forms::Label^ difficulty_label;
	private: System::Windows::Forms::Label^ repetition_label;

	private: System::Windows::Forms::Button^ Vent_Play_Start;
	private: System::Windows::Forms::Button^ enter_play_button;


	private: System::Windows::Forms::Button^ red_button;
	private: System::Windows::Forms::Button^ blue_button;
	private: System::Windows::Forms::Button^ green_button;
	private: System::Windows::Forms::Button^ yellow_button;
	private: System::Windows::Forms::Button^ pink_button;
	private: System::Windows::Forms::Button^ brown_button;

	private: System::Windows::Forms::GroupBox^ play1_groupBox;
	private: System::Windows::Forms::Button^ play1_guess1_button;
	private: System::Windows::Forms::Button^ play1_guess2_button;
	private: System::Windows::Forms::Button^ play1_guess3_button;
	private: System::Windows::Forms::Button^ play1_guess4_button;

	private: System::Windows::Forms::GroupBox^ play1_score_groupBox;
	private: System::Windows::Forms::Button^ play1_score_btn1;
	private: System::Windows::Forms::Button^ play1_score_btn2;
	private: System::Windows::Forms::Button^ play1_score_btn3;
	private: System::Windows::Forms::Button^ play1_score_btn4;

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
	
	private: System::Windows::Forms::Button^ blank_button;
	private: System::Windows::Forms::Button^ blank_score_button;
	private: System::Windows::Forms::Button^ black_button;
	private: System::Windows::Forms::Button^ white_button;



	private: System::Windows::Forms::GroupBox^ play1_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play1_pictureBox4;
	
	private: System::Windows::Forms::GroupBox^ play2_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox4;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play2_pictureBox3;

	private: System::Windows::Forms::GroupBox^ play3_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play3_pictureBox4;

	private: System::Windows::Forms::GroupBox^ play4_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play4_pictureBox4;

	private: System::Windows::Forms::GroupBox^ play5_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play5_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play5_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play5_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play5_pictureBox4;

	private: System::Windows::Forms::GroupBox^ play6_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play6_pictureBox4;

	private: System::Windows::Forms::GroupBox^ play7_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play7_pictureBox4;

	private: System::Windows::Forms::GroupBox^ play8_pic_groupBox;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox1;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox2;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox3;
	private: System::Windows::Forms::PictureBox^ play8_pictureBox4;



	private: System::Windows::Forms::GroupBox^ score_groupBox1;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox4;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play1_score_picBox1;

	private: System::Windows::Forms::GroupBox^ play2_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play2_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play2_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play2_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play2_score_picBox4;

	private: System::Windows::Forms::GroupBox^ play3_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play3_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play3_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play3_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play3_score_picBox4;

	private: System::Windows::Forms::GroupBox^ play4_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play4_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play4_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play4_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play4_score_picBox4;

	private: System::Windows::Forms::GroupBox^ play5_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play5_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play5_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play5_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play5_score_picBox4;

	private: System::Windows::Forms::GroupBox^ play6_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play6_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play6_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play6_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play6_score_picBox4;

	private: System::Windows::Forms::GroupBox^ play7_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play7_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play7_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play7_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play7_score_picBox4;

	private: System::Windows::Forms::GroupBox^ play8_score_groupBox;
	private: System::Windows::Forms::PictureBox^ play8_score_picBox1;
	private: System::Windows::Forms::PictureBox^ play8_score_picBox2;
	private: System::Windows::Forms::PictureBox^ play8_score_picBox3;
	private: System::Windows::Forms::PictureBox^ play8_score_picBox4;



	private: System::Windows::Forms::Label^ label1;
	private: System::Windows::Forms::Label^ label4;
	private: System::Windows::Forms::Label^ label3;
	private: System::Windows::Forms::Label^ label2;
	private: System::Windows::Forms::Label^ label8;
	private: System::Windows::Forms::Label^ label7;
	private: System::Windows::Forms::Label^ label6;
	private: System::Windows::Forms::Label^ label5;


	private: System::Windows::Forms::MenuStrip^ menuStrip1;
	private: System::Windows::Forms::ToolStripMenuItem^ archivoToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ saveToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ loadGameToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ instruccionesToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ salirToolStripMenuItem;

	private: System::Windows::Forms::GroupBox^ load_warning_groupBox;
	private: System::Windows::Forms::Button^ ok_load_warn_btn;
	private: System::Windows::Forms::Label^ load_warn_label;

	private: System::Windows::Forms::GroupBox^ quit_game_groupBox;
	private: System::Windows::Forms::Label^ quit_label;
	private: System::Windows::Forms::RadioButton^ quit_yes_radioButton;
	private: System::Windows::Forms::RadioButton^ quit_no_radioButton;
	private: System::Windows::Forms::Button^ ok_quit_button;


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
			this->label4 = (gcnew System::Windows::Forms::Label());
			this->label3 = (gcnew System::Windows::Forms::Label());
			this->label2 = (gcnew System::Windows::Forms::Label());
			this->label1 = (gcnew System::Windows::Forms::Label());
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
			this->load_warning_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->ok_load_warn_btn = (gcnew System::Windows::Forms::Button());
			this->load_warn_label = (gcnew System::Windows::Forms::Label());
			this->rand_comb4_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb3_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb2_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb1_button = (gcnew System::Windows::Forms::Button());
			this->rand_comb_groupBox = (gcnew System::Windows::Forms::GroupBox());
			this->label8 = (gcnew System::Windows::Forms::Label());
			this->label7 = (gcnew System::Windows::Forms::Label());
			this->label6 = (gcnew System::Windows::Forms::Label());
			this->label5 = (gcnew System::Windows::Forms::Label());
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
			this->you_lose_timer = (gcnew System::Windows::Forms::Timer(this->components));
			this->Username_label = (gcnew System::Windows::Forms::Label());
			this->game_timer = (gcnew System::Windows::Forms::Timer(this->components));
			this->gameTimer_label = (gcnew System::Windows::Forms::Label());
			this->num_gameTimer_label = (gcnew System::Windows::Forms::Label());
			this->menuStrip1->SuspendLayout();
			this->play1_groupBox->SuspendLayout();
			this->play1_score_groupBox->SuspendLayout();
			this->quit_game_groupBox->SuspendLayout();
			this->load_warning_groupBox->SuspendLayout();
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
			this->red_button->Location = System::Drawing::Point(582, 234);
			this->red_button->Name = L"red_button";
			this->red_button->Size = System::Drawing::Size(50, 45);
			this->red_button->TabIndex = 0;
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
			this->blue_button->Location = System::Drawing::Point(582, 285);
			this->blue_button->Name = L"blue_button";
			this->blue_button->Size = System::Drawing::Size(50, 45);
			this->blue_button->TabIndex = 1;
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
			this->green_button->Location = System::Drawing::Point(582, 336);
			this->green_button->Name = L"green_button";
			this->green_button->Size = System::Drawing::Size(50, 45);
			this->green_button->TabIndex = 2;
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
			this->yellow_button->Location = System::Drawing::Point(582, 387);
			this->yellow_button->Name = L"yellow_button";
			this->yellow_button->Size = System::Drawing::Size(50, 45);
			this->yellow_button->TabIndex = 3;
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
			this->pink_button->Location = System::Drawing::Point(582, 438);
			this->pink_button->Name = L"pink_button";
			this->pink_button->Size = System::Drawing::Size(50, 45);
			this->pink_button->TabIndex = 4;
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
			this->brown_button->Location = System::Drawing::Point(582, 489);
			this->brown_button->Name = L"brown_button";
			this->brown_button->Size = System::Drawing::Size(50, 45);
			this->brown_button->TabIndex = 5;
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
			this->saveToolStripMenuItem->Enabled = false;
			this->saveToolStripMenuItem->Name = L"saveToolStripMenuItem";
			this->saveToolStripMenuItem->Size = System::Drawing::Size(134, 22);
			this->saveToolStripMenuItem->Text = L"Save Game";
			this->saveToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::saveToolStripMenuItem_Click);
			// 
			// loadGameToolStripMenuItem
			// 
			this->loadGameToolStripMenuItem->Enabled = false;
			this->loadGameToolStripMenuItem->Name = L"loadGameToolStripMenuItem";
			this->loadGameToolStripMenuItem->Size = System::Drawing::Size(134, 22);
			this->loadGameToolStripMenuItem->Text = L"Load Game";
			this->loadGameToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::loadGameToolStripMenuItem_Click);
			// 
			// ayudaToolStripMenuItem
			// 
			this->ayudaToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->instruccionesToolStripMenuItem });
			this->ayudaToolStripMenuItem->Name = L"ayudaToolStripMenuItem";
			this->ayudaToolStripMenuItem->Size = System::Drawing::Size(44, 20);
			this->ayudaToolStripMenuItem->Text = L"Help";
			this->ayudaToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::ayudaToolStripMenuItem_Click);
			// 
			// instruccionesToolStripMenuItem
			// 
			this->instruccionesToolStripMenuItem->Name = L"instruccionesToolStripMenuItem";
			this->instruccionesToolStripMenuItem->Size = System::Drawing::Size(138, 22);
			this->instruccionesToolStripMenuItem->Text = L"How to play";
			this->instruccionesToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::instruccionesToolStripMenuItem_Click);
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
			this->titulo_label->BackColor = System::Drawing::Color::Gainsboro;
			this->titulo_label->Font = (gcnew System::Drawing::Font(L"Modern No. 20", 26.25F, static_cast<System::Drawing::FontStyle>((System::Drawing::FontStyle::Bold | System::Drawing::FontStyle::Italic)),
				System::Drawing::GraphicsUnit::Point, static_cast<System::Byte>(0)));
			this->titulo_label->ForeColor = System::Drawing::Color::OrangeRed;
			this->titulo_label->Location = System::Drawing::Point(12, 33);
			this->titulo_label->Name = L"titulo_label";
			this->titulo_label->Size = System::Drawing::Size(206, 41);
			this->titulo_label->TabIndex = 20;
			this->titulo_label->Text = L"Mastermind";
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
			this->Vent_Play_Start->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 20.25F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
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
			this->play1_groupBox->Controls->Add(this->label4);
			this->play1_groupBox->Controls->Add(this->label3);
			this->play1_groupBox->Controls->Add(this->label2);
			this->play1_groupBox->Controls->Add(this->label1);
			this->play1_groupBox->Controls->Add(this->play1_guess1_button);
			this->play1_groupBox->Controls->Add(this->play1_guess2_button);
			this->play1_groupBox->Controls->Add(this->play1_guess3_button);
			this->play1_groupBox->Controls->Add(this->play1_guess4_button);
			this->play1_groupBox->Location = System::Drawing::Point(577, 557);
			this->play1_groupBox->Name = L"play1_groupBox";
			this->play1_groupBox->Size = System::Drawing::Size(234, 83);
			this->play1_groupBox->TabIndex = 23;
			this->play1_groupBox->TabStop = false;
			this->play1_groupBox->Text = L"Guess";
			// 
			// label4
			// 
			this->label4->AutoSize = true;
			this->label4->Location = System::Drawing::Point(195, 67);
			this->label4->Name = L"label4";
			this->label4->Size = System::Drawing::Size(13, 13);
			this->label4->TabIndex = 21;
			this->label4->Text = L"4";
			// 
			// label3
			// 
			this->label3->AutoSize = true;
			this->label3->Location = System::Drawing::Point(139, 67);
			this->label3->Name = L"label3";
			this->label3->Size = System::Drawing::Size(13, 13);
			this->label3->TabIndex = 20;
			this->label3->Text = L"3";
			// 
			// label2
			// 
			this->label2->AutoSize = true;
			this->label2->Location = System::Drawing::Point(82, 67);
			this->label2->Name = L"label2";
			this->label2->Size = System::Drawing::Size(13, 13);
			this->label2->TabIndex = 19;
			this->label2->Text = L"2";
			// 
			// label1
			// 
			this->label1->AutoSize = true;
			this->label1->Location = System::Drawing::Point(24, 67);
			this->label1->Name = L"label1";
			this->label1->Size = System::Drawing::Size(13, 13);
			this->label1->TabIndex = 18;
			this->label1->Text = L"1";
			this->label1->Click += gcnew System::EventHandler(this, &VentanaPlay::label1_Click_2);
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
			this->play1_score_groupBox->Location = System::Drawing::Point(697, 340);
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
			this->enter_play_button->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->enter_play_button->Location = System::Drawing::Point(681, 512);
			this->enter_play_button->Name = L"enter_play_button";
			this->enter_play_button->Size = System::Drawing::Size(92, 23);
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
			this->quit_game_groupBox->Location = System::Drawing::Point(198, 33);
			this->quit_game_groupBox->Name = L"quit_game_groupBox";
			this->quit_game_groupBox->Size = System::Drawing::Size(396, 176);
			this->quit_game_groupBox->TabIndex = 35;
			this->quit_game_groupBox->TabStop = false;
			this->quit_game_groupBox->Text = L"Quit Game";
			this->quit_game_groupBox->Visible = false;
			// 
			// quit_yes_radioButton
			// 
			this->quit_yes_radioButton->AutoSize = true;
			this->quit_yes_radioButton->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Regular,
				System::Drawing::GraphicsUnit::Point, static_cast<System::Byte>(0)));
			this->quit_yes_radioButton->Location = System::Drawing::Point(74, 83);
			this->quit_yes_radioButton->Name = L"quit_yes_radioButton";
			this->quit_yes_radioButton->Size = System::Drawing::Size(50, 20);
			this->quit_yes_radioButton->TabIndex = 37;
			this->quit_yes_radioButton->TabStop = true;
			this->quit_yes_radioButton->Text = L"Yes";
			this->quit_yes_radioButton->UseVisualStyleBackColor = true;
			this->quit_yes_radioButton->CheckedChanged += gcnew System::EventHandler(this, &VentanaPlay::quit_yes_radioButton_CheckedChanged);
			// 
			// quit_no_radioButton
			// 
			this->quit_no_radioButton->AutoSize = true;
			this->quit_no_radioButton->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Regular,
				System::Drawing::GraphicsUnit::Point, static_cast<System::Byte>(0)));
			this->quit_no_radioButton->Location = System::Drawing::Point(262, 83);
			this->quit_no_radioButton->Name = L"quit_no_radioButton";
			this->quit_no_radioButton->Size = System::Drawing::Size(44, 20);
			this->quit_no_radioButton->TabIndex = 36;
			this->quit_no_radioButton->TabStop = true;
			this->quit_no_radioButton->Text = L"No";
			this->quit_no_radioButton->UseVisualStyleBackColor = true;
			this->quit_no_radioButton->CheckedChanged += gcnew System::EventHandler(this, &VentanaPlay::quit_no_radioButton_CheckedChanged);
			// 
			// ok_quit_button
			// 
			this->ok_quit_button->Enabled = false;
			this->ok_quit_button->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->ok_quit_button->Location = System::Drawing::Point(154, 120);
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
			this->quit_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 12, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->quit_label->Location = System::Drawing::Point(78, 43);
			this->quit_label->Name = L"quit_label";
			this->quit_label->Size = System::Drawing::Size(222, 20);
			this->quit_label->TabIndex = 20;
			this->quit_label->Text = L"Are you sure you want to quit\?";
			// 
			// load_warning_groupBox
			// 
			this->load_warning_groupBox->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->load_warning_groupBox->Controls->Add(this->ok_load_warn_btn);
			this->load_warning_groupBox->Controls->Add(this->load_warn_label);
			this->load_warning_groupBox->Enabled = false;
			this->load_warning_groupBox->Location = System::Drawing::Point(220, 217);
			this->load_warning_groupBox->Name = L"load_warning_groupBox";
			this->load_warning_groupBox->Size = System::Drawing::Size(356, 130);
			this->load_warning_groupBox->TabIndex = 51;
			this->load_warning_groupBox->TabStop = false;
			this->load_warning_groupBox->Visible = false;
			// 
			// ok_load_warn_btn
			// 
			this->ok_load_warn_btn->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Regular,
				System::Drawing::GraphicsUnit::Point, static_cast<System::Byte>(0)));
			this->ok_load_warn_btn->Location = System::Drawing::Point(148, 83);
			this->ok_load_warn_btn->Name = L"ok_load_warn_btn";
			this->ok_load_warn_btn->Size = System::Drawing::Size(75, 23);
			this->ok_load_warn_btn->TabIndex = 1;
			this->ok_load_warn_btn->Text = L"OK";
			this->ok_load_warn_btn->UseVisualStyleBackColor = true;
			this->ok_load_warn_btn->Click += gcnew System::EventHandler(this, &VentanaPlay::ok_load_warn_btn_Click);
			// 
			// load_warn_label
			// 
			this->load_warn_label->AutoSize = true;
			this->load_warn_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->load_warn_label->Location = System::Drawing::Point(18, 34);
			this->load_warn_label->Name = L"load_warn_label";
			this->load_warn_label->Size = System::Drawing::Size(323, 32);
			this->load_warn_label->TabIndex = 0;
			this->load_warn_label->Text = L"Game could not be loaded\r\n(You can only load a game if it was previously saved)";
			this->load_warn_label->TextAlign = System::Drawing::ContentAlignment::MiddleCenter;
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
			this->rand_comb1_button->UseVisualStyleBackColor = false;
			// 
			// rand_comb_groupBox
			// 
			this->rand_comb_groupBox->Controls->Add(this->label8);
			this->rand_comb_groupBox->Controls->Add(this->label7);
			this->rand_comb_groupBox->Controls->Add(this->label6);
			this->rand_comb_groupBox->Controls->Add(this->label5);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb1_button);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb4_button);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb3_button);
			this->rand_comb_groupBox->Controls->Add(this->rand_comb2_button);
			this->rand_comb_groupBox->Enabled = false;
			this->rand_comb_groupBox->Location = System::Drawing::Point(661, 438);
			this->rand_comb_groupBox->Name = L"rand_comb_groupBox";
			this->rand_comb_groupBox->Size = System::Drawing::Size(132, 68);
			this->rand_comb_groupBox->TabIndex = 40;
			this->rand_comb_groupBox->TabStop = false;
			this->rand_comb_groupBox->Text = L"Random Combination";
			this->rand_comb_groupBox->Visible = false;
			// 
			// label8
			// 
			this->label8->AutoSize = true;
			this->label8->Location = System::Drawing::Point(110, 47);
			this->label8->Name = L"label8";
			this->label8->Size = System::Drawing::Size(13, 13);
			this->label8->TabIndex = 22;
			this->label8->Text = L"4";
			// 
			// label7
			// 
			this->label7->AutoSize = true;
			this->label7->Location = System::Drawing::Point(80, 47);
			this->label7->Name = L"label7";
			this->label7->Size = System::Drawing::Size(13, 13);
			this->label7->TabIndex = 40;
			this->label7->Text = L"3";
			// 
			// label6
			// 
			this->label6->AutoSize = true;
			this->label6->Location = System::Drawing::Point(49, 47);
			this->label6->Name = L"label6";
			this->label6->Size = System::Drawing::Size(13, 13);
			this->label6->TabIndex = 22;
			this->label6->Text = L"2";
			// 
			// label5
			// 
			this->label5->AutoSize = true;
			this->label5->Location = System::Drawing::Point(15, 47);
			this->label5->Name = L"label5";
			this->label5->Size = System::Drawing::Size(13, 13);
			this->label5->TabIndex = 22;
			this->label5->Text = L"1";
			// 
			// win_groupBox
			// 
			this->win_groupBox->BackColor = System::Drawing::Color::DarkGray;
			this->win_groupBox->Controls->Add(this->ok_win_button);
			this->win_groupBox->Controls->Add(this->you_win_label);
			this->win_groupBox->Enabled = false;
			this->win_groupBox->Location = System::Drawing::Point(625, 91);
			this->win_groupBox->Name = L"win_groupBox";
			this->win_groupBox->Size = System::Drawing::Size(159, 112);
			this->win_groupBox->TabIndex = 41;
			this->win_groupBox->TabStop = false;
			this->win_groupBox->Text = L"Win";
			this->win_groupBox->Visible = false;
			// 
			// ok_win_button
			// 
			this->ok_win_button->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 9.75F, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->ok_win_button->Location = System::Drawing::Point(44, 77);
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
			this->you_win_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 20.25F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->you_win_label->ForeColor = System::Drawing::Color::ForestGreen;
			this->you_win_label->Location = System::Drawing::Point(17, 24);
			this->you_win_label->Name = L"you_win_label";
			this->you_win_label->Size = System::Drawing::Size(131, 31);
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
			this->lose_groupBox->Size = System::Drawing::Size(149, 112);
			this->lose_groupBox->TabIndex = 42;
			this->lose_groupBox->TabStop = false;
			this->lose_groupBox->Text = L"Lose";
			this->lose_groupBox->Visible = false;
			this->lose_groupBox->Enter += gcnew System::EventHandler(this, &VentanaPlay::lose_groupBox_Enter);
			// 
			// ok_lose_button
			// 
			this->ok_lose_button->Location = System::Drawing::Point(34, 77);
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
			this->you_lose_label->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 14.25F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->you_lose_label->ForeColor = System::Drawing::Color::DarkRed;
			this->you_lose_label->Location = System::Drawing::Point(15, 31);
			this->you_lose_label->Name = L"you_lose_label";
			this->you_lose_label->Size = System::Drawing::Size(117, 24);
			this->you_lose_label->TabIndex = 0;
			this->you_lose_label->Text = L"You Lose :(";
			// 
			// play1_pictureBox1
			// 
			this->play1_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_pictureBox1.BackgroundImage")));
			this->play1_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play1_pictureBox1->Name = L"play1_pictureBox1";
			this->play1_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox1->TabIndex = 43;
			this->play1_pictureBox1->TabStop = false;
			// 
			// play1_pictureBox2
			// 
			this->play1_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_pictureBox2.BackgroundImage")));
			this->play1_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play1_pictureBox2->Name = L"play1_pictureBox2";
			this->play1_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox2->TabIndex = 44;
			this->play1_pictureBox2->TabStop = false;
			// 
			// play1_pictureBox3
			// 
			this->play1_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_pictureBox3.BackgroundImage")));
			this->play1_pictureBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_pictureBox3->Location = System::Drawing::Point(118, 19);
			this->play1_pictureBox3->Name = L"play1_pictureBox3";
			this->play1_pictureBox3->Size = System::Drawing::Size(50, 45);
			this->play1_pictureBox3->TabIndex = 45;
			this->play1_pictureBox3->TabStop = false;
			// 
			// play1_pictureBox4
			// 
			this->play1_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_pictureBox4.BackgroundImage")));
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
			this->play1_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_picBox4.BackgroundImage")));
			this->play1_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play1_score_picBox4->Name = L"play1_score_picBox4";
			this->play1_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox4->TabIndex = 31;
			this->play1_score_picBox4->TabStop = false;
			// 
			// play1_score_picBox3
			// 
			this->play1_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_picBox3.BackgroundImage")));
			this->play1_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play1_score_picBox3->Name = L"play1_score_picBox3";
			this->play1_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox3->TabIndex = 30;
			this->play1_score_picBox3->TabStop = false;
			// 
			// play1_score_picBox2
			// 
			this->play1_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_picBox2.BackgroundImage")));
			this->play1_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play1_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play1_score_picBox2->Name = L"play1_score_picBox2";
			this->play1_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play1_score_picBox2->TabIndex = 29;
			this->play1_score_picBox2->TabStop = false;
			// 
			// play1_score_picBox1
			// 
			this->play1_score_picBox1->BackColor = System::Drawing::Color::Gainsboro;
			this->play1_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play1_score_picBox1.BackgroundImage")));
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
			this->play2_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_pictureBox1.BackgroundImage")));
			this->play2_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play2_pictureBox1->Name = L"play2_pictureBox1";
			this->play2_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox1->TabIndex = 43;
			this->play2_pictureBox1->TabStop = false;
			// 
			// play2_pictureBox4
			// 
			this->play2_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_pictureBox4.BackgroundImage")));
			this->play2_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play2_pictureBox4->Name = L"play2_pictureBox4";
			this->play2_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox4->TabIndex = 46;
			this->play2_pictureBox4->TabStop = false;
			// 
			// play2_pictureBox2
			// 
			this->play2_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_pictureBox2.BackgroundImage")));
			this->play2_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play2_pictureBox2->Name = L"play2_pictureBox2";
			this->play2_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play2_pictureBox2->TabIndex = 44;
			this->play2_pictureBox2->TabStop = false;
			// 
			// play2_pictureBox3
			// 
			this->play2_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_pictureBox3.BackgroundImage")));
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
			this->play2_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_score_picBox4.BackgroundImage")));
			this->play2_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play2_score_picBox4->Name = L"play2_score_picBox4";
			this->play2_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox4->TabIndex = 31;
			this->play2_score_picBox4->TabStop = false;
			// 
			// play2_score_picBox3
			// 
			this->play2_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_score_picBox3.BackgroundImage")));
			this->play2_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play2_score_picBox3->Name = L"play2_score_picBox3";
			this->play2_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox3->TabIndex = 30;
			this->play2_score_picBox3->TabStop = false;
			// 
			// play2_score_picBox2
			// 
			this->play2_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_score_picBox2.BackgroundImage")));
			this->play2_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play2_score_picBox2->Name = L"play2_score_picBox2";
			this->play2_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox2->TabIndex = 29;
			this->play2_score_picBox2->TabStop = false;
			// 
			// play2_score_picBox1
			// 
			this->play2_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play2_score_picBox1.BackgroundImage")));
			this->play2_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play2_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play2_score_picBox1->Name = L"play2_score_picBox1";
			this->play2_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play2_score_picBox1->TabIndex = 28;
			this->play2_score_picBox1->TabStop = false;
			// 
			// blank_score_button
			// 
			this->blank_score_button->BackColor = System::Drawing::Color::Gainsboro;
			this->blank_score_button->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"blank_score_button.BackgroundImage")));
			this->blank_score_button->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->blank_score_button->Enabled = false;
			this->blank_score_button->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->blank_score_button->Location = System::Drawing::Point(92, 509);
			this->blank_score_button->Name = L"blank_score_button";
			this->blank_score_button->Size = System::Drawing::Size(25, 25);
			this->blank_score_button->TabIndex = 28;
			this->blank_score_button->UseVisualStyleBackColor = false;
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
			this->play3_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_pictureBox1.BackgroundImage")));
			this->play3_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play3_pictureBox1->Name = L"play3_pictureBox1";
			this->play3_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox1->TabIndex = 43;
			this->play3_pictureBox1->TabStop = false;
			// 
			// play3_pictureBox4
			// 
			this->play3_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_pictureBox4.BackgroundImage")));
			this->play3_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play3_pictureBox4->Name = L"play3_pictureBox4";
			this->play3_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox4->TabIndex = 46;
			this->play3_pictureBox4->TabStop = false;
			// 
			// play3_pictureBox2
			// 
			this->play3_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_pictureBox2.BackgroundImage")));
			this->play3_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play3_pictureBox2->Name = L"play3_pictureBox2";
			this->play3_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play3_pictureBox2->TabIndex = 44;
			this->play3_pictureBox2->TabStop = false;
			// 
			// play3_pictureBox3
			// 
			this->play3_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_pictureBox3.BackgroundImage")));
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
			this->play4_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_pictureBox1.BackgroundImage")));
			this->play4_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play4_pictureBox1->Name = L"play4_pictureBox1";
			this->play4_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox1->TabIndex = 43;
			this->play4_pictureBox1->TabStop = false;
			// 
			// play4_pictureBox4
			// 
			this->play4_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_pictureBox4.BackgroundImage")));
			this->play4_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play4_pictureBox4->Name = L"play4_pictureBox4";
			this->play4_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox4->TabIndex = 46;
			this->play4_pictureBox4->TabStop = false;
			// 
			// play4_pictureBox2
			// 
			this->play4_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_pictureBox2.BackgroundImage")));
			this->play4_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play4_pictureBox2->Name = L"play4_pictureBox2";
			this->play4_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play4_pictureBox2->TabIndex = 44;
			this->play4_pictureBox2->TabStop = false;
			// 
			// play4_pictureBox3
			// 
			this->play4_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_pictureBox3.BackgroundImage")));
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
			this->play5_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_pictureBox1.BackgroundImage")));
			this->play5_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play5_pictureBox1->Name = L"play5_pictureBox1";
			this->play5_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox1->TabIndex = 43;
			this->play5_pictureBox1->TabStop = false;
			// 
			// play5_pictureBox4
			// 
			this->play5_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_pictureBox4.BackgroundImage")));
			this->play5_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play5_pictureBox4->Name = L"play5_pictureBox4";
			this->play5_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox4->TabIndex = 46;
			this->play5_pictureBox4->TabStop = false;
			// 
			// play5_pictureBox2
			// 
			this->play5_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_pictureBox2.BackgroundImage")));
			this->play5_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play5_pictureBox2->Name = L"play5_pictureBox2";
			this->play5_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play5_pictureBox2->TabIndex = 44;
			this->play5_pictureBox2->TabStop = false;
			// 
			// play5_pictureBox3
			// 
			this->play5_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_pictureBox3.BackgroundImage")));
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
			this->play6_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_pictureBox1.BackgroundImage")));
			this->play6_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play6_pictureBox1->Name = L"play6_pictureBox1";
			this->play6_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox1->TabIndex = 43;
			this->play6_pictureBox1->TabStop = false;
			// 
			// play6_pictureBox4
			// 
			this->play6_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_pictureBox4.BackgroundImage")));
			this->play6_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play6_pictureBox4->Name = L"play6_pictureBox4";
			this->play6_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox4->TabIndex = 46;
			this->play6_pictureBox4->TabStop = false;
			// 
			// play6_pictureBox2
			// 
			this->play6_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_pictureBox2.BackgroundImage")));
			this->play6_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play6_pictureBox2->Name = L"play6_pictureBox2";
			this->play6_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play6_pictureBox2->TabIndex = 44;
			this->play6_pictureBox2->TabStop = false;
			// 
			// play6_pictureBox3
			// 
			this->play6_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_pictureBox3.BackgroundImage")));
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
			this->play7_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_pictureBox1.BackgroundImage")));
			this->play7_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play7_pictureBox1->Name = L"play7_pictureBox1";
			this->play7_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox1->TabIndex = 43;
			this->play7_pictureBox1->TabStop = false;
			// 
			// play7_pictureBox4
			// 
			this->play7_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_pictureBox4.BackgroundImage")));
			this->play7_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play7_pictureBox4->Name = L"play7_pictureBox4";
			this->play7_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox4->TabIndex = 46;
			this->play7_pictureBox4->TabStop = false;
			// 
			// play7_pictureBox2
			// 
			this->play7_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_pictureBox2.BackgroundImage")));
			this->play7_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play7_pictureBox2->Name = L"play7_pictureBox2";
			this->play7_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play7_pictureBox2->TabIndex = 44;
			this->play7_pictureBox2->TabStop = false;
			// 
			// play7_pictureBox3
			// 
			this->play7_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_pictureBox3.BackgroundImage")));
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
			this->play8_pictureBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_pictureBox1.BackgroundImage")));
			this->play8_pictureBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox1->Location = System::Drawing::Point(6, 19);
			this->play8_pictureBox1->Name = L"play8_pictureBox1";
			this->play8_pictureBox1->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox1->TabIndex = 43;
			this->play8_pictureBox1->TabStop = false;
			// 
			// play8_pictureBox4
			// 
			this->play8_pictureBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_pictureBox4.BackgroundImage")));
			this->play8_pictureBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox4->Location = System::Drawing::Point(174, 19);
			this->play8_pictureBox4->Name = L"play8_pictureBox4";
			this->play8_pictureBox4->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox4->TabIndex = 46;
			this->play8_pictureBox4->TabStop = false;
			// 
			// play8_pictureBox2
			// 
			this->play8_pictureBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_pictureBox2.BackgroundImage")));
			this->play8_pictureBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_pictureBox2->Location = System::Drawing::Point(62, 19);
			this->play8_pictureBox2->Name = L"play8_pictureBox2";
			this->play8_pictureBox2->Size = System::Drawing::Size(50, 45);
			this->play8_pictureBox2->TabIndex = 44;
			this->play8_pictureBox2->TabStop = false;
			// 
			// play8_pictureBox3
			// 
			this->play8_pictureBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_pictureBox3.BackgroundImage")));
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
			this->play3_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_score_picBox4.BackgroundImage")));
			this->play3_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play3_score_picBox4->Name = L"play3_score_picBox4";
			this->play3_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox4->TabIndex = 31;
			this->play3_score_picBox4->TabStop = false;
			// 
			// play3_score_picBox3
			// 
			this->play3_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_score_picBox3.BackgroundImage")));
			this->play3_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play3_score_picBox3->Name = L"play3_score_picBox3";
			this->play3_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox3->TabIndex = 30;
			this->play3_score_picBox3->TabStop = false;
			// 
			// play3_score_picBox2
			// 
			this->play3_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_score_picBox2.BackgroundImage")));
			this->play3_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play3_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play3_score_picBox2->Name = L"play3_score_picBox2";
			this->play3_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play3_score_picBox2->TabIndex = 29;
			this->play3_score_picBox2->TabStop = false;
			// 
			// play3_score_picBox1
			// 
			this->play3_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play3_score_picBox1.BackgroundImage")));
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
			this->play4_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_score_picBox4.BackgroundImage")));
			this->play4_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play4_score_picBox4->Name = L"play4_score_picBox4";
			this->play4_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox4->TabIndex = 31;
			this->play4_score_picBox4->TabStop = false;
			// 
			// play4_score_picBox3
			// 
			this->play4_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_score_picBox3.BackgroundImage")));
			this->play4_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play4_score_picBox3->Name = L"play4_score_picBox3";
			this->play4_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox3->TabIndex = 30;
			this->play4_score_picBox3->TabStop = false;
			// 
			// play4_score_picBox2
			// 
			this->play4_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_score_picBox2.BackgroundImage")));
			this->play4_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play4_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play4_score_picBox2->Name = L"play4_score_picBox2";
			this->play4_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play4_score_picBox2->TabIndex = 29;
			this->play4_score_picBox2->TabStop = false;
			// 
			// play4_score_picBox1
			// 
			this->play4_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play4_score_picBox1.BackgroundImage")));
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
			this->play5_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_score_picBox4.BackgroundImage")));
			this->play5_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play5_score_picBox4->Name = L"play5_score_picBox4";
			this->play5_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox4->TabIndex = 31;
			this->play5_score_picBox4->TabStop = false;
			// 
			// play5_score_picBox3
			// 
			this->play5_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_score_picBox3.BackgroundImage")));
			this->play5_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play5_score_picBox3->Name = L"play5_score_picBox3";
			this->play5_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox3->TabIndex = 30;
			this->play5_score_picBox3->TabStop = false;
			// 
			// play5_score_picBox2
			// 
			this->play5_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_score_picBox2.BackgroundImage")));
			this->play5_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play5_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play5_score_picBox2->Name = L"play5_score_picBox2";
			this->play5_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play5_score_picBox2->TabIndex = 29;
			this->play5_score_picBox2->TabStop = false;
			// 
			// play5_score_picBox1
			// 
			this->play5_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play5_score_picBox1.BackgroundImage")));
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
			this->play6_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_score_picBox4.BackgroundImage")));
			this->play6_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play6_score_picBox4->Name = L"play6_score_picBox4";
			this->play6_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox4->TabIndex = 31;
			this->play6_score_picBox4->TabStop = false;
			// 
			// play6_score_picBox3
			// 
			this->play6_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_score_picBox3.BackgroundImage")));
			this->play6_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play6_score_picBox3->Name = L"play6_score_picBox3";
			this->play6_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox3->TabIndex = 30;
			this->play6_score_picBox3->TabStop = false;
			// 
			// play6_score_picBox2
			// 
			this->play6_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_score_picBox2.BackgroundImage")));
			this->play6_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play6_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play6_score_picBox2->Name = L"play6_score_picBox2";
			this->play6_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play6_score_picBox2->TabIndex = 29;
			this->play6_score_picBox2->TabStop = false;
			// 
			// play6_score_picBox1
			// 
			this->play6_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play6_score_picBox1.BackgroundImage")));
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
			this->play7_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_score_picBox4.BackgroundImage")));
			this->play7_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play7_score_picBox4->Name = L"play7_score_picBox4";
			this->play7_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox4->TabIndex = 31;
			this->play7_score_picBox4->TabStop = false;
			// 
			// play7_score_picBox3
			// 
			this->play7_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_score_picBox3.BackgroundImage")));
			this->play7_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play7_score_picBox3->Name = L"play7_score_picBox3";
			this->play7_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox3->TabIndex = 30;
			this->play7_score_picBox3->TabStop = false;
			// 
			// play7_score_picBox2
			// 
			this->play7_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_score_picBox2.BackgroundImage")));
			this->play7_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play7_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play7_score_picBox2->Name = L"play7_score_picBox2";
			this->play7_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play7_score_picBox2->TabIndex = 29;
			this->play7_score_picBox2->TabStop = false;
			// 
			// play7_score_picBox1
			// 
			this->play7_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play7_score_picBox1.BackgroundImage")));
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
			this->play8_score_picBox4->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_score_picBox4.BackgroundImage")));
			this->play8_score_picBox4->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox4->Location = System::Drawing::Point(37, 44);
			this->play8_score_picBox4->Name = L"play8_score_picBox4";
			this->play8_score_picBox4->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox4->TabIndex = 31;
			this->play8_score_picBox4->TabStop = false;
			// 
			// play8_score_picBox3
			// 
			this->play8_score_picBox3->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_score_picBox3.BackgroundImage")));
			this->play8_score_picBox3->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox3->Location = System::Drawing::Point(6, 44);
			this->play8_score_picBox3->Name = L"play8_score_picBox3";
			this->play8_score_picBox3->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox3->TabIndex = 30;
			this->play8_score_picBox3->TabStop = false;
			// 
			// play8_score_picBox2
			// 
			this->play8_score_picBox2->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_score_picBox2.BackgroundImage")));
			this->play8_score_picBox2->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox2->Location = System::Drawing::Point(37, 13);
			this->play8_score_picBox2->Name = L"play8_score_picBox2";
			this->play8_score_picBox2->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox2->TabIndex = 29;
			this->play8_score_picBox2->TabStop = false;
			// 
			// play8_score_picBox1
			// 
			this->play8_score_picBox1->BackgroundImage = (cli::safe_cast<System::Drawing::Image^>(resources->GetObject(L"play8_score_picBox1.BackgroundImage")));
			this->play8_score_picBox1->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->play8_score_picBox1->Location = System::Drawing::Point(6, 13);
			this->play8_score_picBox1->Name = L"play8_score_picBox1";
			this->play8_score_picBox1->Size = System::Drawing::Size(25, 25);
			this->play8_score_picBox1->TabIndex = 28;
			this->play8_score_picBox1->TabStop = false;
			// 
			// you_lose_timer
			// 
			this->you_lose_timer->Interval = 1000;
			this->you_lose_timer->Tick += gcnew System::EventHandler(this, &VentanaPlay::you_lose_timer_Tick);
			// 
			// Username_label
			// 
			this->Username_label->AutoSize = true;
			this->Username_label->Font = (gcnew System::Drawing::Font(L"Modern No. 20", 18, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->Username_label->Location = System::Drawing::Point(656, 40);
			this->Username_label->Name = L"Username_label";
			this->Username_label->Size = System::Drawing::Size(134, 25);
			this->Username_label->TabIndex = 50;
			this->Username_label->Text = L"(Username)";
			// 
			// game_timer
			// 
			this->game_timer->Interval = 1000;
			this->game_timer->Tick += gcnew System::EventHandler(this, &VentanaPlay::game_timer_Tick);
			// 
			// gameTimer_label
			// 
			this->gameTimer_label->AutoSize = true;
			this->gameTimer_label->Location = System::Drawing::Point(710, 327);
			this->gameTimer_label->Name = L"gameTimer_label";
			this->gameTimer_label->Size = System::Drawing::Size(49, 13);
			this->gameTimer_label->TabIndex = 52;
			this->gameTimer_label->Text = L"00:00:00";
			this->gameTimer_label->Visible = false;
			// 
			// num_gameTimer_label
			// 
			this->num_gameTimer_label->AutoSize = true;
			this->num_gameTimer_label->Location = System::Drawing::Point(710, 309);
			this->num_gameTimer_label->Name = L"num_gameTimer_label";
			this->num_gameTimer_label->Size = System::Drawing::Size(43, 13);
			this->num_gameTimer_label->TabIndex = 53;
			this->num_gameTimer_label->Text = L"000000";
			this->num_gameTimer_label->Visible = false;
			// 
			// VentanaPlay
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Gainsboro;
			this->BackgroundImageLayout = System::Windows::Forms::ImageLayout::Stretch;
			this->ClientSize = System::Drawing::Size(823, 652);
			this->Controls->Add(this->num_gameTimer_label);
			this->Controls->Add(this->gameTimer_label);
			this->Controls->Add(this->load_warning_groupBox);
			this->Controls->Add(this->Username_label);
			this->Controls->Add(this->quit_game_groupBox);
			this->Controls->Add(this->play3_pic_groupBox);
			this->Controls->Add(this->play4_pic_groupBox);
			this->Controls->Add(this->rand_comb_groupBox);
			this->Controls->Add(this->yellow_button);
			this->Controls->Add(this->play8_score_groupBox);
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
			this->play1_groupBox->PerformLayout();
			this->play1_score_groupBox->ResumeLayout(false);
			this->quit_game_groupBox->ResumeLayout(false);
			this->quit_game_groupBox->PerformLayout();
			this->load_warning_groupBox->ResumeLayout(false);
			this->load_warning_groupBox->PerformLayout();
			this->rand_comb_groupBox->ResumeLayout(false);
			this->rand_comb_groupBox->PerformLayout();
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

	private: System::Void MyForm_Load(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: sets al timers/clocks to its initial value

		seconds = 0;
		minutes = 0;
		hours = 0;

		secondsP = 60;
		minutesP = 0;
		secondsG = 60;
		minutesG = 29;
		hoursG = 1;

		hoursTimer = 0;
		minutesTimer = 0;
		secondsTimer = 0;
	}
	
	private: System::Void titulo_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void label2_Click(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void red_button_Click_1(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;


		bool_red_button = true; 

	}
	private: System::Void blue_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;


		bool_blue_button = true;
	}
	private: System::Void green_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;


		bool_green_button = true;
	}
	private: System::Void yellow_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;


		bool_yellow_button = true;
	}
	private: System::Void pink_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;


		bool_pink_button = true;
	}
	private: System::Void brown_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: Enables the guess buttons
		play1_guess1_button->Enabled = true;
		play1_guess2_button->Enabled = true;
		play1_guess3_button->Enabled = true;
		play1_guess4_button->Enabled = true;


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
		//Functioning: opens the "Are you shure you wanna quit" window (groupBox)
		quit_game_groupBox->Visible = true;
		quit_game_groupBox->Enabled = true;
		quit_game_groupBox->BringToFront();
	}

	private: System::Void win_lose_disable()
	{
		//Functioning: Disables all buttons except for the OK button to get out of the window

		red_button->Enabled = false;
		blue_button->Enabled = false;
		green_button->Enabled = false;
		yellow_button->Enabled = false;
		pink_button->Enabled = false;
		brown_button->Enabled = false;

		play1_guess1_button->Enabled = false;
		play1_guess2_button->Enabled = false;
		play1_guess3_button->Enabled = false;
		play1_guess4_button->Enabled = false;

		enter_play_button->Enabled = false;
		salirToolStripMenuItem->Enabled = false;
		archivoToolStripMenuItem->Enabled = false;

	}

	private: System::Void play1_guess1_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: if a color/letter/number/shape button was Clicked before it gives this button the BackgroundImage of the Clicked button

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

			bool_yellow_button = false;
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
		if (play1_guess1_button->BackgroundImage != blank_button->BackgroundImage) 
			if (play1_guess2_button->BackgroundImage != blank_button->BackgroundImage)
				if (play1_guess3_button->BackgroundImage != blank_button->BackgroundImage)
					if (play1_guess4_button->BackgroundImage != blank_button->BackgroundImage)
						enter_play_button->Enabled = true;
			
		//&& (play1_guess2_button->BackgroundImage != blank_button->BackgroundImage) && (play1_guess3_button->BackgroundImage != blank_button->BackgroundImage) && (play1_guess4_button->BackgroundImage != blank_button->BackgroundImage))

			
	}
	private: System::Void play1_guess2_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: if a color/letter/number/shape button was Clicked before it gives this button the BackgroundImage of the Clicked button

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
		if (play1_guess1_button->BackgroundImage != blank_button->BackgroundImage)
			if (play1_guess2_button->BackgroundImage != blank_button->BackgroundImage)
				if (play1_guess3_button->BackgroundImage != blank_button->BackgroundImage)
					if (play1_guess4_button->BackgroundImage != blank_button->BackgroundImage)
						enter_play_button->Enabled = true;
	}
	private: System::Void play1_guess3_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: if a color/letter/number/shape button was Clicked before it gives this button the BackgroundImage of the Clicked button

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
		if (play1_guess1_button->BackgroundImage != blank_button->BackgroundImage)
			if (play1_guess2_button->BackgroundImage != blank_button->BackgroundImage)
				if (play1_guess3_button->BackgroundImage != blank_button->BackgroundImage)
					if (play1_guess4_button->BackgroundImage != blank_button->BackgroundImage)
						enter_play_button->Enabled = true;
	}
	private: System::Void play1_guess4_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: if a color/letter/number/shape button was Clicked before it gives this button the BackgroundImage of the Clicked button

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
		if (play1_guess1_button->BackgroundImage != blank_button->BackgroundImage)
			if (play1_guess2_button->BackgroundImage != blank_button->BackgroundImage)
				if (play1_guess3_button->BackgroundImage != blank_button->BackgroundImage)
					if (play1_guess4_button->BackgroundImage != blank_button->BackgroundImage)
						enter_play_button->Enabled = true;
	}

	private: System::Void Clock_Tick(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: starts the correspondent clock/timekeeper

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
		}

		else if (objSettings->getTimekeeperPlay() == true)
		{
			//CODIGO TIMEKEEPER POR JUGADA
			secondsP--;
			if (secondsP == 0)
			{
				secondsP = 00;
				bool TimeKP = false;
				objSettings->setTimekeeperPlay(TimeKP);

				//Tiempo llega a cero
				lose_groupBox->Visible = true;
				lose_groupBox->Enabled = true;
				you_lose_timer->Enabled = true;
				win_lose_disable();

				backg->Stop();
				disappointment->PlayLooping();
			}
			secP = Convert::ToString(secondsP);
			minP = Convert::ToString(minutesP);

			if (hours < 10)
			{
				if (minutesP < 10)
				{
					if (secondsP < 10)
					{
						Time->Text = "00" + ":0" + minP + ":0" + secP;
					}
					else if (secondsP >= 10)
					{
						Time->Text = "00" + ":0" + minP + ":" + secP;
					}
				}
				else if (minutesP >= 10)
				{
					if (secondsP < 10)
					{
						Time->Text = "00" + ":" + minP + ":0" + secP;
					}
					else if (secondsP >= 10)
					{
						Time->Text = "00" + ":" + minP + ":" + secP;
					}
				}
			}
			else if (hours >= 10)
			{
				if (minutesP < 10)
				{
					if (secondsP < 10)
					{
						Time->Text = "00" + ":0" + minP + ":0" + secP;
					}
					else if (secondsP >= 10)
					{
						Time->Text = "00" + ":0" + minP + ":" + secP;
					}
				}
				else if (minutesP >= 10)
				{
					if (secondsP < 10)
					{
						Time->Text = "00" + ":" + minP + ":0" + secP;
					}
					else if (seconds >= 10)
					{
						Time->Text = "00" + ":" + minP + ":" + secP;
					}
				}
			}

		}

		else if (objSettings->getTimekeeperGame() == true)
		{
			//CODIGO TIMEKEEPER POR JUEGO
			secondsG--;
			if (secondsG == 0)
			{
				secondsG = 60;
				minutesG--;
			}
			if (minutesG == 0)
			{
				minutesG = 60;
				hoursG--;
			}
			if (hoursG == 0)
			{
				hoursG = 00;
			}
			if ((hoursG == 0) && (minutesG == 0) && (secondsG == 0))
			{
				secondsG = 00;
				minutesG = 00;
				hoursG = 00;

				bool TimeKG = false;
				objSettings->setTimekeeperGame(TimeKG);

				//Finish Game / Lose
				lose_groupBox->Visible = true;
				lose_groupBox->Enabled = true;
				you_lose_timer->Enabled = true;
				win_lose_disable();

				backg->Stop();
				disappointment->PlayLooping();

			}


			secG = Convert::ToString(secondsG);
			minG = Convert::ToString(minutesG);
			hourG = Convert::ToString(hoursG);

			if (hoursG < 10)
			{
				if (minutesG < 10)
				{
					if (secondsG < 10)
					{
						Time->Text = "0" + hourG + ":0" + minG + ":0" + secG;
					}
					else if (secondsG >= 10)
					{
						Time->Text = "0" + hourG + ":0" + minG + ":" + secG;
					}
				}
				else if (minutesG >= 10)
				{
					if (secondsG < 10)
					{
						Time->Text = "0" + hourG + ":" + minG + ":0" + secG;
					}
					else if (secondsG >= 10)
					{
						Time->Text = "0" + hourG + ":" + minG + ":" + secG;
					}
				}
			}
			else if (hoursG >= 10)
			{
				if (minutesG < 10)
				{
					if (secondsG < 10)
					{
						Time->Text = hourG + ":0" + minG + ":0" + secG;
					}
					else if (secondsG >= 10)
					{
						Time->Text = hourG + ":0" + minG + ":" + secG;
					}
				}
				else if (minutesG >= 10)
				{
					if (secondsG < 10)
					{
						Time->Text = hourG + ":" + minG + ":0" + secG;
					}
					else if (secondsG >= 10)
					{
						Time->Text = hourG + ":" + minG + ":" + secG;
					}
				}
			}
		}

	}

	private: System::Void Vent_Play_Start_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: creates random combination, starts clock/timekeeper enables color/letter/number/shape buttons

		if (loaded_game == false)
		{
			//creates random combination

			//combination
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

			//gameTimer starts
			game_timer->Enabled = true;
		}


		//Enables the colors buttons
		red_button->Enabled = true;
		blue_button->Enabled = true;
		green_button->Enabled = true;
		yellow_button->Enabled = true;
		pink_button->Enabled = true;
		brown_button->Enabled = true;

		/*
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
		*/

		//gameTimer starts
		////game_timer->Enabled = true;


		Vent_Play_Start->Enabled = false;
		salirToolStripMenuItem->Enabled = true;
		saveToolStripMenuItem->Enabled = true;
		loadGameToolStripMenuItem->Enabled = true;

		//actual_play = 1;
	}


	private: System::Void asign_white()
	{
		//Functioning: asigns white button background image to que score

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

	private: System::Void enter_play_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: enters the submitted play and qualifies it; has the code for winning or loosing the game

		srand(time(0)); //srand to 0 so it can create a new different random combination

		if (objSettings->getElementRep() == true)
		{
			//1 = red
			//2 = blue
			//3 = green
			//4 = yellow
			//5 = pink
			//6 = brown

			int guess1_int = 0;
			int guess2_int = 0;
			int guess3_int = 0;
			int guess4_int = 0;

			int rand_comb1_int = 0;
			int rand_comb2_int = 0;
			int rand_comb3_int = 0;
			int rand_comb4_int = 0;

			int red_int = 1;
			int blue_int = 2;
			int green_int = 3;
			int yellow_int = 4;
			int pink_int = 5;
			int brown_int = 6;


			//random int combination 
			if (rand_comb1_button->BackgroundImage == red_button->BackgroundImage)
			{
				rand_comb1_int = red_int;
			}
			else if (rand_comb1_button->BackgroundImage == blue_button->BackgroundImage)
			{
				rand_comb1_int = blue_int;
			}
			else if (rand_comb1_button->BackgroundImage == green_button->BackgroundImage)
			{
				rand_comb1_int = green_int;
			}
			else if (rand_comb1_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				rand_comb1_int = yellow_int;
			}
			else if (rand_comb1_button->BackgroundImage == pink_button->BackgroundImage)
			{
				rand_comb1_int = pink_int;
			}
			else if (rand_comb1_button->BackgroundImage == brown_button->BackgroundImage)
			{
				rand_comb1_int = brown_int;
			}

			if (rand_comb2_button->BackgroundImage == red_button->BackgroundImage)
			{
				rand_comb2_int = red_int;
			}
			else if (rand_comb2_button->BackgroundImage == blue_button->BackgroundImage)
			{
				rand_comb2_int = blue_int;
			}
			else if (rand_comb2_button->BackgroundImage == green_button->BackgroundImage)
			{
				rand_comb2_int = green_int;
			}
			else if (rand_comb2_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				rand_comb2_int = yellow_int;
			}
			else if (rand_comb2_button->BackgroundImage == pink_button->BackgroundImage)
			{
				rand_comb2_int = pink_int;
			}
			else if (rand_comb2_button->BackgroundImage == brown_button->BackgroundImage)
			{
				rand_comb2_int = brown_int;
			}

			if (rand_comb3_button->BackgroundImage == red_button->BackgroundImage)
			{
				rand_comb3_int = red_int;
			}
			else if (rand_comb3_button->BackgroundImage == blue_button->BackgroundImage)
			{
				rand_comb3_int = blue_int;
			}
			else if (rand_comb3_button->BackgroundImage == green_button->BackgroundImage)
			{
				rand_comb3_int = green_int;
			}
			else if (rand_comb3_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				rand_comb3_int = yellow_int;
			}
			else if (rand_comb3_button->BackgroundImage == pink_button->BackgroundImage)
			{
				rand_comb3_int = pink_int;
			}
			else if (rand_comb3_button->BackgroundImage == brown_button->BackgroundImage)
			{
				rand_comb3_int = brown_int;
			}

			if (rand_comb4_button->BackgroundImage == red_button->BackgroundImage)
			{
				rand_comb4_int = red_int;
			}
			else if (rand_comb4_button->BackgroundImage == blue_button->BackgroundImage)
			{
				rand_comb4_int = blue_int;
			}
			else if (rand_comb4_button->BackgroundImage == green_button->BackgroundImage)
			{
				rand_comb4_int = green_int;
			}
			else if (rand_comb4_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				rand_comb4_int = yellow_int;
			}
			else if (rand_comb4_button->BackgroundImage == pink_button->BackgroundImage)
			{
				rand_comb4_int = pink_int;
			}
			else if (rand_comb4_button->BackgroundImage == brown_button->BackgroundImage)
			{
				rand_comb4_int = brown_int;
			}

			//guess int
			if (play1_guess1_button->BackgroundImage == red_button->BackgroundImage)
			{
				guess1_int = red_int;
			}
			else if (play1_guess1_button->BackgroundImage == blue_button->BackgroundImage)
			{
				guess1_int = blue_int;
			}
			else if (play1_guess1_button->BackgroundImage == green_button->BackgroundImage)
			{
				guess1_int = green_int;
			}
			else if (play1_guess1_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				guess1_int = yellow_int;
			}
			else if (play1_guess1_button->BackgroundImage == pink_button->BackgroundImage)
			{
				guess1_int = pink_int;
			}
			else if (play1_guess1_button->BackgroundImage == brown_button->BackgroundImage)
			{
				guess1_int = brown_int;
			}

			if (play1_guess2_button->BackgroundImage == red_button->BackgroundImage)
			{
				guess2_int = red_int;
			}
			else if (play1_guess2_button->BackgroundImage == blue_button->BackgroundImage)
			{
				guess2_int = blue_int;
			}
			else if (play1_guess2_button->BackgroundImage == green_button->BackgroundImage)
			{
				guess2_int = green_int;
			}
			else if (play1_guess2_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				guess2_int = yellow_int;
			}
			else if (play1_guess2_button->BackgroundImage == pink_button->BackgroundImage)
			{
				guess2_int = pink_int;
			}
			else if (play1_guess2_button->BackgroundImage == brown_button->BackgroundImage)
			{
				guess2_int = brown_int;
			}

			if (play1_guess3_button->BackgroundImage == red_button->BackgroundImage)
			{
				guess3_int = red_int;
			}
			else if (play1_guess3_button->BackgroundImage == blue_button->BackgroundImage)
			{
				guess3_int = blue_int;
			}
			else if (play1_guess3_button->BackgroundImage == green_button->BackgroundImage)
			{
				guess3_int = green_int;
			}
			else if (play1_guess3_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				guess3_int = yellow_int;
			}
			else if (play1_guess3_button->BackgroundImage == pink_button->BackgroundImage)
			{
				guess3_int = pink_int;
			}
			else if (play1_guess3_button->BackgroundImage == brown_button->BackgroundImage)
			{
				guess3_int = brown_int;
			}

			if (play1_guess4_button->BackgroundImage == red_button->BackgroundImage)
			{
				guess4_int = red_int;
			}
			else if (play1_guess4_button->BackgroundImage == blue_button->BackgroundImage)
			{
				guess4_int = blue_int;
			}
			else if (play1_guess4_button->BackgroundImage == green_button->BackgroundImage)
			{
				guess4_int = green_int;
			}
			else if (play1_guess4_button->BackgroundImage == yellow_button->BackgroundImage)
			{
				guess4_int = yellow_int;
			}
			else if (play1_guess4_button->BackgroundImage == pink_button->BackgroundImage)
			{
				guess4_int = pink_int;
			}
			else if (play1_guess4_button->BackgroundImage == brown_button->BackgroundImage)
			{
				guess4_int = brown_int;
			}


			//Black Score
			if (play1_guess1_button->BackgroundImage == rand_comb1_button->BackgroundImage)
			{
				objSettings->setRandomNUM();
				num_rand1 = objSettings->getRandomNUM();

				if (num_rand1 == 1)
				{
					play1_score_btn1->BackgroundImage = black_button->BackgroundImage;
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
				rand_comb1_int = 0;
				guess1_int = -1;
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
				rand_comb2_int = 0;
				guess2_int = -1;
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
				rand_comb3_int = 0;
				guess3_int = -1;
			}
			if (play1_guess4_button->BackgroundImage == rand_comb4_button->BackgroundImage)
			{
				objSettings->setRandomNUM();
				num_rand4 = objSettings->getRandomNUM();

				while ((num_rand4 == num_rand1) || (num_rand4 == num_rand2) || (num_rand4 == num_rand3))
				{
					objSettings->setRandomNUM();
					num_rand4 = objSettings->getRandomNUM();
				}

				if (num_rand4 == 1)
				{
					play1_score_btn1->BackgroundImage = black_button->BackgroundImage;
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
				rand_comb4_int = 0;
				guess4_int = -1;
			}

			//white score
			if (guess1_int == rand_comb2_int)
			{
				asign_white();

				rand_comb2_int = 0;
				guess1_int = -1;
			}
			else if (guess1_int == rand_comb3_int)
			{
				asign_white();

				rand_comb3_int = 0;
				guess1_int = -1;
			}
			else if (guess1_int == rand_comb4_int)
			{
				asign_white();

				rand_comb4_int = 0;
				guess1_int = -1;

			}

			if (guess2_int == rand_comb1_int)
			{
				asign_white();

				rand_comb1_int = 0;
				guess2_int = -1;
			}
			else if (guess2_int == rand_comb3_int)
			{
				asign_white();

				rand_comb3_int = 0;
				guess2_int = -1;
			}
			else if (guess2_int == rand_comb4_int)
			{
				asign_white();

				rand_comb4_int = 0;
				guess2_int = -1;
			}

			if (guess3_int == rand_comb1_int)
			{
				asign_white();

				rand_comb1_int = 0;
				guess3_int = -1;
			}
			else if (guess3_int == rand_comb2_int)
			{
				asign_white();

				rand_comb2_int = 0;
				guess3_int = -1;
			}
			else if (guess3_int == rand_comb4_int)
			{
				asign_white();

				rand_comb4_int = 0;
				guess3_int = -1;
			}

			if (guess4_int == rand_comb1_int)
			{
				asign_white();

				rand_comb1_int = 0;
				guess4_int = -1;
			}
			else if (guess4_int == rand_comb2_int)
			{
				asign_white();

				rand_comb2_int = 0;
				guess4_int = -1;
			}
			else if (guess4_int == rand_comb3_int)
			{
				asign_white();

				rand_comb3_int = 0;
				guess4_int = -1;
			}

			/*
			if (play1_guess1_button->BackgroundImage == rand_comb1_button->BackgroundImage)
			{
				if (play1_guess1_button->BackgroundImage == red_button->BackgroundImage)
				{
					guess_cant_red--;
					rand_cant_red--;
				}
				else if (play1_guess1_button->BackgroundImage == blue_button->BackgroundImage)
				{
					guess_cant_blue--;
					rand_cant_blue--;
				}
				else if (play1_guess1_button->BackgroundImage == green_button->BackgroundImage)
				{
					guess_cant_green--;
					rand_cant_green--;
				}
				else if (play1_guess1_button->BackgroundImage == yellow_button->BackgroundImage)
				{
					guess_cant_yellow--;
					rand_cant_yellow--;
				}
				else if (play1_guess1_button->BackgroundImage == pink_button->BackgroundImage)
				{
					guess_cant_pink--;
					rand_cant_pink--;
				}
				else if (play1_guess1_button->BackgroundImage == brown_button->BackgroundImage)
				{
					guess_cant_brown--;
					rand_cant_brown--;
				}

			}
			if (play1_guess2_button->BackgroundImage == rand_comb2_button->BackgroundImage)
			{
				if (play1_guess2_button->BackgroundImage == red_button->BackgroundImage)
				{
					guess_cant_red--;
					rand_cant_red--;
				}
				else if (play1_guess2_button->BackgroundImage == blue_button->BackgroundImage)
				{
					guess_cant_blue--;
					rand_cant_blue--;
				}
				else if (play1_guess2_button->BackgroundImage == green_button->BackgroundImage)
				{
					guess_cant_green--;
					rand_cant_green--;
				}
				else if (play1_guess2_button->BackgroundImage == yellow_button->BackgroundImage)
				{
					guess_cant_yellow--;
					rand_cant_yellow--;
				}
				else if (play1_guess2_button->BackgroundImage == pink_button->BackgroundImage)
				{
					guess_cant_pink--;
					rand_cant_pink--;
				}
				else if (play1_guess2_button->BackgroundImage == brown_button->BackgroundImage)
				{
					guess_cant_brown--;
					rand_cant_brown--;
				}

			}
			if (play1_guess3_button->BackgroundImage == rand_comb3_button->BackgroundImage)
			{
				if (play1_guess3_button->BackgroundImage == red_button->BackgroundImage)
				{
					guess_cant_red--;
					rand_cant_red--;
				}
				else if (play1_guess3_button->BackgroundImage == blue_button->BackgroundImage)
				{
					guess_cant_blue--;
					rand_cant_blue--;
				}
				else if (play1_guess3_button->BackgroundImage == green_button->BackgroundImage)
				{
					guess_cant_green--;
					rand_cant_green--;
				}
				else if (play1_guess3_button->BackgroundImage == yellow_button->BackgroundImage)
				{
					guess_cant_yellow--;
					rand_cant_yellow--;
				}
				else if (play1_guess3_button->BackgroundImage == pink_button->BackgroundImage)
				{
					guess_cant_pink--;
					rand_cant_pink--;
				}
				else if (play1_guess3_button->BackgroundImage == brown_button->BackgroundImage)
				{
					guess_cant_brown--;
					rand_cant_brown--;
				}

			}
			if (play1_guess4_button->BackgroundImage == rand_comb4_button->BackgroundImage)
			{
				if (play1_guess4_button->BackgroundImage == red_button->BackgroundImage)
				{
					guess_cant_red--;
					rand_cant_red--;
				}
				else if (play1_guess4_button->BackgroundImage == blue_button->BackgroundImage)
				{
					guess_cant_blue--;
					rand_cant_blue--;
				}
				else if (play1_guess4_button->BackgroundImage == green_button->BackgroundImage)
				{
					guess_cant_green--;
					rand_cant_green--;
				}
				else if (play1_guess4_button->BackgroundImage == yellow_button->BackgroundImage)
				{
					guess_cant_yellow--;
					rand_cant_yellow--;
				}
				else if (play1_guess4_button->BackgroundImage == pink_button->BackgroundImage)
				{
					guess_cant_pink--;
					rand_cant_pink--;
				}
				else if (play1_guess4_button->BackgroundImage == brown_button->BackgroundImage)
				{
					guess_cant_brown--;
					rand_cant_brown--;
				}

			}


			if ((guess_cant_red != 0) && (guess_cant_red < rand_cant_red))
			{
				int count = 0;
				while (count < guess_cant_red)
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

					count++;
				}
			}
			if ((guess_cant_blue != 0) && (guess_cant_blue < rand_cant_blue))
			{
				int count = 0;
				while (count < guess_cant_blue)
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

					count++;
				}
			}
			if ((guess_cant_green != 0) && (guess_cant_green < rand_cant_green))
			{
				int count = 0;
				while (count < guess_cant_green)
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

					count++;
				}
			}
			if ((guess_cant_yellow != 0) && (guess_cant_yellow < rand_cant_yellow))
			{
				int count = 0;
				while (count < guess_cant_yellow)
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

					count++;
				}
			}
			if ((guess_cant_pink != 0) && (guess_cant_pink < rand_cant_pink))
			{
				int count = 0;
				while (count < guess_cant_pink)
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

					count++;
				}
			}
			if ((guess_cant_brown != 0) && (guess_cant_brown < rand_cant_brown))
			{
				int count = 0;
				while (count < guess_cant_brown)
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

					count++;
				}
			}


			if ((guess_cant_red != 0) && (guess_cant_red > rand_cant_red))
			{
				int count = 0;
				while (count < rand_cant_red)
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

					count++;
				}
			}
			if ((guess_cant_blue != 0) && (guess_cant_blue > rand_cant_blue))
			{
				int count = 0;
				while (count < rand_cant_blue)
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

					count++;
				}
			}
			if ((guess_cant_green != 0) && (guess_cant_green > rand_cant_green))
			{
				int count = 0;
				while (count < rand_cant_green)
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

					count++;
				}
			}
			if ((guess_cant_yellow != 0) && (guess_cant_yellow > rand_cant_yellow))
			{
				int count = 0;
				while (count < rand_cant_yellow)
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

					count++;
				}
			}
			if ((guess_cant_pink != 0) && (guess_cant_pink > rand_cant_pink))
			{
				int count = 0;
				while (count < rand_cant_pink)
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

					count++;
				}
			}
			if ((guess_cant_brown != 0) && (guess_cant_brown > rand_cant_brown))
			{
			int count = 0;
			while (count < rand_cant_brown)
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

				count++;
			}
			}
			*/


		}
		else if (objSettings->getElementRep() == false)
		{
			//Black Score
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


				while ((num_rand4 == num_rand1) || (num_rand4 == num_rand2) || (num_rand4 == num_rand3))
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

			//white score
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

		//win game / lose game
		if ((play1_score_btn1->BackgroundImage == black_button->BackgroundImage) && (play1_score_btn2->BackgroundImage == black_button->BackgroundImage) && (play1_score_btn3->BackgroundImage == black_button->BackgroundImage) && (play1_score_btn4->BackgroundImage == black_button->BackgroundImage))
		{
			//Code if the player wins

			Clock->Enabled = false;
			game_timer->Enabled = false;

			win_groupBox->Visible = true;
			win_groupBox->Enabled = true;

			rand_comb_groupBox->Visible = true;
			win = true;

			win_lose_disable();

			//saves records of the winner in a file
			using namespace std;
			if (win == true)
			{
				ofstream winnerinfo;//File with winner information

				//winnerinfo.open("SavedWinners.txt",ios::out);
				//winnerinfo.close();

				winnerinfo.open("SavedWinners.txt", ios::app); //opens the file
				
				winnerinfo << "Difficulty: ";//Saves difficulty
				if (objSettings->getDifficulty() == 1)
					winnerinfo << "Easy" << endl;
				else if (objSettings->getDifficulty() == 2)
					winnerinfo << "Medium" << endl;
				else if (objSettings->getDifficulty() == 3)
					winnerinfo << "Hard" << endl;


				string game_timer_str = msclr::interop::marshal_as<std::string>(gameTimer_label->Text);
				string num_game_timer_str = msclr::interop::marshal_as<std::string>(num_gameTimer_label->Text);
				game_timer_int = stoi(num_game_timer_str);

				winnerinfo << "Time_encrip: ";//Saves encripted time
				winnerinfo << num_game_timer_str << endl;

				winnerinfo << "Username: ";//Saves the username
				string winnername = msclr::interop::marshal_as<std::string>(Username_label->Text);
				winnerinfo << winnername << endl;

				winnerinfo << "Time_encrip: ";//Saves time
				winnerinfo << game_timer_str << endl;


				winnerinfo << "Combination: ";//Saves combination

				auto actual_Comb_Btn_BackIma = rand_comb1_button->BackgroundImage;
				int combi = 0;
				while (combi < 4)
				{
					if (combi == 1)
						actual_Comb_Btn_BackIma = rand_comb2_button->BackgroundImage;
					else if (combi == 2)
						actual_Comb_Btn_BackIma = rand_comb3_button->BackgroundImage;
					else if (combi == 3)
						actual_Comb_Btn_BackIma = rand_comb4_button->BackgroundImage;

					if (objSettings->getElementType() == 1)
					{

						if (actual_Comb_Btn_BackIma == red_button->BackgroundImage)
							winnerinfo << "Red ";

						else if (actual_Comb_Btn_BackIma == blue_button->BackgroundImage)
							winnerinfo << "Blue ";

						else if (actual_Comb_Btn_BackIma == green_button->BackgroundImage)
							winnerinfo << "Green ";

						else if (actual_Comb_Btn_BackIma == yellow_button->BackgroundImage)
							winnerinfo << "Yellow ";

						else if (actual_Comb_Btn_BackIma == pink_button->BackgroundImage)
							winnerinfo << "Pink ";

						else if (actual_Comb_Btn_BackIma == brown_button->BackgroundImage)
							winnerinfo << "Brown ";
					}
					else if (objSettings->getElementType() == 2)
					{

						if (actual_Comb_Btn_BackIma == red_button->BackgroundImage)
							winnerinfo << "A ";

						else if (actual_Comb_Btn_BackIma == blue_button->BackgroundImage)
							winnerinfo << "B ";

						else if (actual_Comb_Btn_BackIma == green_button->BackgroundImage)
							winnerinfo << "C ";

						else if (actual_Comb_Btn_BackIma == yellow_button->BackgroundImage)
							winnerinfo << "D ";

						else if (actual_Comb_Btn_BackIma == pink_button->BackgroundImage)
							winnerinfo << "E ";

						else if (actual_Comb_Btn_BackIma == brown_button->BackgroundImage)
							winnerinfo << "F ";
					}
					if (objSettings->getElementType() == 3)
					{

						if (actual_Comb_Btn_BackIma == red_button->BackgroundImage)
							winnerinfo << "0 ";

						else if (actual_Comb_Btn_BackIma == blue_button->BackgroundImage)
							winnerinfo << "1 ";

						else if (actual_Comb_Btn_BackIma == green_button->BackgroundImage)
							winnerinfo << "2 ";

						else if (actual_Comb_Btn_BackIma == yellow_button->BackgroundImage)
							winnerinfo << "3 ";

						else if (actual_Comb_Btn_BackIma == pink_button->BackgroundImage)
							winnerinfo << "4 ";

						else if (actual_Comb_Btn_BackIma == brown_button->BackgroundImage)
							winnerinfo << "5 ";
					}
					if (objSettings->getElementType() == 4)
					{

						if (actual_Comb_Btn_BackIma == red_button->BackgroundImage)
							winnerinfo << "Lightning ";

						else if (actual_Comb_Btn_BackIma == blue_button->BackgroundImage)
							winnerinfo << "Triangle ";

						else if (actual_Comb_Btn_BackIma == green_button->BackgroundImage)
							winnerinfo << "DoubleTriangle ";

						else if (actual_Comb_Btn_BackIma == yellow_button->BackgroundImage)
							winnerinfo << "Square ";

						else if (actual_Comb_Btn_BackIma == pink_button->BackgroundImage)
							winnerinfo << "Pentagon ";

						else if (actual_Comb_Btn_BackIma == brown_button->BackgroundImage)
							winnerinfo << "Hexagon ";
					}
					combi++;
				}

				winnerinfo << endl;

				winnerinfo << "Time_and_date: "; // Saves Time and Date
				char fecha[25];//ctime devuelve 26 caracteres pero tambien se podría usar un puntero de char
				time_t current_time;
				current_time = time(NULL);
				ctime(&current_time);
				strcpy(fecha, ctime(&current_time));
				winnerinfo << fecha << endl;

				winnerinfo << endl; //leaves a space between winners info

				winnerinfo.close(); //closes the file
			}
			backg->Stop(); //stops the music of backg
			applause->PlayLooping(); //plays the music of applause

		}
		else
		{
			//Code if the player lose
			
			if ((objSettings->getDifficulty() == 1) && (win == false))
			{
				if (actual_play == 8)
				{
					enter_play_button->Enabled = false;

					//codigo para terminar el juego
					Clock->Enabled = false;
					game_timer->Enabled = false;

					lose_groupBox->Visible = true;
					lose_groupBox->Enabled = true;
					you_lose_timer->Enabled = true;

					rand_comb_groupBox->Visible = true;

					win_lose_disable();

					backg->Stop();
					disappointment->PlayLooping();
				}
			}
			else if ((objSettings->getDifficulty() == 2) && (win == false))
			{
				if (actual_play == 7)
				{
					enter_play_button->Enabled = false;

					//codigo para terminar el juego
					Clock->Enabled = false;
					game_timer->Enabled = false;

					lose_groupBox->Visible = true;
					lose_groupBox->Enabled = true;
					you_lose_timer->Enabled = true;

					rand_comb_groupBox->Visible = true;

					win_lose_disable();

					backg->Stop();
					disappointment->PlayLooping();
				}
			}
			else if ((objSettings->getDifficulty() == 3) && (win == false))
			{
				if (actual_play == 6)
				{
					enter_play_button->Enabled = false;

					//codigo para terminar el juego
					Clock->Enabled = false;
					game_timer->Enabled = false;

					lose_groupBox->Visible = true;
					lose_groupBox->Enabled = true;
					you_lose_timer->Enabled = true;

					rand_comb_groupBox->Visible = true;

					win_lose_disable();

					backg->Stop();
					disappointment->PlayLooping();
				}
			}

		}

		//plays
		if (actual_play == 1)
		{
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

		//Timekeeper for play
		secondsP = 60;
		minutesP = 0;

		enter_play_button->Enabled = false;
		actual_play++;
		saved_plays++;
	}


	private: System::Void color_position_bbtn_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void color_wbtn_label_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void play7_groupBox_Enter(System::Object^ sender, System::EventArgs^ e){
	}
	private: System::Void label1_Click(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void ok_quit_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: closes VentanaPlay if Yes was selected, else it continues the game

		if (quit_game == true)
		{

			backg->Stop();
			VentanaPlay::Close();

			//devuleve los valores del reloj/cronometro a 0
			seconds = 0;
			minutes = 0;
			hours = 0;

			secondsP = 60;
			minutesP = 0;
			secondsG = 60;
			minutesG = 29;
			hoursG = 1;

			secondsTimer = 0;
			minutesTimer = 0;
			hoursTimer = 0;
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
		//Functioning: closes VentanaPlay, reboots time values to its initial values

		applause->Stop();
		VentanaPlay::Close();

		//devuleve los valores del reloj/cronometro a 0
		seconds = 0;
		minutes = 0;
		hours = 0;

		secondsP = 60;
		minutesP = 0;
		secondsG = 60;
		minutesG = 29;
		hoursG = 1;

		secondsTimer = 0;
		minutesTimer = 0;
		hoursTimer = 0;
	}
	private: System::Void ok_lose_button_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: closes VentanaPlay, reboots time values to its initial values

		you_lose_timer->Enabled = false;

		disappointment->Stop();
		VentanaPlay::Close();

		//devuleve los valores del reloj/cronometro a 0
		seconds = 0;
		minutes = 0;
		hours = 0;

		secondsP = 60;
		minutesP = 0;
		secondsG = 60;
		minutesG = 29;
		hoursG = 1;

		secondsTimer = 0;
		minutesTimer = 0;
		hoursTimer = 0;

	}

	private: System::Void you_lose_timer_Tick(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: makes the "you lose" text blink

		static int blink_color = 1;
		if (blink_color == 1)
		{
			you_lose_label->Visible = false;
			blink_color = 2;
		}
		else if (blink_color == 2)
		{
			you_lose_label->Visible = true;
			blink_color = 1;
		}
	}


	private: System::Void lose_groupBox_Enter(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void ayudaToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
	}

	private: System::Void instruccionesToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: shows the how to play window

		//How to Play
		HowToPlay instrucciones;
		instrucciones.ShowDialog();
	}

	private: System::Void save_game()
	{
		//Functioning: funtion for saving the game's actual state in a file (.txt)

		using namespace std;
		using std::string;
		int play_count = 1;

		ofstream saved_game_file;

		//code for creating file or overwriting it
		saved_game_file.open("SavedGameData.txt", ios::out); // opens file
		saved_game_file.close(); // closes file

		saved_game_file.open("SavedGameData.txt", ios::app); // opens file, in mode append

		if (saved_game_file.fail())
		{
			//error
			//exit(1);
		}

		//saved bool
		saved_game_file << "Saved: ";
		saved_game_file	<< "true" << endl;

		//save username
		saved_game_file << "Username ";
		string username = msclr::interop::marshal_as<std::string>(Username_label->Text);
		saved_game_file << username << endl;

		//save difficulty
		saved_game_file << "Difficulty: ";
		if (objSettings->getDifficulty() == 1)
			saved_game_file << "Easy" << endl;
		else if (objSettings->getDifficulty() == 2)
			saved_game_file << "Medium" << endl;
		else if (objSettings->getDifficulty() == 3)
			saved_game_file << "Hard" << endl;

		//save random comb
		saved_game_file << "Random_Combination: ";

		auto actual_randCombBtn_backImg = rand_comb1_button->BackgroundImage;

		int count_comb = 0;
		while (count_comb < 4)
		{
			if (count_comb == 1)
				actual_randCombBtn_backImg = rand_comb2_button->BackgroundImage;
			else if (count_comb == 2)
				actual_randCombBtn_backImg = rand_comb3_button->BackgroundImage;
			else if (count_comb == 3)
				actual_randCombBtn_backImg = rand_comb4_button->BackgroundImage;


			if (actual_randCombBtn_backImg == red_button->BackgroundImage)
				saved_game_file << "red ";
			else if (actual_randCombBtn_backImg == blue_button->BackgroundImage)
				saved_game_file << "blue ";
			else if (actual_randCombBtn_backImg == green_button->BackgroundImage)
				saved_game_file << "green ";
			else if (actual_randCombBtn_backImg == yellow_button->BackgroundImage)
				saved_game_file << "yellow ";
			else if (actual_randCombBtn_backImg == pink_button->BackgroundImage)
				saved_game_file << "pink ";
			else if (actual_randCombBtn_backImg == brown_button->BackgroundImage)
				saved_game_file << "brown ";

			count_comb++;
		}
		saved_game_file << endl;

		//save element rep
		saved_game_file << "Element_Repetition: ";

		if (objSettings->getElementRep() == true)
			saved_game_file << "Enabled";
		else if (objSettings->getElementRep() == false)
			saved_game_file << "Disabled";
		saved_game_file << endl;

		//save saved_plays
		saved_game_file << "saved_plays_counter: ";
		saved_game_file << saved_plays << endl;

		//save clock
		saved_game_file << "Clock: ";
		if (objSettings->getClock() == true)
			saved_game_file << "Clock_Enabled ";
		else if ((objSettings->getClock() == false) && (objSettings->getTimekeeperGame() == false) && (objSettings->getTimekeeperPlay() == false))
			saved_game_file << "Clock_Disabled ";
		else if (objSettings->getTimekeeperGame() == true)
			saved_game_file << "Timekeeper_Game ";
		else if (objSettings->getTimekeeperPlay() == true)
			saved_game_file << "Timekeeper_Play ";
		saved_game_file << endl;

		//save time
		saved_game_file << "Time: ";

		if (objSettings->getClock() == true)
		{
			saved_game_file << hours << " ";
			saved_game_file << minutes << " ";
			saved_game_file << seconds << " ";
			saved_game_file << endl;
		}
		else if (objSettings->getTimekeeperGame() == true)
		{
			saved_game_file << hoursG << " ";
			saved_game_file << minutesG << " ";
			saved_game_file << secondsG << " ";
			saved_game_file << endl;
		}
		else if (objSettings->getTimekeeperPlay() == true)
		{
			saved_game_file << "0 ";
			saved_game_file << minutesP << " ";
			saved_game_file << secondsP << " ";
			saved_game_file << endl;
		}

		//save time_hms_encrip
		saved_game_file << "Time_hms_encrip: ";

		saved_game_file << hoursTimer << " ";
		saved_game_file << minutesTimer << " ";
		saved_game_file << secondsTimer << " ";
		saved_game_file << endl;
		

		//save time_encrip
		string gameT_str;
		saved_game_file << "Time_encrip: ";
		gameT_str = msclr::interop::marshal_as<std::string>(num_gameTimer_label->Text);
		saved_game_file << gameT_str << endl;
		saved_game_file << "Time_encrip_str: ";
		gameT_str = msclr::interop::marshal_as<std::string>(gameTimer_label->Text);
		saved_game_file << gameT_str << endl;

		// saves combinations per play
		auto play_picBox1_backImg = play1_pictureBox1->BackgroundImage;
		auto play_picBox2_backImg = play1_pictureBox2->BackgroundImage;
		auto play_picBox3_backImg = play1_pictureBox3->BackgroundImage;
		auto play_picBox4_backImg = play1_pictureBox4->BackgroundImage;

		while (play_count <= saved_plays)
		{
			saved_game_file << "Combination: ";

			if (play_count == 1)
			{
				/*
				auto play_picBox1_backImg = play1_pictureBox1->BackgroundImage;
				auto play_picBox2_backImg = play1_pictureBox2->BackgroundImage;
				auto play_picBox3_backImg = play1_pictureBox3->BackgroundImage;
				auto play_picBox4_backImg = play1_pictureBox4->BackgroundImage;
				*/
			}
			if (play_count == 2)
			{
				play_picBox1_backImg = play2_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play2_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play2_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play2_pictureBox4->BackgroundImage;
			}
			if (play_count == 3)
			{
				play_picBox1_backImg = play3_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play3_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play3_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play3_pictureBox4->BackgroundImage;
			}
			if (play_count == 4)
			{
				play_picBox1_backImg = play4_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play4_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play4_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play4_pictureBox4->BackgroundImage;
			}
			if (play_count == 5)
			{
				play_picBox1_backImg = play5_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play5_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play5_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play5_pictureBox4->BackgroundImage;
			}
			if (play_count == 6)
			{
				play_picBox1_backImg = play6_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play6_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play6_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play6_pictureBox4->BackgroundImage;
			}
			if (play_count == 7)
			{
				play_picBox1_backImg = play7_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play7_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play7_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play7_pictureBox4->BackgroundImage;
			}
			if (play_count == 8)
			{
				play_picBox1_backImg = play8_pictureBox1->BackgroundImage;
				play_picBox2_backImg = play8_pictureBox2->BackgroundImage;
				play_picBox3_backImg = play8_pictureBox3->BackgroundImage;
				play_picBox4_backImg = play8_pictureBox4->BackgroundImage;
			}

			if (play_picBox1_backImg == red_button->BackgroundImage)
				saved_game_file << "red ";
			else if (play_picBox1_backImg == blue_button->BackgroundImage)
				saved_game_file << "blue ";
			else if (play_picBox1_backImg == green_button->BackgroundImage)
				saved_game_file << "green ";
			else if (play_picBox1_backImg == yellow_button->BackgroundImage)
				saved_game_file << "yellow ";
			else if (play_picBox1_backImg == pink_button->BackgroundImage)
				saved_game_file << "pink ";
			else if (play_picBox1_backImg == brown_button->BackgroundImage)
				saved_game_file << "brown ";

			if (play_picBox2_backImg == red_button->BackgroundImage)
				saved_game_file << "red ";
			else if (play_picBox2_backImg == blue_button->BackgroundImage)
				saved_game_file << "blue ";
			else if (play_picBox2_backImg == green_button->BackgroundImage)
				saved_game_file << "green ";
			else if (play_picBox2_backImg == yellow_button->BackgroundImage)
				saved_game_file << "yellow ";
			else if (play_picBox2_backImg == pink_button->BackgroundImage)
				saved_game_file << "pink ";
			else if (play_picBox2_backImg == brown_button->BackgroundImage)
				saved_game_file << "brown ";

			if (play_picBox3_backImg == red_button->BackgroundImage)
				saved_game_file << "red ";
			else if (play_picBox3_backImg == blue_button->BackgroundImage)
				saved_game_file << "blue ";
			else if (play_picBox3_backImg == green_button->BackgroundImage)
				saved_game_file << "green ";
			else if (play_picBox3_backImg == yellow_button->BackgroundImage)
				saved_game_file << "yellow ";
			else if (play_picBox3_backImg == pink_button->BackgroundImage)
				saved_game_file << "pink ";
			else if (play_picBox3_backImg == brown_button->BackgroundImage)
				saved_game_file << "brown ";

			if (play_picBox4_backImg == red_button->BackgroundImage)
				saved_game_file << "red ";
			else if (play_picBox4_backImg == blue_button->BackgroundImage)
				saved_game_file << "blue ";
			else if (play_picBox4_backImg == green_button->BackgroundImage)
				saved_game_file << "green ";
			else if (play_picBox4_backImg == yellow_button->BackgroundImage)
				saved_game_file << "yellow ";
			else if (play_picBox4_backImg == pink_button->BackgroundImage)
				saved_game_file << "pink ";
			else if (play_picBox4_backImg == brown_button->BackgroundImage)
				saved_game_file << "brown ";

			saved_game_file << endl;

			play_count++;
		}

		//save scores per play
		auto score_picBox1_backImg = play1_score_picBox1->BackgroundImage;
		auto score_picBox2_backImg = play1_score_picBox2->BackgroundImage;
		auto score_picBox3_backImg = play1_score_picBox3->BackgroundImage;
		auto score_picBox4_backImg = play1_score_picBox4->BackgroundImage;

		play_count = 1;
		while (play_count <= saved_plays)
		{

			if (play_count == 1)
			{
				
				score_picBox1_backImg = play1_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play1_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play1_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play1_score_picBox4->BackgroundImage;
				
			}
			if (play_count == 2)
			{
				score_picBox1_backImg = play2_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play2_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play2_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play2_score_picBox4->BackgroundImage;
			}
			if (play_count == 3)
			{
				score_picBox1_backImg = play3_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play3_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play3_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play3_score_picBox4->BackgroundImage;
			}
			if (play_count == 4)
			{
				score_picBox1_backImg = play4_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play4_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play4_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play4_score_picBox4->BackgroundImage;
			}
			if (play_count == 5)
			{
				score_picBox1_backImg = play5_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play5_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play5_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play5_score_picBox4->BackgroundImage;
			}
			if (play_count == 6)
			{
				score_picBox1_backImg = play6_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play6_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play6_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play6_score_picBox4->BackgroundImage;
			}
			if (play_count == 7)
			{
				score_picBox1_backImg = play7_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play7_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play7_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play7_score_picBox4->BackgroundImage;
			}
			if (play_count == 8)
			{
				score_picBox1_backImg = play8_score_picBox1->BackgroundImage;
				score_picBox2_backImg = play8_score_picBox2->BackgroundImage;
				score_picBox3_backImg = play8_score_picBox3->BackgroundImage;
				score_picBox4_backImg = play8_score_picBox4->BackgroundImage;
			}

			saved_game_file << "Score: ";

			if (score_picBox1_backImg == black_button->BackgroundImage)
				saved_game_file << "black ";
			else if (score_picBox1_backImg == white_button->BackgroundImage)
				saved_game_file << "white ";
			else if (score_picBox1_backImg == blank_score_button->BackgroundImage)
				saved_game_file << "blank ";
			else
				saved_game_file << "blank ";

			if (score_picBox2_backImg == black_button->BackgroundImage)
				saved_game_file << "black ";
			else if (score_picBox2_backImg == white_button->BackgroundImage)
				saved_game_file << "white ";
			else if (score_picBox2_backImg == blank_score_button->BackgroundImage)
				saved_game_file << "blank ";
			else
				saved_game_file << "blank ";

			if (score_picBox3_backImg == black_button->BackgroundImage)
				saved_game_file << "black ";
			else if (score_picBox3_backImg == white_button->BackgroundImage)
				saved_game_file << "white ";
			else if (score_picBox3_backImg == blank_score_button->BackgroundImage)
				saved_game_file << "blank ";
			else
				saved_game_file << "blank ";

			if (score_picBox4_backImg == black_button->BackgroundImage)
				saved_game_file << "black ";
			else if (score_picBox4_backImg == white_button->BackgroundImage)
				saved_game_file << "white ";
			else if (score_picBox4_backImg == blank_score_button->BackgroundImage)
				saved_game_file << "blank ";
			else
				saved_game_file << "blank ";

			saved_game_file << endl;

			play_count++;
		}


		saved_game_file.close(); // closes file 

	}

	private: System::Void load_game()
	{
		//Functioning: function for loading the saved game

		using namespace std;

		string titulo;
		string dato;

		if (saved_game == true)
		{
			ifstream saved_game_file;
			saved_game_file.open("SavedGameData.txt", ios::in); //opens file, in read-only mode

			saved_game_file >> titulo;
			saved_game_file >> dato;

			// code for loading the game
			int line_counter = 0;
			while (line_counter <= 10)
			{
				if (line_counter == 1)
				{
					//loads username

					saved_game_file >> titulo;
					saved_game_file >> dato;

					string username = dato;
					Username_label->Text = gcnew String(username.c_str());
				}
				if (line_counter == 2)
				{
					//loads the difficulty conf.

					saved_game_file >> titulo;
					saved_game_file >> dato;

					if (dato == "Easy")
					{
						objSettings->setDifficulty(1);
						difficulty_label->Text = "Difficulty: Easy";
					}
					else if (dato == "Medium")
					{
						objSettings->setDifficulty(2);
						difficulty_label->Text = "Difficulty: Medium";
					}
					else if (dato == "Hard")
					{
						objSettings->setDifficulty(3);
						difficulty_label->Text = "Difficulty: Hard";
					}
				}
				if (line_counter == 3)
				{
					//loads the random combination

					saved_game_file >> titulo;

					auto color = blank_button->BackgroundImage;
					int local_count = 0;
					while (local_count < 4)
					{
						saved_game_file >> dato;

						if (dato == "red")
							color = red_button->BackgroundImage;
						else if (dato == "blue")
							color = blue_button->BackgroundImage;
						else if (dato == "green")
							color = green_button->BackgroundImage;
						else if (dato == "yellow")
							color = yellow_button->BackgroundImage;
						else if (dato == "pink")
							color = pink_button->BackgroundImage;
						else if (dato == "brown")
							color = brown_button->BackgroundImage;

						if (local_count == 0)
							rand_comb1_button->BackgroundImage = color;
						if (local_count == 1)
							rand_comb2_button->BackgroundImage = color;
						if (local_count == 2)
							rand_comb3_button->BackgroundImage = color;
						if (local_count == 3)
							rand_comb4_button->BackgroundImage = color;

						local_count++;
					}
				}
				if (line_counter == 4)
				{
					//loads the element repetition conf.

					saved_game_file >> titulo;
					saved_game_file >> dato;

					if (dato == "Disabled")
					{
						objSettings->setElementRep(false);
						repetition_label->Text = "Element Repetition: OFF";
					}
					else if (dato == "Enabled")
					{
						objSettings->setElementRep(true);
						repetition_label->Text = "Element Repetition: ON";
					}
				}
				if (line_counter == 5)
				{
					//loads the value of the saved_plays variable

					saved_game_file >> titulo;
					saved_game_file >> dato;

					saved_plays = stoi(dato);

					actual_play = saved_plays + 1; // actual play controls in which play the enter_play_button will write the score
				}
				if (line_counter == 6)
				{
					//loads the clock/Timekeeper conf.

					saved_game_file >> titulo;
					saved_game_file >> dato;

					if (dato == "Clock_Enabled")
					{
						Time->Visible = true;

						objSettings->setClock(true);
						objSettings->setTimekeeperGame(false);
						objSettings->setTimekeeperPlay(false);

						saved_game_file >> titulo;
						saved_game_file >> dato;
						hours = stoi(dato);
						saved_game_file >> dato;
						minutes = stoi(dato);
						saved_game_file >> dato;
						seconds = stoi(dato);

						//Gives the clock its initial value
						if (hours < 10)
						{
							if (minutes < 10)
							{
								if (seconds < 10)
								{
									Time->Text = "0" + hours + ":0" + minutes + ":0" + seconds;
								}
								else if (seconds >= 10)
								{
									Time->Text = "0" + hours + ":0" + minutes + ":" + seconds;
								}
							}
							else if (minutes >= 10)
							{
								if (seconds < 10)
								{
									Time->Text = "0" + hours + ":" + minutes + ":0" + seconds;
								}
								else if (seconds >= 10)
								{
									Time->Text = "0" + hours + ":" + minutes + ":" + seconds;
								}
							}
						}
						else if (hours >= 10)
						{
							if (minutes < 10)
							{
								if (seconds < 10)
								{
									Time->Text = hours + ":0" + minutes + ":0" + seconds;
								}
								else if (seconds >= 10)
								{
									Time->Text = hours + ":0" + minutes + ":" + seconds;
								}
							}
							else if (minutes >= 10)
							{
								if (seconds < 10)
								{
									Time->Text = hours + ":" + minutes + ":0" + seconds;
								}
								else if (seconds >= 10)
								{
									Time->Text = hours + ":" + minutes + ":" + seconds;
								}
							}
						}
					}
					else if (dato == "Clock_Disabled")
					{
						objSettings->setClock(false);
						objSettings->setTimekeeperGame(false);
						objSettings->setTimekeeperPlay(false);
						saved_game_file >> titulo;

						Time->Visible = false;
					}
					else if (dato == "Timekeeper_Play")
					{
						Time->Visible = true;

						objSettings->setTimekeeperPlay(true);
						objSettings->setTimekeeperGame(false);
						objSettings->setClock(false);

						saved_game_file >> titulo;
						saved_game_file >> dato; // for the hours
						saved_game_file >> dato;
						minutesP = stoi(dato);
						saved_game_file >> dato;
						secondsP = stoi(dato);

						if (hours < 10)
						{
							if (minutesP < 10)
							{
								if (secondsP < 10)
								{
									Time->Text = "00" + ":0" + minutesP + ":0" + secondsP;
								}
								else if (secondsP >= 10)
								{
									Time->Text = "00" + ":0" + minutesP + ":" + secondsP;
								}
							}
							else if (minutesP >= 10)
							{
								if (secondsP < 10)
								{
									Time->Text = "00" + ":" + minutesP + ":0" + seconds;
								}
								else if (secondsP >= 10)
								{
									Time->Text = "00" + ":" + minutesP + ":" + seconds;
								}
							}
						}
						else if (hours >= 10)
						{
							if (minutesP < 10)
							{
								if (secondsP < 10)
								{
									Time->Text = "00" + ":0" + minutesP + ":0" + seconds;
								}
								else if (secondsP >= 10)
								{
									Time->Text = "00" + ":0" + minutesP + ":" + seconds;
								}
							}
							else if (minutesP >= 10)
							{
								if (secondsP < 10)
								{
									Time->Text = "00" + ":" + minutesP + ":0" + seconds;
								}
								else if (seconds >= 10)
								{
									Time->Text = "00" + ":" + minutesP + ":" + seconds;
								}
							}
						}
					}
					else if (dato == "Timekeeper_Game")
					{
						Time->Visible = true;

						objSettings->setTimekeeperGame(true);
						objSettings->setTimekeeperPlay(false);
						objSettings->setClock(false);

						saved_game_file >> titulo;
						saved_game_file >> dato;
						hoursG = stoi(dato);
						saved_game_file >> dato;
						minutesG = stoi(dato);
						saved_game_file >> dato;
						secondsG = stoi(dato);

						if (hoursG < 10)
						{
							if (minutesG < 10)
							{
								if (secondsG < 10)
								{
									Time->Text = "0" + hoursG + ":0" + minutesG + ":0" + secondsG;
								}
								else if (secondsG >= 10)
								{
									Time->Text = "0" + hoursG + ":0" + minutesG + ":" + secondsG;
								}
							}
							else if (minutesG >= 10)
							{
								if (secondsG < 10)
								{
									Time->Text = "0" + hoursG + ":" + minutesG + ":0" + secondsG;
								}
								else if (secondsG >= 10)
								{
									Time->Text = "0" + hoursG + ":" + minutesG + ":" + secondsG;
								}
							}
						}
						else if (hoursG >= 10)
						{
							if (minutesG < 10)
							{
								if (secondsG < 10)
								{
									Time->Text = hoursG + ":0" + minutesG + ":0" + secondsG;
								}
								else if (secondsG >= 10)
								{
									Time->Text = hoursG + ":0" + minutesG + ":" + secondsG;
								}
							}
							else if (minutesG >= 10)
							{
								if (secondsG < 10)
								{
									Time->Text = hoursG + ":" + minutesG + ":0" + secondsG;
								}
								else if (secondsG >= 10)
								{
									Time->Text = hoursG + ":" + minutesG + ":" + secondsG;
								}
							}
						}

					}

					line_counter++;
				}
				if (line_counter == 7)
				{
					//loads time_hms_encrip, hms stands for: hours, minutes, seconds and encrip for encripted
					
					int dato_int;
					
					saved_game_file >> titulo;

					saved_game_file >> dato;
					dato_int = stoi(dato);
					hoursTimer = dato_int;

					saved_game_file >> dato;
					dato_int = stoi(dato);
					minutesTimer = dato_int;

					saved_game_file >> dato;
					dato_int = stoi(dato);
					secondsTimer = dato_int;
				}
				if (line_counter == 8)
				{
					//loads Time_encrip and Time_encrip_str values

					//Time_encrip
					saved_game_file >> titulo;
					saved_game_file >> dato;

					String^ num_gameT_STR = gcnew String(dato.c_str());
					num_gameTimer_label->Text = num_gameT_STR;

					//Time_encrip_str
					saved_game_file >> titulo;
					saved_game_file >> dato;

					String^ gameT_STR = gcnew String(dato.c_str());
					gameTimer_label->Text = gameT_STR;
				}
				if (line_counter == 9)
				{
					//loads the color/letter/number/shape combination for each play

					auto color = blank_button->BackgroundImage;

					int play_counter = 1;
					while (play_counter <= saved_plays)
					{
						saved_game_file >> titulo;

						int color_counter = 1;
						while (color_counter <= 4)
						{
							saved_game_file >> dato;

							if (dato == "red")
								color = red_button->BackgroundImage;
							else if (dato == "blue")
								color = blue_button->BackgroundImage;
							else if (dato == "green")
								color = green_button->BackgroundImage;
							else if (dato == "yellow")
								color = yellow_button->BackgroundImage;
							else if (dato == "pink")
								color = pink_button->BackgroundImage;
							else if (dato == "brown")
								color = brown_button->BackgroundImage;

							if (play_counter == 1)
							{
								if (color_counter == 1)
									play1_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play1_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play1_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play1_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play2_pic_groupBox->Visible = true;
								play2_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play2_score_groupBox->Visible = true;
								play2_score_groupBox->Enabled = true;
							}
							else if (play_counter == 2)
							{
								if (color_counter == 1)
									play2_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play2_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play2_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play2_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play3_pic_groupBox->Visible = true;
								play3_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play3_score_groupBox->Visible = true;
								play3_score_groupBox->Enabled = true;
							}
							else if (play_counter == 3)
							{
								if (color_counter == 1)
									play3_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play3_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play3_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play3_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play4_pic_groupBox->Visible = true;
								play4_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play4_score_groupBox->Visible = true;
								play4_score_groupBox->Enabled = true;
							}
							else if (play_counter == 4)
							{
								if (color_counter == 1)
									play4_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play4_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play4_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play4_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play5_pic_groupBox->Visible = true;
								play5_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play5_score_groupBox->Visible = true;
								play5_score_groupBox->Enabled = true;
							}
							else if (play_counter == 5)
							{
								if (color_counter == 1)
									play5_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play5_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play5_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play5_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play6_pic_groupBox->Visible = true;
								play6_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play6_score_groupBox->Visible = true;
								play6_score_groupBox->Enabled = true;
							}
							else if (play_counter == 6)
							{
								if (color_counter == 1)
									play6_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play6_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play6_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play6_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play7_pic_groupBox->Visible = true;
								play7_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play7_score_groupBox->Visible = true;
								play7_score_groupBox->Enabled = true;
							}
							else if (play_counter == 7)
							{
								if (color_counter == 1)
									play7_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play7_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play7_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play7_pictureBox4->BackgroundImage = color;

								//Enables next pic_groupBox
								play8_pic_groupBox->Visible = true;
								play8_pic_groupBox->Enabled = true;
								//Enables next score_groupBox
								play8_score_groupBox->Visible = true;
								play8_score_groupBox->Enabled = true;
							}
							else if (play_counter == 8)
							{
								if (color_counter == 1)
									play8_pictureBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play8_pictureBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play8_pictureBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play8_pictureBox4->BackgroundImage = color;
							}

							color_counter++;
						}

						play_counter++;
					}
				}
				if (line_counter == 10)
				{
					//loads the score for each play

					auto color = blank_score_button->BackgroundImage;
					int play_counter = 1;
					while (play_counter <= saved_plays)
					{
						saved_game_file >> titulo;

						int color_counter = 1;
						while (color_counter <= 4)
						{
							saved_game_file >> dato;

							if (dato == "black")
								color = black_button->BackgroundImage;
							else if (dato == "white")
								color = white_button->BackgroundImage;
							else if (dato == "blank")
								color = blank_score_button->BackgroundImage;


							if (play_counter == 1)
							{
								if (color_counter == 1)
									play1_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play1_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play1_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play1_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play2_score_groupBox->Visible = true;
								play2_score_groupBox->Enabled = true;
							}
							else if (play_counter == 2)
							{
								if (color_counter == 1)
									play2_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play2_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play2_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play2_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play3_score_groupBox->Visible = true;
								play3_score_groupBox->Enabled = true;
							}
							else if (play_counter == 3)
							{
								if (color_counter == 1)
									play3_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play3_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play3_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play3_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play4_score_groupBox->Visible = true;
								play4_score_groupBox->Enabled = true;
							}
							else if (play_counter == 4)
							{
								if (color_counter == 1)
									play4_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play4_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play4_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play4_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play5_score_groupBox->Visible = true;
								play5_score_groupBox->Enabled = true;
							}
							else if (play_counter == 5)
							{
								if (color_counter == 1)
									play5_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play5_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play5_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play5_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play6_score_groupBox->Visible = true;
								play6_score_groupBox->Enabled = true;
							}
							else if (play_counter == 6)
							{
								if (color_counter == 1)
									play6_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play6_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play6_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play6_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play7_score_groupBox->Visible = true;
								play7_score_groupBox->Enabled = true;
							}
							else if (play_counter == 7)
							{
								if (color_counter == 1)
									play7_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play7_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play7_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play7_score_picBox4->BackgroundImage = color;

								//Enables next score_groupBox
								play8_score_groupBox->Visible = true;
								play8_score_groupBox->Enabled = true;
							}
							else if (play_counter == 8)
							{
								if (color_counter == 1)
									play8_score_picBox1->BackgroundImage = color;
								else if (color_counter == 2)
									play8_score_picBox2->BackgroundImage = color;
								else if (color_counter == 3)
									play8_score_picBox3->BackgroundImage = color;
								else if (color_counter == 4)
									play8_score_picBox4->BackgroundImage = color;
							}

							color_counter++;
						}

						play_counter++;
					}
				}

				line_counter++;
			}

			saved_game_file.close(); // closes file
		}

	}

	private: System::Void saveToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e)
	{
		save_game(); //calls save_game() function
	}

	private: System::Void loadGameToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e)
	{
		//Functioning: loads the saved game

		Clock->Enabled = false; //stops the Clock

		if (saved_game == true)
		{
			load_game(); //calls load_game() function

			if (saved_plays == 1)
			{
				//combination
				play2_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play2_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play2_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play2_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play3_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play3_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play3_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play3_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play4_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play5_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play2_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play2_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play2_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play2_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play3_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play3_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play3_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play3_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play4_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play5_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}
			else if (saved_plays == 2)
			{
				//combinations
				play3_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play3_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play3_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play3_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play4_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play5_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play3_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play3_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play3_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play3_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play4_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play5_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}
			else if (saved_plays == 3)
			{
				//combinations
				play4_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play4_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play5_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play4_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play4_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play5_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}
			else if (saved_plays == 4)
			{
				//combination
				play5_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play5_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play5_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play6_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}
			else if (saved_plays == 5)
			{
				//combinations
				play6_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play6_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play6_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play7_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}
			else if (saved_plays == 6)
			{
				//combinations
				play7_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play7_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play7_score_picBox4->BackgroundImage = blank_button->BackgroundImage;

				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}
			else if (saved_plays == 7)
			{
				//combinations
				play8_pictureBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_pictureBox4->BackgroundImage = blank_button->BackgroundImage;

				//score
				play8_score_picBox1->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox2->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox3->BackgroundImage = blank_button->BackgroundImage;
				play8_score_picBox4->BackgroundImage = blank_button->BackgroundImage;
			}


			play1_guess1_button->Enabled = false;
			play1_guess2_button->Enabled = false;
			play1_guess3_button->Enabled = false;
			play1_guess4_button->Enabled = false;
			red_button->Enabled = false;
			blue_button->Enabled = false;
			green_button->Enabled = false;
			yellow_button->Enabled = false;
			pink_button->Enabled = false;
			brown_button->Enabled = false;

			Vent_Play_Start->Enabled = true;
			loaded_game = true;

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

			//gameTimer starts
			game_timer->Enabled = true;


			//deletes the saved game data
			using namespace std;
			ofstream SavedGame;
			SavedGame.open("SavedGameData.txt", ios::out);
			SavedGame.close();

			saved_game = false;

		}
		else if (saved_game == false)
		{
			load_warning_groupBox->BringToFront();
			load_warning_groupBox->Visible = true;
			load_warning_groupBox->Enabled = true;
		}
	}


	private: System::Void ok_load_warn_btn_Click(System::Object^ sender, System::EventArgs^ e) 
	{
		//Functioning: closes the Load Warning window

		load_warning_groupBox->Visible = false;
		load_warning_groupBox->Enabled = false;

		Clock->Enabled = true; //Clock continues
	}


	private: System::Void label1_Click_2(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void game_timer_Tick(System::Object^ sender, System::EventArgs^ e) 
	{
		//Functioning: runs a chronometer to keep track of the game's total time for every game

		secondsTimer++;
		if (secondsTimer == 60)
		{
			secondsTimer = 0;
			minutesTimer++;
		}
		if (minutesTimer == 60)
		{
			minutesTimer = 0;
			hoursTimer++;
		}
		if (hoursTimer == 2)
		{
			secondsTimer = 0;
			minutesTimer = 0;
			hoursTimer = 0;
		}
		

		String^ secT = Convert::ToString(secondsTimer);
		String^ minT = Convert::ToString(minutesTimer);
		String^ hourT = Convert::ToString(hoursTimer);

		if (hoursTimer < 10)
		{
			if (minutesTimer < 10)
			{
				if (secondsTimer < 10)
				{
					gameTimer_label->Text = "0" + hourT + ":0" + minT + ":0" + secT;
					num_gameTimer_label->Text = "0" + hourT + "0" + minT + "0" + secT;
				}
				else if (secondsTimer >= 10)
				{
					gameTimer_label->Text = "0" + hourT + ":0" + minT + ":" + secT;
					num_gameTimer_label->Text = "0" + hourT + "0" + minT + secT;
				}
			}
			else if (minutesTimer >= 10)
			{
				if (secondsTimer < 10)
				{
					gameTimer_label->Text = "0" + hourT + ":" + minT + ":0" + secT;
					num_gameTimer_label->Text = "0" + hourT + minT + "0" + secT;
				}
				else if (secondsTimer >= 10)
				{
					gameTimer_label->Text = "0" + hourT + ":" + minT + ":" + secT;
					num_gameTimer_label->Text = "0" + hourT + minT + secT;
				}
			}
		}
		else if (hoursTimer >= 10)
		{
			if (minutesTimer < 10)
			{
				if (secondsTimer < 10)
				{
					gameTimer_label->Text = hourT + ":0" + minT + ":0" + secT;
					num_gameTimer_label->Text = hourT + "0" + minT + "0" + secT;
				}
				else if (secondsTimer >= 10)
				{
					gameTimer_label->Text = hourT + ":0" + minT + ":" + secT;
					num_gameTimer_label->Text = hourT + "0" + minT + secT;
				}
			}
			else if (minutesTimer >= 10)
			{
				if (secondsTimer < 10)
				{
					gameTimer_label->Text = hourT + ":" + minT + ":0" + secT;
					num_gameTimer_label->Text = hourT + minT + "0" + secT;
				}
				else if (secondsTimer >= 10)
				{
					gameTimer_label->Text = hourT + ":" + minT + ":" + secT;
					num_gameTimer_label->Text = hourT + minT + secT;
				}
			}
		}


	}



};
}
