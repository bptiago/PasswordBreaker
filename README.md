# PasswordBreaker

Este algoritmo em Java faz a quebra de hashes SHA-256 e MD5 sem sal (unsalted) via força bruta. Nesse sentido, são checadas todas as combinações de caracteres possíveis dentro de um tamanho de senha prederteminado.

> <b>Esse programa foi desenvolvido exclusivamente para fins educacionais!</b>

## Funcionalidades
Isso é um programa de linha de comando, então é necessário executar o Main.java e seguir as instruções de input para seu funcionamento.

O programa oferece as seguintes operações:

1. **Linha de comando**: A navegação dentro do programa é feita pelo terminal/linha de comando.
2. **Opção de hash**: Permite escolher para input hashes de tipo SHA-256 ou MD5.
3. **Senha**: Retorna a senha descoberta após a quebra de hash

### Função delimitadora de tamanho de senha
Para alterar o tamanho de senha processada, basta mexer no valor limit da função abaixo em `BruteForce.java`.

```java
public void forceHash(String hash) {
        long initTime = System.currentTimeMillis();
        int limit = 4;

        // Limitar em {limit} número de chars por senha
        for (int size = 1; size <= limit; size++) {
            if (findPasswordsBySize(size, hash)) {
                break;
            }

            if (size == limit) {
                String str = String.format("Algoritmo falhou. É possível que a senha não tenha sido encontrada ou que ela seja maior que %d letras.", size);
                System.out.println(str);
                return;
            }
        }

        double timeElapsed = (double) (System.currentTimeMillis() - initTime) / 1000;
        String str = String.format("O algoritmo executou por %.2f segundos.", timeElapsed);
        System.out.println(str);
    }
```
