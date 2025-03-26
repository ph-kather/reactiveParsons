Mit diesen Aufgaben möchte ich die Grundlegende Syntax von reaktiver Programmierung in Java einüben.
Hierbei geht es nur darum, die richtige Reihenfolge der Codeblöcke zu finden.
Zieht dafür einfach die Elemente aus dem Aufgabenbereich in den Lösungsbereich und prüft Eure Antwort.
Beachtet, dass meist nicht alle Elemente notwendig sind.
Zudem ist es wichtig, dass alle Elemente linksbündig sind!

##  Aufgabe 1
In der folgenden Aufgabe soll – analog zum Beispiel – aus einer Liste ein `Flux` erzeugt werden. Anschließend soll für alle Werte, die kleiner als 10 sind, der Kehrwert berechnet werden. Falls sich eine 0 in der Liste befindet, soll ein Fehler ausgelöst werden.


<div id="Task1-sortableTrash" class="sortable-code"></div> 
<div id="Task1-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="Task1-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="Task1-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "Flux.fromIterable(List.of(5,15,3,0,17,-1))\n" +
    ".filter(i -&gt; i &lt; 10)\n" +
    ".map(i-&gt;  {\n" +
    "if (i == 0) {throw new IllegalArgumentException(&quot;Division by zero!&quot;);}\n" +
    "return (double) 1/i;}\n" +
    ")\n" +
    ".subscribe(\n" +
    "i -&gt; System.out.print(i + &quot;,&quot;),\n" +
    "err -&gt; System.err.println(err.toString())\n" +
    ");\n" +
    ".filter(i -&gt; i &gt;= 10) #distractor\n" +
    "return 1/i;} #distractor\n" +
    ".map(list -&gt; { #distractor\n" +
    "for(int i: list){ #distractor\n" +
    "} #distractor\n" +
    "Flux.just(List.of(5,15,3,0,17,-1)) #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "Task1-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "Task1-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#Task1-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#Task1-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

## Aufgabe 2

In der folgenden Aufgabe soll – analog zum Beispiel – aus einer Liste von IDs ein `Flux` erzeugt werden und mehrere Rating-Objekte abgefragt werden. Anschließend sollen nur die Bewertungen berücksichtigt werden, deren Zeitstempel vor dem Stichtag 01.01.2025 liegt. Diese gefilterten Bewertungen sollen anschließend zur Normierung mit dem Faktor *20* multipliziert und ausgegeben werden.

<div id="Task2-sortableTrash" class="sortable-code"></div> 
<div id="Task2-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="Task2-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="Task2-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "Instant cutoff = Instant.parse(&quot;2025-01-01T00:00:00Z&quot;);\n" +
    "Flux.fromIterable(List.of(5,15,3,17))\n" +
    ".flatMap(id-&gt;  webClient.get()\n" +
    ".uri(&quot;/ratings/{id}&quot;, id)\n" +
    ".retrieve()\n" +
    ".bodyToMono(RatingResponseDTO.class)\n" +
    ")\n" +
    ".filter(ratingResponseDTO -&gt; ratingResponseDTO.getDate().toInstant().isBefore(cutoff))\n" +
    ".map(rating -&gt; rating.getRating() * 20)\n" +
    ".subscribe(\n" +
    "res -&gt; System.out.print(res + &quot;,&quot;),\n" +
    "err -&gt; System.err.println(err.toString()));\n" +
    ".flatMap(rating -&gt; rating.getRating() * 20) #distractor\n" +
    ".map(id-&gt;  webClient.get() #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "Task2-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "Task2-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#Task2-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#Task2-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

## Aufgabe 3
Sortiert die Elemente so, dass der Code alle Einträge kleiner oder gleich 0 entfernt, und anschlißend eine neue Liste erzeugt, der diese in ihren "Kehrwert" umwandelt (also z -> 1/z).

<div id="A3-sortableTrash" class="sortable-code"></div> 
<div id="A3-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="A3-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="A3-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "List&lt;Double&gt; neueListeMitZahlen3 = listeMitZahlen\n" +
    ".stream()\n" +
    ".filter(z -&gt; z &gt; 0)\n" +
    ".map(z -&gt;  1.0 / z)\n" +
    ".toList();\n" +
    "  \n" +
    ".filter(z -&gt; z &lt;= 0) #distractor\n" +
    "List&lt;Integer&gt; neueListeMitZahlen3 = listeMitZahlen #distractor\n" +
    ".map(z -&gt;  z != 0) #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "A3-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "A3-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#A3-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#A3-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

## Aufgabe 4

Sortiert die Elemente so, dass der Code das Produkt aller Einträge bestimmt.

<div id="A4-sortableTrash" class="sortable-code"></div> 
<div id="A4-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="A4-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="A4-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "int produktAllerZahlen = listeMitZahlen\n" +
    ".stream()\n" +
    ".reduce(1, (produkt, z) -&gt; produkt * z);\n" +
    "  \n" +
    ".toList(); #distractor\n" +
    ".reduce(0, (produkt, z) -&gt; produkt * z); #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "A4-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "A4-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#A4-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#A4-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

## Aufgabe 5

Sortiert die Elemente so, dass der Code alle Einträge quadriert und anschließend aufsummiert.

<div id="A5-sortableTrash" class="sortable-code"></div> 
<div id="A5-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="A5-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="A5-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "int quadrataggregiert = listeMitZahlen\n" +
    ".stream()\n" +
    ".map(z -&gt; z * z)\n" +
    ".reduce(0, Integer::sum);\n" +
    ".toList(); #distractor\n" +
    ".reduce(1, Integer::sum); #distractor\n" +
    ".filter(z -&gt; z == z*z) #distractor\n" +
    ".reduce(0, (produkt, z) -&gt; produkt * z); #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "A5-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "A5-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#A5-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#A5-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

## Aufgabe 6

Sortiert die Elemente so, dass der Code dem Code auf den Slides entspricht, d.h. nur Werte verarbeitet, die nicht null sind und anschließend die Summe aller Werte bildet.
Dabei sollen zuvor alle Werte über 100 mit dem Faktor 0.8 multipliziert werden.

<div id="A6-sortableTrash" class="sortable-code"></div> 
<div id="A6-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="A6-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="A6-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "public double berechneSumme(List&lt;Optional&lt;Integer&gt;&gt; zahlenListe) {\n" +
    "return zahlenListe\n" +
    ".stream()\n" +
    ".filter(Optional::isPresent)\n" +
    ".map(Optional::get)\n" +
    ".map(zahl -&gt; zahl &gt; 100 ? zahl * 0.8 : zahl)\n" +
    ".reduce(0.0, Double::sum);\n" +
    "}\n" +
    ".map(z -&gt; z + s) #distractor\n" +
    ".toList(); #distractor\n" +
    "public double berechneSumme(List&lt;Integer&gt; zahlenListe) { #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "A6-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": false,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "A6-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#A6-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#A6-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>




