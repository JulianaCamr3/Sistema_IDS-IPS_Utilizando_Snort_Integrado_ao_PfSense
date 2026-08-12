# Sistema_IDS-IPS_Utilizando_Snort_Integrado_ao_PfSense


# 🛡️ Implementação e Avaliação de um Sistema IDS/IPS Baseado em Snort e pfSense para Redes Corporativas

> Projeto desenvolvido como Trabalho de Conclusão de Curso (TCC) do Bacharelado em Ciência da Computação da Universidade Federal do Maranhão (UFMA).

Este projeto apresenta a implementação de um ambiente de segurança de redes utilizando **pfSense** e **Snort** para detectar e prevenir ataques direcionados a serviços de rede e aplicações web.

O ambiente foi construído em um laboratório virtual composto por um firewall pfSense, uma máquina vulnerável Metasploitable2 e uma máquina física atacante Ubuntu. Foram simulados diferentes cenários de ataque para validar a capacidade do sistema em detectar e bloquear atividades maliciosas, incluindo varreduras de rede, identificação de serviços, detecção de sistema operacional, ataques de Path Traversal e Cross-Site Scripting (XSS).

Além da implementação do ambiente, o projeto apresenta a configuração das regras do Snort, a análise dos alertas gerados e uma avaliação da eficiência do sistema como solução IDS/IPS para redes corporativas.

# 📖 Visão Geral

## 🎯 Motivação

O desenvolvimento deste projeto foi motivado pelo crescimento expressivo dos ataques cibernéticos direcionados às organizações, especialmente às pequenas e médias empresas, que muitas vezes possuem recursos financeiros e equipes reduzidas para investir em soluções robustas de segurança da informação.

Nesse contexto, a implementação de sistemas de detecção e prevenção de intrusões (**IDS/IPS**) representa uma alternativa eficiente para aumentar a visibilidade sobre o tráfego da rede, identificar atividades maliciosas e reduzir a superfície de ataque dos ambientes corporativos.

---

## 🖥️ Ambiente de Testes

Para validar a solução proposta, foi desenvolvido um ambiente de testes totalmente isolado utilizando o **Oracle VirtualBox**.

O laboratório é composto por três máquinas, cada uma desempenhando uma função específica:

- 🛡️ **pfSense + Snort:** responsável pelo roteamento do tráfego da rede, aplicação das políticas de firewall e execução do Snort como sistema IDS/IPS.
- 🎯 **Metasploitable2:** máquina vulnerável utilizada como alvo dos ataques simulados.
- 💻 **Ubuntu (máquina física):** utilizada como máquina atacante para executar testes controlados e validar a capacidade de detecção e bloqueio do ambiente.

O **pfSense** é um firewall e roteador *open source* baseado em **FreeBSD**, amplamente utilizado em ambientes corporativos devido à sua flexibilidade e ao suporte para diversos pacotes de segurança. Neste projeto, foi utilizado como plataforma principal para instalação e gerenciamento do **Snort**, integrado nativamente por meio do gerenciador de pacotes do próprio sistema.

Como alvo dos testes, foi utilizada a distribuição **Metasploitable2**, um sistema Linux propositalmente vulnerável e amplamente empregado em laboratórios de segurança e testes de intrusão.

---

## 🌐 Arquitetura da Rede

Para garantir que todo o tráfego fosse analisado pelo sistema de detecção de intrusões, a máquina **Metasploitable2** foi configurada para utilizar o **pfSense** como gateway padrão. Dessa forma, a máquina vulnerável não era exposta diretamente à Internet, fazendo com que toda comunicação entre a máquina atacante e o servidor passasse obrigatoriamente pelo firewall, permitindo ao **Snort** inspecionar os pacotes e aplicar suas regras de detecção e prevenção.

A máquina virtual do **pfSense** foi configurada com duas interfaces de rede:

- **WAN (Bridge):** conectada à rede física por meio do modo **Bridge**, recebendo um endereço IP diretamente do roteador e simulando a conexão com a Internet.
- **LAN (Internal Network):** configurada como uma rede interna denominada **Rede_TCC**, utilizada para comunicação entre o **pfSense** e a máquina **Metasploitable2**.

Essa arquitetura permitiu reproduzir um cenário semelhante ao encontrado em redes corporativas, no qual o firewall atua como ponto central de inspeção e controle do tráfego entre redes externas e internas.

> **A figura abaixo apresenta a arquitetura de rede utilizada durante o desenvolvimento e a validação deste projeto.**


![Arquitetura da Rede](Arquitetura-TCC.drawio(2).png)

 
