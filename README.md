TESTE-123# Analisador de Preço

Calculadora de **preço-teto** de ações pelo modelo de dividendos, para a B3 e para o mercado
americano. Informe o ticker, ajuste a sua projeção de lucro e descubra até quanto vale a pena
pagar pela ação para obter o dividend yield que você considera aceitável.

## Como funciona

```
Preço-teto = (Lucro líquido projetado ÷ Nº de ações × Payout) ÷ Yield aceitável
```

O resultado é comparado com a cotação atual e traduzido em um veredito:

| Margem de segurança | Veredito |
| --- | --- |
| ≥ +15% | Boa compra |
| entre −5% e +15% | Neutro |
| < −5% | Caro |

Além do preço-teto, a página calcula LPA, DPA, dividend yield projetado, P/L, margem de
segurança, desconto sobre o teto e um comparativo com o histórico de proventos dos últimos
cinco anos.

## Campos

| Campo | Origem |
| --- | --- |
| Cotação atual | Automática (Yahoo Finance) — editável para simular outro preço |
| Lucro líquido projetado | Manual, ou automática com token da brapi.dev (ações da B3) |
| Quantidade de ações | Manual, ou automática com token da brapi.dev (ações da B3) |
| Payout | Manual — quanto do lucro a empresa distribui |
| Yield aceitável | Manual — o retorno mínimo que você exige |

Tickers da B3 podem ser digitados sem sufixo (`ITSA4`, `BBAS3`, `TAEE11`) — a página
acrescenta `.SA` automaticamente. Ações americanas vão direto (`AAPL`, `KO`).

## Fontes de dados

- **Yahoo Finance** — cotação, nome da empresa, moeda, máxima e mínima de 52 semanas e
  histórico de proventos. Não exige cadastro. Como a API não envia cabeçalhos CORS, as
  requisições passam por uma cadeia de proxies públicos com múltiplas tentativas.
- **brapi.dev** (opcional) — lucro e quantidade de ações de empresas da B3. Requer um token
  gratuito, colado no botão ⚙ da página. O token fica apenas no `localStorage` do seu
  navegador e nunca é enviado para outro lugar.

## Executando

A página é um único arquivo HTML, sem dependências e sem build.

**Publicada (recomendado):** acesse pelo GitHub Pages. A busca automática funciona em
qualquer navegador.

**Localmente:** abrir o `index.html` direto do disco funciona no Chrome, mas **não no
Safari** — o Safari bloqueia qualquer requisição de rede em páginas de origem `file://`, e
a busca automática falha (o cálculo manual continua funcionando). Para rodar local no
Safari, sirva a pasta por HTTP:

```bash
python3 -m http.server 8000
# depois abra http://localhost:8000
```

## Aviso

Ferramenta de apoio ao seu próprio cálculo. Não é recomendação de investimento, e as
projeções de lucro e payout são premissas suas — o resultado é tão bom quanto elas.
