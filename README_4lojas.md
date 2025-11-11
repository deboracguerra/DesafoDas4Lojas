# README — Análise de Vendas das Lojas (Alura Store)

> Projeto em Python para analisar o desempenho de **4 lojas** do Sr. João e recomendar **qual loja vender**, com base em faturamento, avaliações de clientes, frete médio, mix de categorias e comportamento de produtos.

---

## 🎯 Objetivo

- Carregar e tratar dados das lojas (CSV).
- Gerar **métricas-chave** (faturamento, avaliações, frete, mix).
- Produzir **gráficos** (barras, pizza, dispersão/boxplot/Pareto).
- Entregar um **relatório conclusivo** com a recomendação de desinvestimento.

---

## 🧰 Stack & Dependências

- **Python** ≥ 3.10  
- Bibliotecas:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `jupyter` (opcional, para notebooks)
  - `scipy` (opcional, se usar testes/intervalos)
- (Opcional) `python-dotenv` para variáveis de ambiente

Instalação rápida:

```bash
# via venv
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

> Se não houver `requirements.txt`, instale manualmente:
> `pip install pandas numpy matplotlib jupyter`

---

## 🗂️ Estrutura Sugerida do Repositório

```
.
├── data/
│   ├── loja1.csv
│   ├── loja2.csv
│   ├── loja3.csv
│   └── loja4.csv
├── notebooks/
│   └── 01_analise_exploratoria.ipynb
├── src/
│   ├── io_utils.py
│   ├── metrics.py
│   ├── viz.py
│   └── analyze.py        # script principal (CLI)
├── reports/
│   ├── figuras/          # gráficos gerados (.png)
│   └── Relatorio_Final.md
├── tests/
│   └── test_metrics.py
├── README.md
└── requirements.txt
```

> Adeque os nomes dos arquivos às suas implementações.

---

## 🔢 Dados de Entrada (Exemplo)

Arquivos CSV por loja contendo (campos típicos):

- `id_venda`, `data`, `produto`, `categoria`, `preco`, `quantidade`, `frete`, `avaliacao`  
- Cada loja possui seu próprio CSV: `loja1.csv` … `loja4.csv`.

---

## ▶️ Como Executar

### 1) Via script (CLI)

```bash
python src/analyze.py   --inputs data/loja1.csv data/loja2.csv data/loja3.csv data/loja4.csv   --outdir reports   --figdir reports/figuras   --format md
```

Parâmetros sugeridos:
- `--inputs`: caminhos dos CSVs das lojas (1..n).
- `--outdir`: pasta do relatório.
- `--figdir`: pasta para salvar as figuras.
- `--format`: `md` (markdown) ou `html` (se exportar HTML).

### 2) Via notebook

Abra `notebooks/01_analise_exploratoria.ipynb`:

```bash
jupyter notebook notebooks/01_analise_exploratoria.ipynb
```

---

## 📈 Métricas & Visualizações

O projeto calcula e plota:

- **Faturamento total** por loja (gráfico de barras).
- **Média de avaliações** por loja (barras/colunas).
- **Frete médio** por loja (barras/boxplot).
- **Mix de categorias** (barras horizontais por loja).
- **Top 5 produtos mais vendidos** e **Top 5 menos vendidos** (tabelas/gráficos).
- (Opcional) **Pareto** de menos vendidos por loja para identificar cauda de baixo giro.

Figuras são salvas em `reports/figuras/` (ex.: `faturamento_barras.png`, `avaliacoes.png`, `frete_boxplot.png`, `categorias_loja1.png`, etc.).

---

## 🧮 Resultados (Resumo do Estudo de Caso)

> Com base nos dados disponibilizados:

- **Faturamento total** (R$):  
  L1: 1.534.509,12 · L2: 1.488.459,06 · L3: 1.464.025,03 · **L4: 1.384.497,58** *(menor)*

- **Avaliação média**:  
  **L3: 4,05** · L2: 4,04 · L4: 4,00 · L1: 3,98

- **Frete médio (R$)**:  
  **L4: 31,28** *(melhor)* · L3: 33,07 · L2: 33,62 · L1: 34,69

- **Mix e produtos**:  
  Lojas 1–3 possuem **núcleo consistente** (móveis/eletrônicos) e melhor **coerência de portfólio**.  
  **Loja 4** apresenta **heterogeneidade** de mix e **vários itens de alto ticket** entre os **menos vendidos** (ex.: geladeira, lavadora, guarda-roupas, guitarra/violão), indicando **giro fraco** e **risco de capital imobilizado**.

### ✅ Recomendação

**Vender a Loja 4.**

**Motivos principais:**
1. **Menor faturamento** da rede.  
2. **Avaliação apenas mediana** (não compensa a menor tração).  
3. **Frete baixo** é um ponto forte, **mas isolado** (não se traduz em liderança de vendas).  
4. **Mix com baixa tração** em itens caros → **estoque arriscado** e **fluxo de caixa pressionado**.

**Implicação:** concentrar esforços nas lojas com **vantagens claras**:
- **L1**: maior receita; foco em elevar satisfação e otimizar frete.  
- **L2**: equilíbrio de reputação e receita; escalar linhas educacional/instrumentos.  
- **L3**: referência em experiência e logística; ampliar ticket em mobiliário.

> Um **Relatório Final** gerado pelo script é salvo em `reports/Relatorio_Final.md` (ou `.html`), contendo os gráficos e a justificativa detalhada.

---

## ✅ Testes

Execute testes unitários (se incluídos):

```bash
pytest -q
```

---

## 🧪 Reprodutibilidade

- Defina um **seed** quando houver amostragem/simulação.  
- Fixe versões em `requirements.txt`.  
- Mantenha o **schema** dos CSVs consistente entre lojas.

---

## 🤝 Contribuição

1. Crie um branch: `git checkout -b feature/minha-melhoria`
2. Commit: `git commit -m "feat: descreva a melhoria"`
3. Push: `git push origin feature/minha-melhoria`
4. Abra um Pull Request

Sugestões de melhorias:
- Pipeline `make`/`tox`/`pre-commit`.
- Exportar relatório em **PDF/HTML** com sumário e hyperlinks.
- Adicionar **dashboard** (ex.: Streamlit).

---

## 📜 Licença

Este projeto está sob a licença **MIT**. Veja `LICENSE` (se aplicável).

---

## 👩‍💻 Autoria

**Déb** — análise, código e relatório.  
Sinta-se à vontade para abrir *issues* com dúvidas, bugs ou ideias de novos gráficos.
