import java.io.*;  
// Importa todas as classes do pacote java.io, usadas para operações de entrada e saída (I/O), como salvar ou ler arquivos.
sc.nextLine();  
// Lê a próxima linha digitada no console (Scanner "sc").  
// Muitas vezes é usado após sc.nextInt() para "limpar" o buffer do Enter.
if (op == 0) break;  
// Se a variável 'op' (opção escolhida no menu) for igual a 0, interrompe o loop (encerra o programa/menu).
switch (op) {  
// Estrutura condicional de múltipla escolha (menu).  
// Verifica o valor de 'op' e executa o bloco correspondente.
switch (op) {  
// Estrutura condicional de múltipla escolha (menu).  
// Verifica o valor de 'op' e executa o bloco correspondente.
case 1:  
System.out.print("Nome: ");  
String nome = sc.nextLine();  
// Pede e lê o nome do usuário.

System.out.print("Email: ");  
String email = sc.nextLine();  
// Pede e lê o e-mail.

System.out.print("Cidade: ");  
String cidade = sc.nextLine();  
 // Pede e lê a cidade.

usuario = new Usuario(nome, email, cidade);  
// Cria um objeto da classe Usuario com os dados informados.

break;  
// Sai do case 1 e volta para o switch.case 2:  
    System.out.print("Nome do evento: ");  
    String enome = sc.nextLine();  
    // Lê o nome do evento.

System.out.print("Endereço: ");  
String end = sc.nextLine();  
// Lê o endereço do evento.

System.out.print("Categoria (FESTA, ESPORTIVO, SHOW, EDUCACAO, OUTROS): ");  
Categoria cat = Categoria.valueOf(sc.nextLine().toUpperCase());  
// Lê a categoria como texto, converte para maiúscula e transforma no Enum Categoria.

System.out.print("Início (dd/MM/yyyy HH:mm): ");  
String inicio = sc.nextLine();  
// Lê a data e hora de início.

System.out.print("Fim (dd/MM/yyyy HH:mm): ");  
String fim = sc.nextLine();  
// Lê a data e hora de término.

 System.out.print("Descrição: ");  
 String desc = sc.nextLine();  
// Lê a descrição do evento.

service.cadastrarEvento(enome, end, cat, inicio, fim, desc);  
// Chama o método de serviço para cadastrar o evento.

break;  case 3:  
    service.listarEventos();  
    // Lista todos os eventos cadastrados.  
    break;
    case 4:  
    service.listarEventosAtuais();  
    // Lista somente os eventos que ainda estão acontecendo.  
    break;
    case 5:  
    service.listarEventosPassados();  
    // Lista apenas os eventos que já terminaram.  
    break;
case 6:  
    System.out.println("Digite o nome do evento: ");  
    String eventoP = sc.nextLine();  
    // Pede o nome do evento que o usuário quer participar.

for (Evento e : service.eventos) {  
        // Percorre todos os eventos cadastrados.

if (e.nome.equalsIgnoreCase(eventoP)) {  
            // Se o nome do evento for igual ao digitado (ignora maiúsculas/minúsculas):

e.participantes.add(usuario);  
// Adiciona o usuário na lista de participantes do evento.

System.out.println("Você está participando de: " + e.nome);  
            // Informa que a participação foi confirmada.
        }  
    }  
    break;
case 7:  
    System.out.println("Digite o nome do evento: ");  
    String eventoC = sc.nextLine();  
    // Pede o nome do evento para cancelar a participação.

for (Evento e : service.eventos) {  
        // Percorre todos os eventos.

e.participantes.removeIf(u -> u.equals(usuario));  
        // Remove o usuário da lista de participantes (se ele estiver lá).
    }  

 System.out.println("Participação cancelada se existia.");  
    // Informa que a remoção foi feita (ou já não existia).  
    break;
    case 8:  
    for (Evento e : service.eventos) {  
        // Percorre todos os eventos.

if (e.participantes.contains(usuario)) {  
            // Verifica se o usuário está na lista de participantes.

System.out.println(e);  
            // Imprime as informações do evento (toString() da classe Evento).
        }  
    }  
    break;

try {  
service.salvarEventos(arquivo);  
    // Tenta salvar todos os eventos em um arquivo.

} catch (IOException e) {  
    System.out.println("Erro ao salvar eventos: " + e.getMessage());  
    // Caso ocorra erro de I/O (arquivo), mostra a mensagem de erro.
}
}  
sc.close();  
// Fecha o objeto Scanner para liberar os recursos.

}  
}  
// Fecha os blocos do while, switch, ou da classe principal.







