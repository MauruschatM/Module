<h1>Klausurtipps und Themen</h1>  
  
<nav id="menu">  
 <ul> <li><a href="#tipps">Tipps</a></li>  
 <li><a href="#annotationsklassen">Annotationsklassen</a></li>  
 <li><a href="#reflections">Reflections</a></li>  
 <li><a href="#lombok">Lombok</a></li>  
 <li><a href="#xsd">XSD & XPath</a></li>  
 <li><a href="#architektur">Architektur</a></li>  
 <li><a href="#jpa">JPA</a></li>  
 <li><a href="#messaging">Messaging</a></li>  
 <li><a href="#wsdl">WSDL</a></li>  
 <li><a href="#protobuf">Protobuf</a></li>  
 <li><a href="#rest">REST</a></li>  
 </ul></nav>  
  
<section id="tipps">  
 <h2>Some hints</h2>  
  
 <div class="tip">  
 <h3>1\. Genaues Lesen</h3>  
 <p>Lesen Sie die Aufgaben sorgfältig und achten Sie auf Details. Übersehen Sie keine wichtigen Informationen  
            oder Hinweise, die den Unterschied zwischen 0% und 100% der Punkte ausmachen können.</p>  
 </div>  
 <div class="tip">  
 <h3>2\. Zeitmanagement</h3>  
 <p>Achten Sie auf Ihre Zeit. Bleiben Sie nicht zu lange an einer Aufgabe hängen. Nutzen Sie die Lesezeit zur  
            Planung. 1 Punkt entspricht 1 Minute Bearbeitungszeit.</p>  
 </div>  
 <div class="tip">  
 <h3>3\. Zusatzpunkte</h3>  
 <p>Die Klausur enthält Zusatzpunkte, damit Sie einige Aufgaben überspringen können.</p>  
 </div>  
 <div class="tip">  
 <h3>4\. Bewertung</h3>  
 <p>"am besten geeignet" - Wählen Sie die am besten geeignete Antwort aus.</p>  
 </div>  
 <div class="tip">  
 <h3>5\. Punktevergabe</h3>  
 <p>1 bedeutet 1, 2 bedeutet 2, 3 bedeutet 3, und so weiter.</p>  
 </div></section>  
  
<h2>More hints</h2>  
  
<section id="annotationsklassen">  
 <div class="topic">  
 <h3>Annotationsklassen in Java</h3>  
  
 <h4>Grundlagen</h4>  
 <p>Annotations sind spezielle Interfaces in Java, die Metainformationen zu Klassen, Methoden oder Feldern  
            hinzufügen. Sie werden mit <code>@interface</code> definiert.</p>  
 <code>   public @interface ClassMetadata {<br>  
   &nbsp;&nbsp;String author();<br>  
   &nbsp;&nbsp;String date();<br>  
   &nbsp;&nbsp;String\[\] reviewers() default "None";<br>  
   }  
        </code>  
  
 <h4>Verwendung von Annotationen</h4>  
 <p>Annotations können auf verschiedene Java-Elemente angewendet werden, z.B.:</p>  
 <code>   @Override<br>  
   public void myMethod() { ... }  
        </code>  
 <p>Hier wird sichergestellt, dass die Methode aus einer Superklasse überschrieben wird.</p>  
  
 <h4>Erstellung eigener Annotationen</h4>  
 <p>Eigene Annotationen können spezifische Attribute enthalten:</p>  
 <code>   public @interface Author {<br>  
   &nbsp;&nbsp;String name();<br>  
   &nbsp;&nbsp;String date();<br>  
   }  
        </code>  
 <p>Verwendung:</p>  
 <code>   @Author(name = "Max Mustermann", date = "2024-07-20")<br>  
   public class MyClass { ... }  
        </code>  
  
 <h4>Meta-Annotationen</h4>  
 <p>Zur Steuerung der Anwendbarkeit von Annotationen gibt es Meta-Annotationen wie <code>@Target</code> und  
            <code>@Retention</code>:</p>  
 <code>   @Retention(RetentionPolicy.RUNTIME)<br>  
   @Target(ElementType.TYPE)<br>  
   public @interface MyAnnotation { ... }  
        </code>  
  
 <h4>Erweiterte Java Annotationen</h4>  
 <p>Zusätzliche Meta-Annotationen:</p>  
 <code>   @Inherited<br>  
   @Documented<br>  
   @Repeatable(Annotations.class)  
        </code>  
  
 <h4>Verwendung in Frameworks</h4>  
 <p>Annotationen werden häufig in Frameworks wie Spring verwendet, um Dependency Injection und  
            Konfigurationsmanagement zu vereinfachen:</p>  
 <code>   @Autowired<br>  
   private MyService service;  
        </code>  
  
 <h4>Reflektierte Annotationen</h4>  
 <p>Mit Reflektion können Annotationen zur Laufzeit ausgelesen werden:</p>  
 <code>   Author authorInfo = MyClass.class.getAnnotation(Author.class);<br>  
   System.out.println("Author: " + authorInfo.name());  
        </code>  
  
 <h4>Best Practices</h4>  
 <p>Empfehlungen:</p>  
 <ul> <li>Vermeiden Sie übermäßige Verwendung von Annotationen.</li>  
 <li>Verwenden Sie sprechende Namen für Annotationen und deren Attribute.</li>  
 <li>Dokumentieren Sie eigene Annotationen gut.</li>  
 </ul>  
 <h4>Projekt Lombok</h4>  
 <p>Lombok bietet eine Reihe von Annotationen zur Reduzierung von Boilerplate-Code:</p>  
 <code>   @Data<br>  
   @AllArgsConstructor<br>  
   @NoArgsConstructor<br>  
   @Builder  
        </code>  
 <p>Beispiel:</p>  
 <code>   @Data<br>  
   @AllArgsConstructor<br>  
   @NoArgsConstructor<br>  
   public class User {<br>  
   &nbsp;&nbsp;private String name;<br>  
   &nbsp;&nbsp;private int age;<br>  
   }  
        </code>  
 </div></section>  
  
<section id="reflections">  
 <div class="topic">  
 <h3>Reflections in Java</h3>  
  
 <h4>Einführung</h4>  
 <p>Reflections ermöglichen es Java-Programmen, zur Laufzeit Informationen über Klassen, Methoden und Felder zu  
            ermitteln und zu manipulieren. Dies ist besonders nützlich für Frameworks, die allgemeine Lösungen für  
            verschiedene Klassen bereitstellen müssen.</p>  
  
 <h4>Grundlegende Konzepte</h4>  
 <p>Mit Reflections kann ein Programm:</p>  
 <ul> <li>Informationen über eine Klasse und ihre Methoden, Felder und Konstruktoren ermitteln.</li>  
 <li>Methoden und Felder unabhängig von deren Zugriffsmodifikatoren aufrufen oder ändern.</li>  
 <li>Neue Instanzen von Klassen zur Laufzeit erstellen.</li>  
 </ul>  
 <h4>Codebeispiel: Zugriff auf private Felder</h4>  
 <pre><code>public class Beispiel {  
    private String geheim = "versteckt";  
  
    public static void main(String\[\] args) throws Exception {  
        Beispiel obj = new Beispiel();  
        Field feld = Beispiel.class.getDeclaredField("geheim");  
        feld.setAccessible(true);  
        System.out.println(feld.get(obj)); // Ausgabe: versteckt  
    }  
}</code></pre>  
  
 <h4>Codebeispiel: Aufrufen von Methoden</h4>  
 <pre><code>public class Beispiel {  
    private String geheim = "versteckt";  
  
    private String getGeheim() {  
        return geheim;  
    }  
  
    public static void main(String\[\] args) throws Exception {  
        Beispiel obj = new Beispiel();  
        Method methode = Beispiel.class.getDeclaredMethod("getGeheim");  
        methode.setAccessible(true);  
        String ergebnis = (String) methode.invoke(obj);  
        System.out.println(ergebnis); // Ausgabe: versteckt  
    }  
}</code></pre>  
  
 <h4>Praktische Anwendungen</h4>  
 <p>Reflections werden häufig in Frameworks wie Spring und Hibernate verwendet, um Abhängigkeiten zu injizieren,  
            Objekte zu serialisieren/deserialisieren und Konfigurationen zur Laufzeit zu ändern.</p>  
  
 <h4>Erstellung neuer Instanzen</h4>  
 <pre><code>public class Beispiel {  
    public Beispiel() {  
        System.out.println("Neue Instanz erstellt");  
    }  
  
    public static void main(String\[\] args) throws Exception {  
        Class<Beispiel> clazz = Beispiel.class;  
        Beispiel obj = clazz.getDeclaredConstructor().newInstance();  
    }  
}</code></pre>  
  
 <h4>Gefahren und Risiken</h4>  
 <p>Die Verwendung von Reflections kann die Performance verschlechtern und führt zu Code, der schwer zu debuggen  
            und zu warten ist. Es können Sicherheitslücken entstehen, wenn private Felder und Methoden geändert  
            werden.</p>  
 </div></section>  
  
<section id="lombok">  
 <div class="topic">  
 <h3>Lombok: Vereinfachung von Java-Code</h3>  
  
 <h4>Was ist Lombok?</h4>  
 <p>Project Lombok ist eine Java-Bibliothek, die Boilerplate-Code reduziert, indem sie über Annotations  
            automatisch Methoden wie Getter, Setter, Konstruktoren und mehr generiert.</p>  
  
 <h4>Wichtige Annotations</h4>  
 <p>Hier sind einige der wichtigsten Lombok-Annotations mit Beispielen:</p>  
 <ul> <li><code>@Getter</code> und <code>@Setter</code>: Generiert Getter- und Setter-Methoden für die Felder.  
                <code>  
 <pre>   public class User {  
                @Getter @Setter private String name;  
            }  
            </pre>  
 </code> </li> <li><code>@ToString</code>: Generiert eine <code>toString()</code>-Methode.  
                <code>  
 <pre>   @ToString  
            public class User {  
                private String name;  
            }  
            </pre>  
 </code> </li> <li><code>@EqualsAndHashCode</code>: Generiert <code>equals()</code> und <code>hashCode()</code>-Methoden.  
                <code>  
 <pre>   @EqualsAndHashCode  
            public class User {  
                private String name;  
            }  
            </pre>  
 </code> </li> <li><code>@AllArgsConstructor</code>: Generiert einen Konstruktor mit allen Feldern als Parameter.  
                <code>  
 <pre>   @AllArgsConstructor  
            public class User {  
                private String name;  
            }  
            </pre>  
 </code> </li> <li><code>@NoArgsConstructor</code>: Generiert einen Standardkonstruktor.  
                <code>  
 <pre>   @NoArgsConstructor  
            public class User {  
                private String name;  
            }  
            </pre>  
 </code> </li> <li><code>@Log</code>: Erstellt eine Logger-Instanz.  
                <code>  
 <pre>   @Log  
            public class User {  
                public User() {  
                    log.info("User created");  
                }  
            }  
            </pre>  
 </code> </li> </ul>  
 <h4>Erweiterte Annotations</h4>  
 <p>Lombok bietet auch erweiterte Annotations für spezifische Anwendungsfälle:</p>  
 <ul> <li><code>@Builder</code>: Erzeugt einen Builder für die Klasse.  
                <code>  
 <pre>   @Builder  
            public class User {  
                private String name;  
                private int age;  
            }  
            </pre>  
 </code> </li> <li><code>@Data</code>: Eine Kombination aus <code>@Getter</code>, <code>@Setter</code>,  
                <code>@ToString</code>, <code>@EqualsAndHashCode</code> und <code>@RequiredArgsConstructor</code>.  
                <code>  
 <pre>   @Data  
            public class User {  
                private String name;  
                private int age;  
            }  
            </pre>  
 </code> </li> </ul>  
 <h4>Kompatibilität und Einschränkungen</h4>  
 <p>Während Lombok viele Vorteile bietet, gibt es auch einige Einschränkungen und Kompatibilitätsprobleme:</p>  
 <ul> <li>Kann Probleme mit bestimmten IDEs oder Build-Tools verursachen.</li>  
 <li>Erfordert eine zusätzliche Konfiguration für einige Annotations.</li>  
 <li>Kann den Lesefluss des Codes für Entwickler stören, die Lombok nicht kennen.</li>  
 </ul>  
 <h4>Praktische Tipps zur Nutzung von Lombok</h4>  
 <ul> <li>Stelle sicher, dass alle Teammitglieder mit Lombok vertraut sind.</li>  
 <li>Verwende Lombok-Annotations sparsam, um die Code-Lesbarkeit zu erhalten.</li>  
 <li>Nutze die Lombok-Dokumentation für detaillierte Informationen und Best Practices.</li>  
 </ul>  
 <h4>Häufige Probleme und Lösungen</h4>  
 <p>Einige häufige Probleme und deren Lösungen bei der Verwendung von Lombok:</p>  
 <ul> <li><strong>Problem:</strong> Lombok-Annotations werden nicht erkannt.  
                <br><strong>Lösung:</strong> Stelle sicher, dass Lombok korrekt in den Build-Tools (z.B. Maven, Gradle)  
                integriert ist.  
            </li>  
 <li><strong>Problem:</strong> Konflikte mit anderen Bibliotheken.  
                <br><strong>Lösung:</strong> Überprüfe die Dokumentation und Foren für bekannte Konflikte und Lösungen.  
            </li>  
 </ul> </div></section>  
  
<section id="xsd">  
 <div class="topic">  
 <h3>XSD und XPath</h3>  
  
 <h4>Einführung in XSD</h4>  
 <p>XML Schema Definition (XSD) ist eine Sprache zur Definition der Struktur und des Inhalts von XML-Dokumenten.  
            Es ermöglicht die Validierung von XML-Dokumenten gegen ein definiertes Schema.</p>  
 <code>&lt;xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"&gt; ... &lt;/xs:schema&gt;</code>  
  
 <h4>Grundstruktur eines XSD-Dokuments</h4>  
 <code>   &lt;xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"&gt;  
 &lt;xs:element name="note"&gt;  
 &lt;xs:complexType&gt;  
 &lt;xs:sequence&gt;  
 &lt;xs:element name="to" type="xs:string"/&gt;  
 &lt;xs:element name="from" type="xs:string"/&gt;  
 &lt;xs:element name="heading" type="xs:string"/&gt;  
 &lt;xs:element name="body" type="xs:string"/&gt;  
 &lt;/xs:sequence&gt;  
 &lt;/xs:complexType&gt;  
 &lt;/xs:element&gt;  
 &lt;/xs:schema&gt;  
   </code>  
  
 <h4>Namespace in XML</h4>  
 <p>Namespaces in XML dienen zur Vermeidung von Namenskonflikten und zur Zuordnung von Elementen zu bestimmten  
            Schemas.</p>  
 <code>   &lt;note xmlns="http://www.example.com/note"&gt;  
 &lt;to&gt;Tove&lt;/to&gt;  
 &lt;from&gt;Jani&lt;/from&gt;  
 &lt;/note&gt;  
   </code>  
  
 <h4>XSD-Elemente und Attribute</h4>  
 <p>XSD unterscheidet zwischen einfachen und komplexen Typen. Einfache Typen enthalten nur Text, während komplexe  
            Typen verschachtelte Elemente und Attribute enthalten können.</p>  
 <code>   &lt;xs:element name="price" type="xs:decimal"/&gt;  
 &lt;xs:complexType name="address"&gt;  
 &lt;xs:sequence&gt;  
 &lt;xs:element name="street" type="xs:string"/&gt;  
 &lt;xs:element name="city" type="xs:string"/&gt;  
 &lt;xs:element name="zipcode" type="xs:string"/&gt;  
 &lt;/xs:sequence&gt;  
 &lt;/xs:complexType&gt;  
   </code>  
  
 <h4>Selbstdefinierte einfache Typen</h4>  
 <p>Selbstdefinierte einfache Typen basieren auf Basistypen und werden durch Einschränkungen (Facets)  
            definiert.</p>  
 <code>   &lt;xs:simpleType name="restrictedString"&gt;  
 &lt;xs:restriction base="xs:string"&gt;  
 &lt;xs:minLength value="5"/&gt;  
 &lt;xs:maxLength value="10"/&gt;  
 &lt;/xs:restriction&gt;  
 &lt;/xs:simpleType&gt;  
   </code>  
  
 <h4>XPath-Grundlagen</h4>  
 <p>XPath ist eine Sprache zur Abfrage von XML-Dokumenten. Sie ermöglicht die Auswahl von Knoten basierend auf  
            einer hierarchischen Struktur.</p>  
 <code>   /child::A/child::B/child::C\[@num &lt; 3\]  
        </code>  
  
 <h4>XPath-Achsen</h4>  
 <p>Achsen definieren die Richtung, in die von dem aktuellen Knoten aus navigiert wird. Beispiele sind <code>child</code>,  
            <code>descendant</code>, <code>parent</code> und <code>following-sibling</code>.</p>  
 <code>   /descendant::book/child::title  
        </code>  
  
 <h4>Knotentests in XPath</h4>  
 <p>Knotentests bestimmen, welche Knoten als Ergebnis eines Ortsschritts ausgewählt werden. Beispiele sind <code>node()</code>,  
            <code>text()</code> und <code>comment()</code>.</p>  
 <code>   /descendant::text()  
        </code>  
  
 <h4>XPath-Funktionen</h4>  
 <p>XPath bietet eine Reihe von Funktionen zur Manipulation von Werten und Knoten, wie <code>count()</code>,  
            <code>sum()</code> und <code>string()</code>.</p>  
 <code>   count(//book)  
        </code>  
  
 <h4>Validierung mit XSD</h4>  
 <p>Die Validierung eines XML-Dokuments gegen ein XSD stellt sicher, dass das Dokument einer vordefinierten  
            Struktur entspricht.</p>  
 <code>   &lt;xs:schema ...&gt;  
 &lt;xs:element name="person" type="personType"/&gt;  
 &lt;xs:complexType name="personType"&gt;  
 &lt;xs:sequence&gt;  
 &lt;xs:element name="firstname" type="xs:string"/&gt;  
 &lt;xs:element name="lastname" type="xs:string"/&gt;  
 &lt;/xs:sequence&gt;  
 &lt;xs:attribute name="id" type="xs:integer" use="required"/&gt;  
 &lt;/xs:complexType&gt;  
 &lt;/xs:schema&gt;  
   </code>  
 </div></section>  
  
<section id="architektur">  
 <div class="topic">  
 <h3>Architektur</h3>  
  
 <h4>Architekturstile</h4>  
  
 <h5>Monolithische Architektur</h5>  
 <p>Eine Architektur, bei der alle Funktionen in einer einzigen Anwendung integriert sind.</p>  
  
 <h5>Microservice-basierte Architektur</h5>  
 <p>Architektur, bei der Anwendungen aus kleinen, unabhängigen Diensten bestehen, die jeweils eine spezifische  
            Funktion erfüllen.</p>  
  
 <h5>Service-orientierte Architektur (SOA)</h5>  
 <p>Architektur, die Dienste nutzt, die über ein Netzwerk kommunizieren, um Geschäftsprozesse zu  
            unterstützen.</p>  
  
 <h4>Schichten und Komponenten</h4>  
  
 <h5>1-Tier Architektur</h5>  
 <p>Eine monolithische Architektur, bei der alle Schichten in einer einzigen Einheit kombiniert sind.</p>  
  
 <h5>2-Tier Architektur</h5>  
 <p>Client-Server-Architektur, bei der die Präsentationsschicht auf dem Client und die Anwendungsschicht auf dem  
            Server liegt.</p>  
  
 <h5>3-Tier Architektur</h5>  
 <p>Die 3-Tier Architektur teilt ein Informationssystem in drei Schichten:</p>  
 <ul> <li><strong>Präsentationsschicht:</strong> Schnittstelle für den Benutzer (z.B. <code>HTML</code>,  
                <code>CSS</code>).  
            </li>  
 <li><strong>Anwendungsschicht:</strong> Geschäftslogik (z.B. <code>Java</code>, <code>Python</code>).</li>  
 <li><strong>Datenhaltungsschicht:</strong> Datenverwaltung (z.B. <code>SQL</code>, <code>NoSQL</code>).</li>  
 </ul>  
 <h5>n-Tier Architektur</h5>  
 <p>Die n-Tier Architektur erweitert die 3-Tier Architektur durch zusätzliche Schichten:</p>  
 <ul> <li><strong>Webserver-Schicht:</strong> Vermittler zwischen Client und Anwendung (z.B. <code>Apache</code>,  
                <code>NGINX</code>).  
            </li>  
 <li><strong>Middleware-Schicht:</strong> Dienste wie Transaktionsmanagement, Sicherheit (z.B. <code>API  
                Gateway</code>).  
            </li>  
 <li><strong>Dienste-Schicht:</strong> Spezifische Dienste wie Authentifizierung (z.B. <code>OAuth</code>).  
            </li>  
 </ul>  
 <h5>Vergleich 3-Tier vs. n-Tier</h5>  
 <p>Hauptunterschiede:</p>  
 <ul> <li><strong>Komplexität:</strong> n-Tier ist komplexer durch zusätzliche Schichten.</li>  
 <li><strong>Flexibilität:</strong> Höhere Anpassungsfähigkeit durch modulare Struktur.</li>  
 <li><strong>Skalierbarkeit:</strong> Bessere Skalierbarkeit durch feinere Granularität.</li>  
 <li><strong>Wartung:</strong> Einfachere Wartung und Aktualisierung einzelner Komponenten.</li>  
 </ul>  
 <h5>Middleware in n-Tier Architekturen</h5>  
 <p>Middleware bietet folgende Vorteile:</p>  
 <ul> <li>Vereinfachung des Client-Designs durch Reduzierung der Schnittstellen.</li>  
 <li>Transparenter Zugriff auf zugrunde liegende Systeme.</li>  
 <li>Unterstützung der Skalierbarkeit und Erweiterbarkeit.</li>  
 </ul> <code>   Beispiel: Middleware kann als API Gateway fungieren, das Anfragen vom Client an den entsprechenden  
            Microservice weiterleitet.  
        </code>  
  
 <h5>Skalierbarkeit und Flexibilität</h5>  
 <p>n-Tier Architekturen bieten bessere Skalierbarkeit und Flexibilität durch:</p>  
 <ul> <li>Feinere Granularität der Schichten.</li>  
 <li>Unabhängige Skalierung der stateless und stateful Komponenten.</li>  
 </ul>  
 <h5>Sicherheitsaspekte</h5>  
 <p>Implementierung von Sicherheitsaspekten:</p>  
 <ul> <li><strong>Authentifizierung:</strong> Sicherstellung der Identität (z.B. <code>OAuth</code>).</li>  
 <li><strong>Autorisierung:</strong> Rechteüberprüfung (z.B. <code>ACL</code>).</li>  
 <li><strong>Vertraulichkeit:</strong> Schutz der Daten (z.B. <code>SSL/TLS</code>).</li>  
 </ul>  
 <h5>Beispiele für 3-Tier und n-Tier Architekturen</h5>  
 <p>Beispiel für eine 3-Tier Architektur:</p>  
 <pre><code>Client (Browser)  
    |  
Webserver (Apache)  
    |  
Anwendungsserver (Tomcat)  
    |  
Datenbankserver (MySQL)  
</code></pre>  
  
 <p>Beispiel für eine n-Tier Architektur:</p>  
 <pre><code>Client (Browser)  
    |  
Load Balancer  
    |  
Webserver (NGINX)  
    |  
Application Server (Spring Boot)  
    |  
Middleware (API Gateway)  
    |  
Microservices  
    |  
Datenbankserver (MongoDB)  
</code></pre>  
 </div> <div class="topic">  
 <h3>Architektur und QoS (Quality of Service)</h3>  
  
 <h4>Einführung in die Softwarearchitektur</h4>  
 <p>Softwarearchitektur beschreibt die Struktur von Software auf einer größeren Ebene, einschließlich  
            existierendem Code, externen Systemen, neuen Code und Hardware-Adaptern.</p>  
  
 <h4>Komponenten als logische Einheiten</h4>  
 <p>Komponenten sind logische Abstraktionen mit festgelegten Schnittstellen und Abhängigkeiten. Sie können in  
            verschiedenen Programmiersprachen realisiert und aus anderen Softwarekomponenten zusammengesetzt werden.</p>  
 <p><code>interface Komponente { void operation(); }</code></p>  
  
 <h4>Schichten und Komponenten</h4>  
 <p>Komponenten werden oft in Schichten (Layers) gruppiert, z.B. Präsentationsschicht, Anwendungsschicht und  
            Ressourcenverwaltungsschicht.</p>  
 <p><code>// Beispiel: Präsentationsschicht  
            class GUI { void render(); }</code></p>  
  
 <h4>Middleware</h4>  
 <p>Middleware ist eine Zwischenschicht, die die Komplexität der Interaktion zwischen verschiedenen Systemen  
            reduziert und eine gemeinsame Schnittstelle bereitstellt.</p>  
 <p><code>class Middleware { void handleRequest(Request req); }</code></p>  
  
 <h4>Design Patterns</h4>  
 <p>Gängige Design Patterns helfen bei der Lösung wiederkehrender Probleme in der Softwarearchitektur:</p>  
 <ul> <li><strong>Adapter:</strong> Konvertiert eine Schnittstelle in eine andere.</li>  
 <li><strong>Fabrikmethode:</strong> Erzeugt Objekte, ohne die konkrete Klasse anzugeben.</li>  
 <li><strong>Singleton:</strong> Stellt sicher, dass eine Klasse nur eine Instanz hat.</li>  
 </ul> <code>   Beispiel: Der Adapter Pattern kann verwendet werden, um zwei inkompatible Schnittstellen zu verbinden.  
        </code>  
  
 <h4>Top-Down vs. Bottom-Up Design</h4>  
 <p>Top-Down Design beginnt mit der Definition der Zugriffskanäle und Client-Plattformen, während Bottom-Up  
            Design bestehende Ressourcen und deren Funktionalität integriert.</p>  
  
 <h4>Qualität von Service (QoS)</h4>  
 <p>QoS umfasst Leistung, Verfügbarkeit, Skalierbarkeit und Sicherheit eines Systems, oft festgelegt in Service  
            Level Agreements (SLAs).</p>  
  
 <h5>Leistung</h5>  
 <p>Leistung wird in Latenz (Antwortzeit) und Durchsatz (Anfragen pro Sekunde) gemessen.</p>  
  
 <h5>Verfügbarkeit</h5>  
 <p>Verfügbarkeit beschreibt die Fähigkeit eines Systems, auf Anfragen zu reagieren, quantifiziert durch MTTR,  
            MTBF und Uptime.</p>  
  
 <h5>Skalierbarkeit</h5>  
 <p>Skalierbarkeit beschreibt die Fähigkeit eines Systems, sich an Laständerungen anzupassen. Elasticität  
            beschreibt, was während der Skalierung geschieht.</p>  
  
 <h5>Sicherheit</h5>  
 <p>Sicherheit umfasst Authentifizierung, Autorisierung, Vertraulichkeit, Integrität und  
            Nichtabstreitbarkeit.</p>  
  
 <h5>Design Patterns</h5>  
 <p>Design Patterns wie das Adapter-Pattern ermöglichen die Zusammenarbeit inkompatibler Klassen durch  
            Schnittstellenanpassung.</p>  
 <p><code>class Adapter { float convertToKelvin(float celsius) { return celsius + 273.15; } }</code></p>  
 </div> <div class="topic">  
 <h3>Architekturdiagramme</h3>  
 <p>Siehe Block 02-Distributed Architecture</p>  
 <p><strong>Lines and boxes:</strong> Seite 15-25</p>  
 </div></section>  
  
<section id="jpa">  
 <div class="topic">  
 <h3>JPA und Transaktionen</h3>  
  
 <h4>Einführung in JPA</h4>  
 <p>Die Jakarta Persistence API (JPA) ist eine Java-Spezifikation für das Management von relationalen Daten in  
            Java-Anwendungen. Sie ermöglicht es, Java-Objekte (Entitäten) in Datenbanktabellen abzubilden und bietet  
            eine API für das Speichern, Abrufen und Verwalten dieser Objekte.</p>  
  
 <h4>Grundlegende Konzepte von JPA</h4>  
 <p>JPA basiert auf der Idee von Entitäten, die als Java-Objekte definiert und mit Datenbanktabellen verknüpft  
            werden. Wichtige Annotationen sind:</p>  
 <ul> <li><code>@Entity</code>: Markiert eine Klasse als JPA-Entität.</li>  
 <li><code>@Id</code>: Markiert das Primärschlüsselfeld der Entität.</li>  
 <li><code>@Table</code>: Gibt den Namen der Datenbanktabelle an.</li>  
 <li><code>@Column</code>: Gibt den Namen der Datenbankspalte an.</li>  
 <li><code>@OneToMany</code>, <code>@ManyToOne</code>: Definieren Beziehungen zwischen Entitäten.</li>  
 </ul> <pre><code>@Entity  
@Table(name = "CUSTOMER")  
public class Customer {  
    @Id  
    @GeneratedValue(strategy = GenerationType.IDENTITY)  
    private Long id;  
  
    @Column(name = "NAME")  
    private String name;  
  
    @OneToMany(mappedBy = "customer", cascade = CascadeType.ALL, orphanRemoval = true)  
    private List<Order> orders = new ArrayList<>();  
}  
    </code></pre>  
  
 <h4>Lebenszyklus von JPA-Entitäten</h4>  
 <p>Entitäten durchlaufen verschiedene Zustände: transient, persistent und detached. Eine neue Instanz ist  
            transient, bis sie durch den EntityManager persistiert wird. Nach dem Entfernen (remove) ist sie wieder  
            transient.</p>  
 <pre><code>Customer customer = new Customer();  
customer.setName("John Doe");  
entityManager.persist(customer);  // Jetzt persistent  
entityManager.remove(customer);   // Jetzt wieder transient  
    </code></pre>  
  
 <h4>Konfiguration von JPA</h4>  
 <p>Die Konfiguration von JPA erfolgt hauptsächlich über die Datei <code>persistence.xml</code> oder durch  
            Annotationen in den Entitätsklassen.</p>  
 <pre><code>&lt;persistence xmlns="http://xmlns.jcp.org/xml/ns/persistence"  
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"  
    xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/persistence  
    http://xmlns.jcp.org/xml/ns/persistence/persistence\_2\_1.xsd"  
    version="2.1"&gt;  
 &lt;persistence-unit name="exampleUnit"&gt;  
 &lt;class&gt;com.example.Customer&lt;/class&gt;  
 &lt;properties&gt;  
 &lt;property name="javax.persistence.jdbc.url" value="jdbc:h2:mem:test"/&gt;  
 &lt;property name="javax.persistence.jdbc.user" value="sa"/&gt;  
 &lt;property name="javax.persistence.jdbc.driver" value="org.h2.Driver"/&gt;  
 &lt;property name="javax.persistence.jdbc.password" value=""/&gt;  
 &lt;/properties&gt;  
 &lt;/persistence-unit&gt;  
&lt;/persistence&gt;  
   </code></pre>  
  
 <h4>Transaktionsmanagement</h4>  
 <p>Transaktionen sind entscheidend, um sicherzustellen, dass eine Serie von Datenbankoperationen entweder  
            vollständig durchgeführt oder komplett rückgängig gemacht wird. JPA-Transaktionen werden üblicherweise durch  
            die <code>@Transactional</code> Annotation oder durch direkte Nutzung des EntityManagers gesteuert.</p>  
 <pre><code>@Transactional  
public void placeOrder(Customer customer, Order order) {  
    entityManager.persist(customer);  
    entityManager.persist(order);  
    order.setCustomer(customer);  
    customer.getOrders().add(order);  
}  
    </code></pre>  
  
 <h4>JPA-Abfrage-APIs</h4>  
 <p>JPA bietet mehrere APIs zum Abfragen von Daten:</p>  
 <ul> <li><strong>JPQL</strong>: Eine SQL-ähnliche Sprache zur Abfrage von Entitäten.</li>  
 <li><strong>Criteria API</strong>: Ein objektorientierter Ansatz zur Erstellung von Abfragen.</li>  
 <li><strong>Native Queries</strong>: Direkte SQL-Abfragen.</li>  
 </ul> <pre><code>@PersistenceContext  
EntityManager em;  
  
public List<Customer> findCustomersByName(String name) {  
    String jpql = "SELECT c FROM Customer c WHERE c.name = :name";  
    return em.createQuery(jpql, Customer.class)  
             .setParameter("name", name)  
             .getResultList();  
}  
    </code></pre>  
  
 <h4>EntityManager und Persistence Context</h4>  
 <p>Der EntityManager ist das zentrale Interface für die Arbeit mit JPA. Er verwaltet den Lebenszyklus der  
            Entitäten und bietet Methoden zum Persistieren, Abrufen und Entfernen von Entitäten.</p>  
 <pre><code>EntityManagerFactory emf = Persistence.createEntityManagerFactory("exampleUnit");  
EntityManager em = emf.createEntityManager();  
em.getTransaction().begin();  
Customer customer = new Customer();  
customer.setName("John Doe");  
em.persist(customer);  
em.getTransaction().commit();  
em.close();  
    </code></pre>  
 </div></section>  
  
<section id="messaging">  
 <div class="topic">  
 <h3>Messaging-Konzepte</h3>  
  
 <h4>Einführung in die Kommunikation</h4>  
 <p>Verteilte Systeme benötigen Kommunikation zwischen verschiedenen Komponenten. Diese erfolgt meist über  
            Middleware, um die direkte Socket-Programmierung zu vermeiden.</p>  
  
 <h4>Middleware</h4>  
 <p>Middleware bietet Abstraktionen zur Vereinfachung der Kommunikation zwischen verteilten Komponenten.  
            Beispiele sind Remote Procedure Calls (RPC) und Messaging-Systeme.</p>  
  
 <h4>Remote Procedure Calls (RPC)</h4>  
 <p>RPCs ermöglichen es, Funktionen auf entfernten Maschinen so aufzurufen, als wären sie lokal:</p>  
 <code>   // Beispiel für einen RPC-Aufruf  
            rpc PlaceOrder(Order) returns (OrderId);  
        </code>  
 <p>Vorteile von RPCs:</p>  
 <ul> <li>Einfachheit der Nutzung</li>  
 <li>Plattformunabhängigkeit</li>  
 </ul> <p>Nachteile:</p>  
 <ul> <li>Hohe Latenz bei entfernten Aufrufen</li>  
 <li>Fehleranfälligkeit</li>  
 </ul>  
 <h4>Messaging</h4>  
 <p>Nachrichtenwarteschlangen ermöglichen das Speichern und Abrufen von Nachrichten:</p>  
 <code>   // Beispiel für eine Nachricht in Java  
            Message msg = new Message("Hello, World!");  
            queue.send(msg);  
        </code>  
 <p>Vorteile von Messaging:</p>  
 <ul> <li>Lose Kopplung der Komponenten</li>  
 <li>Asynchrone Kommunikation</li>  
 </ul> <p>Nachteile:</p>  
 <ul> <li>Komplexität der Implementierung</li>  
 <li>Erhöhte Latenz</li>  
 </ul>  
 <h4>Synchron vs. Asynchron</h4>  
 <p>Synchron: Der Sender wartet auf eine Antwort:</p>  
 <code>   // Synchroner Aufruf  
            response = service.call(request);  
        </code>  
 <p>Asynchron: Der Sender wartet nicht auf eine Antwort:</p>  
 <code>   // Asynchroner Aufruf  
            service.callAsync(request, callback);  
        </code>  
  
 <h4>Publish/Subscribe (Pub/Sub)</h4>  
 <p>Beim Pub/Sub-Muster veröffentlichen Sender Nachrichten auf einem Kanal, und Empfänger abonnieren diese  
            Kanäle:</p>  
 <code>   // Beispiel für Pub/Sub in MQTT  
            client.subscribe("sensors/temperature");  
            client.publish("sensors/temperature", "22.5°C");  
        </code>  
  
 <h4>Gängige Protokolle</h4>  
 <p>Beispiele für Messaging-Protokolle:</p>  
 <ul> <li>MQTT: Ein leichtgewichtiges Protokoll für IoT</li>  
 <li>Apache Kafka: Ein hochdurchsatzorientiertes Pub/Sub-System</li>  
 </ul> </div></section>  
  
<section id="wsdl">  
 <div class="topic">  
 <h3>Einführung in WSDL</h3>  
 <p>WSDL (Web Services Description Language) ist eine XML-basierte Sprache, die Webservices beschreibt. Sie  
            standardisiert, wie Webservices definiert werden, damit sie von anderen Systemen verstanden und genutzt  
            werden können.</p>  
  
 <h3>SOAP und WSDL</h3>  
 <p>SOAP (Simple Object Access Protocol) ist ein Protokoll für den Nachrichtenaustausch in Webservices. WSDL  
            beschreibt, wie SOAP-Nachrichten zwischen dem Client und dem Server ausgetauscht werden.</p>  
  
 <h3>Wichtige WSDL-Elemente</h3>  
 <h4>definitions</h4>  
 <p>Das root-Element des WSDL-Dokuments.</p>  
 <pre><code>&lt;definitions&gt;...&lt;/definitions&gt;</code></pre>  
  
 <h4>types</h4>  
 <p>Definiert die Datentypen, die in den Nachrichten verwendet werden.</p>  
 <pre><code>&lt;types&gt;  
 &lt;xsd:schema&gt;  
 &lt;xsd:element name="exampleElement" type="xsd:string"/&gt;  
 &lt;/xsd:schema&gt;  
&lt;/types&gt;  
   </code></pre>  
  
 <h4>message</h4>  
 <p>Beschreibt die Daten, die zwischen Client und Server ausgetauscht werden.</p>  
 <pre><code>&lt;message name="exampleMessage"&gt;  
 &lt;part name="parameters" element="tns:exampleElement"/&gt;  
&lt;/message&gt;  
   </code></pre>  
  
 <h4>portType</h4>  
 <p>Definiert die Operationen des Webservices.</p>  
 <pre><code>&lt;portType name="examplePortType"&gt;  
 &lt;operation name="exampleOperation"&gt;  
 &lt;input message="tns:exampleMessage"/&gt;  
 &lt;output message="tns:exampleMessage"/&gt;  
 &lt;/operation&gt;  
&lt;/portType&gt;  
   </code></pre>  
  
 <h4>binding</h4>  
 <p>Legt fest, wie die Operationen über das Netzwerk zugänglich sind.</p>  
 <pre><code>&lt;binding name="exampleBinding" type="tns:examplePortType"&gt;  
 &lt;soap:binding style="rpc" transport="http://schemas.xmlsoap.org/soap/http"/&gt;  
 &lt;operation name="exampleOperation"&gt;  
 &lt;soap:operation soapAction="urn:exampleOperation"/&gt;  
 &lt;input&gt;  
 &lt;soap:body use="literal"/&gt;  
 &lt;/input&gt;  
 &lt;output&gt;  
 &lt;soap:body use="literal"/&gt;  
 &lt;/output&gt;  
 &lt;/operation&gt;  
&lt;/binding&gt;  
   </code></pre>  
  
 <h4>service</h4>  
 <p>Definiert die Endpunkte, an denen der Service verfügbar ist.</p>  
 <pre><code>&lt;service name="exampleService"&gt;  
 &lt;port name="examplePort" binding="tns:exampleBinding"&gt;  
 &lt;soap:address location="http://example.com/service"/&gt;  
 &lt;/port&gt;  
&lt;/service&gt;  
   </code></pre>  
  
 <h3>WSDL und REST</h3>  
 <p>Im Gegensatz zu WSDL und SOAP, die XML verwenden, nutzen RESTful Services JSON und sind einfacher und  
            leichter zu integrieren. WSDL bietet jedoch eine strengere Typisierung und ist oft in Unternehmensumgebungen  
            zu finden.</p>  
 </div></section>  
  
<section id="protobuf">  
 <div class="topic">  
 <h3>Protocol Buffers</h3>  
 <h4>Grundlagen der Serialisierung</h4>  
 <p>Serialisierung ist der Prozess, bei dem Datenstrukturen oder Objekte in ein Format umgewandelt werden, das  
            gespeichert oder übertragen werden kann. Protocol Buffers (Protobuf) sind ein effizientes und  
            plattformunabhängiges Serialisierungsformat, das von Google entwickelt wurde.</p>  
  
 <h4>Was sind Protocol Buffers?</h4>  
 <p>Protocol Buffers sind ein binäres Serialisierungsformat, das für Inter-Maschinen-Kommunikation optimiert ist.  
            Es ist hoch effizient in Bezug auf Speicherplatz und Performance und unterstützt verschiedene  
            Programmiersprachen wie Java, Python, C++ und viele mehr.</p>  
  
 <h4>Grundlegende Syntax</h4>  
 <p>Eine Protobuf-Datei definiert Nachrichten, die aus Feldern bestehen. Jedes Feld hat einen Namen, einen Typ  
            und eine eindeutige Nummer.</p>  
 <code>   message Person {  
            string name = 1;  
            int32 id = 2;  
            string email = 3;  
            }  
        </code>  
  
 <h4>Verwendung in Java</h4>  
 <p>Nach dem Definieren einer Protobuf-Nachricht in einer <code>.proto</code>-Datei, wird der folgende Java-Code  
            verwendet, um eine Nachricht zu erstellen:</p>  
 <code>   Person.Builder builder = Person.newBuilder();  
            builder.setName("John Doe");  
            builder.setId(1234);  
            builder.setEmail("john.doe@example.com");  
            Person person = builder.build();  
        </code>  
  
 <h4>Verwendung in Python</h4>  
 <p>Ähnlich wie in Java wird auch in Python ein Builder verwendet:</p>  
 <code>   person = person_pb2.Person()  
            person.name = "John Doe"  
            person.id = 1234  
            person.email = "john.doe@example.com"  
        </code>  
  
 <h4>Erweiterbarkeit und Versionsverwaltung</h4>  
 <p>Protobuf unterstützt die Erweiterung von Schemas ohne Abwärtskompatibilität zu brechen. Neue Felder können  
            hinzugefügt werden, alte können optional gemacht werden.</p>  
 <code>   message Person {  
            string name = 1;  
            int32 id = 2;  
            string email = 3;  
            string phone = 4; // neues Feld  
            }  
        </code>  
  
 <h4>Vor- und Nachteile von Protobuf</h4>  
 <p><strong>Vorteile:</strong></p>  
 <ul> <li>Effizienter Speicherplatzverbrauch</li>  
 <li>Schnelle Serialisierung und Deserialisierung</li>  
 <li>Sprach- und plattformunabhängig</li>  
 </ul> <p><strong>Nachteile:</strong></p>  
 <ul> <li>Schwieriger zu debuggen als textbasierte Formate</li>  
 <li>Erfordert das Kompilieren von .proto-Dateien</li>  
 </ul>  
 <h4>Praktische Anwendung</h4>  
 <p>Lesen und Schreiben von Protobuf-Nachrichten:</p>  
 <code>   // Schreiben  
            byte\[\] data = person.toByteArray();  
  
            // Lesen  
            Person newPerson = Person.parseFrom(data);  
        </code>  
  
 <h4>Zusammenfassung</h4>  
 <p>Protocol Buffers sind ein leistungsfähiges Tool für die effiziente und plattformübergreifende  
            Datenserialisierung. Sie bieten eine Vielzahl von Vorteilen gegenüber textbasierten Formaten wie JSON und  
            XML, insbesondere in Bezug auf Speicherplatz und Performance.</p>  
 </div></section>  
  
<section id="rest">  
 <div class="topic">  
 <h3>REST-Interaktionen</h3>  
 <h4>Einführung</h4>  
 <p>REST (Representational State Transfer) ist ein Architekturstil für verteilte Systeme, der häufig für Web-APIs  
            verwendet wird. Die Konzepte von REST wurden 2000 von Roy Fielding entwickelt und sind heute der Standard  
            für Web-APIs.</p>  
  
 <h4>Grundprinzipien von REST</h4>  
 <p>Die sechs Grundprinzipien von REST sind:</p>  
 <ul> <li><strong>Client-Server-Architektur:</strong> Trennung von Benutzeroberfläche und Datenspeicherung.</li>  
 <li><strong>Zustandslosigkeit:</strong> Jede Anfrage muss alle notwendigen Informationen enthalten.</li>  
 <li><strong>Cachefähigkeit:</strong> Antworten sollten als cachefähig oder nicht cachefähig gekennzeichnet  
                sein.  
            </li>  
 <li><strong>Schichtsystem:</strong> Der Client sollte nicht erkennen, ob er direkt mit dem Server oder über  
                einen Vermittler kommuniziert.  
            </li>  
 <li><strong>Einheitliche Schnittstelle:</strong> Einheitliche Methode zur Kommunikation zwischen  
                Komponenten.  
            </li>  
 <li><strong>Code on Demand:</strong> (optional) Server können ausführbaren Code an Clients senden.</li>  
 </ul>  
 <h4>HTTP-Methoden in REST</h4>  
 <p>REST verwendet die folgenden HTTP-Methoden für CRUD-Operationen:</p>  
 <ul> <li><strong>GET:</strong> Ruft eine Ressource ab. Beispiel:  
                <code>GET /api/users/123 HTTP/1.1</code></li>  
 <li><strong>POST:</strong> Erstellt eine neue Ressource. Beispiel:  
                <code>POST /api/users HTTP/1.1<br>Content-Type: application/json<br>{ "name": "John Doe", "email":  
                    "john.doe@example.com" }</code></li>  
 <li><strong>PUT:</strong> Aktualisiert eine bestehende Ressource. Beispiel:  
                <code>PUT /api/users/123 HTTP/1.1<br>Content-Type: application/json<br>{ "email": "john.new@example.com"  
                    }</code></li>  
 <li><strong>DELETE:</strong> Löscht eine Ressource. Beispiel:  
                <code>DELETE /api/users/123 HTTP/1.1</code></li>  
 </ul>  
 <h4>HTTP-Statuscodes</h4>  
 <ul> <li><strong>200 OK:</strong> Die Anfrage war erfolgreich.</li>  
 <li><strong>201 Created:</strong> Eine Ressource wurde erfolgreich erstellt.</li>  
 <li><strong>400 Bad Request:</strong> Die Anfrage war fehlerhaft.</li>  
 <li><strong>401 Unauthorized:</strong> Authentifizierung erforderlich.</li>  
 <li><strong>404 Not Found:</strong> Die angeforderte Ressource wurde nicht gefunden.</li>  
 <li><strong>500 Internal Server Error:</strong> Serverseitiger Fehler.</li>  
 </ul>  
 <h4>Ressourcenidentifikation und -manipulation</h4>  
 <p>Ressourcen werden durch URIs identifiziert und durch Repräsentationen (z.B. JSON, XML) manipuliert. Beispiel  
            für eine Ressourcen-URI: <code>http://example.com/api/users/123</code></p>  
  
 <h4>Hypermedia as the Engine of Application State (HATEOAS)</h4>  
 <p>Ein REST-Client sollte alle notwendigen Informationen durch Hypermedia in den Antworten des Servers erhalten.  
            Beispiel:  
            <code>  
   {<br>  
   "id": 123,<br>  
   "name": "John Doe",<br>  
   "links": \[<br>  
   {"rel": "self", "href": "/api/users/123"},<br>  
   {"rel": "friends", "href": "/api/users/123/friends"}<br>  
   \]<br>  
   }</code>  
 </p>  
 <h4>Sicherheit</h4>  
 <p>REST-APIs sollten durch Mechanismen wie OAuth oder API-Schlüssel geschützt werden, um sicherzustellen, dass  
            nur autorisierte Benutzer Zugriff haben.</p>  
 </div></section>  
  
<section id="concepts">  
 <div class="topic">  
 <h3>Konzeptuelles Verständnis</h3>  
  
 <h4>Einführung in Anwendungsplattformen</h4>  
 <p>Komplexe Anwendungen werden heute auf Anwendungsplattformen aufgebaut, z.B. Java EE/Jakarta,  
            serviceorientierte Architekturen, Microservices, Cloud-Services und serverlose Computer.</p>  
  
 <h4>Evolution von Architektur-Stilen</h4>  
 <p>Die Entwicklung der Architektur hat verschiedene Phasen durchlaufen:</p>  
 <ul> <li>Anwendungsserver (z.B. Java EE/Jakarta, Spring)</li>  
 <li>Komposition</li>  
 <li>Serviceorientierte Architekturen (SOA)</li>  
 <li>Microservices</li>  
 </ul>  
 <h4>Anwendungsserver</h4>  
 <p>Anwendungsserver bieten Middleware-Runtime-Funktionen wie Dependency Injection, Concurrency Control,  
            Sicherheit, ereignisgesteuerte Programmierung, Persistenz und Transaktionen in sogenannten Containern.</p>  
 <p><code>public class HelloWorld extends HttpServlet { ... }</code></p>  
  
 <h4>Komposition: Orchestrierung vs. Choreographie</h4>  
 <p>Moderne Anwendungen bestehen aus vielen Komponenten. Es gibt zwei grundlegende Kompositionsstile:</p>  
 <p><strong>Orchestrierung:</strong> Ein zentraler Orchestrator kennt den globalen Prozess und ruft einzelne  
            Komponenten auf. Vorteile: Zentralisierte Prozesskenntnis, leicht zu konzeptualisieren. Nachteile:  
            Einzelpunkt des Versagens, Leistungseinbußen.</p>  
 <p><strong>Choreographie:</strong> Dezentrale Kompositionskenntnisse, wobei die Komponenten wissen, wie sie  
            interagieren sollen. Vorteile: Keine zusätzlichen Netzwerkaufrufe, keine zentrale Engstelle. Nachteile:  
            Schwer zu überblicken.</p>  
  
 <h4>Serviceorientierte Architekturen (SOA)</h4>  
 <p>In SOA werden Softwarekomponenten als Dienste implementiert. Diese haben bestimmte Merkmale wie  
            Wiederverwendbarkeit und klare Ergebnisse. Eine SOA basiert oft auf SOAP/WSDL-Webdiensten und verwendet  
            häufig Orchestrierung.</p>  
  
 <h4>Microservices</h4>  
 <p>Microservices-basierte Architekturen ähneln SOA, gelten jedoch als leichter und flexibler. Unterschiede  
            zwischen SOA und Microservices:</p>  
 <ul> <li>SOA wird von technischen Bedürfnissen getrieben (Wiederverwendbarkeit), Microservices von  
                organisatorischen Teams.  
            </li>  
 <li>SOA favorisiert Orchestrierung, Microservices Choreographie.</li>  
 </ul>  
 <h4>Virtualisierung</h4>  
 <p>Virtualisierung ist der Prozess der Bereitstellung einer virtuellen Ressource auf derselben Abstraktionsebene  
            wie eine physische. Es gibt verschiedene Arten der Virtualisierung:</p>  
 <ul> <li>Paravirtualisierung: Gast-OS kommuniziert mit Hypervisor.</li>  
 <li>Vollständige Virtualisierung: Unverändertes Gast-OS.</li>  
 <li>Hardwareunterstützt: CPU hat Unterstützung für vollständige Virtualisierung.</li>  
 </ul>  
 <h4>Container und Docker</h4>  
 <p>Container virtualisieren das Betriebssystem, sodass Anwendungen glauben, sie wären alleine auf einem  
            Betriebssystem. Docker ist heute der De-facto-Standard für die Bereitstellung von Software in  
            Containern.</p>  
 <p><code>FROM ubuntu:22.04</code></p>  
  
 <h4>Cloud-Computing</h4>  
 <p>Cloud-Computing umfasst verschiedene Dienstmodelle:</p>  
 <ul> <li>Infrastruktur als Dienst (IaaS): z.B. AWS EC2</li>  
 <li>Plattform als Dienst (PaaS): z.B. Google App Engine</li>  
 <li>Software als Dienst (SaaS): z.B. Gmail, Dropbox</li>  
 </ul> <p>Cloud-Computing bietet Vorteile wie einfache Skalierbarkeit, elastische Ressourcen und ein nutzungsbasiertes  
            Zahlungsmodell.</p>  
  
 <h4>Serverlose Computer</h4>  
 <p>Serverlose Computer bedeutet, dass DevOps-Teams keine Server mehr verwalten müssen. Stattdessen wird die  
            Anwendungslebensdauer vom Anbieter verwaltet. Dies führt zu einem echten On-Demand-Modell: "pay per use"  
            statt "pay as provisioned".</p>  
  
 <h4>Funktion als Dienst (FaaS)</h4>  
 <p>FaaS-Plattformen ermöglichen das Ausführen von Backend-Code ohne eigene Serversysteme oder langlebige  
            Serveranwendungen zu verwalten. Funktionen sind zustandslos und ereignisgesteuert.</p>  
 </div></section>