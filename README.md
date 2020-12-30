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

********** Configurar Servidor Telnet **********

telnet server enable

*********************************************************************************************************

********** Configurando OLT DATACOM 4610 **********

Datacom Provisionamento onu

1 - Configuração vlan

2 - Configuração bandwidth profile

3 - Line profile

4 - Ativação Ramo Pon & onu


############### Script Configuração ################

1 - Etapa

***Criar vlan 

dot1q vlan 1000 name vlan-teste-pppoe interface gigabit-ethernet-1/1/10 tagged

***Criar service vlan

service vlan 1000 type n:1


****Criar profile de banda

profile gpon bandwidth-profile nomedoprofile

****Criar traffic no profile

Entrar no profile criado

traffic type-4 max-bw 1106944

############### Criação do profile ###############

profile gpon bandwidth-profile PPPoe-INTERNET
 
 traffic type-4 max-bw 1106944

profile gpon line-profile PPPoe-INTERNET
 
 upstream-fec
 
 tcont 1 bandwidth-profile PPPoe-INTERNET
 
 gem 1
  
  tcont 1 priority 0
  
  map PPPoe
   
   ethernet 1 vlan 1000 cos any
  

############### Criação do service vlan ###############
service vlan 1000
 
 type n:1


############### Configuração das ONU ###############

interface gpon 1/1/1
 
 no shutdown
 
 onu 0
  
  serial-number DD72E60C6F9F
  
  line-profile PPPoe-INTERNET
  
  ethernet 1
   
   negotiation
   
   no shutdown
   
   native vlan vlan-id 1000


############### Adicionando as informações ao service-port ###############

service-port 1 gpon 1/1/1 onu 0 gem 1 match vlan vlan-id 1000 action vlan replace vlan-id 1000


*********************************************************************************************************


############### Verificando o status da porta lan da ONU ###############

show interface gpon 1/1/1 onu 1 ethernet 1 brief

############### Verificando quais vlans estão na interface ###############

show dot1q vlan interface ten-gigabit-ethernet-1/1/4











