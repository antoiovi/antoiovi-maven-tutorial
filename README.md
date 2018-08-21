# antoiovi-maven-tutorial

Sono contenuti diversi progetti in ordine crescente di difficoltà per spiegare l'utilizzo di maven per la realizzazione di applicazioni java ;
Inoltre continunando nella complessità è possibile utilizzare i framework come modelli base per diversi tipi di applicazione.


# Intro

Maven si esegue da riga di comando inserendo mvn ed il nome del comando da eseguire
$ mvn plugin:goal  -arg --arg
$ mvn goal -arg --arg
I comandi di maven si riferiscono tutti a dei plugin. alcuni inseriti nel core del programma , altri esterni e/o importati.
Ogni comando da eseguire ha un goal (obbiettivo) a cui è mirato, ovvero lo scopo del comando.
## Esempi di comandi
>Vengono mostarti alcuni esempi di comandi per mostrare la sintassi .

Questi comandi eseguono il goal di default del rispettivo plugin e non necessitano del nome del plugin (clean:clean, esegue la fase clean; compiler:compile, install:install...)

    $ mvn clean
    $ mvn compile
    $ mvn install
Mostra l'help :

    $ mvn -h
    $ mvn --help
    
Il seguente comando esegue il plugin archetype con goal generate ; opzione  -D (--define) : definisce una proprietà e gli assegna (=) un valore;

    $ mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart  -DarchetypeVersion=1.3
    
 
## Punti chiave
Alcuni punti seguenti potrebbero inizialmente essere poco chiari; ma questo vuole essere uno specchietto di riferimento a cui riferirsi anche successivamente.

I punti chiave sono
* La struttura delle directories del progetto
* il file POM.xml
* gli archetipes
* le dependencies
* i goals (obbbiettivi)

#### Plugins e Goals

#### Lifecycles
[Riferimento : https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html]
Il processo di costruzione e distribuzione di un progetto è chiaramente definito.
La definzione precisa del processo di esecuzione è una sequenza di fasi.
Le fasi sono esgeuite da alcuni comandi di alcuni plugins (vedere [https://maven.apache.org/plugins/index.html]) .
Sono definite tre built-in sequenze di fasi (lifecicles) : **default, clean, deploy**.
Per completezza vi sono diverese fasi intermedie non qui elencate (vedere https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html Life Cycle Reference)

##### default
La **default** lifecicle è :
- validate
- compile
- test
- package
- verify
- install
- deploy

se eseguo

    $mvn install

vengono eseguite tutte le fasi in ordine fino a install (deploy esluso)

se eseguo 

    $mvn compile

vengono eseguite le fasi validate e compile;

##### clean e deploy

per queste fasi vedere la documentazione ufficiale (https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html)






## 01-base
In un progetto java la struttura delle directory è molto importante in quanto è strettamente correlata al concetto di package;

Un primo vantaggio di utilizzare un framework come maven è che creando un progetto viene creata una struttura di directories standard, ed i comandi di compilazione terranno conto di questa struttura nella creazione del progetto finale;

Qunindi in questo capitolo si vedono : 
    
	- la creazione di un progetto basico
	- la compilazione ed esecuzione del progetto
        - la modifica del progetto per creare un modello (archetype) personalizzato
    
### Creazione del più semplice progetto (del più semplice archetype)
* [Riferimento ](https://maven.apache.org/archetypes/maven-archetype-quickstart/) - Pagina ufficiale di MAVEN : Maven quickstart archetype
Eseguendo il seguente comando in una directory qualsiasi :
```sh
     mvn archetype:generate -DarchetypeGroupId=org.apache.maven.archetypes -DarchetypeArtifactId=maven-archetype-quickstart  -DarchetypeVersion=1.3
```
Vengono richiesti i seguenti input :
```sh
    Define value for property 'groupId': $package
    Define value for property 'artifactId': project
    Define value for property 'version' 1.0-SNAPSHOT: : 
    Define value for property 'package' $package : 
```
dove per groupId si inserisce , per esempio 'com.antoiovi.project'; e  alla propietà 'package viene proposto di default il valore inserito per la proprieta groupId;
Per aertifactId viene iserito il nome del progetto da creare, e viene creta la directory con questo nome.
Viene quindio creata la seguente struttura di cartelle e files :

```sh
    project
    |-- pom.xml
    `-- src
        |-- main
        |   `-- java
        |       `-- $package
        |           `-- App.java
        `-- test
            `-- java
                `-- $package
                    `-- AppTest.java
```

Nella cartella 01-Base si trova il progetto base01 creato inserendo i seguenti valori :
```sh
    Define value for property 'groupId': com.antoiovi.base01
    Define value for property 'artifactId': base01
```


## 03-jpa
