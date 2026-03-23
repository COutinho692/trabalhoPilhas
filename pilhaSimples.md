public class Main {
    public static void main(String[] args) {
        
        PilhaSimples pilhaSimples = new PilhaSimples(6);

        pilhaSimples.adicionarElementoPilha("pedro");
        pilhaSimples.adicionarElementoPilha("joao");
        pilhaSimples.adicionarElementoPilha("iane");
        pilhaSimples.adicionarElementoPilha("yasmin");
        pilhaSimples.adicionarElementoPilha("isa");
        pilhaSimples.exibirPilha();
        pilhaSimples.excluirElemento("iane");
        pilhaSimples.exibirPilha();
        pilhaSimples.alterarElementoPilha("joao","karol");
        pilhaSimples.quantidadeElementos();
        pilhaSimples.exibirPilha();
        
    }
}

public class PilhaSimples{
    String[] pilha;

    public PilhaSimples(int tamanho) {
        this.pilha = new String[tamanho];
    }

    public void exibirPilha() {
        for (int i = this.pilha.length - 1; i >= 0; i--) {
            if (this.pilha[i] != null) {
                System.out.println("Pilha[" + i + "] = " + this.pilha[i]);
            }
        }
    }

    public void adicionarElementoPilha(String elemento) {
        if (!pilhaCheia()) {
            this.pilha[posicaoVaziaPilha()] = elemento;
            System.out.println("Elemento " + elemento + " adicionado com sucesso!");
        }
    }


    private boolean pilhaCheia() {
        for (int i = 0; i < this.pilha.length; i++) {
            if (this.pilha[i] == null) {
                return false;
            }
        }
        System.out.println("A lista está cheia!");
        return true;
    }

    private boolean pilhaVazia() {
        for (int i = 0; i < this.pilha.length; i++) {
            if (this.pilha[i] != null) {
                return false;
            }
        }
        System.out.println("A lista está vazia!");
        return true;
    }

    private int posicaoVaziaPilha() {
        int i;
        for (i = 0; i < this.pilha.length; i++) {
            if (this.pilha[i] == null) {
                return i;
            }
        }
        return i;
    }

    public void excluirElemento(String elemento) {
        if (!pilhaVazia()) {
            if (this.buscarElementoPilha(elemento) >= 0) {
                this.pilha[this.buscarElementoPilha(elemento)] = null;
                System.out.println("Elemento " + elemento + " removido com sucesso!");
            }
        }
    }

    public int buscarElementoPilha(String elemento){
        int i;
        if (!pilhaVazia()) {
            for (i = 0; i < this.pilha.length; i++) {
                if (this.pilha[i].equals(elemento)) {
                    return i;
                }
            }
        }
        System.out.println("Elemento não encontrado na pilha.");
        return -1;
    }

    public void alterarElementoPilha(String elementoASerAlterado, String alteracao) {
        if(buscarElementoPilha(elementoASerAlterado) >= 0) {
            this.pilha[buscarElementoPilha(elementoASerAlterado)] = alteracao;
            System.out.println("Elemento " + elementoASerAlterado + " alterado com sucesso para " + alteracao);
        }
    }

    public void quantidadeElementos() {
        int cont = 0;
        if(!pilhaVazia()) {
            for (int i = 0; i < this.pilha.length; i++) {
                if(this.pilha[i] != null) {
                    cont++;
                }
            }
        }
        System.out.println("A lista possui " + cont + " elementos!");
    }
}
