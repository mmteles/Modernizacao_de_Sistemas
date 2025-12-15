# Modernizacao_de_Sistemas
Repositorio criado para submissao do projeto de Gerenciamento de AWS

## O projeto
Documentar os primeiros passos de um aplicativo de gestao de conteudo e conhecimento baseado em Inteligencia Artificial que, atraves de artefatos enviados pelo usuario, ira popular um banco de dados vetorial e salvar os artefatos por longo prazo.

## A solucao
1. Interface
   O usuario tera uma interface onde, uma das funcionalidades sera enviar artefatos para o seu perfil. Uma ver selecionada essa opcao, o aplicativo, web ou mobile, abrira a janela para envio de arquivos

2. Armazenamento
   O armazenamento temporario ocorrera em um bucket S3.

3. Processamento
   Uma vez salvo o arquivo, cujo nome seguirá padroes de identificacao e unicidade, uma funcao Lambda sera disparada, onde ocorrera a leitura e envio dos arquivos para o aplicativo principal, executando em um servidor EC2
   Esse aplicativo realizara a tokenizacao e armazenamento dos vetores em um banco de dados proprio, sobre o qual serao executadas funcoes de inteligencia artificial
   O aplicativo tambem guardara uma copia dos arquivos, em uma unidade EBS para que o usuario possa:
   * Restaurar algum artefato
   * Re-gerar a vetorizacao
   * Selecionar os artefatos utilizados na requisicao

## Diagrama
O diagrama simplificado da solucao e visto abaixo, ilustrando os recursos AWS e o fluxo das interacoes:
<img width="825" height="540" alt="image" src="https://github.com/user-attachments/assets/6c0413aa-9a3f-4656-a5d0-0aebe98c6492" />

## Recursos
Para a execucao da configuracao da infra estrutura, serao utilizados os aprendizados do curso AWS, a saber:
* Criacao de conta e estrutura de usuarios atraves do IAM, seguindo as praticas de seguranca ilustradas no slide abaixo:
<img width="1179" height="627" alt="image" src="https://github.com/user-attachments/assets/b2e708ba-438a-416e-82be-d64c04ea074c" />

* A Priori, a instancia EC2 sera de uso geral, A1/T2, para o desenvolvimento e sera redimencionada conforme o aumento do numero de usuarios.
<img width="892" height="525" alt="image" src="https://github.com/user-attachments/assets/7b6240a2-1da8-405a-b73a-87a5f39248b3" />

* Os volumes EBS serao configurados para otimizar o fluxo e o custo de recursos, obecedendo diretrizes de localizacao da informacao conforme o sistema e disponibilizado e utilizado.

* Devido ao uso de EBS para armazenamento de artefatos, o S3 sera utilizado apenas na fase de envio/tratamento dos mesmos, send utilizado apenas o S3 Padrao
<img width="795" height="354" alt="image" src="https://github.com/user-attachments/assets/9b5ee43f-fd17-4468-a8f9-60953ed012bd" />


