# Projeto Clipping de Notícias com IA

Este projeto demonstra a criação de um sistema automatizado para gerar e enviar clippings de notícias sobre tópicos de interesse utilizando Inteligência Artificial e integração com o serviço de e-mail.

## Visão Geral

O projeto consiste em um pipeline de agentes de IA que trabalham em conjunto para:

1.  **Buscar Notícias:** Um agente utiliza o Google Search para encontrar as notícias mais relevantes sobre um tópico especificado pelo usuário, buscando em diferentes idiomas (inglês, espanhol, português).
2.  **Processar e Formatar:** O agente consolida os resultados, resume as notícias principais, e formata o conteúdo em HTML, incluindo links clicáveis para as fontes originais.
3.  **Enviar por E-mail:** O conteúdo HTML gerado é então enviado como um e-mail para um destinatário especificado, utilizando a API do Gmail.

A automação e a inteligência do sistema residem na capacidade do agente de buscar, filtrar, resumir e formatar as notícias de forma autônoma, entregando um produto final pronto para consumo.

## Funcionalidades

*   Busca de notícias sobre tópicos múltiplos.
*   Consolidação e resumo de notícias relevantes.
*   Formatação do clipping em HTML com links clicáveis.
*   Envio automatizado do clipping por e-mail (requer autenticação com a API do Gmail).
*   Utiliza o Google Gemini para a inteligência dos agentes.
*   Utiliza o Google ADK (Agent Development Kit) para a orquestração dos agentes.

## Pré-requisitos

Para executar este código, você precisará de:

1.  **Acesso ao Google Gemini API:** Obtenha uma API Key e configure-a (instruções no código).
2.  **Credenciais da API do Gmail:**
    *   Ative a Gmail API na Google Cloud Console.
    *   Crie um OAuth 2.0 Client ID do tipo "Desktop app".
    *   Faça o download do arquivo `credentials.json`.
3.  **Ambiente Python:** Recomenda-se utilizar um ambiente como Google Colab ou um ambiente Python local com as bibliotecas listadas nos imports.
4.  **Bibliotecas Python:** As bibliotecas necessárias serão instaladas automaticamente no notebook (`google-genai`, `google-adk`, `google-auth-oauthlib`, `google-api-python-client`, etc.).

## Como Executar

1.  **Abra o Notebook:** Carregue o arquivo Jupyter Notebook (`.ipynb`) em um ambiente compatível (Google Colab é o recomendado devido à integração com `userdata` e `files.upload`).
2.  **Execute as Células:** Execute as células do notebook em sequência.
3.  **Configuração da API Key:** A célula que configura a API Key do Gemini buscará a chave de um segredo do Colab (`GOOGLE_API_KEY`). Certifique-se de ter este segredo configurado.
4.  **Autenticação do Gmail:** A célula de autenticação do Gmail guiará você pelo processo:
    *   Ele verificará se o arquivo `credentials.json` existe. Se não, solicitará que você faça o upload.
    *   Ele tentará usar um token de autenticação salvo (`token.json`) se existir e for válido.
    *   Se necessário, ele iniciará um novo fluxo de autenticação OAuth 2.0, gerando um link para autorização e pedindo que você cole o código de autorização de volta no notebook.
    *   O token válido será salvo em `token.json` para usos futuros.
5.  **Execução do Orquestrador:** A célula final atua como orquestrador:
    *   Pedirá que você insira o tópico para o clipping.
    *   Pedirá o e-mail do destinatário.
    *   Chama o agente buscador de notícias.
    *   Exibe o conteúdo do clipping gerado.
    *   Chama a função para enviar o e-mail.

## Estrutura do Código

O código é organizado em células de notebook que:

*   Instalam as bibliotecas necessárias.
*   Configuram as APIs (Gemini e Gmail).
*   Definem funções auxiliares (`call_agent`, `to_markdown`).
*   Definem os agentes de IA (`buscador_noticias`).
*   Definem funções de ferramentas (`send_email`).
*   Orquestram o fluxo principal do sistema.

## Personalização

*   Você pode modificar as instruções do agente `buscador_noticias` para alterar o formato da saída, os critérios de busca, ou a quantidade de notícias.
*   Você pode expandir o sistema adicionando novos agentes ou ferramentas (ex: um agente para resumir artigos longos, uma ferramenta para buscar notícias em outras fontes).
*   A validação de e-mail pode ser aprimorada.

## Contato

Se tiver dúvidas ou sugestões, envie e-mail gabrielschiavoni@gmail.com.

Github: https://github.com/gabriel-schiavoni/imersao-alura
