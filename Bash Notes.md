

${parameter##word}
       Remove matching prefix pattern.  The word is expanded to produce a pattern just as in pathname expansion.  If the pattern matches
       the beginning of the value of parameter, then the result of the expansion is the expanded value of parameter with the shortest
       matching pattern (the ``#'' case) or the longest matching pattern (the ``##'' case) deleted.
