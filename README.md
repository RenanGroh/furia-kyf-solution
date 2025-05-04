# Challenge #2: Know Your Fan [HARD] - FURIA 🐾

## 🎯 Objetivo do Projeto

Este repositório contém a solução para o Challenge #2: Know Your Fan, apresentado pela comunidade FURIA. O objetivo é desenvolver uma solução (neste caso, um **Google Colab Notebook**) que demonstre um processo de coleta e análise do máximo de informações sobre um fã de e-sports, com foco especial na torcida da FURIA.

A ideia é simular como estratégias de "Know Your Fan" poderiam ser usadas para entender melhor o perfil do torcedor e, potencialmente, oferecer experiências e serviços mais personalizados.

## ✨ Solução Proposta: Notebook Colab

Foi escolhido utilizar um **Google Colab Notebook** como a solução devido a:

*   **Foco na Lógica:** Permite concentrar nos aspectos de coleta de dados (real ou simulada), processamento, chamadas a APIs externas (IA, e-sports data) e análise, sem a sobrecarga de desenvolver um frontend/backend completo.
*   **Simulação Facilitada:** Tornou mais simples e seguro demonstrar processos que envolvem dados sensíveis (PII, verificação de ID) e integrações complexas (OAuth), focando no *conceito* e não na implementação de infraestrutura robusta e segura que estaria fora do escopo do desafio.
*   **Demonstração Clara:** O formato sequencial de células do notebook permite apresentar cada etapa do processo de forma clara e comentada.
*   **Conformidade com o Desafio:** O próprio desafio sugere "app ou solução (ex: python notebook)".

## Implemented Etapas Implementadas (Demonstradas no Notebook)

O notebook `kyf-FURIA.ipynb`

1.  **Coleta de Dados Básicos:**
    *   Coleta interativa de interesses gerais (jogo favorito, jogador favorito, etc.).
    *   **Simulação** da coleta de Dados Pessoais Identificáveis (PII) como Nome, Localização, CPF, com ênfase na **não utilização de dados reais** por segurança e privacidade (LGPD).
2.  **Verificação de Identidade (Simulada com Demonstração Técnica):**
    *   Explicação da complexidade da verificação real.
    *   **Simulação** do resultado da verificação.
    *   **Demonstração** de uso de OCR (`pytesseract`) para ler texto de uma *imagem de documento de exemplo*.
    *   **Demonstração** do uso de IA (Google Gemini) para tentar extrair dados estruturados do texto lido pelo OCR.
    *   *Disclaimer:* **Não** valida a autenticidade real do documento.
3.  **Vinculação de Redes Sociais (Simulada/Limitada):**
    *   Explicação das dificuldades com OAuth e APIs restritas.
    *   Tentativa de **Web Scraping básico** de perfis públicos (com limitações).
    *   Coleta de **descrição/posts fornecidos pelo usuário**.
    *   Uso **real** de IA (Google Gemini) para analisar o texto fornecido e inferir relevância/palavras-chave sobre e-sports/FURIA.
    *   **Simulação** de dados que seriam obtidos via API (contas seguidas, etc.), informada pela análise IA.
4.  **Validação de Links de Perfis E-sports:**
    *   Coleta de URL (ex: Liquipedia).
    *   Implementação **real** de Web Scraping (`requests`, `BeautifulSoup`) para buscar conteúdo da página.
    *   Implementação **real** de validação com IA (Google Gemini) para analisar a relevância do conteúdo para um fã da FURIA/CS.
5.  **Sumário do Perfil do Fã:**
    *   Apresentação final de todas as informações coletadas (reais e simuladas) em um formato HTML organizado dentro do notebook.
    *   Geração de um objeto **JSON final** representando o perfil consolidado, pronto (em teoria) para ser enviado a um banco de dados.

## 🛠️ Tecnologias Utilizadas

*   **Linguagem:** Python 3
*   **Ambiente:** Google Colaboratory (Colab)
*   **Bibliotecas Python Principais:**
    *   `requests` (Requisições HTTP para Scraping e APIs)
    *   `beautifulsoup4` (Parseamento de HTML)
    *   `google-generativeai` (Interação com a API do Google Gemini)
    *   `python-dotenv` (Carregamento de variáveis de ambiente do arquivo `.env`)
    *   `pytesseract` & `Pillow` (OCR - Leitura de texto em imagem)
    *   `pandas` (Formatação do sumário final - opcional)
    *   `IPython.display` (Renderização de HTML no Colab)
*   **APIs Externas:**
    *   Google Gemini API (Análise de texto, estruturação de dados OCR)
    *   *PandaScore API (Se utilizada para complementar dados)*

## ⚙️ Como Executar o Notebook

1.  **Abra no Google Colab:**
    *   Clique no link do notebook neste repositório (se já comitado) ou faça o upload do arquivo `.ipynb` para o seu Google Drive e abra-o com o Colab.
    *   Alternativamente, vá em `Arquivo > Abrir notebook > GitHub`, cole a URL deste repositório e selecione o notebook.
2.  **Configure a API Key do Gemini:**
    *   **Método 1 (Recomendado - Secrets):** No painel esquerdo do Colab, clique no ícone de chave inglesa ("Secrets"), ative, e adicione um novo segredo com o nome `GEMINI_API_KEY` e cole sua chave como valor.
    *   **Método 2 (Upload `.env`):** Crie um arquivo `.env` na sua máquina local contendo a linha `GEMINI_API_KEY=SUA_CHAVE_AQUI`. Use o botão "Fazer upload" no painel de arquivos do Colab (ícone de pasta) para enviar este arquivo para a sessão *temporária*. **Não versione o `.env` com sua chave no Git!**
3.  **Instale as Dependências:** Execute a primeira célula de código que contém `!pip install ...`.
4.  **Execute as Células:** Execute cada célula sequencialmente, de cima para baixo, usando o botão "Play" (▶️) ou pressionando `Shift + Enter`.
5.  **Interaja:** O notebook solicitará informações via campos de `input()` em algumas etapas (URL de perfil, descrição social). Forneça as informações quando solicitado.
6.  **Observe a Saída:** Acompanhe os logs e os resultados exibidos abaixo de cada célula, especialmente o sumário final formatado.

## ⚠️ Simulações e Limitações IMPORTANTES

É crucial entender que, devido a limitações técnicas, de privacidade (LGPD) e segurança, várias partes desta solução são **SIMULADAS**:

*   **Coleta de PII:** Nome completo, CPF, endereço **NÃO SÃO** coletados realmente. Valores fictícios são usados apenas para estrutura.
*   **Verificação de ID REAL:** A análise de segurança do documento e a verificação facial **NÃO SÃO** implementadas. Apenas a leitura OCR e uma tentativa de estruturação por IA são demonstradas em uma imagem de exemplo.
*   **Vinculação OAuth:** O fluxo de autenticação real com redes sociais **NÃO É** implementado.
*   **Leitura de Dados Sociais:** A extração de listas de seguidores/seguidos, interações privadas ou atividades detalhadas das APIs sociais **NÃO É** feita. Os dados são **simulados**, embora informados pela análise IA do texto fornecido pelo usuário.
*   **Web Scraping:** Pode falhar em sites que exigem login (Instagram) ou que possuem proteções anti-scraping robustas (algumas partes do Twitter/X, HLTV).

O foco é demonstrar o *conceito* do "Know Your Fan" e as *tecnologias* que poderiam ser aplicadas (IA, OCR, Scraping), respeitando as barreiras do mundo real.

## 👤 Autor

*   **Renan Groh**
*   **Contato:** renangroh@gmail.com

---

Solução desenvolvida para o Challenge #2 da Comunidade FURIA.
