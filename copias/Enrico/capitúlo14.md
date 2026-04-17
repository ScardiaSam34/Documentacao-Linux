## Capitúlo 14
### Sobre
Neste Capitúlo veremos conceitos básicos de redes, como tipos de rede, problemas de endereçamento, configurações de rede com os comandos ifconfig, ip, ping, route e traceroute. Iremos utilizar navegadores gráficos e não gráficos como Lynx, w3m, Firefox e Epiphany

### Conceitos de IPv4 e IPv6
O IPv4 utiliza 32 bits para endereços; existem apenas 4,3 bilhões de endereços únicos disponíveis. Além disso, muitos endereços são alocados e reservados, mas não são efetivamente utilizados. O IPv4 é considerado inadequado para atender às necessidades futuras, pois o número de dispositivos disponíveis na rede global aumentou enormemente nos últimos anos.
O IPv6 utiliza 128 bits para endereços, o que permite 3,4 x 10³⁸ endereços únicos. Se você possui uma rede de computadores grande e deseja adicionar mais dispositivos, pode ser interessante migrar para o IPv6, pois ele oferece mais endereços únicos. No entanto, a migração para o IPv6 pode ser complexa, já que os dois protocolos nem sempre interoperam bem. Portanto, a migração de equipamentos e endereços para o IPv6 exige um esforço considerável e não tem sido tão rápida quanto o previsto inicialmente. Abordaremos o IPv4 com mais detalhes, pois é mais provável que você trabalhe com ele.

## Decodificação de endereços IPv4

A decodificação de um endereço IPv4 envolve entender sua estrutura de 32 bits, que é organizada em quatro octetos (grupos de 8 bits) separados por pontos, geralmente representados em formato decimal pontuado (ex: 192.168.1.1) para facilitar a leitura humana. 

Principais Aspectos da Estrutura e Decodificação IPv4:
- Estrutura de 32 bits: Um endereço IPv4 é um número de 32 bits, o que significa que ele pode representar 2^32(mais de 4 bilhões) de endereços únicos.
- Octetos e Decimal: Cada endereço é composto por quatro octetos (8 bits cada). Cada octeto é convertido de binário para um número decimal variando de 0 a 255.
- Conversão Binária: Computadores processam o endereço em binário (0s e 1s). Por exemplo, o endereço 192.168.1.1 é convertido em quatro octetos binários: 11000000.10101000.00000001.00000001.
- Máscaras de Sub-rede: Utilizadas para dividir uma rede grande em sub-redes menores, definindo qual parte do IP corresponde à rede e qual parte corresponde ao host. 

## Arquivos de configuração de rede

Para configurações da família Debian, os arquivos básicos de configuração de rede podem ser encontrados em  /etc/network/ , enquanto para sistemas da família Red Hat e SUSE é necessário inspecionar /etc/sysconfig/network .
As distribuições Ubuntu mais recentes incluem o netplan , que vem ativado por padrão e substitui o Network Manager. Como nenhuma outra distribuição demonstrou interesse e como ele pode ser facilmente desativado caso lhe incomode, vamos ignorá-lo.

## Interfaces de rede

As interfaces de rede são um canal de conexão entre um dispositivo e uma rede. Fisicamente, as interfaces de rede podem ser implementadas por meio de uma placa de interface de rede (NIC) ou, de forma mais abstrata, por software. É possível ter várias interfaces de rede operando simultaneamente. Interfaces específicas podem ser ativadas ou desativadas a qualquer momento.

O utilitário IP
Para visualizar o endereço IP:

$ /sbin/ip addr show

Para visualizar as informações de roteamento:

$ /sbin/ip route show

O comando `ip` é um programa muito poderoso que pode realizar diversas tarefas. Utilitários mais antigos (e mais específicos), como  `ifconfig` e `route`,  são frequentemente usados ​​para tarefas semelhantes.   Consultar as páginas de manual relevantes pode fornecer mais informações sobre esses utilitários.





