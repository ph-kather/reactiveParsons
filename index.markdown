Mit diesen Aufgaben möchte ich die grundlegende Syntax von reaktiver Programmierung in Java einüben.
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

---

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

---


# Übung

## Aufgabe 1

In dieser Aufgabe soll der Endpunkt `ratings/originalRatings` implementiert werden.
Dieser erhält eine Liste von IDs als Eingabe. Für jede dieser IDs soll mithilfe des `webClient` eine GET-Anfrage an den Endpunkt `/{id}/getOriginalVersion` eines weiteren Services durchgeführt werden.
Die Antworten sollen anschließend gesammelt und als ein `Flux<RatingResponseDTO> zurückgegeben werden.

<div id="Exercise1-sortableTrash" class="sortable-code"></div> 
<div id="Exercise1-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="Exercise1-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="Exercise1-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "return Flux.fromIterable(ids)\n" +
    ".flatMap(id -&gt;\n" +
    "webClient.get()\n" +
    ".uri(&quot;/{id}/getOriginalVersion&quot;, id)\n" +
    ".retrieve()\n" +
    ".bodyToMono(RatingResponseDTO.class)\n" +
    ");\n" +
    " .map(id -&gt; #distractor\n" +
    " .subscribe( #distractor\n" +
    " rating -&gt; return rating, #distractor\n" +
    " err -&gt; System.out.println(&quot;Error!&quot;)); #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "Exercise1-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "Exercise1-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#Exercise1-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#Exercise1-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>

## Aufgabe 2

In dieser Aufgabe soll der Endpunkt `ratings/trends` implementiert werden.
Dieser soll mithilfe des `webClient` eine GET-Anfrage an den Endpunkt `ratings/mostRecent` duchführen, um aktuelle Bewertungen abzurufen.
Aus der Antwort soll anschließend der Durchschnitt gebildet werden und als `Mono<Double>` zurückgegeben werden.
Sollte es zu einem Fehler kommen, soll als Fallback -1 ausgegeben werden.

<div id="Exercise2-sortableTrash" class="sortable-code"></div> 
<div id="Exercise2-sortable" class="sortable-code"></div> 
<div style="clear:both;"></div> 
<p> 
    <input id="Exercise2-feedbackLink" value="Get Feedback" type="button" /> 
    <input id="Exercise2-newInstanceLink" value="Reset Problem" type="button" /> 
</p> 
<script type="text/javascript"> 
(function(){
  var initial = "return webClient.get()\n" +
    ".uri(&quot;/mostRecent&quot;)\n" +
    ".retrieve()\n" +
    ".bodyToFlux(RatingResponseDTO.class)\n" +
    ".map(RatingResponseDTO::getRating)\n" +
    ".collectList()\n" +
    ".map(this::calculateAverage)\n" +
    ".onErrorResume(e -&gt; Mono.just(-1.0));\n" +
    ".flatMap(RatingResponseDTO::getRating) #distractor\n" +
    ".flatMap(this::calculateAverage) #distractor\n" +
    ".subscribe( #distractor\n" +
    "err -&gt; return Mono.just(-1.0)); #distractor\n" +
    "rating -&gt; return this::calculateAverage, #distractor";
  var parsonsPuzzle = new ParsonsWidget({
    "sortableId": "Exercise2-sortable",
    "max_wrong_lines": 10,
    "grader": ParsonsWidget._graders.LineBasedGrader,
    "exec_limit": 2500,
    "can_indent": true,
    "x_indent": 50,
    "lang": "en",
    "show_feedback": true,
    "trashId": "Exercise2-sortableTrash"
  });
  parsonsPuzzle.init(initial);
  parsonsPuzzle.shuffleLines();
  $("#Exercise2-newInstanceLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.shuffleLines(); 
  }); 
  $("#Exercise2-feedbackLink").click(function(event){ 
      event.preventDefault(); 
      parsonsPuzzle.getFeedback(); 
  }); 
})(); 
</script>


