//ConfigurationClass.h
//Fully documented
#pragma once
#include "pch.h"

class ConfigurationClass
{
private:

	//Difficulty
	int Difficulty_conf;

	//Clock
	bool Clock_conf;
	bool TimekeeperPlay_conf;
	bool TimekeeperGame_conf;

	//Element repetition
	bool ElementRep_conf;

	//Circle style
	int ElementType_conf;

	//random numbers
	int randomNUM;

	int random_num1;
	int random_num2;
	int random_num3;
	int random_num4;

public:
	ConfigurationClass();
	~ConfigurationClass();
	
	void setDifficulty(int);
	void setClock(bool);
	void setTimekeeperPlay(bool);
	void setTimekeeperGame(bool);
	void setElementRep(bool);
	void setElementType(int);

	void setRandomNUM();
	void setRandomNum1();
	void setRandomNum2();
	void setRandomNum3();
	void setRandomNum4();



	int getDifficulty();
	bool getClock();
	bool getTimekeeperPlay();
	bool getTimekeeperGame();
	bool getElementRep();
	int getElementType();

	int getRandomNUM();
	int getRandomNum1();
	int getRandomNum2();
	int getRandomNum3();
	int getRandomNum4();

};
