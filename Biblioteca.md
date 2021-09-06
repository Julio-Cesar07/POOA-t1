struct livro {
  emprestimo = 0;
  ...
}Livro;

public class Biblioteca {
    public void emprestar_livro(Livro livro){
          livro.mprestimo = 1; #Livro emprestado
    }
    
    public void devolver_livro(Livro livro){
          livro.emprestimo = 0; #Livro devolvido
    }
    
    public void imprimir_livros(Livro livro){
          printf("%s", livro.dados);
    }
}
