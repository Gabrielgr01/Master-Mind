# Master-Mind

//VentanaPlay.h
//CONFIGURACION DEFAULT

#pragma once

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
	public:
		VentanaPlay(void)
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
		~VentanaPlay()
		{
			if (components)
			{
				delete components;
			}
		}

	protected:






	private: System::Windows::Forms::Button^ button1;
	private: System::Windows::Forms::Button^ button2;
	private: System::Windows::Forms::Button^ button3;
	private: System::Windows::Forms::Button^ button4;
	private: System::Windows::Forms::Button^ button5;
	private: System::Windows::Forms::Button^ button6;
	private: System::Windows::Forms::Timer^ TimeKeeper;







	private: System::Windows::Forms::Button^ button8;
	private: System::Windows::Forms::Button^ button9;
	private: System::Windows::Forms::Button^ button10;
	private: System::Windows::Forms::Button^ button11;

	private: System::Windows::Forms::MenuStrip^ menuStrip1;





	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ instruccionesToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ salirToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ archivoToolStripMenuItem;






	private: System::Windows::Forms::Label^ label1;
	private: System::Windows::Forms::ToolStripMenuItem^ saveToolStripMenuItem;
	private: System::Windows::Forms::Label^ Time;



	private: System::ComponentModel::IContainer^ components;

	protected:

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
			this->button1 = (gcnew System::Windows::Forms::Button());
			this->button2 = (gcnew System::Windows::Forms::Button());
			this->button3 = (gcnew System::Windows::Forms::Button());
			this->button4 = (gcnew System::Windows::Forms::Button());
			this->button5 = (gcnew System::Windows::Forms::Button());
			this->button6 = (gcnew System::Windows::Forms::Button());
			this->TimeKeeper = (gcnew System::Windows::Forms::Timer(this->components));
			this->button8 = (gcnew System::Windows::Forms::Button());
			this->button9 = (gcnew System::Windows::Forms::Button());
			this->button10 = (gcnew System::Windows::Forms::Button());
			this->button11 = (gcnew System::Windows::Forms::Button());
			this->menuStrip1 = (gcnew System::Windows::Forms::MenuStrip());
			this->archivoToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->saveToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->ayudaToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->instruccionesToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->salirToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->label1 = (gcnew System::Windows::Forms::Label());
			this->Time = (gcnew System::Windows::Forms::Label());
			this->menuStrip1->SuspendLayout();
			this->SuspendLayout();
			// 
			// button1
			// 
			this->button1->BackColor = System::Drawing::Color::Red;
			this->button1->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button1->ImageAlign = System::Drawing::ContentAlignment::BottomLeft;
			this->button1->Location = System::Drawing::Point(924, 45);
			this->button1->Name = L"button1";
			this->button1->Size = System::Drawing::Size(69, 60);
			this->button1->TabIndex = 0;
			this->button1->Text = L"Red";
			this->button1->UseVisualStyleBackColor = false;
			this->button1->Click += gcnew System::EventHandler(this, &VentanaPlay::button1_Click_1);
			// 
			// button2
			// 
			this->button2->BackColor = System::Drawing::Color::Blue;
			this->button2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button2->Location = System::Drawing::Point(924, 111);
			this->button2->Name = L"button2";
			this->button2->Size = System::Drawing::Size(69, 65);
			this->button2->TabIndex = 1;
			this->button2->Text = L"Blue";
			this->button2->UseVisualStyleBackColor = false;
			// 
			// button3
			// 
			this->button3->BackColor = System::Drawing::Color::Green;
			this->button3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button3->Location = System::Drawing::Point(924, 182);
			this->button3->Name = L"button3";
			this->button3->Size = System::Drawing::Size(69, 63);
			this->button3->TabIndex = 2;
			this->button3->Text = L"Green";
			this->button3->UseVisualStyleBackColor = false;
			this->button3->Click += gcnew System::EventHandler(this, &VentanaPlay::button3_Click);
			// 
			// button4
			// 
			this->button4->BackColor = System::Drawing::Color::Yellow;
			this->button4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button4->Location = System::Drawing::Point(924, 251);
			this->button4->Name = L"button4";
			this->button4->Size = System::Drawing::Size(69, 63);
			this->button4->TabIndex = 3;
			this->button4->Text = L"Yellow";
			this->button4->UseVisualStyleBackColor = false;
			// 
			// button5
			// 
			this->button5->BackColor = System::Drawing::Color::FromArgb(static_cast<System::Int32>(static_cast<System::Byte>(255)), static_cast<System::Int32>(static_cast<System::Byte>(128)),
				static_cast<System::Int32>(static_cast<System::Byte>(255)));
			this->button5->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button5->Location = System::Drawing::Point(924, 320);
			this->button5->Name = L"button5";
			this->button5->Size = System::Drawing::Size(69, 63);
			this->button5->TabIndex = 4;
			this->button5->Text = L"Pink";
			this->button5->UseVisualStyleBackColor = false;
			this->button5->Click += gcnew System::EventHandler(this, &VentanaPlay::button5_Click);
			// 
			// button6
			// 
			this->button6->BackColor = System::Drawing::Color::SaddleBrown;
			this->button6->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button6->Location = System::Drawing::Point(924, 389);
			this->button6->Name = L"button6";
			this->button6->Size = System::Drawing::Size(69, 63);
			this->button6->TabIndex = 5;
			this->button6->Text = L"Brown";
			this->button6->UseVisualStyleBackColor = false;
			// 
			// TimeKeeper
			// 
			this->TimeKeeper->Enabled = true;
			this->TimeKeeper->Interval = 1000;
			this->TimeKeeper->Tick += gcnew System::EventHandler(this, &VentanaPlay::TimeKeeper_Tick);
			// 
			// button8
			// 
			this->button8->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button8->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button8->Location = System::Drawing::Point(223, 377);
			this->button8->Name = L"button8";
			this->button8->Size = System::Drawing::Size(72, 63);
			this->button8->TabIndex = 14;
			this->button8->Text = L"Guess 1";
			this->button8->UseVisualStyleBackColor = false;
			this->button8->Click += gcnew System::EventHandler(this, &VentanaPlay::button8_Click);
			// 
			// button9
			// 
			this->button9->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button9->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button9->Location = System::Drawing::Point(301, 377);
			this->button9->Name = L"button9";
			this->button9->Size = System::Drawing::Size(72, 63);
			this->button9->TabIndex = 15;
			this->button9->Text = L"Guess 2";
			this->button9->UseVisualStyleBackColor = false;
			// 
			// button10
			// 
			this->button10->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button10->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button10->Location = System::Drawing::Point(379, 377);
			this->button10->Name = L"button10";
			this->button10->Size = System::Drawing::Size(72, 63);
			this->button10->TabIndex = 16;
			this->button10->Text = L"Guess 3";
			this->button10->UseVisualStyleBackColor = false;
			// 
			// button11
			// 
			this->button11->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button11->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button11->Location = System::Drawing::Point(457, 377);
			this->button11->Name = L"button11";
			this->button11->Size = System::Drawing::Size(72, 63);
			this->button11->TabIndex = 17;
			this->button11->Text = L"Guess 4";
			this->button11->UseVisualStyleBackColor = false;
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
			this->menuStrip1->Size = System::Drawing::Size(1047, 24);
			this->menuStrip1->TabIndex = 19;
			this->menuStrip1->Text = L"menuStrip1";
			this->menuStrip1->ItemClicked += gcnew System::Windows::Forms::ToolStripItemClickedEventHandler(this, &VentanaPlay::menuStrip1_ItemClicked);
			// 
			// archivoToolStripMenuItem
			// 
			this->archivoToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->saveToolStripMenuItem });
			this->archivoToolStripMenuItem->Name = L"archivoToolStripMenuItem";
			this->archivoToolStripMenuItem->Size = System::Drawing::Size(37, 20);
			this->archivoToolStripMenuItem->Text = L"File";
			this->archivoToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::archivoToolStripMenuItem_Click);
			// 
			// saveToolStripMenuItem
			// 
			this->saveToolStripMenuItem->Name = L"saveToolStripMenuItem";
			this->saveToolStripMenuItem->Size = System::Drawing::Size(98, 22);
			this->saveToolStripMenuItem->Text = L"Save";
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
			// label1
			// 
			this->label1->AutoSize = true;
			this->label1->BackColor = System::Drawing::Color::OrangeRed;
			this->label1->BorderStyle = System::Windows::Forms::BorderStyle::FixedSingle;
			this->label1->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 48, System::Drawing::FontStyle::Regular, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->label1->ForeColor = System::Drawing::Color::Yellow;
			this->label1->Location = System::Drawing::Point(301, 51);
			this->label1->Name = L"label1";
			this->label1->Size = System::Drawing::Size(369, 75);
			this->label1->TabIndex = 20;
			this->label1->Text = L"MasterMind";
			this->label1->Click += gcnew System::EventHandler(this, &VentanaPlay::label1_Click);
			// 
			// Time
			// 
			this->Time->AutoSize = true;
			this->Time->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->Time->Font = (gcnew System::Drawing::Font(L"Microsoft Sans Serif", 26.25F, System::Drawing::FontStyle::Bold, System::Drawing::GraphicsUnit::Point,
				static_cast<System::Byte>(0)));
			this->Time->Location = System::Drawing::Point(40, 540);
			this->Time->Name = L"Time";
			this->Time->Size = System::Drawing::Size(159, 39);
			this->Time->TabIndex = 21;
			this->Time->Text = L"00:00:00";
			this->Time->Click += gcnew System::EventHandler(this, &VentanaPlay::label2_Click);
			// 
			// VentanaPlay
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Sienna;
			this->ClientSize = System::Drawing::Size(1047, 622);
			this->Controls->Add(this->Time);
			this->Controls->Add(this->label1);
			this->Controls->Add(this->button11);
			this->Controls->Add(this->button10);
			this->Controls->Add(this->button9);
			this->Controls->Add(this->button8);
			this->Controls->Add(this->button6);
			this->Controls->Add(this->button5);
			this->Controls->Add(this->button4);
			this->Controls->Add(this->button3);
			this->Controls->Add(this->button2);
			this->Controls->Add(this->button1);
			this->Controls->Add(this->menuStrip1);
			this->FormBorderStyle = System::Windows::Forms::FormBorderStyle::FixedDialog;
			this->MainMenuStrip = this->menuStrip1;
			this->Name = L"VentanaPlay";
			this->Text = L"{";
			this->Load += gcnew System::EventHandler(this, &VentanaPlay::MyForm_Load);
			this->menuStrip1->ResumeLayout(false);
			this->menuStrip1->PerformLayout();
			this->ResumeLayout(false);
			this->PerformLayout();

		}
#pragma endregion
	private: System::Void MyForm_Load(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void button1_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void button3_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void textBox1_TextChanged(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void timer1_Tick(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void richTextBox1_TextChanged(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void button1_Click_1(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void button5_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void radioButton1_CheckedChanged(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void button12_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void menuStrip1_ItemClicked(System::Object^ sender, System::Windows::Forms::ToolStripItemClickedEventArgs^ e) {
	}
	private: System::Void groupBox1_Enter(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void radioButton1_CheckedChanged_1(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void repeticionToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void salirToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
		VentanaPlay::Close();
	}
	private: System::Void button7_Click(System::Object^ sender, System::EventArgs^ e) {
	}
	private: System::Void label1_Click(System::Object^ sender, System::EventArgs^ e) {
	}
private: System::Void archivoToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void button8_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void label2_Click(System::Object^ sender, System::EventArgs^ e) {
}
private: System::Void TimeKeeper_Tick(System::Object^ sender, System::EventArgs^ e) { 

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
};
}
