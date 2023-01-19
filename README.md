<p align="center">
    <img src="https://www.freepnglogos.com/uploads/server-png/server-icon-download-icons-17.png" alt="Logo" width="80" height="80">
</p>

# <h1 align="center">Gestor de bloqueios a recursos para leituras e
escritas</h3>
<h4 align="center">Projeto para a cadeira de Aplicações Distribuídas (Parte1) (2021/2022)</h5>

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

* **pgrepwc** - pesquisa até um máximo de três palavras em um ou mais ficheiros, devolvendo as linhas de texto que contêm unicamente uma das palavras (isoladamente) ou todas as palavras. Também, conta o número de ocorrências encontradas de cada palavra e o número de linhas devolvidas de cada palavra ou de todas as palavras. A pesquisa e contagem são realizadas em paralelo, em vários ficheiros. 

* **-a**: opção que define se o resultado da pesquisa são as linhas de texto que contêm unicamente uma das palavras ou
todas as palavras. Por omissão (ou seja, se a opção não for usada), somente as linhas contendo unicamente uma das
palavras serão devolvidas.

* **-c**: opção que permite obter o número de ocorrências encontradas das palavras a pesquisar.

* **-l**: opção que permite obter o número de linhas devolvidas da pesquisa. Caso a opção -a não esteja ativa, o número
de linhas devolvido é por palavra.

* **-p n**: opção que permite definir o nível de paralelização n do comando (ou seja, o número de processos
(filhos)/threads que são utilizados para efetuar as pesquisas e contagens). Por omissão, deve ser utilizado apenas
um processo (o processo pai) para realizar as pesquisas e contagens.

* **palavras**: as palavras a pesquisar no conteúdo dos ficheiros. O número máximo de palavras a pesquisar é de 3.  

* **-f** ficheiros: podem ser dados um ou mais ficheiros, sobre os quais é efetuada a pesquisa e contagem. Caso
não sejam dados ficheiros na linha de comandos (ou seja, caso não seja passada a opção -f), estes devem ser lidos
de stdin (o comando no início da sua execução pedirá ao utilizador quem são os ficheiros a processar).

Inicialmente, após a validação das opções do comando, o processo pai cria os processos filhos/threads
definidos pelo nível de paralelização do comando (valor n). Estes processos/threads pesquisam as palavras nos
ficheiros, contam as ocorrências das palavras e o número de linhas onde estas foram encontradas nos ficheiros e
escrevem os resultados (linhas encontradas e contagens) para stdout. Os resultados das pesquisas e contagens são
escritos para stdout de forma não intercalada, ou seja, os resultados de cada processo/thread são apresentados
sequencialmente, sem serem intercalados com os resultados dos outros processos/threads. <br>

Os processos/threads realizam as pesquisas e as contagens nos ficheiros atribuídos pelo processo pai. Um dado
ficheiro é atribuído a um só processo/thread, não havendo assim divisão do conteúdo de um ficheiro por vários
processos/threads. Neste sentido, se o valor de n for superior ao número de ficheiros, o comando (o processo pai)
redefine-o automaticamente para o número de ficheiros. <br>

No final, o processo pai escreve para stdout o número total de ocorrências das palavras ou de linhas
encontradas, de acordo com a opção especificada de contagem (c ou l).

#### **For process: run it on terminal** 
```bash
python3 pgrepwc.py [-a] [-c|-l] [-p n] {palavras} [-f ficheiros]
```

#### **For threads: run it on terminal** 
```bash
python3 pgrepwc_threads.py [-a] [-c|-l] [-p n] {palavras} [-f ficheiros]
```


