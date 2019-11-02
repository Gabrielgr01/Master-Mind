# Master-Mind

//ConfigurationClass.h

#pragma once
#include "pch.h"

class ConfigurationClass
{
private:
	int Difficulty_conf;

	bool Clock_conf;
	bool TimekeeperPlay_conf;
	bool TimekeeperGame_conf;

	bool ElementRep_conf;

	//agregar variables para la configuracion de  Element Type Used In Combination (GameSettings)
	//...

public:
	ConfigurationClass();
	~ConfigurationClass();
	
	void setDifficulty(int);
	void setClock(bool);
	void setTimekeeperPlay(bool);
	void setTimekeeperGame(bool);
	void setElementRep(bool);

	int getDifficulty();
	bool getClock();
	bool getTimekeeperPlay();
	bool getTimekeeperGame();
	bool getElementRep();

};
