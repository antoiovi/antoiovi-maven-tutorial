# antoiovi-maven-tutorial

Sono contenuti diversi progetti in ordine crescente di difficoltà per spiegare l'utilizzo di maven per la realizzazione di applicazioni java ;
Inoltre continunando nella complessità è possibile utilizzare i framework come modelli base per diversi tipi di applicazione.


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
e viene creata la seguente struttura di cartelle e files :

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



## 03-jpa
