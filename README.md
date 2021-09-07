## Princípio da Responsabilidade Única
<p align="justify"> Nome: Linneu Augusto Mendo Zanco - 769155 </br>
Nome: Julio Cesar dos Santos Oliveira Filho - 779800
 </p>
 
## Introdução
<p align="justify"> O Princípio da Responsabilidade Única (SRP - Single Responsibility Principle) é um dos 5 princípios SOLID da programação orientada a objetos. 
Nesse artigo será discutido o significado do SRP e estratégias para implementá-lo em projetos de programação orientada a objetos. 
Serão discutidos também exemplos de um programa construído sem a utilização do princípio e as alterações necessárias nas classes desse programa para que ele esteja adequado ao SRP.
</p>

## Conceito
<p align="justify"> O Princípio da Responsabilidade Única diz que, em programação orientada a objetos, uma classe deve ter apenas uma única razão para mudar. Isso significa que cada classe deve possuir apenas uma tarefa, uma especialidade.
	A importância do SRP se deve ao chamado “acoplamento”. Quando as classes em um programa não são especializadas, diz-se que elas possuem um alto acoplamento. Isso significa que os métodos dessa classe podem ser altamente dependentes entre si, o que pode trazer dificuldades nos momentos de realizar alterações à classe. Realizar mudanças no código de classes altamente acopladas pode trazer diversos resultados inesperados, já que diferentes métodos da classe podem estar utilizando do mesmo atributo ou serem dependentes um do outro.
	O SRP é importante também para manter a coesão em códigos de programação. A coesão é definida como a afinidade funcional entre os elementos de um módulo, ou seja, é a relação que os métodos de uma classe possuem entre si. Para mantermos um código coeso, é necessário que cada classe não realize as responsabilidades que não são suas. Assim, podemos manter a simplicidade do nosso código e facilitar seu entendimento, além de tornar mais fácil encontrar e resolver erros.
</p>

## Aplicação
No exemplo 1 podemos ver o código para um sistema de biblioteca:


~~~C++
struct livro {
  emprestimo = 0; </br>
  ...
} Livro;

public class Biblioteca {
    public void emprestar_livro(Livro livro){
          livro.emprestimo = 1; #Livro emprestado
    }
    
    public void devolver_livro(Livro livro){
          livro.emprestimo = 0; #Livro devolvido
    }
    
    public void imprimir_livros(Livro livro){
          printf("%s", livro.dados);
    }
}
~~~

<p align="center">Exemplo 1</p></br>
<p align="justify">No código desse sistema temos uma única classe “Biblioteca” com três métodos. O primeiro método, “emprestar_livro”, realiza um empréstimo, alterando os atributos do livro para indicar que ele foi emprestado. No método “devolver_livro” vemos o comportamento oposto, ele altera o valor do atributo “emprestimo” para indicar que o cliente devolveu um livro que havia sido emprestado. O último método, “imprimir_livros”, imprime os dados de um livro.
	Podemos ver que esse programa não segue o conceito do SRP. Os métodos da classe “Biblioteca” possuem responsabilidades diferentes. Enquanto os dois primeiros métodos são responsáveis pela retirada e manipulação de livros na biblioteca, o último método é responsável por mostrar as informações de um livro.
	Para manter a coesão de nosso código e diminuir o acoplamento, podemos dividir essa classe em duas novas classes diferentes, cada uma assumindo uma das responsabilidades descritas previamente. Podemos ver isso no exemplo 2.
</p></br></br>

~~~C++
struct livro {
  emprestimo = 0;
  ...
} Livro;

public class Imprimir {
    public void imprimir_livros(Livro livro){
          printf("%s", livro.dados);
    }
    
 }
 
 public class Manuseio_livro {
    public void devolver_livro(Livro livro){
          livro.emprestimo = 0; #Livro devolvido
    }
    
    public void emprestar_livro(Livro livro){
          livro.mprestimo = 1; #Livro emprestado
    }
 }
~~~
<p align="center">Exemplo 2</p></br>
<p align="justify">Agora temos duas classes. A classe “Imprimir” manteve o método “imprimir_livros”, ela se torna assim unicamente responsável por exibir os dados do livro cadastrado. Já a classe “Manuseio_livro” adotou os métodos “devolver_livro” e “emprestar_livro”, sendo então responsável por realizar a retirada e manuseio dos livros da biblioteca. Dessa forma o código se tornou mais coeso e de fácil manutenção. Ao realizar alteração nos métodos de empréstimo, por exemplo, já não temos mais que nos preocupar em afetar a função de imprimir.
	É importante notar que os métodos para emprestar e devolver livros são diferentes, porém realizam a mesma função. Assim, ao se aplicar o SRP, ambos os métodos pertencem à mesma classe. Isso deve ser frisado, pois um erro comum é se confundir nas responsabilidades de cada método. Muitas vezes isso leva à implementação errada do conceito, criando códigos com classes que deveriam estar juntas, pois são utilizadas em conjunto, possuem a mesma função ou são altamente coesas. 
</p>

## Conclusão
<p align="justify">O Princípio da Responsabilidade Única é um importante método para manter um programa enxuto e de fácil manutenção. Apesar de ser um conceito simples, é importante se atentar à coesão para não realizar alterações erradas. Devemos pensar maneira simples para garantir que não estamos fazendo alterações desnecessárias.
</p>
</br></br>

## Referências
<p align="justify">
Robert Martin, Micah Martin, Princípios, Padrões e Práticas Ágeis em C#,  Bookman Editora, 2009.
</p>
