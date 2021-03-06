Update
------
Why use M.A.D?

Making electronic music with visualizations?
No, making music on the fly. 
No, making music that makes sense, on the fly.

So, you need to be able to do live programming.
That means:
1. You can define ALL music notes, signs, tempos
2. You can run/play a pattern (phrase) in a loop for 'debugging'
3. You can combine multiple phrases into a 'conversation'
4. There has to be a sync for theses phrases

It would be fun if I could load only chiptunes for default.

# Language specification 0.8 #
M.A.D (music-as-data) tries to extend the Lisp philosophy that code -> is data -> is code, to music.
That means that notes are data (frequencies) but are also code (their placement creates complex structures). 
Using a Lisp language (Clojure) we can manipulate music structures, make genetic music and release our creative minds.

This specification defines the core elements of the language.

# Timing #
The main thing we have to understand is timing.
  	   (play! [A3 B4 C4#])

# Notes #
A1 means note A, octave 1. If you want to get more technical, this means 440Hz.

# Core functions


# Effects #

# Misc




Play a sample or note like this:
  	 (play! [kick])
  
Play two samples (or notes):
	 (play! [kick kick])

Each sample is being played at one time.


If you want to play a sample at the same time:
   	   (play! [kick (+snare hihat)])	

This will play kick at one time and snare+hihat at another.

You can also play triplets:
		(play! [kick [snare snare snare]])

Now kick will be at one time and for the same duration, you'll have three snare hits.


Of course you can play notes:
      (play! [A4 B4 D#5])

Mix, notes and samples:
	 (play! [hihat A4 kick G6])


The fun begins when you understand that you can manipulate music as data by apply tranformations.
For example:

	(p (reverse (pattern [kick kick])))


Now, instead of using play! (which plays samples in a loop - perfect for building stuff on the fly)
you can create a pattern and then run it only for once using the p function. 
The advantage is that you can manipulate data and their properties thus mess around with note frequences,
tempo, scaling whatever.


# How to use #
First, build the project (see Building). Some examples are included and I would be happy to include any of yours.
If you don't use emacs, you can try this one:

      lein compile
   	  lein repl
	  clj=> (require 'music-as-data.core)
	  clj=> (in-ns 'music-as-data.core)

and keep reading after the emacs block.

If you use emacs, start your repl (lein swank) and go to core.clj .
Go inside emacs, run slime-connect, go to the core namespace, select everything and press CTRL+C, CTRL+R to compile the selection. 

After you have access to a REPL you are ready to go! Just run:

		(start main)

Don't close the window that will pop-up. This is the processing window (so you can have graphics too!).
After that, run

	  (create-notes)

and you are ready to start playing!

	(p (pattern [A4 A2]))

	(p (pattern [kick snare (+ hihat snare)]))

You can have it playing on a loop by executing:
	(keep-looping)

and then:

	(play! [A4])
	(play! [C5])

In order to play a pause, you can play the _ note:

      (play! [A4 _ A4])


# Building #

    lein deps


# Authors #

Designed and developed by Jon Vlachoyiannis (http://jon.is.emotionull.com).

# Thanks #

@mar_nas (for the incredible site mad.emotionull.com)

https://github.com/rosado (for clj-processing)

http://processing.org ('cause it rocks)

http://code.compartmental.net/tools/minim/ (for the AWESOME sound system)

zero (for how to use it without emacs)



