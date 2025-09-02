import java.io.*;
sc.nextLine();
if (op == 0) break;
switch (op) {
case 1:
System.out.print("Nome: ");
String nome = sc.nextLine();
System.out.print("Email: ");
String email = sc.nextLine();
System.out.print("Cidade: ");
String cidade = sc.nextLine();
usuario = new Usuario(nome, email, cidade);
break;
case 2:
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
service.listarEventos();
break;
case 4:
service.listarEventosAtuais();
break;
case 5:
service.listarEventosPassados();
break;
case 6:
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
System.out.println("Digite o nome do evento: ");
String eventoC = sc.nextLine();
for (Evento e : service.eventos) {
e.participantes.removeIf(u -> u.equals(usuario));
}
System.out.println("Participação cancelada se existia.");
break;
case 8:
for (Evento e : service.eventos) {
if (e.participantes.contains(usuario)) {
System.out.println(e);
}
}
break;
}
try {
service.salvarEventos(arquivo);
} catch (IOException e) {
System.out.println("Erro ao salvar eventos: " + e.getMessage());
}
}
sc.close();
}
}
