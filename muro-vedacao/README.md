# Muro de vedação – v13

Aplicativo em uma única página HTML para dimensionar muro de vedação de divisa. Para usar: https://engrafaeljralves.github.io/DIMI--Concreto/muro-vedacao/ (GitHub Pages), ou abra `muro-vedacao-v13.html` no navegador.

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


## v10
- Empuxo sem desconto entre os lados: as peças (pilar, pescoço, parede de concreto, pano, cintas, nó parede–sapata) usam a envoltória do empuxo ativo cheio de cada lado com o vento nos dois sentidos; cada face é dimensionada pelo seu maior momento.
- Estabilidade (Rankine, NBR 11682): a ação é o empuxo ativo do lado que empurra mais o vento; o lado oposto só resiste, com o empuxo passivo × fator (campo numérico, 0 a 1).
- FS mínimo ao tombamento 2,0 (NBR 11682).

## v11
- Parede de concreto do painel inferior e pilares resolvidos como uma placa única de Kirchhoff com rigidez variável (D ∝ t³): a carga se divide pela rigidez real de cada parte; o pilar deixa de ser apoio indeslocável da parede.
- Modelo do eixo do pilar ao meio do vão (simetria), base engastada na sapata, topo livre com a reação do pano na parede e o cortante e o momento do pilar acima na largura do pilar; dois limites para o pano (parcela na base ou inteiro no pilar).
- Pilar na altura da parede dimensionado pelos esforços da sua faixa na placa; memorial e diagramas atualizados.
- Memorial lista só os dados usados; item 4.3 enxuto.

## v12
- Nova aba **3D**: modelo do muro (sapata, pescoços ou baldrame, pilares, cintas, canaletas, pano de alvenaria com textura de blocos, parede de concreto, solo dos dois lados e divisa) com rotação, zoom e deslocamento (Three.js r147 + OrbitControls, carregados do jsDelivr só quando a aba é aberta).
- Ações no 3D por componente: vento, empuxo ativo de cada lado (tardoz) e passivo resistente × fator, com opção "Todos os carregamentos", por caso de cálculo ou isoladas com setas e valor máximo, sobrecarga nos terrenos e seleção de elementos por clique com nome e dimensões.
- Vistas rápidas (isométrica, lado interno, lado do vizinho, lateral, topo), camadas liga/desliga, alvenaria transparente e escolha de 1 a 4 vãos; o modelo acompanha os dados.
- Detalhamento da alvenaria armada: desenhos F (planta baixa da 1ª fiada com furos grauteados, V1 e enrijecedores com E1/E2/E3) e G (vista pelo lado interno com canaletas H1, cotas entre eixos das canaletas, grampos E3 e furos V1), gerados a partir dos dados e incluídos no memorial (Figuras após o detalhamento).

## v13
- Botão **Dimensionar com menor custo** (aba Dados): mantém cotas, solo, vento e critérios; testa os dois sistemas (pilares + alvenaria/parede de concreto e alvenaria armada com ou sem enrijecedores), tipo de sapata, espaçamentos, bloco, cinta intermediária, canaletas, profundidade de apoio, largura e altura da sapata, fck, fbk e classe da argamassa; aplica a solução mais barata que passa em todas as verificações e no detalhamento, e lista as alternativas.
- Custo por metro de muro (concreto, aço, fôrma, alvenaria, graute, escavação e reaterro) com preços unitários de referência editáveis.
- **Chaveta (dente) sob a sapata** contra o deslizamento: altura, largura, posição (sob o muro, meio, ponta) e fator do passivo; o passivo na face da chaveta (com a sobrecarga do solo acima do fundo) soma na resistência ao deslizamento; dimensionamento como balanço de concreto (flexão, armadura mínima, VRd1) para a força que ela mobiliza; armadura N21 em U, desenhos (corte, seção, elevação, detalhamento e 3D) e memorial.
- O dimensionamento otimizado testa a chaveta (sem, 30, 50 e 80 cm) junto com a profundidade de apoio; largura da sapata por bisseção.
