<p align="center">
  <img width="600" height="374" alt="Fight! Free Pixel Font - Mehmet Reha Tuğcu" src="https://github.com/user-attachments/assets/05632c7b-0cb5-4d5c-a311-7c7569207f3f" />
</p>

![Soul of Fighters Banner](https://private-user-images.githubusercontent.com/169305728/591449887-05632c7b-0cb5-4d5c-a311-7c7569207f3f.gif)

# ⚔️ Soul of Fighters

*Um simulador de combate 2D desenvolvido em Java, focado na aplicação prática e profunda de Programação Orientada a Objetos (POO).*

---

## 📌 Visão Geral do Produto

O **Soul of Fighters** é um jogo de luta local para dois jogadores (mesmo teclado). O projeto une a atmosfera sombria de **Dark Souls** com a jogabilidade arcade clássica de jogos de luta 2D.

O diferencial técnico é a ausência de atalhos de engines visuais de alto nível: a máquina de estados, o controle de animações (sprites) e as *hitboxes* são construídos do zero no framework **Greenfoot**.

---

## 🎮 Fluxo do Jogo

```
Tela de Seleção de Personagens
        ↓  (P1 e P2 confirmam)
Tela de Seleção de Arena
        ↓  (primeiro a escolher define o palco)
Combate
        ↓  (vida de um lutador chega a zero)
Tela de Seleção de Personagens  ← retorna aqui
```

- **Seleção de Personagens:** O jogo só avança quando os dois jogadores confirmam sua escolha.
- **Seleção de Arena:** 2 cenários disponíveis. Os personagens não interagem com o cenário, apenas com os limites da tela.
- **Combate:** Cada jogador tem dois ataques básicos (Soco e Chute) e um Poder Especial dependente de Stamina.
- **Vitória:** A luta encerra imediatamente quando a vida de um lutador zera.

---

## 🥋 Ficha Técnica dos Lutadores

| Personagem | Elemento | Perfil | Vida | Stamina | Vel. Ataque | Dano Básico | Dano Especial |
|---|---|---|---|---|---|---|---|
| **Izalith** | 🔥 Fogo | Frágil, lenta, especial devastador | Baixa | **Alta** | Lenta | Padrão | **Máximo** |
| **Ciaran** | 💧 Água | Combos rápidos, sacrifica poder bruto | Baixa | Média | **Máxima** | Padrão | Médio |
| **Artorias** | 🌑 Escuridão | Equilibrado, sem grandes fraquezas | Média | Média | Média | Padrão | Médio |
| **Ornstein** | ⚡ Trovão | Tank, golpes devastadores, ataques lentos | **Alta** | Baixa | Lenta | **Máximo** | Baixo |

---

## 💻 Arquitetura Técnica (POO em Java)

### 1. Herança e Abstração
- **Classe Abstrata `Lutador`**: contrato principal (`extends Actor`). Define atributos protegidos `vida` e `stamina`.
- **Classes Concretas**: `Izalith`, `Ciaran`, `Artorias` e `Ornstein` herdam e sobrescrevem comportamentos.

### 2. Encapsulamento
- `vida` e `stamina` são privados, acessados apenas via `getVida()`, `setVida()`, `getStamina()`, `setStamina()`.

### 3. Máquina de Estados (Enum)
- Estados: `PARADO`, `ANDANDO`, `ATACANDO`, `APANHANDO`, `CARREGANDO_ESPECIAL`, `MORTO`.
- Bloqueia inputs ilógicos — ex: não permite usar especial enquanto apanha.

### 4. Active Frames (Colisão por Frame)
- `getIntersectingObjects()` só é chamado no frame exato do impacto na animação de ataque.
- Garante jogabilidade justa e sensação de peso nos golpes.

### 5. Special Move com Carregamento
- Segurar a tecla drena Stamina e aumenta o nível do poder (0 → 3).
- Soltar dispara o especial com o poder acumulado.

---

## 🛠️ Tecnologias

- **Linguagem:** Java
- **Framework:** Greenfoot
- **Paradigma:** Programação Orientada a Objetos (POO)
- **Versionamento:** Git + GitHub

---

## 🚀 Como Rodar o Projeto

1. Baixe e instale o [Greenfoot](https://www.greenfoot.org/download)
2. Clone este repositório:
   ```bash
   git clone https://github.com/luis-fernando12/Arena-Java.git
   ```
3. Abra o Greenfoot → **Scenario → Open** → selecione a pasta do projeto
4. Clique em **Run** para iniciar

---

## 👥 Fluxo de Trabalho Git

> **Regra de ouro: ninguém sobe código direto na `develop`. Todo código passa por PR e revisão do outro membro.**

### Branches principais

| Branch | Descrição |
|---|---|
| `main` | Versão estável entregável |
| `develop` | Branch de desenvolvimento — base para todas as features |

### Criando uma branch de trabalho

Sempre crie sua branch a partir da `develop`:

```bash
git checkout develop
git pull origin develop
git checkout -b feature/nome-da-sua-task
```

### Padrão de nomes de branch

```
feature/nome-da-funcionalidade   → funcionalidade nova
fix/nome-do-problema             → correção de bug
```

**Exemplos reais do projeto:**
```
feature/classe-lutador-abstrata
feature/maquina-de-estados
feature/hud-barras-vida-stamina
feature/tela-selecao-personagens
feature/tela-selecao-arena
feature/personagem-izalith
feature/personagem-ciaran
feature/personagem-artorias
feature/personagem-ornstein
feature/sistema-active-frames
feature/special-move-carregamento
fix/active-frame-dano-duplicado
fix/colisao-borda-tela
fix/stamina-recuperacao-incorreta
```

### Abrindo um Pull Request

1. Faça push da sua branch:
   ```bash
   git push origin feature/nome-da-sua-task
   ```
2. Abra um PR no GitHub apontando para a `develop`
3. Descreva o que foi feito e como testar
4. Marque o outro membro para revisar
5. **Nunca faça merge do próprio PR** — quem abre, não aprova

### Checklist de revisão de PR

Antes de aprovar um PR do colega, verifique:

- [ ] O código compila e roda no Greenfoot sem erros
- [ ] A funcionalidade faz o que a task descrevia
- [ ] Nenhum atributo de `vida` ou `stamina` é acessado diretamente (encapsulamento)
- [ ] A máquina de estados está sendo respeitada
- [ ] Não há código comentado ou arquivos desnecessários
- [ ] O nome da branch segue o padrão `feature/` ou `fix/`

---

## 📋 Tasks do Projeto

> As tasks abaixo devem ser criadas como **Issues** no GitHub e vinculadas ao PR correspondente.

### 🏗️ Fundação (fazer primeiro — em dupla ou um de cada)

| # | Task | Branch sugerida |
|---|---|---|
| 1 | Criar estrutura inicial do projeto no Greenfoot | `feature/setup-inicial` |
| 2 | Implementar classe abstrata `Lutador` com atributos e enum de estados | `feature/classe-lutador-abstrata` |
| 3 | Implementar sistema de animação frame a frame | `feature/sistema-animacao` |

### ⚔️ Mecânicas de Combate

| # | Task | Branch sugerida |
|---|---|---|
| 4 | Implementar sistema de Active Frames | `feature/sistema-active-frames` |
| 5 | Implementar carregamento e disparo do Special Move | `feature/special-move-carregamento` |
| 6 | Implementar HUD com barras de vida e stamina | `feature/hud-barras-vida-stamina` |

### 🧙 Personagens

| # | Task | Branch sugerida |
|---|---|---|
| 7 | Implementar Izalith (Fogo) | `feature/personagem-izalith` |
| 8 | Implementar Ciaran (Água) | `feature/personagem-ciaran` |
| 9 | Implementar Artorias (Escuridão) | `feature/personagem-artorias` |
| 10 | Implementar Ornstein (Trovão) | `feature/personagem-ornstein` |

### 🖥️ Telas e Fluxo

| # | Task | Branch sugerida |
|---|---|---|
| 11 | Implementar tela de seleção de personagens (P1 e P2) | `feature/tela-selecao-personagens` |
| 12 | Implementar tela de seleção de arena | `feature/tela-selecao-arena` |
| 13 | Implementar tela de vitória e retorno ao início | `feature/tela-vitoria` |

### 🎨 Arte e Áudio

| # | Task | Branch sugerida |
|---|---|---|
| 14 | Criar/importar sprites dos personagens (placeholders primeiro) | `feature/sprites-personagens` |
| 15 | Criar/importar backgrounds das 2 arenas | `feature/backgrounds-arenas` |
| 16 | Adicionar efeitos sonoros e música | `feature/audio` |

---

## 📁 Estrutura de Arquivos

```
Arena-Java/
├── images/
│   ├── izalith/
│   │   ├── idle_0.png
│   │   ├── idle_1.png
│   │   └── ...
│   ├── ciaran/
│   ├── artorias/
│   ├── ornstein/
│   └── backgrounds/
├── sounds/
├── Lutador.java
├── Izalith.java
├── Ciaran.java
├── Artorias.java
├── Ornstein.java
├── HUD.java
├── Arena.java
├── TelaSelecao.java
├── TelaArena.java
├── TelaVitoria.java
└── README.md
```

---

## 🎨 Nota sobre Arte (Sprites)

O Greenfoot **não possui suporte nativo a spritesheets**. Cada frame de animação deve ser um arquivo `.png` separado. Organize os arquivos por personagem e por ação:

```
izalith_idle_0.png, izalith_idle_1.png, izalith_idle_2.png
izalith_attack_0.png, izalith_attack_1.png, ...
izalith_hurt_0.png, ...
```

**Dica:** comece com retângulos coloridos como placeholder. Só substitua pela arte final quando a mecânica estiver funcionando.

---

*Projeto desenvolvido para fins acadêmicos — aplicação prática de POO em Java.*
