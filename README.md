# TutorIA Exatas

Assistente de estudos em português para apoiar a preparação para o ENEM em Matemática, Física e Química. Projeto de portfólio de **Bruno Dorneles**, com interface de conversa e integração de IA pelo Dify.

[Acessar demonstração](https://tutor-ia-ecru.vercel.app/) · [Perfil do desenvolvedor](https://github.com/dornelesbruno21)

> **Status:** protótipo de interface e integração. A página da demonstração foi conferida; a disponibilidade das respostas depende da configuração e dos limites do serviço de IA. Sem vínculo oficial com o ENEM ou o Inep.

## Objetivo

Facilitar a revisão de conteúdos de exatas por meio de perguntas em linguagem natural, mantendo a experiência simples e acessível pelo navegador.

## Recursos implementados

- Chat em português e sugestões de temas para iniciar o estudo.
- Histórico durante a sessão da página, com continuidade pelo identificador de conversa.
- Botão para iniciar uma nova conversa.
- Indicador de carregamento, bloqueio de envio simultâneo e mensagens de erro.
- Envio com Enter e quebra de linha com Shift+Enter.
- Layout adaptado para telas menores.
- Endpoint serverless que mantém a chave do Dify fora do navegador.

## Tecnologias e arquitetura

| Camada | Implementação |
| --- | --- |
| Interface | HTML5, CSS3 e JavaScript, sem framework |
| Comunicação | Fetch API e JSON |
| Backend | Função JavaScript em api/chat.js |
| Integração de IA | API de conversas do Dify |
| Publicação | Vercel |

Fluxo: navegador → POST /api/chat → Dify → resposta exibida no chat.

O frontend envia a pergunta e o identificador da conversa, quando existe. A função serverless autentica a solicitação usando uma variável de ambiente e devolve a resposta e o identificador para continuar a conversa.

## Estrutura

- **index.html:** interface, estilos e lógica do chat.
- **api/chat.js:** integração serverless com o Dify.
- **vercel.json:** configuração de publicação.
- **README.md:** documentação do projeto.

## Executar e publicar

### Visualizar a interface

Abra **index.html** no navegador para conferir o layout. Isso não executa o endpoint de IA. O GitHub Pages também serve somente arquivos estáticos: não executa api/chat.js.

### Usar a integração completa

1. Clone o projeto com o comando abaixo e entre na pasta TutorIA.
2. Configure um aplicativo de conversa no Dify e obtenha sua chave de API.
3. Importe o repositório na Vercel e configure **DIFY_API_KEY** nas variáveis de ambiente do projeto.
4. Publique novamente após configurar a variável e teste uma pergunta.

```bash
git clone https://github.com/dornelesbruno21/TutorIA.git
cd TutorIA
```

Para executar localmente com as funções serverless, utilize a CLI da Vercel:

```bash
npx vercel dev
```

Configure DIFY_API_KEY também no ambiente local. Nunca coloque a chave no HTML, em commits ou capturas de tela. Os provedores de IA e hospedagem podem ter limites de uso e custos.

## Limitações conhecidas e próximos passos

- Os botões de disciplinas alteram o destaque visual; a seleção ainda não é enviada ao backend.
- A interface menciona RAG, classificador e LLaMA/Groq, mas essas configurações não estão versionadas aqui. Devem ser conferidas no Dify antes de serem apresentadas como capacidades comprovadas.
- Não há autenticação, persistência própria de conversas ou limitação de requisições implementadas neste repositório.
- Antes de ampliar o uso público: proteger a renderização de conteúdo, melhorar validação e erros da API, separar os identificadores por usuário e implementar proteção contra abuso.
- Adicionar testes automatizados, melhorar acessibilidade e a navegação das disciplinas no celular.
- Atualizar o selo do ENEM, que ainda apresenta 2025.

As respostas da IA podem conter erros. Confira cálculos e conceitos em materiais confiáveis e não envie dados pessoais ou informações sensíveis ao chat.

## Sobre o projeto

Este repositório demonstra integração entre frontend, endpoint serverless e serviço de IA, além de estado de conversa e publicação web. Desenvolvido por [Bruno Dorneles](https://github.com/dornelesbruno21) como projeto de aprendizado e portfólio.
