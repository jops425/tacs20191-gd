# Guia do desenvolvedor

## Índice
1. [Introdução](#introdução)
2. [Nomes significativos](#nomes-significativos)
    1. [Utilize nomes que revelem seu propósito](#utilize-nomes-que-revelem-seu-propósito)
    2. [Faça distinções significativas](#faça-distinções-significativas)
    3. [Use nomes pronunciáveis](#use-nomes-pronunciáveis)
    4. [Classes e métodos](#classes-e-métodos)
3. [Funções](#funções)
    1. [Tamanho](#tamanho)
    2. [Objetivo](#objetivo)
    3. [Parâmetros](#parâmetros)
4. [Comentários](#comentários)
    1. [Bons comentários](#bons-comentários)
    2. [Maus comentários](#maus-comentários)
5. [Formatação](#formatação)
    1. [Espaçamento vertical entre conceitos](#espaçamento-vertical-entre-conceitos)
    2. [Ordenação vertical](#ordenação-vertical)
    3. [Formatação horizontal](#formatação-horizontal)
6. [Objetos](#objetos)
7. [Classes](#classes)
8. [Referências](#referências)

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

Serão comentados, a seguir, os principais pontos aos se considerar funções no código.

### Tamanho

A primeira regra sobre funções é que elas devem ser pequenas. Como exemplo, segue uma função que calcula, dentre dois números, o maior destes.

```Java
public static int obtemMaiorNumero(int valorInicial, int valorFinal) {
    if (valorInicial > valorFinal)
        return valorInicial;
    return valorFinal;
}
```

### Objetivo

As funções devem possuir um único objetivo, ou seja, elas devem realizar apenas uma tarefa. O exemplo a seguir mostra uma função que realiza diversas tarefas.

```Java
public static int verificaNumero(int valorInicial, int valorFinal, int[] vetor) {
    int maiorValor, quantidadeDeOcorrencias = 0;
    if (valorInicial > valorFinal) {
        maiorValor = valorInicial;
    } else {
        maiorValor = valorFinal;
    }
    for (int i = 0; i < vetor.length; i++) {
        if (vetor[i] == maiorValor) {
            quantidadeDeOcorrencias++;
        }
    }
    return quantidadeDeOcorrencias;
}
```
A partir disso, observe que o método mostrado pode ser dividido em dois outros:

```Java
public static int obtemMaiorNumero(int valorInicial, int valorFinal) {
    if (valorInicial > valorFinal)
        return valorInicial;
    return valorFinal;
}

public static int verificaOcorrenciaPorVetor(int numero, int[] vetor) {
    int quantidadeDeOcorrencias = 0;
    for (int i = 0; i < vetor.length; i++)
        if (vetor[i] == numero)
            quantidadeDeOcorrencias++;
    return quantidadeDeOcorrencias;
}
```

### Parâmetros

A quantidade ideal de parâmetros em uma função é zero, e a máxima são dois. Deve-se evitar, sempre que possível, o uso de três ou mais parâmetros. Isso porque eles podem requerer determinados conceitos.

```Java
public static void verificaNumero(Scanner scanner, int valorExistente) {
    System.out.println("Entre com um valor: ");
    int valorLido = scanner.nextInt();
    if (valorLido > valorExistente) {
        System.out.println("Valor lido é maior que o existente");
    } else {
        System.out.println("Valor lido é menor que o existente");
    }
}
```

No exemplo, como o parâmetro *scanner* não foi declarado e instanciado dentro do próprio método, os leitores do método podem ter que interpretá-lo toda vez que acessarem a função.

Por outro lado, uma grande quantidade de parâmetros pode tornar mais complexa a atividade de testes. Pode haver maior dificuldade ao se escrever todos os casos de teste para se certificar de que as diversas combinações de parâmetros funcionem adequadamente. 

## Comentários

A verdade é que, se as linguagens de programação fossem expressivas o suficiente ou se os desenvolvedores as manipulassem com eficácia para expressar suas reais intenções, não se precisaria de muitos comentários, provavelmente nenhum. 
A seguir, alguns exemplos de bons e maus comentários:

### Bons comentários

#### Comentário TODO

```Java
public static void gerarArquivoHtml() {
    // TODO Finalizar função. 
}
```

#### Javadocs em APIs públicas

```Java
/**
 * Retorna o número correspondente a um dia da semana, de 0 a 6, a partir de uma data.
 * 
 * @param data Uma data no formato yyyy-mm-dd.
 * @return O dia da semana correspondente à data, de 0 a 6, ou -1 em casos inválidos.
 */
public int calculaNumeroDiaDaSemana(int data) ...
```

### Maus comentários

#### Comentários redundantes

```Java
// Método recebe um número, o qual é dividido por 2. Caso o resto for zero, a função
// retorna true, caso contrário, retorna falso.
public static boolean verificaNumeroPar(int numero) {
    if (numero % 2 == 0)
        return true;
    return false;
}
```

#### Comentários ruidosos

```Java

public class AcademyAwards() {
    
    // Construtor padrão
    protected AcademyAWards() {
    }
    
}

```

## Formatação

A formatação de um código é bastante importante. Ela serve como uma comunicação, devendo ser até mesmo a primeira regra em detrimento a "fazer o código funcionar". Isso deve ser considerado, pois a funcionalidade criada tem grandes chances de ser alterada posteriormente, mas a legibilidade, através da formatação, persistirá, tendo efeito em todas as mudanças posteriores.

### Espaçamento vertical entre conceitos

Para que haja uma boa legibilidade no código, é necessário haver espaçamento entre declarações de pacote, importações e métodos, como no exemplo a seguir:

```Java
package br.ufg.inf.es.awards;

import br.ufg.inf.es.person.Actor;
import java.util.List;

public class AcademyAwards {

    private int year;
    
    private String localCeremony;
    
    public int getYear() {
        return this.year;
    }
    
    public void setYear(int year) {
        this.year = year;
    } 

}
```

Retirando-se os espaçamentos, durante uma leitura, os olhos só parariam após o término do código, o que prejudicaria bastante a legibilidade.

```Java
package br.ufg.inf.es.awards;
import br.ufg.inf.es.person.Actor;
import java.util.List;
public class AcademyAwards {
    private int year;
    private String localCeremony;
    public int getYear() {
        return this.year;
    }
    public void setYear(int year) {
        this.year = year;
    } 
}
```

### Ordenação vertical

Em geral, é desejável que as chamadas das dependências da função apontem para baixo. Ou seja, métodos chamados devem localizar-se abaixo daquele que os chamou. Isso cria um fluxo natural para baixo no módulo do código-fonte, de um nível maior para o menor. 

### Formatação horizontal

É recomendado haver um esforço para se manter as linhas de código não muito extensas, mantendo o limite de 120 caracteres. Em algumas ocasiões, as próprias IDEs possuem mecanismos delimitadores, mostrando quando determinado limite foi atingido e/ou ultrapassado.

## Objetos

## Classes

## Referências

MARTIN, Robert C. Código Limpo: Habilidades Práticas do Agile Software. 1ª edição. Rio de Janeiro: Editora Alta Books, 2011.



