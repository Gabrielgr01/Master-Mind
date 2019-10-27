# Master-Mind

//VentanaPlay.h

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
	private: System::Windows::Forms::Timer^ timer1;
	private: System::Windows::Forms::RichTextBox^ richTextBox1;





	private: System::Windows::Forms::Button^ button8;
	private: System::Windows::Forms::Button^ button9;
	private: System::Windows::Forms::Button^ button10;
	private: System::Windows::Forms::Button^ button11;
	private: System::Windows::Forms::Button^ button12;
	private: System::Windows::Forms::MenuStrip^ menuStrip1;
	private: System::Windows::Forms::ToolStripMenuItem^ configuracionToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ repeticionToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ nivelToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ relojToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ panelToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ ayudaToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ instruccionesToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ salirToolStripMenuItem;
	private: System::Windows::Forms::ToolStripMenuItem^ archivoToolStripMenuItem;
	private: System::Windows::Forms::GroupBox^ RepeticionGB;

	private: System::Windows::Forms::RadioButton^ radioButton1;
	private: System::Windows::Forms::RadioButton^ radioButton2;
	private: System::Windows::Forms::Button^ button7;
	private: System::Windows::Forms::ToolStripMenuItem^ highscoresToolStripMenuItem;


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
			this->timer1 = (gcnew System::Windows::Forms::Timer(this->components));
			this->richTextBox1 = (gcnew System::Windows::Forms::RichTextBox());
			this->button8 = (gcnew System::Windows::Forms::Button());
			this->button9 = (gcnew System::Windows::Forms::Button());
			this->button10 = (gcnew System::Windows::Forms::Button());
			this->button11 = (gcnew System::Windows::Forms::Button());
			this->button12 = (gcnew System::Windows::Forms::Button());
			this->menuStrip1 = (gcnew System::Windows::Forms::MenuStrip());
			this->archivoToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->highscoresToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->configuracionToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->repeticionToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->nivelToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->relojToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->panelToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->ayudaToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->instruccionesToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->salirToolStripMenuItem = (gcnew System::Windows::Forms::ToolStripMenuItem());
			this->RepeticionGB = (gcnew System::Windows::Forms::GroupBox());
			this->button7 = (gcnew System::Windows::Forms::Button());
			this->radioButton2 = (gcnew System::Windows::Forms::RadioButton());
			this->radioButton1 = (gcnew System::Windows::Forms::RadioButton());
			this->menuStrip1->SuspendLayout();
			this->RepeticionGB->SuspendLayout();
			this->SuspendLayout();
			// 
			// button1
			// 
			this->button1->BackColor = System::Drawing::Color::Red;
			this->button1->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button1->ImageAlign = System::Drawing::ContentAlignment::BottomLeft;
			this->button1->Location = System::Drawing::Point(924, 12);
			this->button1->Name = L"button1";
			this->button1->Size = System::Drawing::Size(69, 60);
			this->button1->TabIndex = 0;
			this->button1->Text = L"Rojo";
			this->button1->UseVisualStyleBackColor = false;
			this->button1->Click += gcnew System::EventHandler(this, &VentanaPlay::button1_Click_1);
			// 
			// button2
			// 
			this->button2->BackColor = System::Drawing::Color::Blue;
			this->button2->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button2->Location = System::Drawing::Point(924, 78);
			this->button2->Name = L"button2";
			this->button2->Size = System::Drawing::Size(69, 65);
			this->button2->TabIndex = 1;
			this->button2->Text = L"Azul";
			this->button2->UseVisualStyleBackColor = false;
			// 
			// button3
			// 
			this->button3->BackColor = System::Drawing::Color::Green;
			this->button3->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button3->Location = System::Drawing::Point(924, 149);
			this->button3->Name = L"button3";
			this->button3->Size = System::Drawing::Size(69, 63);
			this->button3->TabIndex = 2;
			this->button3->Text = L"Verde";
			this->button3->UseVisualStyleBackColor = false;
			this->button3->Click += gcnew System::EventHandler(this, &VentanaPlay::button3_Click);
			// 
			// button4
			// 
			this->button4->BackColor = System::Drawing::Color::Yellow;
			this->button4->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button4->Location = System::Drawing::Point(924, 218);
			this->button4->Name = L"button4";
			this->button4->Size = System::Drawing::Size(69, 63);
			this->button4->TabIndex = 3;
			this->button4->Text = L"Amarillo";
			this->button4->UseVisualStyleBackColor = false;
			// 
			// button5
			// 
			this->button5->BackColor = System::Drawing::Color::FromArgb(static_cast<System::Int32>(static_cast<System::Byte>(255)), static_cast<System::Int32>(static_cast<System::Byte>(128)),
				static_cast<System::Int32>(static_cast<System::Byte>(255)));
			this->button5->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button5->Location = System::Drawing::Point(924, 287);
			this->button5->Name = L"button5";
			this->button5->Size = System::Drawing::Size(69, 63);
			this->button5->TabIndex = 4;
			this->button5->Text = L"Rosado";
			this->button5->UseVisualStyleBackColor = false;
			this->button5->Click += gcnew System::EventHandler(this, &VentanaPlay::button5_Click);
			// 
			// button6
			// 
			this->button6->BackColor = System::Drawing::Color::SaddleBrown;
			this->button6->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button6->Location = System::Drawing::Point(924, 356);
			this->button6->Name = L"button6";
			this->button6->Size = System::Drawing::Size(69, 63);
			this->button6->TabIndex = 5;
			this->button6->Text = L"Cafe";
			this->button6->UseVisualStyleBackColor = false;
			// 
			// richTextBox1
			// 
			this->richTextBox1->Location = System::Drawing::Point(12, 33);
			this->richTextBox1->Name = L"richTextBox1";
			this->richTextBox1->Size = System::Drawing::Size(326, 25);
			this->richTextBox1->TabIndex = 8;
			this->richTextBox1->Text = L"Indique su nombre: ";
			this->richTextBox1->TextChanged += gcnew System::EventHandler(this, &VentanaPlay::richTextBox1_TextChanged);
			// 
			// button8
			// 
			this->button8->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button8->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button8->Location = System::Drawing::Point(223, 356);
			this->button8->Name = L"button8";
			this->button8->Size = System::Drawing::Size(72, 63);
			this->button8->TabIndex = 14;
			this->button8->Text = L"Opcion 1";
			this->button8->UseVisualStyleBackColor = false;
			// 
			// button9
			// 
			this->button9->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button9->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button9->Location = System::Drawing::Point(301, 356);
			this->button9->Name = L"button9";
			this->button9->Size = System::Drawing::Size(72, 63);
			this->button9->TabIndex = 15;
			this->button9->Text = L"Opcion 2 ";
			this->button9->UseVisualStyleBackColor = false;
			// 
			// button10
			// 
			this->button10->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button10->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button10->Location = System::Drawing::Point(379, 356);
			this->button10->Name = L"button10";
			this->button10->Size = System::Drawing::Size(72, 63);
			this->button10->TabIndex = 16;
			this->button10->Text = L"Opcion 3";
			this->button10->UseVisualStyleBackColor = false;
			// 
			// button11
			// 
			this->button11->BackColor = System::Drawing::SystemColors::ActiveBorder;
			this->button11->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button11->Location = System::Drawing::Point(457, 356);
			this->button11->Name = L"button11";
			this->button11->Size = System::Drawing::Size(72, 63);
			this->button11->TabIndex = 17;
			this->button11->Text = L"Opcion 4";
			this->button11->UseVisualStyleBackColor = false;
			// 
			// button12
			// 
			this->button12->BackColor = System::Drawing::Color::OrangeRed;
			this->button12->FlatStyle = System::Windows::Forms::FlatStyle::Popup;
			this->button12->Location = System::Drawing::Point(429, 33);
			this->button12->Name = L"button12";
			this->button12->Size = System::Drawing::Size(355, 71);
			this->button12->TabIndex = 18;
			this->button12->Text = L"MASTERMIND";
			this->button12->UseVisualStyleBackColor = false;
			this->button12->Click += gcnew System::EventHandler(this, &VentanaPlay::button12_Click);
			// 
			// menuStrip1
			// 
			this->menuStrip1->Items->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(4) {
				this->archivoToolStripMenuItem,
					this->configuracionToolStripMenuItem, this->ayudaToolStripMenuItem, this->salirToolStripMenuItem
			});
			this->menuStrip1->Location = System::Drawing::Point(0, 0);
			this->menuStrip1->Name = L"menuStrip1";
			this->menuStrip1->Size = System::Drawing::Size(1047, 24);
			this->menuStrip1->TabIndex = 19;
			this->menuStrip1->Text = L"menuStrip1";
			this->menuStrip1->ItemClicked += gcnew System::Windows::Forms::ToolStripItemClickedEventHandler(this, &VentanaPlay::menuStrip1_ItemClicked);
			// 
			// archivoToolStripMenuItem
			// 
			this->archivoToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->highscoresToolStripMenuItem });
			this->archivoToolStripMenuItem->Name = L"archivoToolStripMenuItem";
			this->archivoToolStripMenuItem->Size = System::Drawing::Size(60, 20);
			this->archivoToolStripMenuItem->Text = L"Archivo";
			// 
			// highscoresToolStripMenuItem
			// 
			this->highscoresToolStripMenuItem->Name = L"highscoresToolStripMenuItem";
			this->highscoresToolStripMenuItem->Size = System::Drawing::Size(133, 22);
			this->highscoresToolStripMenuItem->Text = L"Highscores";
			// 
			// configuracionToolStripMenuItem
			// 
			this->configuracionToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(4) {
				this->repeticionToolStripMenuItem,
					this->nivelToolStripMenuItem, this->relojToolStripMenuItem, this->panelToolStripMenuItem
			});
			this->configuracionToolStripMenuItem->Name = L"configuracionToolStripMenuItem";
			this->configuracionToolStripMenuItem->Size = System::Drawing::Size(95, 20);
			this->configuracionToolStripMenuItem->Text = L"Configuracion";
			// 
			// repeticionToolStripMenuItem
			// 
			this->repeticionToolStripMenuItem->Name = L"repeticionToolStripMenuItem";
			this->repeticionToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->repeticionToolStripMenuItem->Text = L"Repeticion";
			this->repeticionToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::repeticionToolStripMenuItem_Click);
			// 
			// nivelToolStripMenuItem
			// 
			this->nivelToolStripMenuItem->Name = L"nivelToolStripMenuItem";
			this->nivelToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->nivelToolStripMenuItem->Text = L"Nivel";
			// 
			// relojToolStripMenuItem
			// 
			this->relojToolStripMenuItem->Name = L"relojToolStripMenuItem";
			this->relojToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->relojToolStripMenuItem->Text = L"Reloj";
			// 
			// panelToolStripMenuItem
			// 
			this->panelToolStripMenuItem->Name = L"panelToolStripMenuItem";
			this->panelToolStripMenuItem->Size = System::Drawing::Size(180, 22);
			this->panelToolStripMenuItem->Text = L" Panel de elementos";
			// 
			// ayudaToolStripMenuItem
			// 
			this->ayudaToolStripMenuItem->DropDownItems->AddRange(gcnew cli::array< System::Windows::Forms::ToolStripItem^  >(1) { this->instruccionesToolStripMenuItem });
			this->ayudaToolStripMenuItem->Name = L"ayudaToolStripMenuItem";
			this->ayudaToolStripMenuItem->Size = System::Drawing::Size(53, 20);
			this->ayudaToolStripMenuItem->Text = L"Ayuda";
			// 
			// instruccionesToolStripMenuItem
			// 
			this->instruccionesToolStripMenuItem->Name = L"instruccionesToolStripMenuItem";
			this->instruccionesToolStripMenuItem->Size = System::Drawing::Size(144, 22);
			this->instruccionesToolStripMenuItem->Text = L"Instrucciones";
			// 
			// salirToolStripMenuItem
			// 
			this->salirToolStripMenuItem->Name = L"salirToolStripMenuItem";
			this->salirToolStripMenuItem->Size = System::Drawing::Size(41, 20);
			this->salirToolStripMenuItem->Text = L"Salir";
			this->salirToolStripMenuItem->Click += gcnew System::EventHandler(this, &VentanaPlay::salirToolStripMenuItem_Click);
			// 
			// RepeticionGB
			// 
			this->RepeticionGB->BackColor = System::Drawing::Color::Silver;
			this->RepeticionGB->Controls->Add(this->button7);
			this->RepeticionGB->Controls->Add(this->radioButton2);
			this->RepeticionGB->Controls->Add(this->radioButton1);
			this->RepeticionGB->Location = System::Drawing::Point(223, 110);
			this->RepeticionGB->Name = L"RepeticionGB";
			this->RepeticionGB->Size = System::Drawing::Size(273, 123);
			this->RepeticionGB->TabIndex = 20;
			this->RepeticionGB->TabStop = false;
			this->RepeticionGB->Text = L"Repeticion";
			this->RepeticionGB->Visible = false;
			this->RepeticionGB->Enter += gcnew System::EventHandler(this, &VentanaPlay::groupBox1_Enter);
			// 
			// button7
			// 
			this->button7->Location = System::Drawing::Point(160, 88);
			this->button7->Name = L"button7";
			this->button7->Size = System::Drawing::Size(87, 20);
			this->button7->TabIndex = 2;
			this->button7->Text = L"Aceptar";
			this->button7->UseVisualStyleBackColor = true;
			this->button7->Click += gcnew System::EventHandler(this, &VentanaPlay::button7_Click);
			// 
			// radioButton2
			// 
			this->radioButton2->AutoSize = true;
			this->radioButton2->Location = System::Drawing::Point(16, 47);
			this->radioButton2->Name = L"radioButton2";
			this->radioButton2->Size = System::Drawing::Size(155, 17);
			this->radioButton2->TabIndex = 1;
			this->radioButton2->TabStop = true;
			this->radioButton2->Text = L"Sin repeticion de elementos";
			this->radioButton2->UseVisualStyleBackColor = true;
			// 
			// radioButton1
			// 
			this->radioButton1->AutoSize = true;
			this->radioButton1->Location = System::Drawing::Point(16, 20);
			this->radioButton1->Name = L"radioButton1";
			this->radioButton1->Size = System::Drawing::Size(159, 17);
			this->radioButton1->TabIndex = 0;
			this->radioButton1->TabStop = true;
			this->radioButton1->Text = L"Con repeticion de elementos";
			this->radioButton1->UseVisualStyleBackColor = true;
			this->radioButton1->CheckedChanged += gcnew System::EventHandler(this, &VentanaPlay::radioButton1_CheckedChanged_1);
			// 
			// VentanaPlay
			// 
			this->AutoScaleDimensions = System::Drawing::SizeF(6, 13);
			this->AutoScaleMode = System::Windows::Forms::AutoScaleMode::Font;
			this->BackColor = System::Drawing::Color::Sienna;
			this->ClientSize = System::Drawing::Size(1047, 622);
			this->Controls->Add(this->RepeticionGB);
			this->Controls->Add(this->button12);
			this->Controls->Add(this->button11);
			this->Controls->Add(this->button10);
			this->Controls->Add(this->button9);
			this->Controls->Add(this->button8);
			this->Controls->Add(this->richTextBox1);
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
			this->Text = L"MASTERMIND";
			this->Load += gcnew System::EventHandler(this, &VentanaPlay::MyForm_Load);
			this->menuStrip1->ResumeLayout(false);
			this->menuStrip1->PerformLayout();
			this->RepeticionGB->ResumeLayout(false);
			this->RepeticionGB->PerformLayout();
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
		RepeticionGB->Visible = true;
	}
	private: System::Void salirToolStripMenuItem_Click(System::Object^ sender, System::EventArgs^ e) {
		VentanaPlay::Close();
	}
	private: System::Void button7_Click(System::Object^ sender, System::EventArgs^ e) {
		RepeticionGB->Visible = false;
	}
	};
}
