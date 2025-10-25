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



4.b) Implement navigation with named routes
PROGRAM:

import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Named Routes Demo',
      initialRoute: '/',
      routes: {
        '/': (context) => HomeScreen(),
        '/second': (context) => SecondScreen(),
        '/third': (context) => ThirdScreen(),
      },
    );
  }
}

class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pushNamed(context, '/second');
          },
          child: Text('Go to Second Screen'),
        ),
      ),
    );
  }
}

class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Second Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.pushNamed(context, '/third');
          },
          child: Text('Go to Third Screen'),
        ),
      ),
    );
  }
}

class ThirdScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Third Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            Navigator.popUntil(context, ModalRoute.withName('/'));
          },
          child: Text('Go Back to Home'),
        ),
      ),
    );
  }
}






10 a) Write unit tests for UI components
Program:



import 'package:flutter/material.dart';
import 'package:flutter_test/flutter_test.dart';
import 'package:untitled9/post_card.dart'; // Import your widget file

void main() {
  testWidgets('PostCard displays title and body', (WidgetTester tester) async {
    // Build our widget and trigger a frame.
    await tester.pumpWidget(
      MaterialApp(
        home: PostCard(
          title: 'Test Title',
          body: 'Test Body',
        ),
      ),
    );

    // Verify that the title and body are displayed correctly.
    expect(find.text('Test Title'), findsOneWidget);
    expect(find.text('Test Body'), findsOneWidget);
  });

  testWidgets('PostCard widget has correct styling', (WidgetTester tester) async {
    // Build our widget and trigger a frame.
    await tester.pumpWidget(
      MaterialApp(
        home: PostCard(
          title: 'Test Title',
          body: 'Test Body',
        ),
      ),
    );

    // Verify that the text styles are applied correctly.
    final titleTextWidget = tester.widget<Text>(find.text('Test Title'));
    expect(titleTextWidget.style?.fontSize, 18);
    expect(titleTextWidget.style?.fontWeight, FontWeight.bold);

    final bodyTextWidget = tester.widget<Text>(find.text('Test Body'));
    expect(bodyTextWidget.style?.fontSize, 16);
  });
}


postcard:

class PostCard extends StatelessWidget {
  final String title;
  final String body;

  const PostCard({
    Key? key,
    required this.title,
    required this.body,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Card(
      margin: EdgeInsets.symmetric(horizontal: 16, vertical: 8),
      child: Padding(
        padding: EdgeInsets.all(16),
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Text(
              title,
              style: TextStyle(
                fontSize: 18,
                fontWeight: FontWeight.bold,
              ),
            ),
            SizedBox(height: 8),
            Text(
              body,
              style: TextStyle(
                fontSize: 16,
              ),
            ),
          ],
        ),
      ),
    );
  }
}







5. b) Implement state management using set state and provider
Stateful Widgets: 


import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: CounterApp(),
    );
  }
}

class CounterApp extends StatefulWidget {
  @override
  _CounterAppState createState() => _CounterAppState();
}

class _CounterAppState extends State<CounterApp> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Counter App'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: [
            Text(
              'Counter:',
              style: TextStyle(fontSize: 24),
            ),
            Text(
              '$_counter',
              style: TextStyle(fontSize: 36, fontWeight: FontWeight.bold),
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: Icon(Icons.add),
      ),
    );
  }
}


