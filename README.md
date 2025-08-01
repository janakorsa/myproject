import 'package:flutter/material.dart';

void main() {
  runApp(const MovieApp());
}

class MovieApp extends StatelessWidget {
  const MovieApp({super.key});

  @override
  Widget build(BuildContext context) {
    return const MaterialApp(
      debugShowCheckedModeBanner: false,
      home: HomeScreen(),
    );
  }
}

class HomeScreen extends StatelessWidget {
  const HomeScreen({super.key});

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.black,
      appBar: AppBar(
        backgroundColor: Colors.black,
        title: const Text("Untitled"),
        centerTitle: true,
      ),
      body: SingleChildScrollView(
        child: Column(
          crossAxisAlignment: CrossAxisAlignment.start,
          children: [
            Stack(
              children: [
                Image.asset(
                  'assets/Image.png',
                  width: 270,
                  height: 200,
                  fit: BoxFit.cover,
                ),
                const Positioned.fill(
                  child: Center(
                    child: Icon(
                      Icons.play_circle_fill,
                      size: 70,
                      color: Colors.white,
                    ),
                  ),
                ),
              ],
            ),

            const Padding(
              padding: EdgeInsets.all(8.0),
              child: Text(
                "Dora and the lost city of gold",
                style: TextStyle(color: Colors.white, fontSize: 16),
              ),
            ),

            sectionTitle("New Releases"),
            movieRow([
              "assets/f8b938401308eabc48c30669869eeac8.png", 
              "assets/d09cbedd39d8c74b576632e50de5c3d3.png", 
              "assets/Annabelle.png",                       
              "assets/e38d645574a267d62c7320ca51baf6d2.png", 
            ]),
            sectionTitle("Recommended"),
            movieRow([
              "assets/d09cbedd39d8c74b576632e50de5c3d3.png",
              "assets/d09cbedd39d8c74b576632e50de5c3d3.png",
              "assets/d09cbedd39d8c74b576632e50de5c3d3.png",
              "assets/d09cbedd39d8c74b576632e50de5c3d3.png",
            ]),
          ],
        ),
      ),
      bottomNavigationBar: BottomNavigationBar(
        backgroundColor: Colors.black,
        selectedItemColor: Colors.orange,
        unselectedItemColor: Colors.white,
        currentIndex: 0,
        onTap: (index) {},
        items: const [
          BottomNavigationBarItem(icon: Icon(Icons.home), label: "Home"),
          BottomNavigationBarItem(icon: Icon(Icons.search), label: "Search"),
          BottomNavigationBarItem(icon: Icon(Icons.movie), label: "Browse"),
          BottomNavigationBarItem(icon: Icon(Icons.bookmark), label: "Watchlist"),
        ],
      ),
    );
  }

  static Widget sectionTitle(String title) {
    return Padding(
      padding: const EdgeInsets.all(8.0),
      child: Text(
        title,
        style: const TextStyle(
          color: Colors.white,
          fontSize: 18,
          fontWeight: FontWeight.bold,
        ),
      ),
    );
  }

  static Widget movieRow(List<String> images) {
    return SizedBox(
      height: 150,
      child: ListView(
        scrollDirection: Axis.horizontal,
        children: images.map((path) => moviePoster(path)).toList(),
      ),
    );
  }

  static Widget moviePoster(String path) {
    return Container(
      width: 100,
      margin: const EdgeInsets.all(5),
      child: ClipRRect(
        borderRadius: BorderRadius.circular(8),
        child: Image.asset(path, fit: BoxFit.cover),
      ),
    );
  }
}
