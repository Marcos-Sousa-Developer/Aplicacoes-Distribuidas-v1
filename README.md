<p align="center">
    <img src="https://www.freepnglogos.com/uploads/server-png/server-icon-download-icons-17.png" alt="Logo" width="80" height="80">
</p>

# <h1 align="center">Gestor de bloqueios a recursos para leituras e escritas</h1>
<h4 align="center">Projeto para a cadeira de Aplicações Distribuídas (Parte1) (2021/2022)</h4>

<hr>

# Objetivo
O objetivo geral do projeto será concretizar um gestor de bloqueios a recursos para leituras e escritas (Read-Write Locks). O seu propósito é controlar o acesso a um conjunto de recursos partilhados num sistema distribuído, onde diferentes clientes podem requerer o acesso aos
mesmos de forma concorrente. <br>
Um recurso pode ser bloqueado para a escrita exclusivamente por um só cliente de cada vez, até um máximo de K bloqueios de escrita ao longo do tempo.
Ou seja, findo os K bloqueios de escrita permitidos, o recurso fica desabilitado (i.e., indisponível para novos bloqueios). Um recurso pode ser bloqueado para a leitura por um número qualquer de clientes, caso o recurso não esteja bloqueado para a escrita ou desabilitado.
Basicamente, o gestor previne conflitos entre escritas de clientes diferentes, assim como previne conflitos entre operações de leitura e escrita enquanto o recurso está ativo. O gestor será concretizado num servidor escrito na linguagem Python 3. A Figura 1 ilustra a arquitetura
a seguir no servidor de bloqueios (lock_server), bem como a estrutura de dados em Python que o suporta.

<hr>

# Instruções  

## Operação anos
Mostra dois gráficos sobrepostos na mesma figura, com um eixo das abcissas comum, e dois eixos distintos para as ordenadas, um à esquerda (como habitualmente), e outro à direita. 

* Gráfico de barras onde as abcissas são os anos (2009, . . . , 2021) e as ordenadas são o número de jogos (representado á esquerda). 
* Curva em que as abcissas são as mesmas do gráfico anterior, isto é, o valor dos anos, e as ordenadas são o número de jogadoras (representado á direita). 

#### **Run it on terminal** 
```bash
python3 projeto.py xadrez.csv anos


