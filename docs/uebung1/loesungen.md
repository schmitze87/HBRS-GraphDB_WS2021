# Erste Übungseinheit

Die Übungseinheit baut auf der in Neo4j mitgeliefertn Movie Database auf. Ziel der Übungs ist es, ein besseres Gefühl und Verständnis für die Abfragesprache Cypher zu erhalten. 

## Frage 1
In welches Filmen hat Tom Hanks mitgespielt?

```
MATCH (p:Person {name: 'Tom Hanks'})-[:ACTED_IN]->(m:Movie)
RETURN m.title;
```

## Frage 2
Jack Nicholson hat in so einigen Filmen mitgespielt. Dabei wurde er von den Regisseuren der Filme in denen er mitgespielt hat immer auf Partys eingeladen, bei denen auch stets seine Schauspielkollegen und Kolleginnen anwesend waren. Wer steht alles auf dieser Liste?

```
MATCH (p:Person {name: 'Jack Nicholson'})-[:ACTED_IN]->(m:Movie)
MATCH (m)<-[:DIRECTED]-(regie:Person)
MATCH (regie)-[:DIRECTED]->(m2:Movie)<--(p2:Person)
RETURN DISTINCT p2.name;
```

## Frage 3
In welchem Jahr sind die meisten Filme erschienen?

```
MATCH (m:Movie)
WITH m.released as `Jahr der Veröfentlichung`, count(*) as `Anzahl Filme`
RETURN * ORDER BY `Anzahl Filme` DESC
```

## Frage 4
Welche Filme wurdem im Jahr 2000 veröffentlich?

```
MATCH (m:Movie)
WHERE m.released = 2000
RETURN m;
```

## Frage 5 
Welche Schauspielerin bzw. Schauspieler hat den meisten Personen am Set zusammengearbeitet.

## Frage 6
Welche Filme wurden in den 90er Jahren veröffentlich?

```
MATCH (m:Movie)
WHERE 1990 < m.released < 2000
RETURN m.title, m.released;
```

## Frage 7
Welche Personen haben bei den Filmen der 90er Regie geführt?

```
MATCH (m:Movie)<-[:DIRECTED]-(p:Person)
WHERE 1990 < m.released < 2000
RETURN m.title, m.released;
```

## Frage 8
Wer war alles an dem Film Cloud Atlas beteiligt?

```
MATCH (m:Movie {title: "Cloud Atlas"})--(p:Person)
RETURN p.name;
```

## Frage 9
Welche Schauspieler haben mit Tom Hanks noch keinen gemeinsamen Film gedreht, haben aber bereits mit Kollegen von TOm Hanks zusammengearbeitet? Sortiere die Liste absteigend nach der Häufigkeit.

```

```