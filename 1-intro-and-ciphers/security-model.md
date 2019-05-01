Modelo de Segurança
-------------------

Anotações sobre [Aula 1 do MIT](https://www.youtube.com/watch?v=GqmQg-cszw4)
----------------------------------------------------------------------------

Segurança é sobre ter um objetivo contra um adversário.

Quanto a segurança, um sistema possui:

- **Política**: Confidencialidade, integridade e disponibilidade;
  > Envolve questões como: como funciona a recuperação de senha? Quem tem
  > acesso a determinados dados?
- **Modelo de Ameaça**: Hipóteses sobre o adversário;
  > Exemplo de modelos ruins: fatores humanos e temporais (e.g. utilizar
  > 56 bits para o DES em 1980 era OK, mas hoje em dia não).
- **Mecanismo**: Software, Hardware, Sistema Operacional, ...;
  > Exemplo de mecanismo ruim: o i-Cloud da Apple não limitava o nº de
  > tentativas de login em um de seus módulos.

Anotações das aulas da disciplina
---------------------------------

### Hierarquia de Insegurança

- **Nível 2 - Fraqueza**:
  Predisposição do sistema a falhas.
- **Nível 1 - Vulnerabilidade**:
  A falha em si.
- **Nível 0 - "Assault"**:
  O ataque em si.

### Avaliando um sistema

Quando se avaliar um sistema no quesito segurança, deve-se levar em conta:
1. **Ativos**
   > O que se tem a perder (ou o que deve permanecer escondido).
2. **Adversários**
   > Quem tem interesse nos ativos do sistema.
3. **Gerenciamento de Risco**
   > Quais características do sistema o predispõe a quais falhas? Por exemplo:
   > um sistema com bibliotecas não atualizadas está predisposto às falhas de
   > segurança que não foram corrigidas nas atualizações.
4. **Contra-medidas**
   > Como prevenir um ataque? Por exemplo: em um sistema web, as entradas devem
   > ser [sanitizadas](https://en.wikipedia.org/wiki/HTML_sanitization).
5. **Custo/Benefício**
   > Quanto custa para um atacante realizar um ataque em relação a o que ele
   > consegue tendo um ataque bem sucedido?

### Defesas

Formas de defesa podem incluir:
- **Componentes Seguros**
  > e.g. _Trusted Platform Module_, um componente de hardware específico para
  > gerar/guardar chaves. Assim, se o software precisa proteger uma chave de
  > integridade dele próprio, ele guarda no TPM, e não no mesmo disco do
  > software (que, passadas as barreiras do SO e do software, podem ser lidos
  > por qualquer um com acesso ao disco).
- **Complexidade**
  > Seguro geralmente é simples: elevar a complexidade eleva a possibilidade de
  > falhas (políticas muito complexas, por exemplo, possuem muitas regras para
  > se prestar atenção, logo é mais fácil de encontrar falhas em alguma delas -
  > ou mesmo de criar uma falha sem querer durante a implementação delas).
