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
<p align="justify">Aplicação
	No exemplo 1 podemos ver o código para um sistema de biblioteca:
</p>

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



~~~~C++
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
