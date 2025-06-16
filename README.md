<h1 align="center">Sci-Graph 📊🔍</h1>
<p align="center">Projeto da disciplina SCC0130 – Engenharia de Software (2025.1)</p>

<p align="center">
  <a href="#estrutura-do-projeto">Estrutura do Projeto</a> • 
  <a href="#instalação-e-uso">Instalação&nbsp;e&nbsp;Uso</a> • 
  <a href="#objetivo">Objetivo</a> • 
  <a href="#metodologia-e-governança">Metodologia&nbsp;e&nbsp;Governança</a> • 
  <a href="#tecnologias">Tecnologias</a> • 
  <a href="#estrutura-de-branches">Estrutura&nbsp;de&nbsp;Branches</a> • 
  <a href="#testes">Testes</a> • 
  <a href="#cumprimento-dos-requisitos">Cumprimento&nbsp;dos&nbsp;Requisitos</a> • 
  <a href="#cronograma">Cronograma</a> • 
  <a href="#riscos">Gerenciamento de Riscos</a> •
  <a href="#contribuição">Contribuição</a> •
  <a href="#licença">Licença</a> •
  <a href="#agradecimentos">Agradecimentos</a>
</p>


<p align="center">
  <img src="assets/preview.png" width="70%" alt="Demonstração do Sci-Graph">
</p>


<p align="center">
  <b>Sci-Graph</b> é uma aplicação web que analisa redes de colaboração acadêmica usando a API pública do ORCID.  
  Focamos em visualização intuitiva, filtros avançados e desempenho otimizado (≤ 4 s para consultas típicas), seguindo SCRUM com sprints quinzenais.
</p>

---

## Links Importantes

- **Backlog & Sprints (Notion)**  
  <!-- substitua pelo link real de leitura → -->
  https://www.notion.so/P-gina-de-projeto-Sci-Graph-1fae657a23738016b1a3e08346491a32?source=copy_link

- **Plano do Projeto**  
  https://onedrive.live.com/:w:/g/personal/1A05459C73E3EC3E/EZ2d58ELecVPqg_nPd7aNOkBA0R0f22GX1un6DW9wOZkxw?resid=1A05459C73E3EC3E!sc1e79d9d790b4fc5aa0fe73ddeda34e9&ithint=file%2Cdocx&e=zyzPha&migratedtospo=true&redeem=aHR0cHM6Ly8xZHJ2Lm1zL3cvYy8xYTA1NDU5YzczZTNlYzNlL0VaMmQ1OEVMZWNWUHFnX25QZDdhTk9rQkEwUjBmMjJHWDF1bjZEVzl3T1preHc_ZT16eXpQaGE

- **Especificação de Requisitos (ERS)**  
  https://onedrive.live.com/personal/1a05459c73e3ec3e/_layouts/15/Doc.aspx?sourcedoc=%7B50692f6d-77c8-487c-a659-1442a23238ca%7D&action=default&redeem=aHR0cHM6Ly8xZHJ2Lm1zL3cvYy8xYTA1NDU5YzczZTNlYzNlL0VXMHZhVkRJZDN4SXBsa1VRcUl5T01vQms2LTFPbWhnOVBZMWFOaGVBVUxXS2c_ZT1id1plb0o&slrid=00000000-0000-0000-0000-000000000000&originalPath=aHR0cHM6Ly8xZHJ2Lm1zL3cvYy8xYTA1NDU5YzczZTNlYzNlL0VXMHZhVkRJZDN4SXBsa1VRcUl5T01vQms2LTFPbWhnOVBZMWFOaGVBVUxXS2c_cnRpbWU9MENtVENHbXMzVWc&CID=cb2c14d8-f73e-4667-948c-dc325e0cd85e&_SRM=0:G:72

- **Entrevistas com docentes**  
  https://docs.google.com/document/d/1coHijbWYTLFooeOFElBToIAFSiWMCZjH9Cu4AjwW9zE/edit?tab=t.0

---

## <div id="estrutura-do-projeto"></div>Estrutura do Projeto

```text
├── assets/              # Imagens, ícones e gifs de demo
├── docs/                # Plano, requisitos, atas, métricas de sprint
├── public/              # Arquivos estáticos servidos pelo Vite
├── src/
│   ├── components/      # React components
│   ├── pages/           # Páginas de rota
│   ├── hooks/           # Hooks reutilizáveis
│   └── services/        # Camada de acesso à API ORCID
├── .github/
│   └── workflows/       # CI (lint, build, tests)
├── README.md
├── package.json
└── vite.config.js
```

---

<!-- ==================== Objetivo ==================== -->
<div id="objetivo"></div>

## Objetivo

- **Resolver** limitações de usabilidade do ORCID original.  
- **Exibir** grafo interativo (≤ 300 nós) com filtros por período, área de pesquisa e grau de colaboração.  
- **Entregar** métricas de produtividade (citações, h-index, centralidade) em ≤ 4 s.  
- **Disponibilizar** testes, documentação e CI completos para fácil manutenção.

---

<!-- ==================== Metodologia e Governança ==================== -->
<div id="metodologia-e-governança"></div>

## Metodologia e Governança

| Artefato                     | Ferramenta / Local                  | Frequência              |
|------------------------------|-------------------------------------|-------------------------|
| **Backlog & board**          | Notion                              | Tempo real              |
| **Sprint planning & review** | Google Meet                         | Quinzenal               |
| **Daily / weekly sync**      | Notion checklist + Discord stand-up | Semanal                 |
| **Retrospectiva**            | Notion template + FunRetro          | Ao final de cada sprint |

> **Governança de qualidade:** ESLint + Prettier • Husky (pre-commit) • CI GitHub Actions.

---

<!-- ==================== Tecnologias ==================== -->
<div id="tecnologias"></div>

## Tecnologias

| Camada                | Stack                                                     |
|-----------------------|-----------------------------------------------------------|
| **Front-end**        | React 18 + Vite, Zustand (state), Tailwind CSS            |
| **Requests**         | Axios + retry/back-off                                    |
| **Visualização grafo**| Sigma.js + WebGL                                         |
| **Testes**           | Vitest (unit), Cypress (E2E), Lighthouse (performance)     |
| **Dev-Ops**          | GitHub Actions (CI) + Vercel (deploy preview)             |

---

<!-- ==================== Estrutura de Branches ==================== -->
<div id="estrutura-de-branches"></div>

## Estrutura de Branches

- **main** – release estável  
- **develop** – integração contínua da sprint corrente  
- **feature/&lt;nome-da-feature&gt;** – uma branch por _user story_  
- **hotfix/&lt;nome-do-hotfix&gt;** – correções emergenciais em produção  

---

<!-- ==================== Testes ==================== -->
<div id="testes"></div>

## Testes

| Nível            | Ferramenta        | Alvo                               |
|------------------|-------------------|------------------------------------|
| **Unitário**     | Vitest            | Hooks, reducers, utils             |
| **Componente**   | Testing Library   | Render e interação                 |
| **Funcional/E2E**| Cypress           | Fluxos UC-01 … UC-04               |
| **Desempenho**   | Lighthouse CI     | TTI ≤ 4 s, CLS < 0.1               |

*Casos de teste completos: `docs/test-cases.md` (10 CTs cobrindo RF-001 … RF-010).*

---

<!-- ==================== Cumprimento dos Requisitos ==================== -->
<div id="cumprimento-dos-requisitos"></div>

## Cumprimento dos Requisitos

| Categoria         | Requisito                 | Status | Evidência / Link              |
|-------------------|---------------------------|:------:|-------------------------------|
| **Documentação**  | Plano do projeto          | ✔      | `docs/Plano_Projeto.pdf`      |
|                   | Entrevistas & ERS         | ✔      | `docs/ERS_SciGraph.pdf`       |
|                   | Modelagem UML             | ✔      | `docs/modelagem/`             |
|                   | Casos de uso              | ✔      | `docs/casos_uso.pdf`          |
|                   | Casos de teste            | ✔      | `docs/test-cases.md`          |
| **Desenvolvimento** | Processo SCRUM         | ✔      | Notion board / velocity chart |
|                   | Organização de tarefas    | ✔      | Issues + GitHub Projects      |
| **Produto**       | Funcionalidades mínimas   | ✔      | Demo video / Vercel app       |
|                   | Código documentado        | ✔      | README + JSDoc                |
|                   | Usabilidade               | ↗      | Teste heurístico – sprint 4   |
|                   | Apresentação final        | 🕓     | 27 / 06 / 2025                |

### Detalhamento dos requisitos cumpridos

- **Plano do projeto**  
  - Arquivo `docs/Plano_Projeto.pdf` descreve escopo, cronograma Gantt, matriz de riscos e baseline de esforço (PERT).

- **Entrevistas & ERS**  
  - Pasta `docs/entrevistas/` contém transcrições e gravações das três entrevistas com docentes.  
  - Síntese e priorização (MoSCoW) reunidas no documento `docs/ERS_SciGraph.pdf`.

- **Modelagem UML**  
  - Diagramas de casos de uso, classes e sequência gerados no StarUML estão em `docs/modelagem/` (arquivos `.png` + `.mdj`).

- **Casos de uso**  
  - Fluxos principais e alternativos (UC-01 → UC-04) descritos em `docs/casos_uso.pdf`, com rastreabilidade direta aos requisitos funcionais.

- **Casos de teste**  
  - Conjunto de 10 CTs em `docs/test-cases.md`; automação Cypress em `cypress/e2e/`.  
  - Cobertura de linhas Vitest: **86 %**.

- **Processo SCRUM**  
  - Backlog, sprints e velocity chart mantidos no Notion (link na seção _Links_). Exportes em `docs/scrum/`.

- **Organização de tarefas**  
  - Issues rotuladas (_user-story_, _bug_, _tech-debt_) e ligadas a PRs no GitHub Projects Kanban.

- **Funcionalidades mínimas**  
  - Implementadas: **busca**, **filtros avançados**, **pop-up de metadados**, **explorar sub-rede** e **agrupamento por publicação**.  
  - Demo pública: <https://sci-graph.vercel.app>.

- **Código documentado**  
  - Comentários JSDoc em `src/`; Storybook gerado em `docs/storybook-static/`.

- **Usabilidade**  
  - Relatório das 10 heurísticas de Nielsen em `docs/usability-report.pdf`; correções de acessibilidade aplicadas na sprint 5.

- **Apresentação final**  
  - Slides (`docs/presentation/slides.pdf`) e vídeo demo (`docs/presentation/demo.mp4`).  
  - Sessão de apresentação marcada para **27 / 06 / 2025 às 15 h**.


---

<!-- ==================== Cronograma ==================== -->
<div id="cronograma"></div>

## Cronograma (sprints = 2 semanas)

| Sprint | Período          | Incremento chave                               |
|------: |------------------|-----------------------------------------------|
|   1    | 05 – 19 / 04     | Setup repo, boilerplate, ERS v1               |
|   2    | 20 / 04 – 03 / 05| Grafo MVP (busca + render)                    |
|   3    | 04 – 17 / 05     | Filtros avançados + testes unitários          |
|   4    | 18 – 31 / 05     | Pop-up de metadados + E2E                     |
|   5    | 01 – 14 / 06     | Refino UX + perf. + beta                      |
|   6    | 15 – 22 / 06     | Congelamento, demo e documentação             |

---

<!-- ==================== Riscos ==================== -->
<div id="riscos"></div>

## Gerenciamento de Riscos

| Risco                                         | Prob. | Impacto | Mitigação                          |
|-----------------------------------------------|:----:|:-------:|------------------------------------|
| Limite da API ORCID                           |  M   |   A     | Cache + fallback JSON dumps        |
| Desempenho WebGL em hardware fraco            |  M   |   M     | Degradar para canvas 2D            |
| Conflitos de merge                            |  M   |   M     | PR template + revisão em 2 pares   |
| Sobrecarga de tarefas (final de semestre)     |  H   |   M     | Buffer de 1 semana no cronograma   |

---

<!-- ==================== Instalação e Uso ==================== -->
<div id="instalação-e-uso"></div>

## Instalação e Uso

```bash
# 1 – clone o repositório
git clone https://github.com/EngSoft2025/orcid-project-grupo-um.git
cd orcid-project-grupo-um

# 2 – instale dependências
npm install

# 3 – inicie o servidor de desenvolvimento
npm run dev

#A aplicação abre em http://localhost:5173.
#Para build de produção:

npm run build && npm run preview
```
---
<!-- ==================== Contribuição ==================== -->
<div id="contribuição"></div>

## Contribuição

1. Abra uma **issue** descrevendo o que deseja mudar.  
2. Faça **fork** e crie sua branch `feature/&lt;sua-feature&gt;`.  
3. Garanta que `npm run test` **e** `npm run lint` passem.  
4. Envie o **pull request** respeitando o template.

---

<!-- ==================== Licença ==================== -->
<div id="licença"></div>

## Licença

Distribuído sob a licença **MIT** – consulte o arquivo [`LICENSE`](LICENSE) para detalhes.

---

<!-- ==================== Agradecimentos ==================== -->
<div id="agradecimentos"></div>

## Agradecimentos

- Prof. Dr. **Seiji Isotani** pela orientação na disciplina.  
- Comunidade **ORCID** & **Sigma.js** pelo código aberto que tornou o projeto possível.  
- Turma **SCC0130 (2025.1)** pelo feedback contínuo.

---

## Equipe

| Aluno                           | NUSP    | Email |
| --------------------------------|---------|-------|
| Vinicius G. Neves               | 14749363| [viniciusgustierrez@usp.br](mailto:viniciusgustierrez@usp.br) |
| Felipe V. de Oliveira           | 14570041| [felipe.volkweis@usp.br](mailto:felipe.volkweis@usp.br) |
| Luiz Felipe Catuzzi             | 11871198| [fellipecatuzzi@usp.br](mailto:fellipecatuzzi@usp.br) |


> **Como usar:**  
> 1. Cole este bloco em `README.md` na raiz do repositório.  
> 2. Substitua `assets/preview.png` por uma captura ou GIF real do **Sci-Graph**.  
> 3. Atualize links para OneDrive/Notion ou artefatos locais, se necessário.

