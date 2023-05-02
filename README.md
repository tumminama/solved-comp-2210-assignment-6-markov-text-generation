Download Link: https://assignmentchef.com/product/solved-comp-2210-assignment-6-markov-text-generation
<br>
The Infinite Monkey Theorem<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a> (IFT) says that if a monkey hits keys at random on a typewriter it will almost surely, given an infinite amount of time, produce a chosen text (like the Declaration of Independence, <em>Hamlet</em>, or a script for … <em>Planet of the Apes</em>). The probability of this actually happening is, of course, very small but the IFT claims that it is still possible. Some people have tested this hypotheis in software and, after billions and billions of simulated years, one virtual monkey was able to type out a sequence of 19 letters that can be found in Shakespeare’s <em>The Two Gentlemen of Verona</em>. (See the April 9, 2007 edition of <em>The New Yorker </em>if you’re interested; but, hypothesis testing with real monkeys<a href="#_ftn2" name="_ftnref2"><sup>[2]</sup></a> is far more entertaining.)

The IFT might lead to some interesting conversations with Rust Cohle, but the practical applications are few. It does, however, bring up the idea of <em>automated text generation</em>, and there the ideas and applications are not only interesting but also important. Claude Shannon essentially founded the field of information theory with the publication of his landmark paper <em>A Mathematical Theory of Computation</em><a href="#_ftn3" name="_ftnref3"><sup>[3]</sup></a> in 1948. Shannon described a method for using Markov chains to produce a reasonable imitation of a known text with sometimes startling results. For example, here is a sample of text generated from a Markov model of the script for the 1967 movie <em>Planet of the Apes</em>.

“PLANET OF THE APES”

Screenplay by Michael Wilson

Based on Novel By Pierre Boulle

DISSOLVE TO: 138 EXT. GROVE OF FRUIT TREES – ESTABLISHING SHOT – DAY Zira run back to the front of Taylor.

The President, I believe the prosecutor’s charge of this man.

ZIRA Well, whoever owned them was in pretty bad shape.

He picks up two of the strain.

You got what you wanted, kid. How does it taste?                                         Silence.

Taylor and cuffs him.

Over this we HEAR from a distance is a crude horse-drawn wagon is silhouetted-against the trunks and branches of great trees and bushes on the horse’s rump. Taylor lifts his right arm to ward off the blow, and the room and lands at the feet of Cornelius and Lucius are sorting out equipment falls to his knees, buries his head silently at the Ranch). DISSOLVE TO: 197 INT. CAGES – CLOSE SHOT FEATURING LANDON – FROM TAYLOR’S VOICE (o.s.) I’ve got a fine veternary surgeons under my direction?

ZIRA Taylor!

ZIRA There is a           small lake, looking like a politician. TAYLOR Dodge takes a pen and notebook from the half-open door of a guard room. Taylor bursts suddenly confronted by his

1

original pursuer (the dismounted cop coming up with a cigar butt and places it in the drawer beside them.

TAYLOR What’s the best there is a. loud RAP at the doll was found beside the building. Zira waits at the third table.

TAYLOR                     Good question. Is he a man?

CORNELIUS                  (impatiently.

DODGE                  Blessed are the vegetation.

These SHOTS are       INTERCUT with: 94 WHAT THE ASTRONAUTS They examine the remnants of the cage.

ZIRA (plunging on)                             Their speech organs are adequate.

The flaw lies not in anatomy but in the back of his left sleeve. TAYLOR (taking off his shirt. 80 DODGE AND LANDON You don’t sound happy in your work.

GALEN (defensively) Gorilla hunter stands over a dead man, one fo

Besides a few spelling errors and some rather odd things that make you wonder about the author, this passage is surprisingly human-like. This is a simple example of <em>natural language generation</em>, a sub-area of <em>natural language processing</em>—a very active area of research in computer science. The particular approach we’re using in this assignment was famously implemented as the fictitious Mark V. Shaney<a href="#_ftn4" name="_ftnref4"><sup>[4]</sup></a> and the Emacs command Disassociated Press<a href="#_ftn5" name="_ftnref5"><sup>[5]</sup></a>.

<h1>Approach</h1>

So, here’s the basic idea: Imagine taking a book (say, <em>Tom Sawyer</em>) and determining the probability with which each character occurs. You would probably find that spaces are the most common, that the character ‘e’ is fairly common, and that the character ‘q’ is rather uncommon. After completing this “level 0” analysis, you would be able to produce random Tom Sawyer text based on character probabilities. It wouldn’t have much in common with the real thing, but at least the characters would tend to occur in the proper proportion. In fact, here’s an example of what you might produce:

<h2>Level 0</h2>

rla bsht eS ststofo hhfosdsdewno oe wee h .mr ae irii ela iad o r te u t mnyto onmalysnce, ifu en c fDwn oee iteo

Now imagine doing a slightly more sophisticated <em>level 1 </em>analysis by determining the probability with which each character follows every other character. You would probably discover that ‘h’ follows ‘t’ more frequently than ‘x’ does, and you would probably discover that a space follows ‘.’ more frequently than ‘,’ does. You could now produce some randomly generated <em>Tom Sawyer </em>text by picking a character to begin with and then always choosing the next character based on the previous one and the probabilities revealed by the analysis. Here’s an example:

<h2>Level 1</h2>

“Shand tucthiney m?” le ollds mind Theybooure He, he s whit Pereg lenigabo Jodind alllld ashanthe ainofevids tre lin-p asto oun theanthadomoere

Now imagine doing a <em>level k </em>analysis by determining the probability with which each character follows every possible sequence of characters of length <em>k </em>(<em>kgrams</em>). A level 5 analysis of <em>Tom Sawyer </em>for example, would reveal that ‘r’ follows “Sawye” more frequently than any other character. After a level <em>k </em>analysis, you would be able to produce random <em>Tom Sawyer </em>by always choosing the next character based on the previous <em>k </em>characters (a kgram) and the probabilities revealed by the analysis.

At only a moderate level of analysis (say, levels 5-7), the randomly generated text begins to take on many of the characteristics of the source text. It probably won’t make complete sense, but you’ll be able to tell that it was derived from <em>Tom Sawyer </em>as opposed to, say, <em>The Sound and the Fury</em>.

Here are some more examples of text that is generated from increasing levels of analysis of <em>Tom Sawyer</em>. (These “levels of analysis” are called <em>order K Markov models</em>.)

<h2>K = 2</h2>

“Yess been.” for gothin, Tome oso; ing, in to weliss of an’te cle – armit. Papper a comeasione, and smomenty, fropeck hinticer, sid, a was Tom, be suck tied. He sis tred a youck to themen

<h2>K = 4</h2>

en themself, Mr. Welshman, but him awoke, the balmy shore. I’ll give him that he couple overy because in the slated snufflindeed structure’s kind was rath. She said that the wound the door a fever eyes that WITH him.

<h2>K = 6</h2>

people had eaten, leaving. Come – didn’t stand it better judgment; His hands and bury it again, tramped herself! She’d never would be. He found her spite of anything the one was a prime feature sunset, and hit upon that of the forever.

<h2>K = 8</h2>

look-a-here – I told you before, Joe. I’ve heard a pin drop. The stillness was complete, how- ever, this is awful crime, beyond the village was sufficient. He would be a good enough to get that night, Tom and Becky.

<h2>K = 10</h2>

you understanding that they don’t come around in the cave should get the word “beauteous” was over-fondled, and that together” and decided that he might as we used to do – it’s nobby fun. I’ll learn you.”

To create an order K Markov model of a given source text, you would need to identify all kgrams in the source text and associate with each kgram all the individual characters that follow it. This association or mapping must also capture the frequency with which a given character follows a given kgram. For example, suppose that <em>k </em>= 2 and the sample text is:

agggcagcgggcg

The Markov model would have to represent all the character strings of length two (2-grams) in the source text, and associate with them the characters that follow them, and in the correct proportion. The following table shows one way of representing this information.

Once you have created an order K Markov model of a given source text, you can generate new text based on this model as follows.

<ol>

 <li>Randomly pick <em>k </em>consecutive characters that appear in the sample text and use them as the initial kgram.</li>

 <li>Append the kgram to the output text being generated.</li>

 <li>Repeat the following steps until the output text is sufficiently long.

  <ul>

   <li>Select a character <em>c </em>that appears in the sample text based on the probability of that character following the current kgram.</li>

   <li>Append this character to the output text.</li>

   <li>Update the kgram by removing its first character and adding the character just chosen (<em>c</em>) as its last character.</li>

  </ul></li>

</ol>

If this process encounters a situation in which there are no characters to choose from (which can happen if the only occurrence of the current kgram is at the exact end of the source), simply pick a new kgram at random and continue.

As an example, suppose that <em>k </em>= 2 and the sample text is that from above:

agggcagcgggcg

Here are four different output text strings of length 10 that could have been the result of the process described above, using the first two characters (’ag’) as the initial kgram.

agcggcagcg aggcaggcgg agggcaggcg agcggcggca

For another example, suppose that <em>k </em>= 2 and the sample text is: the three pirates charted that course the other day

Here is how the first three characters of new text might be generated:

<ul>

 <li>A two-character sequence is chosen at random to become the initial kgram. Let’s suppose that “th” is chosen. So, kgram = th and output = th.</li>

 <li>The first character must be chosen based on the probability that it follows the kgram (currently “th”) in the source. The source contains five occurrences of “th”. Three times it is followed by ’e’, once it is followed by ’r’, and once it is followed by ’a’. Thus, the next character must be chosen so that there is a 3/5 chance that an ’e’ will be chosen, a 1/5 chance that an ’r’ will be chosen, and a 1/5 chance that an ’a’ will be chosen. Let’s suppose that we choose an ’e’ this time. So, kgram = he and output = the.</li>

 <li>The next character must be chosen based on the probability that it follows the kgram (currently “he”) in the source. The source contains three occurrences of “he”. Twice it is followed by a space and once it is followed by ’r’. Thus, the next character must be chosen so that there is a 2/3 chance that a space will be chosen and a 1/3 chance that an ’r’ will be chosen. Let’s suppose that we choose an ’r’ this time. So, kgram = er and output = ther.</li>

 <li>The next character must be chosen based on the probability that it follows the kgram (currently “er”) in the source. The source contains only one occurrence of “er”, and it is followed by a space. Thus, the next character must be a space. So, kgram = r_ and output = ther_, where ’_’ represents a blank space.</li>

</ul>

<h1>Implementation Details</h1>

You are provided with two Java files that you must use to develop your solution: MarkovModel.java and TextGenerator.java.

The constructors of MarkovModel build the order-k model of the source text. You are required to represent the model with the provided HashMap field.

The main method of TextGenerator must process the following three command line arguments (in the args array):

<ul>

 <li>A non-negative integer <em>k</em></li>

 <li>A non-negative integer <em>length</em>.</li>

 <li>The name of an input file <em>source </em>that contains more than <em>k </em></li>

</ul>

Your program must validate the command line arguments by making sure that <em>k </em>and <em>length </em>are nonnegative and that <em>source </em>contains at least <em>k </em>characters and can be opened for reading. If any of the command line arguments are invalid, your program must write an informative error message to System.out and terminate. If there are not enough command line arguments, your program must write an informative error message to System.out and terminate.

With valid command line arguments, your program must use the methods of the MarkovModel class to create an order <em>k </em>Markov model of the sample text, select the initial kgram, and make each character selection. You must implement the MarkovModel methods according to description of the Markov modeling process in the section above.

A few sample texts have been provided, but Project Gutenberg (http://www.gutenberg.org) maintains a large collection of public domain literary works that you can use as source texts for fun and practice.

<a href="#_ftnref1" name="_ftn1">[1]</a> <a href="https://en.wikipedia.org/wiki/Infinite_monkey_theorem">https://en.wikipedia.org/wiki/Infinite</a><a href="https://en.wikipedia.org/wiki/Infinite_monkey_theorem">_</a><a href="https://en.wikipedia.org/wiki/Infinite_monkey_theorem">monkey</a><a href="https://en.wikipedia.org/wiki/Infinite_monkey_theorem">_</a><a href="https://en.wikipedia.org/wiki/Infinite_monkey_theorem">theorem</a>

<a href="#_ftnref2" name="_ftn2">[2]</a> <a href="https://web.archive.org/web/20130120215600/http:/www.vivaria.net/experiments/notes/publication/NOTES_EN.pdf">https://web.archive.org/web/20130120215600/http://www.vivaria.net/experiments/notes/publication/NOTES</a><a href="https://web.archive.org/web/20130120215600/http:/www.vivaria.net/experiments/notes/publication/NOTES_EN.pdf">_</a>

<a href="https://web.archive.org/web/20130120215600/http:/www.vivaria.net/experiments/notes/publication/NOTES_EN.pdf">EN.pdf</a>

<a href="#_ftnref3" name="_ftn3">[3]</a> <a href="http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=6773024">http://ieeexplore.ieee.org/xpl/articleDetails.jsp?arnumber=6773024</a>

<a href="#_ftnref4" name="_ftn4">[4]</a> <a href="https://en.wikipedia.org/wiki/Mark_V._Shaney">https://en.wikipedia.org/wiki/Mark</a><a href="https://en.wikipedia.org/wiki/Mark_V._Shaney">_</a><a href="https://en.wikipedia.org/wiki/Mark_V._Shaney">V.</a><a href="https://en.wikipedia.org/wiki/Mark_V._Shaney">_</a><a href="https://en.wikipedia.org/wiki/Mark_V._Shaney">Shaney</a>

<a href="#_ftnref5" name="_ftn5">[5]</a> <a href="https://en.wikipedia.org/wiki/Dissociated_press">https://en.wikipedia.org/wiki/Dissociated</a><a href="https://en.wikipedia.org/wiki/Dissociated_press">_</a><a href="https://en.wikipedia.org/wiki/Dissociated_press">press</a>