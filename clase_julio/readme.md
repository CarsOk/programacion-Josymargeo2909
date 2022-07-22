# Taller api

import 'dart:convert';

import 'package:flutter/material.dart';
import 'package:taller2/Aprendiz.dart';
import 'package:taller2/contenedor.dart';
import 'package:http/http.dart' as http;

void main() {
  runApp(Sena());
}

class Sena extends StatelessWidget{
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'ADSI',
      home: Scaffold(
        backgroundColor: Colors.orange,
        body: FutureBuilder(
          future: getusuario(),
          builder: (BuildContext context, AsyncSnapshot<Aprendiz> snapshot) {
            print(snapshot.data);
            if (snapshot.connectionState == ConnectionState.waiting){
              return CircularProgressIndicator();
            }           
            else {             
              return  Contenedor(snapshot.data!.data);
            }
          },
        ),
      ),
    );
  }
}

Future<Aprendiz> getusuario() async {
  final url =  Uri.parse('https://reqres.in/api/users?page');
  final respuesta = await http.get(url);
  //print(respuesta.body);
  final dato = jsonDecode(respuesta.body);
  //print(dato['data']);
  return Aprendiz.fromJson(dato);
}




import 'dart:convert';

// To parse this JSON data, do
//
//     final aprendiz = aprendizFromJson(jsonString);

import 'dart:convert';


class Aprendiz {
    Aprendiz({
      required  this.page,
      required  this.perPage,
      required  this.total,
      required  this.totalPages,
      required  this.data,
      required  this.support,
    });

    int page;
    int perPage;
    int total;
    int totalPages;
    List<Estudio> data;
    Support support;

    factory Aprendiz.fromJson(Map<String, dynamic> json) => Aprendiz(
        page: json["page"],
        perPage: json["per_page"],
        total: json["total"],
        totalPages: json["total_pages"],
        data: List<Estudio>.from(json["data"].map((x) => Estudio.fromJson(x))),
        support: Support.fromJson(json["support"]),
    );

   
}

class Estudio {
    Estudio({
      required  this.id,
      required  this.email,
      required  this.firstName,
      required  this.lastName,
      required  this.avatar,
    });

    int id;
    String email;
    String firstName;
    String lastName;
    String avatar;

    factory Estudio.fromJson(Map<String, dynamic> json) => Estudio(
        id: json["id"],
        email: json["email"],
        firstName: json["first_name"],
        lastName: json["last_name"],
        avatar: json["avatar"],
    );

    Map<String, dynamic> toJson() => {
        "id": id,
        "email": email,
        "first_name": firstName,
        "last_name": lastName,
        "avatar": avatar,
    };
}

class Support {
    Support({
       required this.url,
       required this.text,
    });

    String url;
    String text;

    factory Support.fromJson(Map<String, dynamic> json) => Support(
        url: json["url"],
        text: json["text"],
    );

    
}


import 'package:flutter/material.dart';
import 'package:taller2/Aprendiz.dart';

class Contenedor extends StatelessWidget{
  
  final List<Estudio> usuarios;
  

  const Contenedor(
     this.usuarios,
    );

 List<Widget> Listusuarios(){
    List<Widget> estudiantes = [];

    for (var usuario in usuarios) {
      estudiantes.add(
        Column(
          children: [
            Row(
              mainAxisAlignment: MainAxisAlignment.spaceAround,
              children: [
                Container(
                  width: 300,
                  child: Column(
                  children: [
                    Text(usuario.firstName),
                    Text(usuario.email),
                  ],
                )),
                
                Row(
                  children: [
                    Container(child: CircleAvatar(backgroundImage: NetworkImage(usuario.avatar),),),
                  ],
                ),               
              ],
            ),
            
          ],
        ),
      );
    }
    return estudiantes;
  }

  @override
  Widget build(BuildContext context) {
    return Stack(
      children: [
            Positioned(
              top: 0,
              bottom: 450,
              child: 
                Container(
                  color: Colors.cyan,
                  width: 800,
                  height: 400,
                ) ),
            Positioned(
              top: 250,
              bottom: 250,
              left: 20,
              child: 
              Container(               
                width: 450,
                height: 100,
                margin: EdgeInsets.all(10),
                decoration: BoxDecoration(
                  color: Color.fromARGB(255, 84, 86, 98),
                  borderRadius: BorderRadius.all(Radius.circular(20.0)),
                  border: Border.all(color: Colors.black26, width: 10.0),
                ), 
                    child: ListView(
                      children: Listusuarios(),
                    )
                               
              )
            ),
            Positioned(
              top: 700,
              bottom: 100,
              child: 
                Container(
                  width: 500,
                  height: 100,
                  color: Color.fromARGB(230, 76, 112, 4),
                  child: Row(
                    mainAxisAlignment: MainAxisAlignment.spaceAround,
                    children: [
                      Icon(Icons.whatsapp,size: 50,),
                      Icon(Icons.facebook,size: 50),
                       Icon(Icons.apple,size: 50),
                    ],
                  ),
                )
              )
      ],
    );
  }

}