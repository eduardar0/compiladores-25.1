# 📚 Resumo — Compiladores 1: Interpretadores e Compiladores com Brainfuck

## 🧠 O que é Brainfuck?

Brainfuck é uma linguagem esotérica minimalista com apenas **8 comandos**. Opera sobre um vetor de memória (como uma fita de Turing).

### Comandos:

| Comando | Função                               |
|---------|---------------------------------------|
| `>`     | Move o ponteiro para a direita        |
| `<`     | Move o ponteiro para a esquerda       |
| `+`     | Incrementa o valor da célula atual    |
| `-`     | Decrementa o valor da célula atual    |
| `.`     | Imprime o caractere da célula atual   |
| `,`     | Lê um caractere do input              |
| `[`     | Início de um loop (while)             |
| `]`     | Fim de um loop                        |

---

## 🧪 Interpretador (em Python)

### 🛠️ O que é?

Um **interpretador** executa diretamente o código-fonte, linha por linha, **sem gerar código intermediário**.

### 📌 Funcionamento:

- Classe `BF` com:
  - Vetor de memória: `self.memory = [0] * 10_000`
  - Ponteiro: `self.index = 0`
- Método `run(src)` interpreta cada caractere do código:
  - `+`, `-`, `<`, `>`: manipulação de memória e ponteiro
  - `.`, `,`: entrada e saída (com `click.getchar()`)
  - `[`, `]`: **loops recursivos** (executa bloco enquanto a célula for diferente de zero)

### ⚠️ Pontos importantes:

- Proteção contra `IndexError` ao mover para a esquerda
- Uso de `ord()` e `chr()` para entrada e saída de caracteres
- Lógica recursiva para interpretar loops

### ✅ O que pode cair na prova:

- Diferença entre interpretador e compilador
- Execução do loop com `[` e `]`
- Execução de comandos de I/O
- Simular a execução de um código Brainfuck

---

## 🧾 Compilador (Brainfuck → C)

### 🛠️ O que é?

Um **compilador** traduz o código-fonte para outra linguagem (neste caso, C), gerando **código intermediário**.

### 📌 Funcionamento:

- Template C inicial:
  ```c
  char memory[10000];
  int index = 0;
