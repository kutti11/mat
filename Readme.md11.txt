4. a) Setup navigation between different screens using navigator
PROGRAM:


import 'package:flutter/material.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Navigation Example',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: FirstScreen(),
    );
  }
}

class FirstScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('First Screen'),
      ),
      body: Center(
        child: ElevatedButton(
          onPressed: () {
            // Navigate to the second screen
            Navigator.push(
              context,
              MaterialPageRoute(builder: (context) => SecondScreen()),
            );
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
            // Navigate back to the first screen
            Navigator.pop(context);
          },
          child: Text('Go back to First Screen'),
        ),
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
        },
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

