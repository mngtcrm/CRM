# Plano de Implantação — CRM Armazena Mais

Gerenciador de tarefas (estilo kanban) do plano de implantação do CRM da **Armazena Mais** (Grupo MNGT). Cobre as 15 fases do plano — de kickoff a go-live/hypercare — com tarefas atribuídas por responsável, prazo, prioridade e histórico de notas.

## Status atual

🔄 **Protótipo funcional.** Os dados são salvos localmente no navegador de cada pessoa (`localStorage`) — ainda **não há um banco de dados compartilhado** entre os responsáveis. A versão com Google Sheets como banco de dados e login real com Google está em desenvolvimento (ver Roadmap abaixo).

> Enquanto essa mensagem de aviso aparecer no topo da página ("Este link está aberto fora do Claude..."), significa que o board ainda está rodando no modo protótipo — cada pessoa que abrir o link vê e edita apenas a própria cópia local dos dados.

## Como usar

1. Abrir o arquivo `index.html` (local ou pelo link do GitHub Pages, uma vez publicado).
2. Escolher seu nome/perfil no seletor "Você é", no canto superior direito.
3. Criar, mover, editar ou excluir tarefas pelo quadro Kanban ou pela visão em Lista.
4. Clicar no título de qualquer tarefa para ver os detalhes completos e o histórico de notas.

## Funcionalidades

- Kanban com 3 colunas (A fazer / Em andamento / Concluído) + visão alternativa em Lista/tabela.
- Filtro por fase (barra lateral) e por responsável (chips).
- Prioridade por tarefa (Alta / Média / Baixa).
- Modais dedicados para **Nova tarefa**, **Iniciar**, **Concluir** e **Excluir** — cada um com os campos relevantes (data, observações, resultado/entregável, motivo).
- Tela de detalhes por tarefa, com histórico de notas (início, conclusão, comentários livres) e edição.
- Painel lateral com "Próximos prazos" e "Atividade recente" do time.
- Barra de progresso geral e por fase.
- Busca por título/descrição.

## Estrutura do repositório

```
index.html   → aplicação completa (HTML + CSS + JS em um único arquivo, sem dependências externas)
README.md    → este arquivo
```

## Publicando no GitHub Pages

1. Fazer upload do arquivo como `index.html` na raiz do repositório (ou manter o nome atual e apontar o GitHub Pages para ele).
2. No repositório: **Settings → Pages → Source**: branch `main`, pasta `/ (root)`. Salvar.
3. O GitHub gera a URL do site (formato `https://SEU-USUARIO.github.io/NOME-DO-REPOSITORIO/`).
4. Essa URL precisa ser cadastrada como "origem autorizada" no Google Cloud Console assim que o login com Google for implementado (próxima etapa).

## Roadmap — próxima versão (backend real)

- [ ] Planilha Google Sheets como banco de dados (abas Usuários / Tarefas / Atividade)
- [ ] Login com Google (Google Identity Services) com verificação do token no backend
- [ ] Controle de acesso por aprovação manual (conta criada fica pendente até liberação por um admin)
- [ ] `Code.gs` (Google Apps Script) com todas as validações de segurança
- [ ] Auditoria de segurança completa em cima do código real, antes de ir ao ar

### Pendências para destravar essa etapa

1. Confirmar o modelo de controle de acesso (aprovação manual, convite por link, ou outro).
2. Planilha nova ou reaproveitar uma existente.
3. URL final do GitHub Pages, para configurar o Client ID do Google.

## Segurança

O checklist completo de segurança (verificação de token, proteção da planilha, prevenção de injeção de fórmula no Sheets, requisitos de LGPD, sessão/logout, auditoria) está documentado separadamente. Uma nova auditoria será feita em cima do código real assim que o backend (`Code.gs` + planilha) estiver implementado — não considerar pronto para produção antes disso.

## Dados e privacidade

Esta ferramenta é para gestão **operacional** do projeto. Não inserir dados sensíveis de terceiros (leads, clientes) nas tarefas — apenas informações do próprio projeto de implantação.

## Responsáveis

Grupo MNGT — Marketing / CRM.
