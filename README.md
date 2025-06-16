<h1 align="center">Sci-Graph 📊🔍</h1>
<p align="center">Projeto da disciplina SCC0130 – Engenharia de Software (2025.1)</p>

<p align="center">
  <a href="#links-importantes">Links&nbsp;Importantes</a> •
  <a href="#estrutura-do-projeto">Estrutura&nbsp;do&nbsp;Projeto</a> • 
  <a href="#instalação-e-uso">Instalação&nbsp;e&nbsp;Uso</a> • 
  <a href="#objetivo">Objetivo</a> • 
  <a href="#metodologia-e-governança">Metodologia&nbsp;e&nbsp;Governança</a> • 
  <a href="#tecnologias">Tecnologias</a> • 
  <a href="#cumprimento-dos-requisitos">Cumprimento&nbsp;dos&nbsp;Requisitos</a> • 
  <a href="#cronograma">Cronograma</a> • 
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

| Tipo de artefato                               | Descrição / Conteúdo                                   | Link |
|------------------------------------------------|--------------------------------------------------------|------|
| **Backlog & Sprints (Notion)**                 | Página inicial do projeto                              | <https://www.notion.so/P-gina-de-projeto-Sci-Graph-1fae657a23738016b1a3e08346491a32> |
|                                                | Página de controle / backlog e tarefas                 | <https://www.notion.so/1fae657a2373800b80f2f814c37862fb?v=1fae657a2373808097fb000cdc415533> |
| **Plano do Projeto**                           | Escopo, cronograma macro, matriz de riscos             | <https://onedrive.live.com/:w:/g/personal/1A05459C73E3EC3E/EZ2d58ELecVPqg_nPd7aNOkBA0R0f22GX1un6DW9wOZkxw> |
| **Especificação de Requisitos (ERS)**          | Documento completo (versão final) - Modelagem UML, casos de uso, casos de teste, requisitos funcionais e não funcionais.                    | <https://onedrive.live.com/personal/1a05459c73e3ec3e/_layouts/15/Doc.aspx?src=ERS> |
| **Entrevistas com docentes**                   | Transcrição Entrevista - 1                                   | <https://docs.google.com/document/d/1coHijbWYTLFooeOFElBToIAFSiWMCZjH9Cu4AjwW9zE/> |
|                                                | Transcrição Entrevistas - 2                                   | <https://docs.google.com/document/d/1fcnohqzOVHcL6FkHIV_qWi4f4LTkoDWDFn9dg8jpnWU/> |
| **Deploy (Vercel)**                     | Aplicação em produção                                  | <https://sci-graph.vercel.app> |
| **Vídeo de apresentação final**                | Gravação (8 min) - walkthrough do produto              | <https://youtu.be/XXXXXXXXXXX> |

---

## <div id="estrutura-do-projeto"></div>Estrutura do Projeto

```text
├── api-tests/           # scripts de prova-de-conceito e mocks de requisições ORCID
├── basic-api/           # protótipo inicial de consumo da API pública
├── public/              # arquivos estáticos copiados 1-a-1 no build (favicon, robots, etc.)
├── src/                 # código-fonte da aplicação React
│   └── …                # (components, pages, hooks, services…)
├── .gitignore           # exclusões de versionamento
├── API.md               # guia rápido: autenticação e endpoints ORCID usados
├── README.md            # este documento
├── bun.lockb            # lockfile gerado pelo Bun (opcional ao npm/yarn)
├── components.json      # mapeamento para Storybook / Vite Component Analyzer
├── eslint.config.js     # regras de lint + Prettier
├── index.html           # shell HTML servido em modo SPA
├── package.json         # metadados, scripts e dependências
├── package-lock.json    # lockfile npm
├── postcss.config.js    # plugins PostCSS (inclui Tailwind)
├── tailwind.config.ts   # tema e safelist do Tailwind CSS
├── tsconfig.json        # base TS compiler options
├── tsconfig.app.json    # TS options específicos da build web
├── tsconfig.node.json   # TS options para scripts Node/CLI
└── vite.config.ts       # configuração do bundler Vite
```

---
<!-- ==================== Objetivo ==================== -->
<div id="objetivo"></div>

## Objetivo

O **Sci-Graph** tem por missão **tornar visível e navegável a teia de colaborações científicas** hoje escondida em bases dispersas (ORCID, Semantic Scholar e afins). A seguir sintetizamos as metas do MVP (versão 1.0), alinhadas ao documento de requisitos e às discussões deste repositório:

1. **Unificar múltiplas fontes de dados**  
   - Consumir simultaneamente **ORCID (identidade + afiliação)** e **Semantic Scholar (publicações + coautorias)**, abstraindo diferenças de formato e latência.  
   - Implementar _fallback_ para cache local quando as APIs externas estiverem indisponíveis.

2. **Oferecer visualização orientada a descobertas**  
   - Renderizar um **grafo interativo de até 300 nós** com WebGL (Sigma.js) – número definido como compromisso entre legibilidade e desempenho nos testes de esforço.  
   - Disponibilizar filtros dinâmicos (período, área de pesquisa, instituição e grau de colaboração) que se apliquem em **≤ 3 s**.

3. **Detalhar métricas acadêmicas no contexto correto**  
   - Calcular em tempo real **citações, h-index, grau de centralidade e comunidades** do nó selecionado, exibindo resultados em painéis pop-up.  
   - Garantir **tempo-to-interactive ≤ 4 s** para consultas típicas (métrica validada pelo Lighthouse CI).

4. **Ser inclusivo e fácil de usar**  
   - Interface **responsiva** para desktop, notebook e tablets (≥ 768 px).  
   - Compatível com **Chrome e Firefox** nas versões estáveis atuais.  
   - Adoção de ícones, cores e mensagens de erro que não exijam conhecimento técnico avançado.

5. **Manter rastreabilidade e qualidade de engenharia**  
   - Todo requisito funcional possui **caso de uso + caso de teste + especificação Cypress** (vide `docs/test-cases.md`).  
   - Pipeline de CI roda lint, teste unitário, teste E2E, _build_ e _preview_ em cada _pull request_.

---

## Metodologia e Governança

Para o **Sci-Graph** adotamos um **Scrum “enxuto”** adaptado às restrições acadêmicas:

* **Sprints quinzenais (14 dias)** — foco em entregar incrementos testáveis; metas são negociadas no 1º dia e revisadas no 14º.  
* **Rituais semanais** — mesmo em ciclos de 2 semanas, fazemos uma *sync call* curta aos docmingos para alinhar impedimentos e dividir as tarefas da semana.  
* **Papéis claros** —  
  * **Product Owner (PO)**: *Vinicius G. Neves* — prioriza backlog, valida entregas.  
  * **Scrum Master / PM**: *Felipe V. de Oliveira* — remove bloqueios, cuida dos ritos e da qualidade do processo.  
  * **Developers**: *Vinicius G.*, *Felipe V.* e *Luiz F. Catuzzi* — todos codificam, criam testes e revisam PRs (modelo *cross-functional*).  
* **Relatórios de sprint** — ao final de cada ciclo publicamos **print quinzenal** no Notion: tarefas e reuniões feitas.  
* **Definição de Pronto (DoD)** — uma história só é encerrada após testes e aprovação do PO.

| Artefato / Prática           | Ferramenta / Local                              | Ritmo / SLA                               |
|------------------------------|-------------------------------------------------|-------------------------------------------|
| **Backlog & Board**          | Notion (Product Backlog + Kanban)               | Atualização em tempo real                 |
| **Sprint Planning**          | Google Meet (30 min) + checklist Notion         | 1º dia da sprint                          |
| **Relatório / Print da Sprint** | Página Notion “Sprint-N Retrospective”       | Até 24 h após o fim da sprint             |
| **Definition of Done (DoD)** | Testes verdes • cobertura ≥ 80 % • lint ok • story aceita pelo **PO** | Bloqueia merge se falhar                 |

---
<!-- ==================== Tecnologias ==================== -->
<div id="tecnologias"></div>

## Tecnologias

| Camada / Domínio        | Stack / Ferramentas                                                                  |
|-------------------------|--------------------------------------------------------------------------------------|
| **Front-end**           | React 18 • TypeScript • Vite                                                         |
| **UI & Estilo**         | Tailwind CSS • Headless UI                                                           |
| **APIs externas**       | **ORCID Public API v3** _(dados de autor)_ • **Semantic Scholar Graph API v1** _(publicações e coautorias)_ |
| **Dev-Ops**             | GitHub              |

---

<!-- ==================== Cumprimento dos Requisitos ==================== -->
<div id="cumprimento-dos-requisitos"></div>

<!-- ==================== Cumprimento dos Requisitos ==================== -->
<div id="cumprimento-dos-requisitos"></div>

## Cumprimento dos Requisitos

| Categoria             | Item Avaliado                        | Status | Evidência / Link                                                                                                    |
|-----------------------|--------------------------------------|:------:|----------------------------------------------------------------------------------------------------------------------|
| **Documentação**      | **Plano do Projeto**                 | ✔      | OneDrive: Plano v1 (`Plano do Projeto` na seção **Links Importantes**)                                               |
|                       | **Especificação de Requisitos (ERS)**| ✔      | OneDrive: ERS final (inclui UML, casos de uso & teste) na seção **Links Importantes**                                                               |
|                       | **Entrevistas com docentes**         | ✔      | Google Docs Entrevista 1 & 2 (links na seção **Links Importantes**)                                                  |
| **Desenvolvimento**   | **Processo SCRUM**                   | ✔      | Notion board na seção **Links Importantes**                                                                                   |
|                       | **Organização de tarefas**           | ✔      | Realizadas durante as reuniões semanais e pelo grupo de Whatsapp                                                                                   |
| **Produto**           | **Funcionalidades concluídas**          | ✔      | Todos os requisitos dispostos foram cumpridos, apesar de ter havido alteraçoes nos requisitos e ferramentas inicialmente planejadas                                                                       |
|                       | **Código documentado**               | ✔      | README + comentários em código                                                                                           |
|                       | **Usabilidade**                      | ↗      | Código modularizado e bem organizado                                                                                     |
|                       | **Apresentação final**               | 🕓     | Vídeo (8 min) + slides – link na seção **Links Importantes*                       |

---

### Detalhamento dos requisitos cumpridos

- **Plano do Projeto**  
  - Documento no OneDrive detalha escopo, cronograma e matriz de riscos; versãoada a cada sprint.

- **Especificação de Requisitos (ERS)**  
  - Arquivo único contém: requisitos funcionais & não-funcionais, **modelagem UML**, **casos de uso** e **casos de teste**; revisões 0.1 → 1.0 registradas.

- **Entrevistas com docentes**  
  - Duas transcrições Google Docs anexadas; insumos usados para criar e refinar backlog no inicio do projeto.

- **Processo SCRUM**  
  - Sprints quinzenais no Notion; cada encerramento gera impressão (“print quinzenal”) para registro de tarefas e mudanças/imprevistos.

- **Funcionalidades implementadas**  
  - Implementadas: busca, filtros, pop-up de metadados, exploração de sub-rede, agrupamento por publicação; todas acessíveis na versão final do sistema.

---

<!-- ==================== Cronograma ==================== -->
<div id="cronograma"></div>

## Cronograma (sprints quinzenais)

| Sprint | Período            | Objetivos principais                                                                                           | Entregáveis                                                                      |
|:-----: |--------------------|----------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
| **SP1**| 11 – 26 / 04       | • Análise de viabilidade das APIs<br>• Priorização completa do backlog<br>• Rascunho inicial da ERS            | ERS v0.1 • Backlog priorizado • Documento de planejamento                        |
| **SP2**| 27 / 04 – 10 / 05  | • Definição da arquitetura (cliente / servidor / cache)<br>• Protótipo navegável hospedado no **lovable.dev**  | Documento de Arquitetura • Protótipo navegável                                   |
| **SP3**| 11 – 25 / 05       | • Wrapper ORCID + Semantic Scholar com cache local<br>• Estrutura inicial de BD<br>• Renderização de grafo estático | **MVP 0** – backend operante + grafo simples                                     |
| **SP4**| 26 / 05 – 08 / 06  | • Implementar RF-001 → RF-005<br>• Telas de busca e filtros<br>• Cobertura de testes unitários iniciais         | Demo funcional • Relatório de testes v1                                          |
| **SP5**| 09 – 22 / 06       | • Implementar RF-006 → RF-010 (incl. ajuste no RF-008)<br>• Otimizações de performance<br>• Guia do usuário    | **Versão Beta Final** do software + documentação de usuário                      |


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
- Turma **SCC0130 (2025.1)** pelo feedback contínuo.

---

## Equipe

| Aluno                           | NUSP    | Email |
| --------------------------------|---------|-------|
| Vinicius G. Neves               | 14749363| [viniciusgustierrez@usp.br](mailto:viniciusgustierrez@usp.br) |
| Felipe V. de Oliveira           | 14570041| [felipe.volkweis@usp.br](mailto:felipe.volkweis@usp.br) |
| Luiz Felipe Catuzzi             | 11871198| [fellipecatuzzi@usp.br](mailto:fellipecatuzzi@usp.br) |

