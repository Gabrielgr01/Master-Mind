# Master-Mind

//ConfigurationClass.cpp

#include "pch.h"
#include "ConfigurationClass.h"

ConfigurationClass::ConfigurationClass()
{
	Difficulty_conf = 1;
	Clock_conf = true;
	TimekeeperPlay_conf = false;
	TimekeeperGame_conf = false;
	ElementRep_conf = true;
	ElementType_conf = 1;

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
