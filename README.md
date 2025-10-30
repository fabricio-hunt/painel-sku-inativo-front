README – Painel de Consulta Bemol (SKUs Inativos)
Versão: 1.0
Autor: Fabricio Baraúna
Data: Outubro/2025

Descrição:
Painel web em HTML + CSS inline + JavaScript puro para consultar SKUs inativos do ambiente Databricks.
Interface moderna, responsiva e com o tema oficial da Bemol (#0285d1).

Logo:
Coloque o arquivo da logo Bemol no mesmo diretório do projeto e use este caminho no HTML:
<img class="logo" src="./logo-bemol.png" alt="Logo Bemol" />
Caso use outra hospedagem, substitua pelo link público (ex: CDN, GitHub ou servidor da Bemol).

Configuração:
1. Abra o arquivo index.html.
2. Dentro do <script>, localize:
   const DEMO = true;
   - Para modo de demonstração: mantenha true (dados fake).
   - Para modo real: troque para false.
3. Preencha as variáveis de integração Databricks:
   const DATABRICKS_WORKSPACE_URL = "https://<seu-workspace>.azuredatabricks.net";
   const DATABRICKS_TOKEN = "dapiXXXXXXXXXXXXXXXXXXXXXXXX";
   const WAREHOUSE_ID = "xxxxxxxxxxxx";
4. Ajuste a consulta SQL no bloco:
   const SQL_TEMPLATE = (q) => `SELECT ... FROM catalogo.produtos.skus ...`;

Segurança:
Importante: nunca exponha o token Databricks em código cliente (HTML/JS).
Crie um endpoint backend (proxy) para fazer a requisição segura:
/api/skus-inativos?q=notebook
O front-end deve chamar esse endpoint em vez de acessar o Databricks diretamente.

Funcionalidades:
- Busca por SKU, nome ou categoria.
- Tabela responsiva com paginação.
- Skeleton loading (efeito de carregamento).
- Toasts de feedback.
- Exibição de total e data da última atualização.
- Paleta e tipografia no padrão Bemol.

Como usar:
1. Salve o arquivo como index.html.
2. Abra no navegador.
3. Digite um termo e pressione Enter ou clique em Consultar.

Estrutura:
/painel-bemol/
 ├── index.html        → código principal (HTML + CSS + JS inline)
 ├── logo-bemol.png    → imagem da logo Bemol
 └── README.txt         → instruções do projeto

Observações:
- O modo DEMO inclui alguns SKUs de exemplo para testes.
- O layout utiliza apenas HTML + CSS puro, sem dependências externas.
- Para deploy, pode ser hospedado no GitHub Pages, Vercel ou servidor interno da Bemol.
