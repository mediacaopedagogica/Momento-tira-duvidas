# Tarefa Codex — Mercado Imobiliário 3D Premium V5

## Contexto
Este repositório contém várias experiências HTML educacionais. NÃO altere o `index.html` da raiz, NÃO altere `/aviso/` e NÃO altere nenhuma versão aprovada do jogo “Momento Responde Dúvidas”. Trabalhe somente em uma NOVA versão do laboratório.

Crie a nova experiência em:

`laboratorio-testes/mercado-imobiliario-premium-v5/`

O objetivo é substituir o protótipo WebGL bruto da V4 por uma experiência web 3D profissional, estável e visualmente muito mais próxima de um jogo premium. O usuário quer sensação de tabuleiro físico cinematográfico, com profundidade, materiais, iluminação, veículos, mão lançando o dado e movimento real do jogador. Não use pseudo-3D com CSS e não use o renderizador WebGL manual da V4 como base visual.

## Meta técnica
Use uma stack web 3D moderna com dependências INSTALADAS LOCALMENTE e EMPACOTADAS no build, sem CDN em runtime.

Preferência técnica:
- Vite + JavaScript/TypeScript
- Three.js instalado via npm
- cannon-es instalado via npm para física do dado
- loaders e controles importados do pacote local do Three.js
- build final estático que funcione no GitHub Pages

A página final publicada no GitHub Pages precisa funcionar sem buscar Three.js, Cannon ou módulos JS de CDNs externas.

Se usar assets GLB/GLTF, HDR, texturas ou sons externos durante o desenvolvimento, baixe-os para a pasta do projeto e mantenha um `ASSET_LICENSES.md`. Use apenas assets com licença compatível, preferencialmente CC0 ou CC-BY. Nunca hotlink assets externos na versão final. Se não houver assets disponíveis, crie fallback procedural de boa qualidade.

## Direção visual
A experiência deve parecer um jogo de tabuleiro imobiliário físico premium sobre uma mesa de madeira, com estética própria e autoral. Não copiar marca, logotipo, cartas, nomes ou layout de Banco Imobiliário/Monopoly.

Visual desejado:
- câmera cinematográfica em perspectiva, não exageradamente inclinada;
- tabuleiro grosso com moldura azul-marinho e detalhes dourados;
- casas do percurso com relevo, acabamento limpo e texto legível;
- mini cidade central com ruas, faixas, calçadas, lotes, casas, edifícios, árvores, iluminação urbana e pequenos veículos;
- sombras suaves de alta qualidade;
- materiais PBR: madeira, metal, vidro, concreto, asfalto, vegetação e plástico pintado;
- iluminação quente de estúdio/mesa com contraste, sem áreas estouradas;
- fundo/mesa com profundidade e elementos discretos de escritório imobiliário;
- nada de geometria atravessando o chão, triângulos explodidos, clipping evidente ou prédios gigantes tapando o tabuleiro;
- interface elegante azul-marinho + dourado, com boa legibilidade.

## Estrutura do tabuleiro
O percurso pedagógico deve manter estes temas:
- Início
- Captação
- Visita
- Documentação
- Proposta
- Financiamento
- Contrato
- Registro
- Lote
- Casa
- Apartamento
- Sala Comercial
- Edifício
- Condomínio
- Síndico
- Locação
- Vistoria
- Corretagem
- Intermediação
- Marketing
- Incorporação
- Garantias
- Built to Suit
- Sustentabilidade
- Governança
- Oportunidade
- Imprevisto
- Conquista

Cada casa deve ter posição própria e uma área de parada clara para o jogador.

## Transporte do jogador
No topo, permitir que o estudante escolha:
- carro
- carro compacto
- SUV
- bicicleta
- bicicleta elétrica
- moto
- a pé

A seleção não pode ser só um emoji no HUD. O objeto/personagem correspondente deve existir no 3D e ser usado como peça do jogador.

Para carros, crie ao menos três silhuetas visualmente distintas se não houver modelos GLB: hatch compacto, sedan/crossover e SUV. Bicicleta, e-bike e moto precisam ter geometria própria. A opção “a pé” deve usar um pequeno personagem estilizado, não um bloco.

Ao trocar o transporte, substituir imediatamente a peça 3D e manter a posição atual do jogador.

## Dado + mão
Este é um requisito central.

Ao clicar em “Jogar dado”:
1. a câmera faz um pequeno enquadramento para a área de lançamento;
2. uma mão 3D entra pela lateral direita;
3. a mão segura/acompanha o dado por um instante;
4. os dedos abrem;
5. o dado é lançado com velocidade linear e angular;
6. cannon-es simula queda, colisão e quique sobre uma superfície física;
7. o dado deve ter seis faces visuais reais com pontos;
8. quando o dado dormir/parar, calcular qual face está voltada para cima;
9. mostrar o resultado no HUD;
10. a mão sai da cena;
11. a câmera volta ao tabuleiro ou passa para acompanhamento do jogador;
12. a peça/veículo percorre o número sorteado de casas.

Não usar apenas rotação CSS ou troca aleatória de número. O resultado visual deve ser consistente com a orientação final do dado.

A mão pode ser procedural inicialmente, mas deve ter palma, polegar e quatro dedos articulados, proporções plausíveis e material de pele. Evite aparência de cápsula gigante atravessando a cena. Posicione a mão de modo cinematográfico e fora do tabuleiro quando não estiver em uso.

## Movimento do jogador
O veículo/peça deve:
- mover-se casa por casa, não teleportar;
- orientar-se para o sentido do deslocamento;
- ter aceleração/desaceleração suave;
- seguir uma curva/linha de percurso clara;
- evitar atravessar prédios e elementos da cidade;
- parar no centro da casa correspondente;
- permitir câmera “tabuleiro”, “seguir jogador” e “nível da cidade”.

No modo seguir jogador, a câmera deve acompanhar atrás e acima sem causar enjoo e sem atravessar objetos.

## Cidade viva
Adicionar movimento ambiental leve:
- alguns carros pequenos circulando em rotas próprias nas ruas centrais;
- iluminação de janelas sutil;
- árvores e postes coerentes;
- fonte central ou praça;
- elementos suficientes para dar sensação de cidade viva, sem prejudicar desempenho.

## Intencionalidade pedagógica
Não transformar em jogo de dinheiro pelo dinheiro. O HUD deve chamar a moeda de “Capital Profissional”.

Indicadores:
- Capital Profissional
- Patrimônio
- Conhecimento/Acertos
- Rodada

Ao cair em uma casa, abrir uma situação profissional curta e aplicada. Reaproveite e melhore as situações pedagógicas já existentes nas versões anteriores do laboratório, incluindo pelo menos:
- captação e compreensão das necessidades do cliente;
- documentação/registro;
- intermediação e transparência;
- contrato;
- locação;
- condomínio e síndico;
- corretagem;
- marketing;
- incorporação;
- garantias;
- built to suit;
- sustentabilidade;
- governança.

As alternativas devem ensinar por decisão profissional, não por memorização rasa. Depois da resposta, fornecer feedback curto explicando a lógica.

Ao acertar uma casa de patrimônio (lote, casa, apartamento, sala comercial, edifício), aumentar patrimônio e criar uma pequena confirmação visual no tabuleiro/HUD.

## Lobby e equipe
Manter uma opção de laboratório para formar equipe local:
- inserir nomes;
- escolher dupla, trio, grupo de 4 ou 5;
- roleta visível sorteando a equipe;
- cada jogador recebe cor e peça própria.

Não implementar multiplayer online real nesta tarefa. Apenas estruturar o código para que o estado do jogador/equipe esteja separado da renderização, facilitando backend futuro.

## Confiabilidade
A versão final NÃO pode ficar presa em loading infinito.

Implementar:
- tela de loading com etapas (“carregando motor”, “montando cidade”, “preparando física”, “pronto”);
- timeout/fallback;
- `window.onerror` e `unhandledrejection` com mensagem útil;
- se um asset opcional falhar, usar fallback procedural e continuar;
- botão “Recarregar ambiente” apenas quando houver erro fatal;
- console com mensagens claras.

## Performance
- alvo: 60 FPS em desktop comum e experiência aceitável em notebook intermediário;
- limitar pixel ratio;
- usar instancing para árvores/janelas quando fizer sentido;
- reduzir sombras em dispositivos fracos;
- evitar milhares de draw calls;
- manter responsividade para desktop e tablet; celular pode usar versão simplificada.

## Acessibilidade
- botões com rótulo textual e `aria-label` quando necessário;
- foco visível;
- alternativa de teclado para jogar dado e trocar câmera;
- respeitar `prefers-reduced-motion` reduzindo animações de câmera/mão;
- contraste adequado.

## Build e GitHub Pages
A rota final deve ser:
`/Momento-tira-duvidas/laboratorio-testes/mercado-imobiliario-premium-v5/`

Configure `base` do Vite corretamente para funcionar nesse subdiretório OU produza um build estático relativo que funcione em GitHub Pages.

Comite no próprio diretório todos os arquivos finais necessários para publicação. Se usar uma pasta de fonte separada, inclua também o build final pronto para o GitHub Pages.

## Verificação obrigatória antes de terminar
1. Rode instalação limpa das dependências.
2. Rode `npm run build` e corrija todos os erros.
3. Verifique que o HTML final não contém imports de `cdn.jsdelivr.net`, `unpkg.com` ou outros CDNs para Three.js/Cannon.
4. Verifique caminhos relativos dos assets no build.
5. Inicie servidor local e teste que a tela de loading desaparece.
6. Teste troca de todos os 7 transportes.
7. Teste pelo menos 10 lançamentos de dado e confirme que o jogo continua após cada um.
8. Teste as 3 câmeras.
9. Teste abertura e fechamento de desafios.
10. Não altere raiz, `/aviso/` ou outros projetos aprovados.

## Resultado esperado
Entregar uma V5 funcional e estável, muito superior visualmente à V4, com uma base técnica profissional para evoluir depois para modelos 3D e materiais ainda mais realistas. Não declarar que é “nível Unreal Engine” se os assets e o resultado ainda não sustentarem isso; priorize estabilidade, profundidade, iluminação, materiais e sensação de jogo premium.

Ao finalizar, forneça um resumo curto do que mudou, dos arquivos criados, dos testes executados e de qualquer limitação restante.
