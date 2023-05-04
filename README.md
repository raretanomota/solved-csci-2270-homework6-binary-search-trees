Download Link: https://assignmentchef.com/product/solved-csci-2270-homework6-binary-search-trees
<br>
In 2009, Netflix held a competition to see who could best predict user ratings for films based on previous ratings without any other information about the users or films. ​The grand prize of US$1,000,000 was given to the BellKor’s Pragmatic Chaos team which bested Netflix’s own algorithm for predicting ratings by 10.06%. This kind of data science is facilitated with the application of good data structures. In fact, cleaning and arranging data in a conducive manner is half the battle in making successful predictions. Imagine you are attempting to predict user ratings given a​     dataset of IMDB’s top 100 movies. Building a binary search tree will enable you to search for movies and extract their features very efficiently. The movies will be accessed by their titles, but they will also store the following features:

<ul>

 <li>IMDB ranking (1-100)</li>

 <li>Title</li>

 <li>Year released</li>

 <li>IMDB average rating</li>

</ul>

Your binary search tree will utilize the following struct with default and overloaded constructors:

<table width="640">

 <tbody>

  <tr>

   <td width="640"><strong>struct</strong>​ ​<strong>MovieNode</strong>​{     int ranking;     string title;     int year;     float rating;MovieNode* left = ​<strong>NULL</strong>​;MovieNode* right = ​<strong>NULL</strong>​; ​<strong>MovieNode</strong>​(int rank, string t, int y, float r) {         title = t;         ranking = rank;         year = y;         rating = r;}};</td>

  </tr>

 </tbody>

</table>

<h1>MovieTree Class</h1>

Your code should implement a binary search tree of movies. A header file that lays out this tree can be found in ​<em>MovieTree.hpp </em>​on Moodle. As usual, ​<strong>do not </strong>​modify the header file. ​<em>You may implement helper functions in your .cpp file to facilitate recursion if you want as long as you don’t add those functions to the MovieTree class</em>​.

<strong>MovieTree() </strong>

<ul>

 <li>Constructor: Initialize any member variables of the class to default</li>

</ul>

<strong>~MovieTree() </strong>

<ul>

 <li>Destructor: Free all memory that was allocated</li>

</ul>

<h2>void printMovieInventory()</h2>

➔ Print every node in the tree in alphabetical order of titles using the following format:

<strong>// for every Movie node (m) in the tree </strong>

<strong>cout </strong>​&lt;&lt; ​”Movie: “​ &lt;&lt; m-&gt;title &lt;&lt; ​” “​ &lt;&lt; m-&gt;rating &lt;&lt; ​<strong>endl</strong>​;

If there is no movie entry in the tree, print the following message instead:

<strong>cout </strong>​&lt;&lt; ​”Tree is Empty. Cannot print”​ &lt;&lt; ​<strong>endl</strong>​;

<strong> </strong>

<h2>void addMovieNode(int ​ranking​, std::string ​title​, int ​year​, float ​rating​)</h2>

➔ Add a node to the tree in the correct place based on its ​<strong>title</strong>​. Every node’s left children should come before it alphabetically, and every node’s right children should come after it alphabetically. ​<em>Hint: you can compare strings with &lt;, &gt;, ==, string::compare() function etc. </em>​You may assume that no two movies have the same title

<h2>void findMovie(string ​title)​</h2>

➔ Find the movie with the given ​<strong>title</strong>​, then print out its information:

<strong>cout </strong>​&lt;&lt;​ ​”Movie Info:”​ ​&lt;&lt;​<strong> endl; cout </strong>​&lt;&lt;​ ​”==================”​ ​&lt;&lt;​<strong> endl; cout </strong>​&lt;&lt;​ ​”Ranking:”​ ​&lt;&lt; node-&gt;ranking &lt;&lt;​<strong> endl; cout </strong>​&lt;&lt;​ ​”Title  :”​ ​&lt;&lt; node-&gt;title &lt;&lt;​<strong> endl; cout </strong>​&lt;&lt;​ ​”Year   :”​ ​&lt;&lt; node-&gt;year &lt;&lt;​<strong> endl; cout </strong>​&lt;&lt;​ ​”rating :”​ ​&lt;&lt; node-&gt;rating &lt;&lt;​<strong> endl; </strong>

If the movie isn’t found, print the following message instead:

<strong>cout</strong>​ &lt;&lt; ​”Movie not found.”​ &lt;&lt; ​<strong>endl</strong>​;

<strong> </strong>

<h2>void queryMovies(float ​rating​, int ​year)​</h2>

➔ Print all the movies with a rating at least as good as ​<strong>rating </strong>​that are newer than ​<strong>year</strong> ​​in the ​<strong>preorder</strong>​ fashion​ ​using the following format:

<strong>cout</strong>​ &lt;&lt; ​”Movies that came out after ” ​&lt;&lt; year &lt;&lt;​ ” with rating at least ” ​&lt;&lt; rating &lt;&lt;​ “:”​ &lt;&lt; ​<strong>endl</strong>​;

<strong>// each movie that satisfies the constraints should be printed with </strong><strong>cout </strong>​&lt;&lt; m-&gt;title &lt;&lt; ​”(” ​&lt;&lt; m-&gt;year &lt;&lt; ​”) “​ &lt;&lt; m-&gt;rating &lt;&lt; ​<strong>endl</strong>​;

If there is no movie entry in the tree, print the following message instead:

<strong>cout </strong>​&lt;&lt; ​”Tree is Empty. Cannot query Movies”​ &lt;&lt; ​<strong>endl</strong>​;

<h2>void averageRating()</h2>

➔ Print the average rating for all movies in the tree. If the tree is empty, print 0.0. Use the following format:

<strong>cout </strong>​&lt;&lt; ​”Average rating:” ​&lt;&lt; average &lt;&lt; ​<strong>endl</strong>​;




If there is no movie entry in the tree, print the following message instead:

<strong>cout </strong>​&lt;&lt; ​”Average rating:0.0″​ &lt;&lt; ​<strong>endl</strong>​;

<h1>Driver</h1>

Your main function should first read information about each movie from a file and store that information in a MovieTree. <strong>The name of the file with this information should be passed in</strong>​       <strong> as a command-line argument.</strong>​ An example file is ​<em>Movies.csv</em>​ on Moodle. It is in the format:

&lt;Movie 1 ranking&gt;,&lt;Movie 1 title&gt;,&lt;Movie 1 year&gt;,&lt;Movie 1 rating&gt; &lt;Movie 2 ranking&gt;,&lt;Movie 2 title&gt;,&lt;Movie 2 year&gt;,&lt;Movie 2 rating&gt; Etc…

<em>Note: For autograding’s sake, insert the nodes to the tree in the order they are read in. Of course, they will still be inserted in alphabetical order, but a different insertion order may produce a different tree.</em>​<strong> After </strong>​reading the information on each movie from the file, display a menu to the user.

<strong>cout</strong>​ &lt;&lt; ​”======Main Menu======”​ &lt;&lt; ​<strong>endl</strong>​; <strong>cout</strong>​ &lt;&lt; ​”1. Find a movie”​ &lt;&lt; ​<strong>endl</strong>​;

<strong>cout</strong>​ &lt;&lt; ​”2. Query movies”​ &lt;&lt; ​<strong>endl</strong>​; <strong>cout</strong>​ &lt;&lt; ​”3. Print the inventory”​ &lt;&lt; ​<strong>endl</strong>​; <strong>cout</strong>​ &lt;&lt; ​”4. Average Rating of movies”​ &lt;&lt; ​<strong>endl</strong>​; <strong>cout</strong>​ &lt;&lt; ​”5. Quit”​ &lt;&lt; ​<strong>endl</strong>​;

The options should have the following behavior:

<ul>

 <li><strong>Find a movie: </strong>​Call your tree’s ​<em>findMovie </em>​function on a movie specified by the user. Prompt the user for a movie title using the following code:</li>

</ul>

<strong>cout</strong>​ &lt;&lt; ​”Enter title:”​ &lt;&lt; ​<strong>endl</strong>​;

<ul>

 <li><strong>Query movies: </strong>​Call your tree’s ​<strong>queryMovies</strong>​ ​function on a rating and year specified by the user. Prompt the user for a rating and year using the following code:</li>

</ul>

<table width="576">

 <tbody>

  <tr>

   <td width="576"><strong>cout</strong>​ &lt;&lt; ​”Enter minimum rating:”​ &lt;&lt; ​<strong>endl</strong>​;<strong>// get user input </strong><strong>cout</strong>​ &lt;&lt; ​”Enter minimum year:”​ &lt;&lt; ​<strong>endl</strong>​;</td>

  </tr>

 </tbody>

</table>

<ul>

 <li><strong>Print the inventory: </strong>​Call your tree’s ​<strong>printMovieInventory</strong>​ ​function</li>

</ul>

<h2>        ●   Average Rating of movies: ​Call your averageRating ​ ​function</h2>

<ul>

 <li><strong>Quit: </strong>​Exit after printing a friendly message to the user:</li>

</ul>

<strong>cout</strong>​ &lt;&lt; ​”Goodbye!”​ &lt;&lt; ​<strong>endl</strong>​;


