# OffStorm — Product Spec

## 1. Problem Statement

**DOR:** Não existe UM lugar sório para pesquisar produtos nos maiores marketplaces — seja pra vender (e-commerce, dropshipping) ou pra descobrir tendências.

**IMPACTO:** 
- Pesquisadores gastam horas pulando entre múltiplas fontes
- Dados ficam fragmentados, sem visão consolidada
- Decisões baseadas em intuição, não em dados

## 2. Target User

| Persona | Problema | Valor |
|---------|----------|-------|
| **Dropshipper** | Precisa validar se produto vende antes de listar | Confirmação rápida de demanda |
| **E-commerce owner** | Quer comparar sortimento e preços | Inteligência competitiva |
| **Inventor/creator** | Precisa de ideias de produtos | Tendências e oportunidades |
| **Investidor de produto** | Avalia potencial de mercado | Dados consolidados |

## 3. Goal & Success Metrics

**Objetivo v1:** Validar que existe demanda por uma ferramenta de product discovery com dados do Mercado Livre.

**Métricas de sucesso:**
- [ ] Crawler extrai +50 produtos por categoria rodando
- [ ] Dados são completos (título, preço, link, imagem)
- [ ] Interface mostra lista navegável
- [ ] Tempo de pesquisa reduzido vs múltiplas abas

## 4. Scope

### In Scope v1
- Crawler Mercado Livre (Python + Playwright)
- Extração: top 100 produtos por categoria
- Dados: título, preço, link, imagem
- Interface web básica (lista)
- Dados em arquivo JSON (sem DB ainda)

### Out of Scope v1
- Múltiplos marketplaces
- Autenticação
- Payment
- API pública
- Dados históricos
- Deploy/produção

## 5. User Flow

```
1. Usuário acessa interface
2. Seleciona categoria (ex: "Eletrônicos")
3. Sistema exibe top produtos do ML
4. Usuário analiza dados (preço, título)
5. Decide se nicho é viável
```

## 6. Technical Approach

### Estratégia
- Crawler do Mercado Livre (headless browser)
- Por que: ML tem JavaScript rendering, requests simples não funcionam
- Estratégia: Paginação infinita via scroll

### Dados a extrair (v1)
```python
{
    "id": int,
    "title": str,        # Título do produto
    "price": str,        # Preço (R$ 1.234,56)
    "link": str,         # URL do produto
    "image": str,        # URL da imagem
    "category": str,     # Categoria do crawl
    "crawled_at": str    # ISO timestamp
}
```

### Categorias inicial (teste)
- Eletrônicos
- Informática
- Games
- Beleza
- Pets
- Casa
- Esportes
- Brinquedos

## 7. Acceptance Criteria

### Crawler
- [ ] Extrai no mínimo 50 produtos por categoria rodando
- [ ] Trata erros de rede (retry)
- [ ] Salva dados em JSON válido
- [ ] Tempo de execução < 5 min por categoria

### Interface
- [ ] Lista produtos com título e preço
- [ ] Mostra imagem do produto
- [ ] Link para produto no ML
- [ ] Filtro por categoria

### Qualidade
- [ ] Código limpos, com comments
- [ ] README com instruções de setup
- [ ] Requirements.txt completo

---

**Versão:** 1.0  
**Data:** 2026-03-17  
**Status:** Pronto para implementação
