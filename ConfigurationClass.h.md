# Master-Mind

//ConfigurationClass.h

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

public:
	ConfigurationClass();
	~ConfigurationClass();
	
	void setDifficulty(int);
	void setClock(bool);
	void setTimekeeperPlay(bool);
	void setTimekeeperGame(bool);
	void setElementRep(bool);
	void setElementType(int);

	int getDifficulty();
	bool getClock();
	bool getTimekeeperPlay();
	bool getTimekeeperGame();
	bool getElementRep();
	int getElementType();

};
