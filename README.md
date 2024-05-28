# Sistema-chamada
lista de chamada
import java.util.ArrayList;
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class SistemaChamada {
    // Mapa que associa dias a listas de alunos presentes
    private Map<String, ArrayList<String>> presencas;

    public SistemaChamada() {
        this.presencas = new HashMap<>();
    }

    // Método para adicionar aluno em um dia específico
    public void adicionarPresenca(String dia, String aluno) {
        // Se o dia ainda não existe no mapa, cria uma nova entrada
        this.presencas.putIfAbsent(dia, new ArrayList<>());
        // Adiciona o aluno à lista de presença do dia
        this.presencas.get(dia).add(aluno);
    }

    // Método para exibir a presença de todos os dias
    public void exibirPresencas() {
        for (String dia : this.presencas.keySet()) {
            System.out.println("Dia: " + dia);
            System.out.println("Alunos presentes: " + this.presencas.get(dia));
            System.out.println();
        }
    }

    // Método para exibir o menu e receber a interação do usuário
    public void menu() {
        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.println("Menu:");
            System.out.println("1. Adicionar presença");
            System.out.println("2. Exibir presenças");
            System.out.println("3. Sair");
            System.out.print("Escolha uma opção: ");
            int opcao = scanner.nextInt();
            scanner.nextLine(); // Consumir a nova linha

            switch (opcao) {
                case 1:
                    System.out.print("Informe o dia: ");
                    String dia = scanner.nextLine();
                    System.out.print("Informe o nome do aluno: ");
                    String aluno = scanner.nextLine();
                    adicionarPresenca(dia, aluno);
                    break;
                case 2:
                    exibirPresencas();
                    break;
                case 3:
                    System.out.println("Saindo...");
                    return;
                default:
                    System.out.println("Opção inválida. Tente novamente.");
            }
        }
    }

    public static void main(String[] args) {
        SistemaChamada sistema = new SistemaChamada();
        sistema.menu();
    }
}
