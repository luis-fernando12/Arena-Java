<h1 align="center">⚔️ Soul of Fighters</h1>

<p align="center">
  <i>Um simulador de combate 2D desenvolvido em Java, focado na aplicação prática e profunda de Programação Orientada a Objetos (POO).</i>
</p>

---

## 📌 Visão Geral do Produto
O **Soul of Fighters** é um jogo de luta local para dois jogadores (mesmo teclado). O projeto explora o equilíbrio entre diferentes atributos (Vida, Stamina, Velocidade e Dano) baseados em 4 arquétipos de personagens fortemente inspirados em elementos da natureza e figuras de alta fantasia.

O diferencial técnico do projeto é a ausência de atalhos de engines visuais de alto nível: a máquina de estados, o controle de animações (sprites) e as *hitboxes* são construídos do zero no framework Greenfoot.

---

## 🎮 Requisitos e Fluxo do Jogo

- **Seleção de Personagens:** A tela inicial apresenta 4 lutadores. O jogo apenas avança quando os dois jogadores (P1 e P2) confirmam suas escolhas.
- **Seleção de Cenário:** Após a escolha dos lutadores, os jogadores têm 2 arenas disponíveis. O primeiro a selecionar define o palco da luta. Os personagens não interagem com o cenário, apenas com os limites da tela e entre si.
- **Combate:** Cada jogador possui dois ataques básicos (Soco e Chute) e um Poder Especial (dependente de Stamina).
- **Condição de Vitória:** A luta encerra imediatamente quando a barra de vida de um dos lutadores zera, retornando o fluxo para a tela de seleção de personagens.

---

## 🥋 Ficha Técnica dos Lutadores

O equilíbrio do jogo baseia-se em vantagens e desvantagens claras entre os personagens. 

| Personagem | Elemento | Perfil Geral | Vida | Stamina | Vel. Ataque | Dano (Básico) | Dano (Especial) |
| :--- | :--- | :--- | :---: | :---: | :---: | :---: | :---: |
| **Izalith** | 🔥 Fogo | Lenta, frágil, mas com altíssimo potencial destrutivo e "spam" de poderes. | Baixa | **Alta** | Lenta | Padrão | **Máximo** |
| **Ciaran** | 💧 Água | Focada em combos muito rápidos e agilidade, sacrificando poder bruto. | Baixa | Média | **Máxima** | Padrão | Médio |
| **Artorias** | 🌑 Escuridão | O lutador mais equilibrado do jogo, sem grandes fraquezas ou picos. | Média | Média | Média | Padrão | Médio |
| **Ornstein** | ⚡ Trovão | O "Tank". Golpes físicos devastadores e alta resistência, mas ataques lentos. | **Alta** | Baixa | Lenta | **Máximo** | Baixo |

---

## 💻 Arquitetura Técnica (POO em Java)

O núcleo do jogo foi desenhado para garantir escalabilidade e código limpo através de conceitos fundamentais da Orientação a Objetos.

### 1. Herança e Abstração
- **Classe Abstrata `Lutador`**: Atua como o contrato principal (`extends Actor`). Define atributos protegidos como `vida` e `stamina`, garantindo que não existam instâncias genéricas no jogo.
- **Classes Concretas**: `Izalith`, `Ciaran`, `Artorias` e `Ornstein` herdam da classe mãe, implementando seus próprios arrays de sprites e modificadores de atributos no construtor.

### 2. Encapsulamento
- Modificadores de acesso rigorosos para Vida e Stamina, manipulados apenas através de métodos `get` e `set` seguros para refletirem visualmente no HUD.

### 3. Máquina de Estados (Enum)
- Controle de fluxo através de estados como `PARADO`, `ANDANDO`, `ATACANDO`, `APANHANDO`. 
- Isso bloqueia inputs simultâneos ilógicos (ex: impedir que o jogador use o especial enquanto recebe dano ou está no meio de um pulo).

### 4. Sistema de Colisão Avançado (Active Frames)
- As verificações de dano (`getIntersectingObjects()`) não ocorrem continuamente. Elas são acionadas exclusivamente nos frames exatos das animações de ataque, simulando o peso e o momento correto de impacto dos jogos de luta clássicos.

---

## 🛠️ Tecnologias Utilizadas
- **Linguagem:** Java
- **Framework:** Greenfoot
- **Paradigma:** Programação Orientada a Objetos (POO)
