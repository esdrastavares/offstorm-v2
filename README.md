# OffStorm

> Smart product discovery — Encontre produtos em tendência e valide ideias em um só lugar.

## Problema

Não existe um lugar único para descobrir produtos e tendências nos maiores marketplaces. 

Quem precisa validar produtos para vender (dropshippers, e-commerces, inventores) precisa consultar múltiplas fontes分开:
- Google Trends (interesse de busca)
- Amazon (vendas, bestseller)
- Mercado Livre (mais vendidos)
- AliExpress (fornecedores)
- Reddit/Instagram/TikTok (buzz social)

Cada plataforma mostra um pedaço. É seu trabalho conectar os pontos — e isso leva horas.

## Solução

OffStorm é uma plataforma SaaS que consolida dados de múltiplos marketplaces em um só lugar, com inteligência aplicada:

- **Exploração** de produtos por categoria
- **Dados consolidados** (preço, vendas, avaliações, reputação)
- **Tendências** (o que está subindo)
- **Relatórios** para tomada de decisão

## Público-Alvo (ICP)

- **Dropshippers** — procuram produtos pra revender
- **E-commerces** — validam sortimento e preços
- **Inventores/Creators** — pesquisam tendências
- **Investidores de produto** — avaliam demanda

## Escopo v1 (MVP)

### O que faz
- Crawler do Mercado Livre (Brasil)
- Extrai top 100 produtos por categoria
- Dados: título, preço, vendas, avaliações, vendedor

### O que NÃO faz (fora de escopo)
- Múltiplos marketplaces (v2+)
- Dados históricos/trends (v2+)
- API externa (v2+)
- Autenticação/payment (v2+)

## Roadmap

### v1 (MVP) — Atual
- [ ] Crawler Mercado Livre
- [ ] Extração: top 100 por categoria
- [ ] Interface básica (lista)
- [ ] Teste de conceito validado

### v2
- [ ] Mais marketplaces (Amazon, AliExpress)
- [ ] Dados históricos (tendências)
- [ ] Filtros avançados

### v3
- [ ] Autenticação
- [ ] Planos pagos
- [ ] API pública
- [ ] Alertas de tendências

## Como contribuir

```bash
# Setup
pip install -r requirements.txt
playwright install chromium

# Rodar crawler
python -m crawler.mercadolivre
```

## Status

🚧 Em desenvolvimento

---

**Contato:** Esdras Tavares  
**Repo:** github.com/esdrastavares/offstorm-v2
