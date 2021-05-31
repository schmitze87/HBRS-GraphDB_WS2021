# Panama Papers

# TOP 10
MATCH (inter:Intermediary)
MATCH (inter)-[r:INTERMEDIARY_OF]-(e:Entity)
WITH inter, count(r) as anzahl
ORDER BY anzahl DESC
RETURN inter, anzahl LIMIT 10;

# CONET???
MATCH (n)
WHERE n.name =~ '(?i).*conet.*'
RETURN n.name;

# HIG???
MATCH (e:Entity)
WHERE e.name CONTAINS 'H.I.G.'
return e;

- TAMER ANTHONY A. (Co-Founder & Co-CEO)
MATCH (o:Officer {name: 'TAMER ANTHONY A.'})
RETURN o;
- CORREA DAVID A. (‎Vice President, Global Tax & Private Equity Accounting - ‎H.I.G. Capital)

- Michael J. Weetch (DIRECTOR BARBADOS PORT INC.)



# Mossack Fonseca

MATCH (mossack) 
WHERE mossack.name CONTAINS 'MOSSACK FONSECA' 
return mossack.name;

MATCH (mossack) 
WHERE mossack.name = 'MOSSACK FONSECA & CO.' 
return mossack.name;

MATCH (mossack:Intermediary) 
WHERE mossack.name = 'MOSSACK FONSECA & CO.'
OPTIONAL MATCH (mossack)-[i:INTERMEDIARY_OF]->(n)
WITH mossack, count(i) as inters
ORDER BY inters DESC
with mossack LIMIT 1
MATCH (mossack)-[i2:INTERMEDIARY_OF]-(n)
return mossack, i2, n LIMIT 250;

## Interessante Personen
### Ukraine
- Petro Poroshenko (President Ukraine) Konzerne: Roshen, Prime Asset Partners Ltd.
MATCH (o:Officer)
WHERE o.name CONTAINS 'Petro Poroshenko'
OPTIONAL MATCH (o)-[r]-(n)
return *;


- Julia Timoschenko (ehemalige Premieministerin)
- Pawlo Lasarenko (Ex-Premier)
- Gennadij Truchanow (Bürgermeister Odessa) -> prorussiche Proteste

### Saudi Arabien
- Salman ibn Abd al-Aziz (König von Saudi Arabien)

### Azerbaijan
- Ilham Aliyev (President)
- Mehriban (seine Frau) (geborene Pashayev) Heydar Aliyev Foundation
- Leyla (Tocher)
- Arzu (Tochter) Goldmine
- Heydar (Sohn) 

### Island
- Sigmundur David Gunnlaugsson (Premier)
MATCH (n)
WHERE n.name CONTAINS 'Gunnlaugsson'
RETURN n;

### Argentinien
- Mauricio Macri (Präsident) Konzern: Fleg Trading in seiner Zeit als Bürgermeister
- Lionel Messi (argentinischer Fußballer)

### Deutschland
- Helmut Linssen (ehm. NRW Finanzminister CDU)

### Promis
- Michel Platini (Ex Präsident Uefa) Konzern: Balney Enterprises Corp.
- Jerome Valcke (Fifa-Generalsekretär) 
- Robert-Louis Dreyfus (6,7 Mio Euro um die WM 2006 nach Deutschland zu holen)
- Juan Pedro Damiani (Fifa-Ethikkomission gegen Korruption)
MATCH (n)
WHERE n.name =~ '(?i).*juan pedro damiani.*'
OPTIONAL MATCH (n)-[oOf:OFFICER_OF]->(m)-[interOf:INTERMEDIARY_OF]-(inter)
RETURN DISTINCT *;


- Gianni Infantino (Fifa-Chef)

- Ian Cameron (Vater von David Cameron (britischer Premier))
MATCH (n)
WHERE n.name = 'Ian Cameron'
OPTIONAL MATCH (n)-[r]-(m)
RETURN DISTINCT *;

- Nico Rosberg (Formel 1 Weltmeister 2016 - Karriere beendet) Zahlungen von Mercedes an Briefkastenfirma
- Sergej Roldugin (Cellist; einer der engsten Freunde von Putin)
- Jürgen Radomski (ehm. Siemens-Vorstand)


# Paradise Paper

## Unternehmen
- Apple 252 Mrd. $
"Apple International Holdings Ltd."
"Apple Enterprises Limited"
"Apple Trust"
"Apple Capital Ltd."
"Apple Investments Limited"
"Apple Exp Limited"
"Apple Resources Limited"

- Nike
- Uber
- Amazon

## Politiker

# Donald Trump
- Wilbur Ross (connected to Donald Trump "Handelsminister") Verbindung zu Putin 'WL Ross & Co'
- Rex Tillerson (Former CEO ExxonMobil) 'ExxonMobil'
- Randal Quarles 'Carlyle Group'
- Carl Icahn


# Saudi Arabien
- Prince Khaled bin Sultan bin Abdulaziz (Ehemaliger Verteidigungs Minister)

# Canada
- Jean Chrétien (Former Prime Minister)
- Paul Martin (Former Prime Minister)
- Brian Mulroney (Former Prime Minsiter)

# Japan
- Yukio Hatoyama (Former Prime Minsiter)

# Pakistan
- Shaukat Aziz (Former Prime Minsiter)

# UK
- Duchy of Lancaster (" Herzogtum Lancaster") Elizabeth II, Prince Charles 
MATCH (o:Officer {name: 'The Duchy of Lancaster'})-[r]-(e:Entity)
OPTIONAL MATCH (e)-[r2]-(n)
return *;





