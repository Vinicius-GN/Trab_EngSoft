# 🌐 Sci-Graph

> Dashboard interativo para explorar redes de colaboração acadêmica com base em coautorias e afiliações institucionais.

## 🚀 Sobre o Projeto

**Sci-Graph** é uma ferramenta web de visualização de dados que mapeia conexões entre pesquisadores e instituições. Utiliza APIs públicas como **ORCID** e **Google Scholar** para gerar redes de colaboração científica, sendo útil para professores, estudantes e grupos de pesquisa.

## 🔍 Funcionalidades

- 📊 **Dashboard com Grafo Interativo**  
  Explore redes acadêmicas onde cada nó representa um pesquisador ou instituição.

- 🔎 **Busca Inteligente e Filtros**  
  Pesquise por nome, ORCID, área de atuação ou instituição.

- 🔄 **Integração em Tempo Real**  
  Coleta dados ao vivo via APIs externas.

- 🧠 **Detalhamento Contextual**  
  Ao clicar em um nó, exibe publicações, afiliações, evolução de colaborações, etc.

- 🎨 **Agrupamento Visual por Instituição**  
  Pesquisadores são agrupados por universidade ou centro de pesquisa.

## 📸 Preview

> (Adicione aqui uma captura de tela ou GIF demonstrando o sistema)

## 🧱 Arquitetura

Sci-Graph é baseado em arquitetura **cliente-servidor**:
Frontend (React/Vue) ⇄ Backend (Node/Flask) ⇄ APIs Externas (ORCID, Google Scholar)


- **Frontend**: Interface web interativa com renderização de grafos (D3.js).
- **Backend**: API central, agregador de dados e motor de geração de grafos.
- **Serviços externos**: APIs públicas ORCID e Google Scholar.

📎 _Veja o [Diagrama de Arquitetura](docs/architecture.png)_

## ⚙️ Como Funciona

1. Usuário acessa o sistema via navegador.
2. O backend consulta os dados acadêmicos nas APIs.
3. Um grafo de colaboração é gerado e renderizado.
4. O usuário pode navegar, filtrar e consultar os dados.

## 🛠️ Tecnologias Utilizadas

| Camada        | Tecnologia                  |
|---------------|------------------------------|
| Frontend      | HTML, CSS, JS, D3.js / React |
| Backend       | Next.js |
| Integrações   | ORCID API, Google Scholar     |
| Formato de Dados | JSON                       |
| Protocolo     | HTTP/HTTPS                   |

