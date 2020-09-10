# Script-Datacom

#################### SISTEMA OPERACIONAL DMOS ####################

#################### CRIAR USUÁRIO ####################

Logar no equipamento

********** Comando para logar em modo de configuração **********

conf

********** Comando para adicionar usuário **********

aaa user nomedousuário password suasenha

********** Comando para altera senha de usuário **********

aaa user nomedousuário change-password novasenha

********** Comando para deletar usuário **********

no aaa user nomedousuário 

#################### COMANDOS DE VERIFICAÇÃO ####################

********** Vizualizar community utilizada no Siwtch Datacom 4050 **********

show configuration running snmp

********** Verificar status das interfaces **********

show interface link gigabit-ethernet


