# Muro de vedação – v9

Aplicativo em uma única página HTML para dimensionar muro de vedação de divisa. Para usar: https://engrafaeljralves.github.io/DIMI--Concreto/muro-vedacao/ (GitHub Pages), ou abra `muro-vedacao-v9.html` no navegador.

**Sistemas**
- Pilares de concreto com alvenaria de vedação, baldrame, cinta superior e sapata isolada ou corrida, de divisa ou centrada.
- Alvenaria estrutural armada em balanço, com opção de enrijecedores feitos com o próprio bloco, e sapata corrida.

**Verificações**
- Vento (NBR 6123).
- Empuxo dos dois lados, do apoio da sapata até o terreno de cada lado.
- Fundação: tensões no solo, excentricidade, tombamento e deslizamento.
- Concreto armado (NBR 6118).
- Alvenaria (NBR 16868-1): estádio III, esbeltez, cisalhamento e pano pelo Anexo E (Tabelas E.1 e E.2).
- Canaletas horizontais armadas (mínimo de 0,05%, mais próximas no terço inferior), cinta intermediária, treliça no terço inferior e rigidez das cintas.
- Detalhamento editável das armaduras.
- Memorial de cálculo em Word.
- Exportação e importação de modelos (.json).

Os resultados devem ser conferidos e assumidos pelo engenheiro responsável.

Versões anteriores ficam na mesma pasta (por exemplo, `muro-vedacao-v6.html`).

## v8
- Pilares com sapata corrida: painel inferior em bloco ou em parede de concreto armado engastada na sapata (altura, espessura e barra editáveis). Divisão da carga por flechas iguais entre balanço vertical e faixa horizontal até os pilares; armaduras N18/N19 (vertical por face, com esperas) e N20 (horizontal).
- Altura do pescoço editável na sapata corrida; o NA não entra nesse caso.
- Canaletas armadas horizontais no painel inferior (Anexo E, Tabela E.2).
- Cargas das cintas pela reação das faixas sob a pressão lateral real.

## v9
- Parede de concreto do painel inferior calculada como placa (Kirchhoff) resolvida numericamente por diferenças finitas no próprio app: base engastada, topo livre com a reação do pano, laterais engastadas e apoiadas (envoltória), vento nos dois sentidos.
- Momentos vertical e horizontal por face, cortante máximo e parcela da carga que desce pela base; o pilar passa a receber só as reações laterais da placa na altura da parede.
- Conferido contra casos-limite (balanço longo q·h²/2 e P·h; faixa alta q·ℓ²/12, q·ℓ²/24, q·ℓ²/8) e convergência de malha.

