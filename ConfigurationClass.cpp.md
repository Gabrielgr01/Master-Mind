# Master-Mind

//ConfigurationClass.cpp

#include "pch.h"
#include "ConfigurationClass.h"
#include <cstdlib>
#include <ctime>


ConfigurationClass::ConfigurationClass()
{
	Difficulty_conf = 1;
	Clock_conf = true;
	TimekeeperPlay_conf = false;
	TimekeeperGame_conf = false;
	ElementRep_conf = true;
	ElementType_conf = 1;

	srand(time(0));
};

ConfigurationClass::~ConfigurationClass() {};


void ConfigurationClass::setDifficulty(int dif)
{
	this->Difficulty_conf = dif;
};
void ConfigurationClass::setClock(bool clock)
{
	this->Clock_conf = clock;
};
void ConfigurationClass::setTimekeeperPlay(bool TimeKP)
{
	this->TimekeeperPlay_conf = TimeKP;
};
void ConfigurationClass::setTimekeeperGame(bool TimeKG)
{
	this->TimekeeperGame_conf = TimeKG;
};
void ConfigurationClass::setElementRep(bool elem)
{
	this->ElementRep_conf = elem;
};
void ConfigurationClass::setElementType(int elem_type)
{
	this->ElementType_conf = elem_type;
};

void ConfigurationClass::setRandomNum1()
{
	int num = rand() % 6 + 1;
	random_num1 = num;
};
void ConfigurationClass::setRandomNum2()
{
	int num = rand() % 6 + 1;
	random_num2 = num;
};
void ConfigurationClass::setRandomNum3()
{
	int num = rand() % 6 + 1;
	random_num3 = num;
};
void ConfigurationClass::setRandomNum4()
{
	int num = rand() % 6 + 1;
	random_num4 = num;
};
void ConfigurationClass::setRandomNUM()
{
	int num = rand() % 4 + 1;
	randomNUM = num;
};


int ConfigurationClass::getDifficulty()
{
	return Difficulty_conf;
};
bool ConfigurationClass::getClock()
{
	return Clock_conf;
};
bool ConfigurationClass::getTimekeeperPlay()
{
	return TimekeeperPlay_conf;
};
bool ConfigurationClass::getTimekeeperGame()
{
	return TimekeeperGame_conf;
};
bool ConfigurationClass::getElementRep()
{
	return ElementRep_conf;
};
int ConfigurationClass::getElementType()
{
	return ElementType_conf;
};

int ConfigurationClass::getRandomNum1()
{
	return random_num1;
};
int ConfigurationClass::getRandomNum2()
{
	return random_num2;
};
int ConfigurationClass::getRandomNum3()
{
	return random_num3;
};
int ConfigurationClass::getRandomNum4()
{
	return random_num4;
};
int ConfigurationClass::getRandomNUM()
{
	return randomNUM;
};

