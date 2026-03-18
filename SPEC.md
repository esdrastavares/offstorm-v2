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
- [ ] Sistema extrai +50 produtos por categoria
- [ ] Dados são completos (título, preço, link, imagem)
- [ ] Interface mostra lista navegável
- [ ] Tempo de pesquisa reduzido vs múltiplas abas

## 4. Scope

### In Scope v1
- Fonte de dados: Mercado Livre
- Extração: top 100 produtos por categoria
- Dados: título, preço, link, imagem, avaliações, vendas
- Interface web básica (lista)
- Dados em arquivo/local storage (sem DB ainda)

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
3. Sistema carrega produtos do ML
4. Usuário visualiza dados (preço, título, avaliações)
5. Usuário pode filtrar/ordenar
6. Decide se nicho é viável
```

## 6. Funcionalidades

### F1: Listagem de Produtos
- Exibe lista de produtos por categoria
- Mostra: imagem, título, preço, avaliações
- Paginação ou scroll infinito

### F2: Busca por Categoria
- Lista de categorias disponíveis
- Seleção de categoria filtra produtos
- Categorias: Eletrônicos, Informática, Games, Beleza, Pets, Casa, Esportes, Brinquedos

### F3: Filtros
- Por faixa de preço
- Por avaliação (estrelas)
- Por quantidade de vendas

### F4: Ordenação
- Mais vendidos
- Menor preço
- Maior preço
- Melhores avaliações

### F5: Detalhes do Produto
- Título completo
- Preço atual
- Número de avaliações
- Link para o produto no marketplace

## 7. Dados a extrair

```json
{
    "id": "ml123456789",
    "title": "Nome do produto",
    "price": 129.90,
    "currency": "BRL",
    "image": "https://ml...",
    "link": "https://produto.ml/...",
    "reviews_count": 150,
    "rating": 4.5,
    "sales_count": 89,
    "category": "categoria",
    "seller": {
        "id": "seller123",
        "name": "Nome da loja"
    },
    "extracted_at": "2026-03-17T23:30:00Z"
}
```

## 8. Fonte de Dados

- [x] API oficial do Mercado Livre
- [ ] Crawler (scraping)
- [ ] Provedor de dados externo

### API Mercado Livre - Endpoints

**Busca de produtos:**
```
GET https://api.mercadolibre.com/sites/MLB/search?q={query}
GET https://api.mercadolibre.com/sites/MLB/search?category={category_id}
```

**Parâmetros:**
- `q` — termo de busca
- `category` — ID da categoria
- `limit` — número de resultados
- `offset` — paginação

**Autenticação:**
- Acesso público para buscas básicas
- App ID necessário para produção

### Dados retornados

```json
{
  "results": [
    {
      "id": "MLB123456789",
      "title": "Nome do produto",
      "price": 129.90,
      "currency_id": "BRL",
      "thumbnail": "https://ml...",
      "permalink": "https://produto.ml/...",
      "reviews": { "rating": 4.5, "count": 150 },
      "sold_quantity": 89,
      "category_id": "MLB1234",
      "seller": { "id": 123456789, "nickname": "loja" }
    }
  ]
}
```

### Categorias MLB ( Marketplace Brasil)

| Categoria | ID |
|-----------|-----|
| Eletrônicos | MLB1000 |
| Informática | MLB1648 |
| Games | MLB1144 |
| Beleza | MLB1246 |
| Pets | MLB1071 |
| Casa | MLB1574 |
| Esportes | MLB1276 |
| Brinquedos | MLB1132 |

---

## 9. Arquitetura Proposta

```
┌─────────────┐    ┌─────────────┐    ┌─────────────┐
│  Fonte de  │───▶│  Processa   │───▶│  Interface  │
│   Dados    │    │   (parse)   │    │   (lista)   │
└─────────────┘    └─────────────┘    └─────────────┘
```

## 10. Acceptance Criteria

### Sistema
- [ ] Extrai no mínimo 50 produtos por categoria
- [ ] Trata erros de rede
- [ ] Salva dados em formato utilizável

### Interface
- [ ] Lista produtos com imagem, título e preço
- [ ] Link para produto no ML
- [ ] Filtro por categoria
- [ ] Ordenação básica

### Qualidade
- [ ] Código organizado
- [ ] README com instruções

---

**Versão:** 1.1  
**Data:** 2026-03-17  
**Status:** Em revisão
