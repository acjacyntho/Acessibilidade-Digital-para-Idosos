import 'package:flutter/material.dart';

void main() {
  runApp(CentralFacilApp());
}

class CentralFacilApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Central Fácil',
      theme: ThemeData(
        fontFamily: 'Arial',
        textTheme: TextTheme(bodyMedium: TextStyle(fontSize: 20)),
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue),
        useMaterial3: true,
      ),
      home: HomeScreen(),
      debugShowCheckedModeBanner: false,
    );
  }
}

class HomeScreen extends StatelessWidget {
  void _mostrarGuia(BuildContext context, String titulo, String descricao) {
    showDialog(
      context: context,
      builder: (_) => AlertDialog(
        title: Text(titulo),
        content: Text(descricao),
        actions: [
          TextButton(
            child: Text("Entendi"),
            onPressed: () => Navigator.of(context).pop(),
          )
        ],
      ),
    );
  }

  Widget _criarBotao(BuildContext context, String titulo, IconData icone, String descricao) {
    return ElevatedButton.icon(
      icon: Icon(icone, size: 36),
      label: Text(
        titulo,
        style: TextStyle(fontSize: 24),
      ),
      style: ElevatedButton.styleFrom(
        minimumSize: Size(double.infinity, 80),
        padding: EdgeInsets.all(16),
      ),
      onPressed: () => _mostrarGuia(context, titulo, descricao),
    );
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Central Fácil'),
        centerTitle: true,
      ),
      body: Padding(
        padding: EdgeInsets.all(16),
        child: Column(
          children: [
            Text(
              "Escolha o que deseja fazer:",
              style: TextStyle(fontSize: 22),
            ),
            SizedBox(height: 20),
            _criarBotao(
              context,
              'Fazer Chamada de Vídeo',
              Icons.video_call,
              'Vamos te mostrar como fazer uma chamada de vídeo. Passo a passo!',
            ),
            SizedBox(height: 20),
            _criarBotao(
              context,
              'Abrir WhatsApp',
              Icons.message,
              'Você será guiado para enviar mensagens ou fazer ligações.',
            ),
            SizedBox(height: 20),
            _criarBotao(
              context,
              'Consultar Notícias',
              Icons.article,
              'Aprenda a acessar notícias de forma segura.',
            ),
          ],
        ),
      ),
    );
  }
}
