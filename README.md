Download Link: https://assignmentchef.com/product/solved-cs2040s-recitation-8
<br>
<h1>Problem 1.            Winning the Games</h1>

For this problem, consider an <em>n </em>× <em>n </em>chessboard consisting of <em>n </em>columns and <em>n </em>rows. We have labelled the columns with letters and the rows with numbers. For instance in Figure 1a, your piece is at position C4.

<strong>(a)                                                                                                                             (b)</strong>

<h2>Figure 1</h2>

Every square on the board has a reward associated with it, and your goal is to move a piece from the bottom left corner to the top right corner, while collecting as much points as possible.

The rules of the game are as follows: • In every move, your piece can move one square in either the vertical or horizontal direction. It cannot move diagonally. For example, in Figure 1a, the piece at square C4 can potentially move to the squares: C5, C3, D4, B4. It cannot move to square D5, D3, B5, or B3. • Your piece can only move to a square of lesser value. That is, if your piece is on a square with reward <em>r</em>, it can only move to a square with reward <em>&lt; r</em>. In Figure 1b above, the piece

at square C4 can move to square C5 and B4 (since 30 <em>&lt; </em>51 and 50 <em>&lt; </em>51), but not to any other square.

<ul>

 <li>Your piece starts in square A1.</li>

 <li>When your piece reaches the square in the top right corner of the board (in the example above, H8), it is rewarded with the value of every square it traversed.</li>

</ul>

Figure 2 below shows an example of a legal set of moves (with a reward of 586).

<h2>Figure 2</h2>

<strong>Problem 1.a. </strong>Explain how the problem can be modelled as a directed graph. How many nodes does your graph have? State one important property of your graph. Draw a small example (e.g., for <em>n </em>= 2 or <em>n </em>= 3) to illustrate.

<strong>Problem 1.b. </strong>Give an efficient algorithm for finding the sequence of moves which attains the maximum possible reward. You may use any algorithm from class in unmodified form without reproducing it. What is the (asymptotic) performance of your algorithm?

<h1>Problem 2.           StonksX Trader</h1>

One day you decided to get into the <a href="https://en.wikipedia.org/wiki/Foreign_exchange_market">Foreign Exchange Market</a> (Forex). You registered as a trader in the <em>StonksX </em>exchange, a popular exchange for global currencies. There are currently <em>n </em>currencies being traded in the exchange. To help you with analysis, you created a matrix <em>R </em>containing all exchange rates where <em>R</em>[<em>i,j</em>] is the amount of currency <em>j </em>you can get for one unit of currency <em>i</em>. Note that exchange rates are not symmetric: <em>R</em>[<em>i,j</em>] 6= <em>R</em>[<em>j,i</em>]. Alas, there is “no <a href="https://en.wikipedia.org/wiki/Arbitrage">arbitrage</a><a href="https://en.wikipedia.org/wiki/Arbitrage">”</a> possible in the <em>StonksX </em>exchange, meaning that if you start with one currency and then convert it to another, and then another, and so on, and then back to the first currency, you will end up with <em>no more </em>money then what you started with.

You begin the trading day with an account full of Singapore Dollars (SGD), and you want to end the day with only Great Britain Pounds (GBP). Find the sequence of conversions that will maximize the amount of GBPs you have at the end of the trading day.

<strong>Problem 2.a. </strong>How do you model this problem as a graph? What are its vertices and edges? Is it weighted or non-weighted? Are the edges directed or non-directed?

<strong>Problem 2.b. </strong>In your graphical model, which of its property reflects the “no arbitrage” rule? What would happen if such a rule is not enforced by the exchange?

<strong>Problem 2.c. </strong>What graph algorithm will you use to solve the problem? Which modifications are necessary?

<em>Challenge question: </em>How can you use the algorithm without modifying it (i.e. in the form that was presented to you in lecture)?

<h1>Problem 3.             Minimum Edit Distance</h1>

We have already seen the problem of comparing two strings several times in this module. Another metric for measuring the difference (or equivalently, similarity) between two strings is their <em>edit distance</em>. Edit distance measures the <em>total cost </em>of transforming from one string to the other via a sequence of character edit operations. In the typical version of this problem, there are three permitted character edit operations:

<table width="560">

 <tbody>

  <tr>

   <td width="90"><strong>Operation</strong></td>

   <td width="420"><strong>Behaviour</strong></td>

   <td width="50"><strong>Cost</strong></td>

  </tr>

  <tr>

   <td width="90">insert(<em>i,c</em>)</td>

   <td width="420">Inserts a character <em>c </em>at position <em>i </em>in the string.</td>

   <td width="50">$<em>ins</em></td>

  </tr>

  <tr>

   <td width="90">delete(<em>i</em>)</td>

   <td width="420">Removes character at position <em>i </em>in the string.</td>

   <td width="50">$<em>del</em></td>

  </tr>

  <tr>

   <td width="90">replace(<em>i,c</em>)</td>

   <td width="420">Replace a character at position <em>i </em>in the string with character <em>c</em>.</td>

   <td width="50">$<em>rep</em></td>

  </tr>

 </tbody>

</table>

For example, suppose we are given the following two strings representing nucleotide sequences:

<em>S</em>: AGGAACCGTA

<em>T</em>: AGAATCCGAA

One valid sequence of edits to transform from source string <em>S </em>to target string <em>T </em>is as follows:

<ol>

 <li>delete(2): Delete G at position 2</li>

 <li>delete(7): Delete T at position 7</li>

 <li>insert(4<em>,</em>T): Insert T at position 4</li>

</ol>

If every edit operation has a cost of 1 (i.e. $<em>ins </em>= $<em>del </em>= $<em>rep </em>= 1), then the edit distance due to the sequence of edits above is 1+1+1=3.

Clearly, many possible edit sequences are possible and therefore we are only interested in the <em>Minimum Edit Distance </em>(MED): The minimum out of all possible edit distances for transforming a source string to a target string.

Note that the cost for each edit operation varies from problem to problem. When we change the edit operation costs, we may end up with a different MED corresponding to a different sequence of edits.

<strong>Problem 3.a. </strong>How can we represent the MED between 2 strings as a graph? Let <em>m </em>be the length of source string <em>S </em>and <em>n </em>be the length of target string <em>T</em>, how many vertices and edges does your MED graph have (in terms of <em>m </em>and <em>n</em>)? Draw your MED graph for transforming the string CG to the string AGT.

<strong>Problem 3.b. </strong>Suppose that $<em>ins </em>= 3, $<em>del </em>= 5 and $<em>rep </em>= 7. How would you compute the MED between two strings? What graph problem is this? What is the time complexity of your algorithm? Illustrate your solution using the same example of transforming the string CG to the string AGT.