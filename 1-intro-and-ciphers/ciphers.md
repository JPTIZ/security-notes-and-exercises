Cifradores
==========

Cifrador de César
-----------------

Trivial: apenas se aplica o deslicamento de letras. Por exemplo:

| Texto original | Deslocamento | Texto cifrado |
|----------------|--------------|---------------|
| CRIPTOGRAFIA   | 3            | FULSWRJUDILD  |

Implementação:
[Exemplo](https://github.com/JPTIZ/ciphers-sec/blob/master/ciphers/caesar.py)

Cifrador Monoalfabético
-----------------------

Também trivial: apenas um mapeamento Alfabeto -> Alfabeto.

Exemplo: [Ver teste de
implementação](https://github.com/JPTIZ/ciphers-sec/blob/master/tests/test_answers.py#L22)

Playfair
--------

Utiliza uma matriz 5x5 para cifrar um texto.

[Ver
Implementação](https://github.com/JPTIZ/ciphers-sec/blob/master/ciphers/playfair.py).

### Gerando a matriz

1. Considere que I e J são a mesma letra;
2. Escolha uma palavra secreta;
3. Escreva-a elimininando duplicatas;
4. Complete as letras restantes do alfabeto;
5. Trate o resultado disso como uma matriz 5x5.

Exemplo:

2. **Chave inicial**: TESTE
3. Chave sem duplicatas: TES
4. Chave completando o alfabeto: **TES**ABCDFGHIKLMNOPQRUVWXYZ
5. Matriz:

|   | 1 | 2 | 3 | 4 | 5 |
|---|---|---|---|---|---|
| 1 | T | E | S | A | B |
| 2 | C | D | F | G | H |
| 3 | I | K | L | M | N |
| 4 | O | P | Q | R | U |
| 5 | V | W | X | Y | Z |

### Cifrando um texto

- Para cada par de caracteres da entrada:
    - Se o par contém **os mesmos caracteres** (ex: "XX", "AA"),
      coloque um caractere com um caractere de "filtro" (ex: "X") entre eles
      (perceba que isso altera como os pares seguintes estarão formados);
    - Se na matriz 5x5 os dois caracteres do par **estão na mesma linha**, se
      utiliza o caractere **à direita** de cada um. Por exemplo, para o par
      "EA" com a matriz formada pela chave "TESTE", o resultado será "SB" ("S"
      está à direita de "E" e "B" está à direita de "A"). Se passar da coluna
      5, volta para a coluna 1.;
    - Se na matriz 5x5 os dois caracteres do par **estão na mesma coluna**, se
      utiliza o caractere **abaixo** de cada um (mesma ideia de se fossem na
      mesma linha: para "ED", o resultado seria "DK").
    - Em qualquer outro caso, cada caractere é substituído pelo que está na
      **mesma linha dele** na matriz 5x5, porém **na coluna do outro**
      caractere do par. Por exemplo: para "TF", "T" está na linha e coluna 1,
      enquanto "F" está na linha 2 e coluna 3. Assim, "T" é substituído por
      quem está na linha 1 (mesma linha de "T") e coluna 3 (que é a coluna de
      "F") - ou seja, "T" vira "S", que está na linha 1 e coluna 3. Enquanto
      isso, "F" é substituído por "C".


Exemplo: crifrando o texto "balloon" com a matriz gerada por "TESTE":
- Par "ba":
  - Estão na mesma linha: substitui-se por "TB".
- Par "ll":
  - Duplicado, logo se coloca "x" entre os dois;
  - Par fica "lx";
  - Estão na mesma coluna: substitui-se por "QS";
- Par "lo" (perceba que o "L" que sobrou do par anterior ao adicionar o "X"
  veio para o par seguinte, então é como se estivéssemos analisando a palavra
  "balxloon"):
  - Estão em linha e coluna diferentes: substitui-se por "IQ";
- Par "on":
  - Estão em linha e coluna diferentes: substitui-se por "UI";
- Fim da entrada.

**Resultado: "TBQSIQUI".**
