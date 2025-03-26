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




