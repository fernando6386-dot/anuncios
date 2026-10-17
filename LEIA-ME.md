# WR Consórcios · Landing page de cartas contempladas

Site estático, pronto para a Vercel. Não precisa de build nem de programação.

## Estrutura

```
index.html          a página
data/cartas.json    TODOS os dados que mudam: oferta do dia, cartas, estoque, datas, WhatsApp
img/                logo, fotos do Grupo WR e do estoque (img/st/)
vercel.json         cache: fotos por 7 dias, dados sempre atualizados
```

## Publicar na Vercel (5 minutos)

**Opção 1: arrastar a pasta**
1. Acesse vercel.com e entre com sua conta (pode usar o login do GitHub ou e-mail).
2. Clique em **Add New → Project**.
3. Arraste a pasta `wr-vercel` inteira (descompactada).
4. Em *Framework Preset*, escolha **Other**. Não precisa de Build Command.
5. Clique em **Deploy**. Em ~30 segundos o site está no ar em `algo.vercel.app`.

**Opção 2: pelo GitHub (recomendado para atualizar todo dia)**
1. Crie um repositório no GitHub e suba estes arquivos.
2. Na Vercel: **Add New → Project → Import** o repositório → **Deploy**.
3. Toda vez que você editar `data/cartas.json` no GitHub, a Vercel publica sozinha.

## Colocar no domínio da WR

Na Vercel: **Project → Settings → Domains → Add** e digite, por exemplo, `cartas.wrconsorcios.com.br`.
A Vercel mostra um registro **CNAME** para criar no painel onde o domínio está registrado (Registro.br, GoDaddy, Hostinger…). Em até algumas horas o site abre no domínio próprio, com HTTPS.

## Ligar Pixel da Meta e Google Analytics

Abra `index.html` e, no topo, procure os blocos comentados:
- **Pixel da Meta:** troque `SEU_PIXEL_ID` pelo ID do seu pixel e apague as linhas `<!--` e `-->` em volta.
- **GA4:** troque `G-XXXXXXX` pelo seu ID de medição e apague `<!--` e `-->`.

Com eles ligados, todo clique em botão de WhatsApp dispara automaticamente:
- Meta: evento **Contact** (use como conversão nas campanhas de mensagem/lead)
- GA4: evento **generate_lead**

## Atualizar a vitrine e a oferta do dia (só o JSON)

Edite `data/cartas.json`:

| Campo | O que é |
|---|---|
| `meta.dataCurta` / `meta.dataLonga` | Data que aparece na página ("17/10" e "17/10/2026") |
| `meta.novasHoje` | Número de cartas novas do dia (painel Consort) |
| `meta.totalBase` | Total de cartas na base, ex.: "3.098" |
| `meta.whatsapp` | WhatsApp com DDI e DDD, só números |
| `oferta` | Carro da oferta do dia: foto, nome, preço "de" e "por", km e a carta (id, administradora, crédito, entrada, parcela) |
| `ofertaImovel` | Oferta de imóvel que aparece no topo da vitrine |
| `cartas` | Lista de cartas: `[id, tipo I/A/C, administradora, crédito, entrada, % entrada, saldo devedor, "qtd x valor"]` |
| `estoque` | Carros (A) e imóveis (I) do Grupo WR usados no "cabe nessa carta" |

Para tirar a oferta do dia do ar, apague o bloco `"oferta"` (o cartão some sozinho).

**Atenção:** mantenha as vírgulas e aspas do JSON. Se a página ficar em branco depois de editar, cole o arquivo em jsonlint.com para achar o erro.

## Links para anúncios

| Link | Abre |
|---|---|
| `seudominio/` | Página completa (bio, site, orgânico) |
| `seudominio/#auto` | Só cartas de auto + oferta do dia |
| `seudominio/#imovel` | Só cartas de imóvel |
| `seudominio/#investidor` | Foco em investidor |

Toda mensagem de WhatsApp chega com o código da origem: `[LP-SITE]`, `[LP-ANUNCIO-AUTO]`, `[LP-ANUNCIO-IMOVEL]` ou `[LP-ANUNCIO-INVESTIDOR]`.

## Antes de divulgar

- Confirme com a administradora que a carta da oferta aceita o modelo e o ano do carro.
- Atualize a data e as cartas no JSON (as cartas saem rápido).
- Confirme o direito de uso da foto do topo (`img/familia.jpg`), que veio do banner do portal Consort.
