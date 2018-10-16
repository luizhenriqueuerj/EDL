# Trabalho de Estrutura de Linguagens

Alunos: Kleber Luiz Caldas da Silva e Luiz Henrique Inácio da Cruz

# LISP:

## História:

Uma linguagem de programação chamada Lisp (LISt Processor, do inglês) foi desenvolvido para o computador IBM 704, por um grupo de Inteligência Artificial do MIT e John McCarthy, participante desse grupo, elaborou um artigo sobre o LISP.  

A linguagem Lisp nasceu como uma ferramenta matemática, independente de qualquer computador e só posteriormente se procedeu à sua adaptação a uma máquina. Uma vez que em Lisp não existia qualquer dependência, à priori, do processador que iria executar a linguagem, a linguagem também não podia tirar partido das suas potencialidades, sendo as primeiras versões muito ineficientes. 
Esta ineficiência resultava de os programas Lisp serem interpretados, sendo por isso muito mais lentos do que o que uma compilação permite ao reescrever um programa na linguagem do processador. No entanto, com o aparecimento de compiladores eficazes e de um suporte cada vez maior da parte dos processadores, Lisp possui, atualmente, uma eficiência comparável à das restantes linguagens.
Porém, nesse artigo, trataremos do Common Lisp, que é um dialeto do Lisp.
A primeira documentação linguística foi publicada em 1984, com o título de “A linguagem Common Lisp”, porém, o padrão final da linguagem só saiu em 1994, que é utilizada até hoje.

## Classificação:

Common Lisp é uma linguagem dinâmica, cujos programas são constituídos por pequenos módulos, de funcionalidade genérica e que cumprem um objetivo muito simples. 
É a sua combinação que produz um programa completo. Os módulos desenvolvidos em Common Lisp possuem, geralmente, uma funcionalidade que ultrapassa largamente os objetivos para que foram concebidos. 
A não tipificação de dados, a possibilidade de tratar dados e programas de um mesmo modo e a indistinção entre funções definidas pela linguagem e funções definidas pelo programador são algumas das razões da sua flexibilidade.

## Funções de Alta Expressividade:

### Macros:

Macros são usados para definir a extensão que a sintaxe do Lisp oferece. Ou seja, o programador possui a possibilidade de estender e alterar as funcionalidades do Lisp.
Por exemplo, em C, a função switch/case funciona apenas com inteiros e se você desejar usar float ou string, não existe a possibilidade de se criar uma macro em C.
Porém, como uma macro em lisp é, essencialmente, pedaços de código em que o programador insere como um input e retorna como a parte de uma outra macro, você pode “estender” os tipos primitivos que podem ser usados, com o intuito de deixar algum programa mais legível.
Para fazer o mesmo em C, você deveria fazer um pré-processador customizado que ficaria responsável do compilador entender o que você deseja.
Por exemplo, vamos usar uma macro que usa qualquer número e define esse número como sendo igual a 10.

```Lisp
(defmacro setTo10(num)
(setq num 10)(print num))
(setq x 25)
(print x)
(setTo10 x)

Saída:

25
10
```
Ou seja, nessa macro, ele pegou o número 25 (que poderia ser qualquer outro número) e definiu esse número como sendo igual a 10, dentro da sintaxe do Lisp.

### Orientação a objeto:

Como mencionado, Lisp é uma linguagem quer permite o paradigma da OO. Vamos usar, como exemplo, o mesmo programa escrito em duas linguagens diferentes: Lisp e Java.

Em Lisp:

```Lisp
(defclass cubo ()
   ((comprimento :accessor cubo-comprimento)
      (largura :accessor cubo-largura)
      (altura :accessor cubo-altura)
   ))
 

(setf item (make-instance 'cubo))
(setf (cubo-comprimento item) 10)
(setf (cubo-largura item) 10)
(setf (cubo-altura item) 5)


(format t "Comprimento do cubo: ~d~%" (cubo-comprimento item))
(format t "Largura do cubo: ~d~%" (cubo-largura item))
(format t "Altura do cubo: ~d~%" (cubo-altura item))
```
Em Java:
```Java
import java.util*.;

public class Cubo{
    double comprimento;
    double altura;
    double largura;
    public Cubo(double comprimento, double altura, double largura){
        this.comprimento = comprimento;
        this.altura = altura;
        this.largura = largura;
    }
       
    public String getAltura(){
            return this.altura;
    }
    public double getComprimento(){
            return this.comprimento;
    }
    public double getLargura(){
            return this.largura;
    }
    public void setAltura(double EntradaAltura){
        altura = EntradaAltura;
    }
   public void setComprimento(double EntradaComprimento){
        Comprimento = EntradaComprimento;
    }

 public void setLargura(double EntradaLargura){
        largura = EntradaLargura;
    }

public static void main(String[] args){
	Cubo cubo1 = new Cubo();
	cubo1.setAltura(10);
	cubo1.setComprimento(10);
	cubo1.setLargura(5);
	System.out.println(m.getAltura());
System.out.println(m.getComprimento());
System.out.println(m.getLargura());

}
```
Como pode ser visto, a sintaxe do Java exige uma determinada formalidade que o Lisp não exige. Por exemplo, para que os valores do Cubo sejam definidos em Lisp, basta declarar as variáveis da classe e, depois, realizar as devidas alterações necessárias. 
Já em Java, por questões de segurança, eu preciso criar um método para cada variável que se pretende acessar e atribuir algum tipo de valor, fora que, em Lisp, a linguagem se assemelha a ser algo mais natural de se desenvolver, do que Java.
Logo, nesse contexto, Lisp é bem mais expressivo que Java.

### Tipagem:

O Common LIsp tem tipagem forte, pois não permite um mesmo dado ser tratado como se fosse de outro tipo e dinâmica devido a verificação ser feita em cima do dado em si, já que as variáveis podem conter qualquer tipo de dado. Claro que em determinado momento uma variável só pode conter um tipo de dado e isto é verificado. Mas a principal diferença é que a esta verificação é feita em tempo de execução. Isto é feito através de uma infraestrutura auxiliar (uma máquina virtual ou uma biblioteca normalmente chamada de runtime).

Common Lisp fornece uma variedade de tipos de objetos de dados. 
Um tipo de dados é um conjunto (possivelmente infinito) de objetos Lisp. Muitos objetos Lisp pertencem a mais de um conjunto, e por isso nem sempre faz sentido perguntar qual é o tipo de objeto; em vez disso, geralmente é perguntado apenas se um objeto pertence a um determinado tipo. O predicado typep pode ser usado para perguntar se um objeto pertence a um determinado tipo, e a função type-of retorna um tipo ao qual um determinado objeto pertence.

Os tipos de dados definidos no Common Lisp são organizados em uma hierarquia (na verdade, uma ordem parcial) definida pelo relacionamento do subconjunto. Determinados conjuntos de objetos, como o conjunto de números ou o conjunto de cadeias, são interessantes o suficiente para merecer rótulos. Os símbolos são usados ​​para a maioria desses rótulos (aqui, e ao longo deste livro, a palavra "símbolo" refere-se a símbolos atômicos, um tipo de objeto Lisp, conhecido em outros lugares como átomos literais). 

#### Tipos escalares:

Os tipos de números incluem inteiros, ratios, números de ponto flutuante e números complexos. O Common Lisp usa *bignums* para representar valores numéricos de tamanho e precisão arbitrários. O tipo ratio representa exatamente as frações, uma facilidade não disponível em muitas linguagens. O Common Lisp automaticamente força valores numéricos entre esses tipos, conforme apropriado.

O tipo de caractere Common Lisp não está limitado a caracteres ASCII. A maioria das implementações modernas permite caracteres Unicode.

O tipo de símbolo é comum às linguagens Lisp, mas em grande parte desconhecido fora delas. Um símbolo é um objeto de dados único e denominado com várias partes: nome, valor, função, lista de propriedades e pacote. Destes, ***value cell***  e ***function cell*** são os mais importantes. Símbolos em Lisp são frequentemente usados ​​de forma semelhante a identificadores em outras linguagens: para manter o valor de uma variável; no entanto, existem muitos outros usos. Normalmente, quando um símbolo é avaliado, seu valor é retornado. Alguns símbolos são avaliados por si próprios, por exemplo, todos os símbolos no pacote de palavras-chave são autoavaliados. Valores booleanos no Common Lisp são representados pelos símbolos de auto-avaliação T e NIL. O Common Lisp possui namespaces para símbolos, chamados de 'pacotes'.

Diversas funções estão disponíveis para arredondar valores numéricos escalares de várias maneiras. A rodada de função arredonda o argumento para o inteiro mais próximo, com os casos intermediários arredondados para o inteiro par. As funções truncar, andar e teto são arredondadas para zero, para baixo ou para cima, respectivamente. Todas essas funções retornam a parte fracionária descartada como um valor secundário. 

#### Estrutura de dados:

Os tipos de sequência no Common Lisp incluem listas, vetores, vetores de bit e strings. Existem muitas operações que podem funcionar em qualquer tipo de sequência.

Como em quase todos os outros dialetos Lisp, as listas no Common Lisp são compostas de conses, às vezes chamadas de cons cells ou pares. Um contras é uma estrutura de dados com dois slots, chamados seus carros e cdr. Uma lista é uma cadeia de conses vinculada ou a lista vazia. O carro de cada cons refere-se a um membro da lista (possivelmente outra lista). Cada cdr de contras refere-se ao próximo contras - exceto pelos últimos contras de uma lista, cujo cdr se refere ao valor nulo. Conses também podem ser usados ​​facilmente para implementar árvores e outras estruturas de dados complexas; embora geralmente seja aconselhável usar estruturas ou instâncias de classe. Também é possível criar estruturas de dados circulares com conses.

O Common Lisp suporta arrays multidimensionais e pode redimensionar dinamicamente arrays ajustáveis, se necessário. Matrizes multidimensionais podem ser usadas para matemática matricial. Um vetor é um array unidimensional. Matrizes podem transportar qualquer tipo como membros (mesmo tipos mistos na mesma matriz) ou podem ser especializados para conter um tipo específico de membros, como em um vetor de bits. Geralmente apenas alguns tipos são suportados. Muitas implementações podem otimizar as funções de array quando o array usado é especializado em tipos. Dois tipos de array especializados em tipo são padrão: uma string é um vetor de caracteres, enquanto um vetor de bits é um vetor de bits.

- ***Tabela de hash*** armazenam associações entre objetos de dados. Qualquer objeto pode ser usado como chave ou valor. Tabelas de hash são automaticamente redimensionadas conforme necessário.

- ***Pacotes*** são coleções de símbolos, usados ​​principalmente para separar as partes de um programa em namespaces. Um pacote pode exportar alguns símbolos, marcando-os como parte de uma interface pública. Pacotes podem usar outros pacotes.

- ***Estruturas*** (similares em uso a estruturas C e registros Pascal) representam estruturas de dados complexas arbitrárias com qualquer número e tipo de campos (chamados slots). Estruturas permitem herança única.

- ***Classes*** são semelhantes às estruturas, mas oferecem recursos mais dinâmicos e herança múltipla. Classes foram adicionadas tarde ao Common Lisp e há alguma sobreposição conceitual com estruturas. Objetos criados de classes são chamados de instâncias. Um caso especial são funções genéricas. Funções genéricas são funções e instâncias.

## Bibliografia:
1. https://web.archive.org/web/20131004232653/http://www-formal.stanford.edu/jmc/recursive.pdf
2. https://lisp.com.br/
3. https://en.wikipedia.org/wiki/Lisp_(programming_language)
4. https://en.wikipedia.org/wiki/Common_Lisp
5. https://stackoverflow.com/questions/267862/what-makes-lisp-macros-so-special
6. https://www.tutorialspoint.com/lisp/lisp_macros.htm

