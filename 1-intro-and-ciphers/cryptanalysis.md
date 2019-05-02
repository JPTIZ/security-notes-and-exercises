Criptoanálise
=============

Objetivo: recuperar a chave

Ataques:
- Na natureza de um algoritmo (reduzir a complexidade em nº de operações);
- Força bruta (geralmente necessário testar metade das possibilidades até
  acertar).

Tipos de testes de segurança:
- **White Box**: o _tester_ não conhece especificações/implementação interna
  sistema sob teste;
- **Gray Box**: o _tester_ possui conhecimento limitado sobre o sistema;
- **Black Box**: o _tester_ conhece muito bem o sistema sob teste.

### Segurança de um algoritmo de criptografia

Um algoritmo de criptografia pode ser:
- **Incondicionalmente Seguro**:
  > O texto cifrado não contém informações suficientes para determinar o texto
  > de origem.
- **Computacionalmente Seguro**:
  > Computacionalmente complicado de se obter a chave ou o texto original.
- **Computacionalmente Inseguro**:
  > Trivial.
