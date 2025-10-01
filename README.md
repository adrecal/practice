import java.io.*;  
import java.util.*;  

// Classe principal
public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);  // Scanner para ler entradas do usuário
        Usuario usuario = null;               // Variável que vai guardar o usuário logado/cadastrado
        Service service = new Service();      // Classe de serviço que gerencia os eventos
        String arquivo = "eventos.txt";       // Nome do arquivo para salvar eventos

        int op; // opção do menu

        while (true) {  
            // Exibe menu simples
            System.out.println("\n--- MENU ---");
            System.out.println("1 - Cadastrar Usuário");
            System.out.println("2 - Cadastrar Evento");
            System.out.println("3 - Listar Eventos");
            System.out.println("4 - Listar Eventos Atuais");
            System.out.println("5 - Listar Eventos Passados");
            System.out.println("6 - Participar de Evento");
            System.out.println("7 - Cancelar Participação");
            System.out.println("8 - Listar Meus Eventos");
            System.out.println("0 - Sair");
            System.out.print("Opção: ");
            
            op = sc.nextInt();  // Lê a opção digitada
            sc.nextLine();      // Limpa o buffer do Enter

            if (op == 0) break; // Sai do loop se o usuário digitar 0

            switch (op) {  
                case 1:  
                    // Cadastro de usuário
                    System.out.print("Nome: ");  
                    String nome = sc.nextLine();  

                    System.out.print("Email: ");  
                    String email = sc.nextLine();  

                    System.out.print("Cidade: ");  
                    String cidade = sc.nextLine();  

                    usuario = new Usuario(nome, email, cidade);  
                    break;  

                case 2:  
                    // Cadastro de evento
                    System.out.print("Nome do evento: ");  
                    String enome = sc.nextLine();  

                    System.out.print("Endereço: ");  
                    String end = sc.nextLine();  

                    System.out.print("Categoria (FESTA, ESPORTIVO, SHOW, EDUCACAO, OUTROS): ");  
                    Categoria cat = Categoria.valueOf(sc.nextLine().toUpperCase());  

                    System.out.print("Início (dd/MM/yyyy HH:mm): ");  
                    String inicio = sc.nextLine();  

                    System.out.print("Fim (dd/MM/yyyy HH:mm): ");  
                    String fim = sc.nextLine();  

                    System.out.print("Descrição: ");  
                    String desc = sc.nextLine();  

                    service.cadastrarEvento(enome, end, cat, inicio, fim, desc);  
                    break;  

                case 3:  
                    // Lista todos os eventos
                    service.listarEventos();  
                    break;  

                case 4:  
                    // Lista eventos atuais
                    service.listarEventosAtuais();  
                    break;  

                case 5:  
                    // Lista eventos passados
                    service.listarEventosPassados();  
                    break;  

                case 6:  
                    // Participar de um evento
                    System.out.println("Digite o nome do evento: ");  
                    String eventoP = sc.nextLine();  

                    for (Evento e : service.eventos) {  
                        if (e.nome.equalsIgnoreCase(eventoP)) {  
                            e.participantes.add(usuario);  
                            System.out.println("Você está participando de: " + e.nome);  
                        }  
                    }  
                    break;  

                case 7:  
                    // Cancelar participação
                    System.out.println("Digite o nome do evento: ");  
                    String eventoC = sc.nextLine();  

                    for (Evento e : service.eventos) {  
                        e.participantes.removeIf(u -> u.equals(usuario));  
                    }  

                    System.out.println("Participação cancelada se existia.");  
                    break;  

                case 8:  
                    // Listar eventos em que o usuário participa
                    for (Evento e : service.eventos) {  
                        if (e.participantes.contains(usuario)) {  
                            System.out.println(e);  
                        }  
                    }  
                    break;  
            }  

            // Tenta salvar os eventos no arquivo
            try {  
                service.salvarEventos(arquivo);  
            } catch (IOException e) {  
                System.out.println("Erro ao salvar eventos: " + e.getMessage());  
            }  
        }  

        sc.close();  // Fecha o Scanner
    }  
}
