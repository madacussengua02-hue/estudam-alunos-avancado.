# ESTUDAM ALUNOS — aplicação com IA real

## Inclui
- OpenAI Responses API (GPT) e ferramenta `web_search`.
- Google Gemini API com ferramenta Google Search.
- Imagens e documentos PDF, DOCX, TXT, MD e CSV.
- Registo, login e histórico SQLite para estudantes.
- Visitantes podem conversar sem conta; conta guarda histórico.
- Chaves API apenas no servidor.

## Configuração local
1. Instala Node.js 20+.
2. Executa `npm install`.
3. Copia `.env.example` para `.env`.
4. Obtém chaves em https://platform.openai.com/api-keys e https://aistudio.google.com/apikey.
5. Preenche `OPENAI_API_KEY`, `GEMINI_API_KEY` e define um `JWT_SECRET` longo e aleatório.
6. Executa `npm start` e abre http://localhost:3000.

Podes testar com apenas uma chave, mas para alternar entre os dois fornecedores precisas das duas. As APIs têm custos separados; a subscrição ChatGPT não paga o uso da API.

## Publicação
O Pagelet pode alojar a interface estática, mas este projeto precisa de Node.js no servidor para guardar as chaves, autenticar e contactar as APIs. Publica a pasta inteira num serviço Node (por exemplo Render, Railway ou VPS). Build: `npm install`; Start: `npm start`. Define as variáveis de ambiente e configura disco persistente para a pasta `data/` (SQLite).

## Antes de abrir ao público
É uma base funcional para desenvolvimento, não uma auditoria de segurança. Adiciona verificação e recuperação de email, limites de custo por utilizador, monitorização, política de privacidade, moderação, backups e proteção contra abuso. Para escalar, migra SQLite para PostgreSQL e usa armazenamento privado para ficheiros.

Uploads: até 4 ficheiros por mensagem, 15 MB cada. PDFs/DOCX são extraídos como texto no servidor; imagens seguem para o modelo como entrada visual.
