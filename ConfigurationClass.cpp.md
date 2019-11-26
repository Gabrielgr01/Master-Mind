//ConfigurationClass.cpp
//Fully Documented
#include "pch.h"
#include "ConfigurationClass.h"
#include <cstdlib>
#include <ctime>


ConfigurationClass::ConfigurationClass()
{
	//Attributes of the configuration class
	Difficulty_conf = 1;
	Clock_conf = true;
	TimekeeperPlay_conf = false;
	TimekeeperGame_conf = false;
	ElementRep_conf = true;
	ElementType_conf = 1;

	srand(time(0));
};

ConfigurationClass::~ConfigurationClass() {};
//Methods of the configuration class

void ConfigurationClass::setDifficulty(int dif)
{
	//This sets the difficulty
	this->Difficulty_conf = dif;
};
void ConfigurationClass::setClock(bool clock)
{
	//This sets the timer to function as clock
	this->Clock_conf = clock;
};
void ConfigurationClass::setTimekeeperPlay(bool TimeKP)
{
	//This sets the  timer to function as a timekeeper for the plays
	this->TimekeeperPlay_conf = TimeKP;
};
void ConfigurationClass::setTimekeeperGame(bool TimeKG)
{
	//This sets the  timer to function as a timekeeper for the entire game
	this->TimekeeperGame_conf = TimeKG;
};
void ConfigurationClass::setElementRep(bool elem)
{
	//This sets the repetition of the elements
	this->ElementRep_conf = elem;
};
void ConfigurationClass::setElementType(int elem_type)
{
	//This sets the type of element to be shown
	this->ElementType_conf = elem_type;
};

void ConfigurationClass::setRandomNum1()
{
	//This sets the first element of the combination
	int num = rand() % 6 + 1;
	random_num1 = num;
};
void ConfigurationClass::setRandomNum2()
{
	//This sets the second element of the combination
	int num = rand() % 6 + 1;
	random_num2 = num;
};
void ConfigurationClass::setRandomNum3()
{
	//This sets the third element of the combination
	int num = rand() % 6 + 1;
	random_num3 = num;
};
void ConfigurationClass::setRandomNum4()
{
	//This sets the fourth element of the combination
	int num = rand() % 6 + 1;
	random_num4 = num;
};
void ConfigurationClass::setRandomNUM()
{
	//This sets the combination
	int num = rand() % 4 + 1;
	randomNUM = num;
};


int ConfigurationClass::getDifficulty()
{
	//This returns the value of the difficulty
	return Difficulty_conf;
};
bool ConfigurationClass::getClock()
{
	//This returns the value of the clock
	return Clock_conf;
};
bool ConfigurationClass::getTimekeeperPlay()
{
	//This returns the value of the Timekeeper for the plays
	return TimekeeperPlay_conf;
};
bool ConfigurationClass::getTimekeeperGame()
{
	//This returns the value of the timekeeper for the entire game
	return TimekeeperGame_conf;
};
bool ConfigurationClass::getElementRep()
{
	//This returns the value of the repetion of elements in the combination
	return ElementRep_conf;
};
int ConfigurationClass::getElementType()
{
	//This returns the value of the type of element to be used
	return ElementType_conf;
};

int ConfigurationClass::getRandomNum1()
{

	//This returns the first element of the combination
	return random_num1;
};
int ConfigurationClass::getRandomNum2()
{
	//This returns the second element of the combination
	return random_num2;
};
int ConfigurationClass::getRandomNum3()
{
	//This returns the third element of the combination
	return random_num3;
};
int ConfigurationClass::getRandomNum4()
{
	//This returns the fourth element of the combination
	return random_num4;
};
int ConfigurationClass::getRandomNUM()
{
	//This returns the combination
	return randomNUM;
};

