# Guia do desenvolvedor

## Índice
1. [Introdução](#introdução)
2. [Nomes significativos](#nomes-significativos)
    1. [Utilize nomes que revelem seu propósito](#utilize-nomes-que-revelem-seu-propósito)
    2. [Faça distinções significativas](#faça-distinções-significativas)
    3. [Use nomes pronunciáveis](#use-nomes-pronunciáveis)
    4. [Classes e métodos](#classes-e-métodos)
    5. [Contexto significativo](#contexto-significativo)
3. [Funções](#funções)
4. [Comentários](#comentários)
    1. [Bons comentários](#bons-comentários)
    2. [Maus comentários](#maus-comentários)
5. [Formatação](#formatação)
6. [Objetos](#objetos)
7. [Tratamento de erros](#tratamento-de-erros)
8. [Testes unitários](#testes-unitários)
9. [Classes](#classes)
10. [Odores e heurísticas](#odores-e-heurísticas)
11. [Referências](#referências)

---

## Introdução

Sendo uma das linguagens de programação mais utilizadas no desenvolvimento de aplicações, Java possui diversas vantagens, as quais vão desde sua portabilidade até a sua simples sintaxe baseada em C. Tais aspectos fazem com que seu uso seja também difundido no meio acadêmico, sendo uma das principais linguagens para a aprendizagem de orientação a objetos, paradigma presente em diversas aplicações. Tal abrangência da linguagem pode possibilitar um aprendizado nem sempre tão adequado às boas práticas de programação, havendo uma difusão de determinados vícios ao se codificar, dificultando bastante a compreensão do produto final. Por causa disso, é recomendado desenvolver códigos de maneira limpa, de modo a possibilitar maior manutenibilidade do software, afinal, programa-se também para outras pessoas e não apenas para computadores.
Tendo em vista os aspectos anteriormente citados, este guia fornece ao desenvolvedor dicas de como escrever códigos de maneira mais limpa, focando a linguagem Java, tendo como base o livro "Código Limpo", de Robert C. Martin. 

## Nomes significativos

A seguir, serão dadas algumas dicas quanto à nomeação de variáveis, classes e métodos.

### Utilize nomes que revelem seu propósito

O nome de uma variável, função ou classe necessita de responder todas às principais questões de um código, devendo dizer por que existe, o que faz e como é utilizado. Caso este necessite de um comentário para ser explicado, então não é adequado.

``` Java
int a; // área do polígono
```
No exemplo anterior, o nome "a" não revela nada. Por isso, deve ser escolhido um nome que possa especificar seu uso para calcular a área de um polígono:

``` Java
int areaDoPoligono;
```
### Faça distinções significativas

Em algumas ocasiões, pode ser necessário referir-se a duas variáveis diferentes no mesmo escopo. Como estas não podem possuir o mesmo nome, geralmente opta-se por adicionar números ou letras sequenciais em nomes. Ainda que isso não gere confusão, não oferece informações ou dicas sobre a intenção de seu programador.

``` Java
public static void copiarNumeros(int a1[], int a2[]) {
    for (int i = 0; i < a1.length; i++) {
        a2[i] = ai[i];   
    }
}
```

Tal método pode ser lido mais facilmente caso o nome de seus parâmetros sejam "vetorOrigem" e "vetorDestino", por exemplo.

### Use nomes pronunciáveis
```Java
class CerimEm2019 {
       private Date datInYmdhsm;
       private Date datFYmdhsm;
       private int anoCerim = 2019;
}
```
Em um diálogo entre desenvolvedores, soa um tanto incoerente pronunciar os nomes das classes e atributos do exemplo, já que estes são uma junção de abreviações e siglas. Para proporcionar um diálogo inteligível, é preferível utilizar termos existentes do idioma:

```Java
class EmmyAwards {
       private Date dataInicalTimestamp;
       private Date dataFinalTimestamp;
       private int anoCerimonia = 2019;
}
```

### Classes e métodos

Classes e objetos devem ser denominadas com substantivos, propriamente ditos, por exemplo, Estudante, SalaDeAula, AcademyAwards. Palavras genéricas como Gerente, Processador, Dados devem ser evitadas, além de não poderem ser utilizados verbos para nomeá-las.

Em relação aos nomes dos métodos, estes devem conter verbos, como atualizarEstudante, removerSalaDeAula, adicionarDiscente. É preciso nomear métodos de acesso, alteração e autenticação de acordo com seus valores, adicionando prefixos *get*, *set* ou *is*, segundo o padrão *javabean*.

```Java
String nome = estudante.getNome();
turma.setTurma("Técnicas Avançadas de Programação");
if (oscar.isEmpty()) ...
```

## Funções

## Comentários
### Bons comentários
### Maus comentários

## Formatação

## Objetos

## Tratamento de erros

## Testes unitários

## Classes

## Odores e heurísticas

## Referências

MARTIN, Robert C. Código Limpo: Habilidades Práticas do Agile Software. 1ª edição. Rio de Janeiro: Editora Alta Books, 2011.



