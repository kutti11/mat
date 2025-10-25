
1.c) Write a Dart console program that prints your name, checks age
with conditionals, uses a loop to count from 1 to 5, and defines a function
to return the sum of two numbers.



int addNumbers(int a, int b) {
  return a + b;
}

void main() {
  // 1. Print your name
  String name = "Chandini"; // you can replace with your own name
  print("My name is $name");

  // 2. Check age with conditionals
  int age = 22; // change value to test
  if (age >= 18) {
    print("You are an adult.");
  } else {
    print("You are a minor.");
  }

  // 3. Loop to count from 1 to 5
  print("Counting from 1 to 5:");
  for (int i = 1; i <= 5; i++) {
    print(i);
  }

  // 4. Use the sum function
  int x = 10, y = 20;
  int result = addNumbers(x, y);
  print("The sum of $x and $y is $result");
}






2) b) Implement different layout structures using Row, Column, and Stack widgets.
PROGRAM: ROW WIDETS.

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Row Layout'),
        ),
        body: Row(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            Container(
              color: Colors.red,
              width: 100,
              height: 100,
            ),
            Container(
              color: Colors.green,
              width: 100,
              height: 100,
            ),
            Container(
              color: Colors.blue,
              width: 100,
              height: 100,
            ),
          ],
        ),
      ),
    );
  }
}


PROGRAM: COLUMN WIDETS.

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Column Layout'),
        ),
        body: Column(
          mainAxisAlignment: MainAxisAlignment.spaceEvenly,
          children: [
            Container(
              color: Colors.red,
              width: 100,
              height: 100,
            ),
            Container(
              color: Colors.green,
              width: 100,
              height: 100,
            ),
            Container(
              color: Colors.blue,
              width: 100,
              height: 100,
            ),
          ],
        ),
      ),
    );
  }
}


PROGRAM: STACK WIDETS.

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Stack Layout'),
        ),
        body: Stack(
          alignment: Alignment.center,
          children: [
            Container(
              color: Colors.red,
              width: 200,
              height: 200,
            ),
            Container(
              color: Colors.green,
              width: 150,
              height: 150,
            ),
            Container(
              color: Colors.blue,
              width: 100,
              height: 100,
            ),
          ],
        ),
      ),
    );
  }
}






1b) Write a simple dart program to understand the language basics

import 'package:flutter/material.dart';

void main() {
  runApp(Abc());
}

class Abc extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Def(),
    );
  }
}

class Def extends StatelessWidget {
  const Def({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("Welcome"),
        backgroundColor: Colors.purple,
      ),
      body: Column(
        children: [
          // Widgets will go here
        ],
      ),
    );
  }
}










5. a) Learn about stateful and stateless widgets
PROGRAM:

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Cards Example'),
        ),
        body: CardList(),
      ),
    );
  }
}

class CardList extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return ListView.builder(
      itemCount: 10,
      itemBuilder: (context, index) {
        return CardItem(
          title: 'Card $index',
          subtitle: 'Subtitle $index',
        );
      },
    );
  }
}

class CardItem extends StatelessWidget {
  final String title;
  final String subtitle;

  const CardItem({
    Key? key,
    required this.title,
    required this.subtitle,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      margin: EdgeInsets.symmetric(horizontal: 16, vertical: 8),
      child: ListTile(
        title: Text(title),
        subtitle: Text(subtitle),
        leading: CircleAvatar(
          child: Text(title.substring(0, 1)),
        ),
        onTap: () {
          // Handle card tap
          ScaffoldMessenger.of(context).showSnackBar(
            SnackBar(content: Text('You tapped on $title')),
          );
        },
      ),
    );
  }
}
