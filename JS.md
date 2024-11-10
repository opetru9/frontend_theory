### JS

# tipuri de date 
- string , number, boolean , symbol, null, undefined, BigInt ,object (unicul tip ne-primitiv)
* BigInt - este folosit pentru a reprezenta numere întregi mai mari decât 2 la puterea 53 - 1 

# variabile let si const
 diferenta dintre "var" si "let" 
- "var" poate fi accesata inainte de declarea sa dar va da undefined, deoarece este hosted(trasă în vârf) în contextul său.
* console.log(a) // undefined
  var a = 0

- "var" e function scope - sunt accesibilie in interiorul intregii functii spre diferenta de 'let' (care e block scope),var poate fi accesata din afara buclei "for" chiar daca a fost declarata in interiorul ei. 
* function f1(){
    for (let i = 0; i < 5; i++){
        var a = 1
        let b = 2
    }
    console.log(a) // 1
    console.log(b) // ReferenceError: b is not defined
}
** din afara functie nu va fi accesibila nici var nici let

- "var" permite redeclarearea aceliasi variabile in acelasi scope sau block.
{
    var a = 1
    var a = 2
    cosole.log(a) // 2

    let a = 1
    let a = 2 // SyntaxError: Identifier 'a' has already been declared
    
}

# clear function
- returneaza acelasi rezultat cu aceleasi date transmise , nu depinde de nici un factor exter ca de ex API
- nu schimba variabile externe si nimic din jur.
- depinde doar de argumentii ei , de nimic altceva.
- exemplu cel mai popular e o functioe care primeste argumentii a si b si returneaza suma lor.

# cycles
- for.. of.. este utilizat pentru string, array ..
- for.. in.. este utilizat pentru obiecte
- while si do while :
 * diferenta este ca 'while' evalueaza conditia si executa actiunea daca conditia e true sau nu daca e false,
    let i = 1;
    while (i <= 5) {
    console.log(i);
    i++; // Incrementare
}
 * in schimb 'do while' va executa o actiune indiferent de conditie ,apoi va repeta actiunea doar daca 'while' e true.
    let j = 1;
    do {
        console.log(j);
        j++; // Incrementare
    } while (j <= 5);
- for:
 * for (let i = 0; i < 5; i++) utiliziarea clasica 
 * for (let i = 0; i < 5; ){i++} se poate utiliza si asa , va functiona bine , dar nu este legibil , deobicei folosim asta cind dorim un incrimentare conditionata :
    for (let i = 0; i < 10; ) {
        if (i % 2 === 0) {
            i += 2; // Incrementare condiționată
        } else {
            i++;
        }
    }
- for si while : 
 * for se foloseste cind stim exact de cite ori va trebui de derulat conditia
 * while se foloseste cind nu stim numarul exact de executari pentru ca depinde de un context logic

- for of si .forEach
 * for of permite o iterare mai controlata (break si continue) este mai putin compacta.
 * .forEach nu da control asupra iteratinunii dar este mai compact si mai legibil , la fel ofera utilizarea unei functii de callbak care va lucra cu fiecare item din array in parte.


# metode string
- "hello".charAt(1) - intoarce simbolul de pe indexul indicat.
- "hello".concat("world) - va lipi "world" de "hello". 
- "hello".includes("he") - intoarce "true" daca include asa simboluri. 
- "hello".indexOf("e")
- "hello".toLowerCase()
- "hello".toUpperCase()
- "hello".replace("hello", "replaced text")
- "hello".slice(2,5) - extrage caractere in baza indicilor / "llo" / . mai flexibil
    * Dacă lucrați cu indici negativi sau dacă există posibilitatea ca primul argument să fie mai mare decât al doilea, slice() oferă mai multă flexibilitate.
    * Dacă doriți să vă asigurați că indicii sunt întotdeauna pozitivi și că rezultatul este întotdeauna consistent, substring() poate fi o opțiune mai sigură.
- "hello".substring(2,5) - extrage caractere in baza indicilor / "llo" /. mai strict
- "hello".split(",")
- "hello".trim() - elimina spatiile albe
- "hello".repeat(3) - / "hellohellohello"

# metode Array
- .forEach - se foloseste pentru a gasi un element anume din masiv sau pentru a primi oricare informatie depsre masiv, nu returneaza nimic
- .map - se foloseste pentru a modifica fiecare element dintr-un masiv si a returna alt masiv modificat
- .reudce( (accumulator, currentValue, currentIndex, array) => accumulator + currentValue,initialValue ) - va returna suma tuturor elementelor in interior 
- .push(element) - lipeste "element" la sfirsitul masivului
- .splice(  2, 1, element) adauga element in masiv pe o un index specificat (2) si elimina la dorinta un numar (1) de elemente din maisv. 
- .pop() - elimina ultimul element si il returneaza.
- .shift() - elimina primul element si il returneaza.
- .unshift(element) - adauga element la inceputul masivului.
- .slice(1,3) - returneaza o copie cu o segventa din masiv 
- .join(", ") - uneste elementele masivului intrun string
- .filter( x => x > 2) gaseste toate elementele care satiface conditiiei
- .find( x => x > 2 ) returneaza primul element care satisface conditiiei
- .findIndex( x => x > 2 ) returneaza indexul primului element care satisface conditiiei
- .some( x => x > 2) returneaza true daca gaseste un asa element
- .every( x => x > 2) returneaza true daca toate elementele satisfac conditiiei
- .includes (elementToFind, hisIndex)

## Object
 let myObj = {a:1, b:2}
 const entries = Object.entries(myObj);
 enteries = [ ['a', 1], ['b',2] ]

# clone objects
1. Clonare superficiala : cind obiectul contine doar primitive 
- Object.assign():
        let obj = {
            a:1,
            b:2,
            c:3
        }
        let clone = Object.assign({},obj)
        clone.c = 4
        console.log(obj,clone) // {a: 1, b: 2, c: 3} , {a: 1, b: 2, c: 4}

- Spread operator: 
        let clone = {...obj}
* nu cloneaza getteri si setteri 

2. Clonare profunda : cind obiectul contine alte obiecte 
- JSON.parse(JSON.stringify(obj))
        let obj = {
            a:1,
            b:2,
            c:3,
            d:{
                e:4,
                f:5
            }
        }
        let clone = JSON.parse(JSON.stringify(obj))
        clone.d.f = 4
        console.log(obj.d, clone.d) // {e: 4, f: 5} , {e: 4, f: 4}
* functioneaza doar cu obiecte simple fara simbol si functii deaorece json nu poate intrepreta
- structuredClone()
        let clone = structuredClone(obj)
* functioneaza doar cu obiecte simple fara simbol si functii deaorece json nu poate intrepreta.



# clonarea superficiala unui Array
1. cu slice()
    const originalArray = [1, 2, 3];
    const clonedArray = originalArray.slice();
2. cu concat()
    const originalArray = [1, 2, 3];
    const clonedArray = [].concat(originalArray);
3. cu spread() 
    const originalArray = [1, 2, 3];
    const clonedArray = [...originalArray];
* Dacă array-ul nu conține obiecte sau alte structuri de date complexe (cum ar fi alte array-uri), atunci o clonare superficială a acestuia va crea o copie completă și independentă a array-ului original. Aceasta înseamnă că modificările făcute în array-ul clonat nu vor afecta array-ul original și viceversa.

# spread si rest
- spread descompune un masiv in elementele din interiorul sau [...array], se foloseste pentru a concata array si obiecte , 
- rest compune un numar de elemente intr-un masiv , se foloseste cel mai des ca argument pentru functii , f(...arg) astfel putem transmite oricite elemente ca argument lui f

# diferenta dintre Parametru si Argument
- Parametrii sunt variabilele definite în semnătura funcției, servind ca locuri deținătoare pentru valorile care vor fi procesate ---> f(a,b){...}
- Argumentele sunt valorile efective transmise funcției în momentul apelării acesteia, care completează parametrii definiți  ---> f(2,4)

# Rest API
Un numar de principii care este binevetnit de respecat la schimbul de date intre client si server:
- model client ( request ) - server ( response )
- pentru a face un request la server folosim "url".
- resursele sunt transportate in format JSON sau XML.
- pentru schimbul de resurse se utilizeaza metode HTTP:
1. GET
2. POST - pentru a adauga o resursa noua
3. PUT  - pentru a actualiza o resursa existenta
4. DELETE
- StateLess - serverul nu stie nimic despre requesturile anterioare , de aceia trebuie sa transmitem toate datele complete la fiecare request.(cind dam undo in browser doar trimitem ultimul requiest inca o data )
- Cacheing - serverul ne poate spune sa bagam in cache un resurs pentru a nul cere de mai multe ori de ex o img.
- STATUS CODES
1. 1xx - info
2. 2xx - success
3. 3xx - redirectional
4. 4xx - client error
5. 5xx - server error

----------

* Request structure:
- method
- url
- header
- body (*)

* Response structure:
- status code
- header
- body (*)

# closure function
- functie definita in interiorul altei functii unde doar functia din interior are acces la variabilele din functia exterioara astfel incapsulind variabile intr-un cimp lexical inaccesibil si pastrind stari (memorizeaza valori schimbate)
**folosita in JS frameworkuri ca React, Vue si Angular

Beneficiile utilizării closure-urilor
1. Encapsularea datelor: Closure-urile permit crearea de variabile private. Variabilele definite în mediul lexical al unei funcții nu sunt accesibile din exterior, dar pot fi utilizate de funcțiile returnate:

function outer(){
    let variable = 'hello'

    function inner(){
        cosole.log(variable);
    }

    inner()
}
* functia inner are acces la tot scopul functiei outer inluzind si variabelile , 
inner prelucreaza variabila si este unica care are acces la aceasta variabila , astfel variabila sa incapsulat si a devenit privata.

2. Persistența stării(state maintenances): Closure-urile pot păstra starea între apelurile funcției. Acest lucru este util pentru implementarea unor funcționalități cum ar fi contorizarea, gestionarea de resurse, etc.

function myScore(){
    let score = 0

    function addScore(){
        score++
    }
    function decScore(){
        score--
    }
    function getScore(){
        return score
    }

    return {addScore, decScore, getScore}
}
let myObj = myScore()
myObj.addScore() // {score++}
myObj.decScore() // {score--}
myObj.getScore() //  score
myObj.score      // - error -

sau

function outerFunction() {
    let count = 0; // variabila locală a funcției externe

    function innerFunction() {
        count++; // accesarea și modificarea variabilei locale
        console.log(count);
    }

    return innerFunction;
}

const closureInstance = outerFunction();

closureInstance(); // Output: 1
closureInstance(); // Output: 2
closureInstance(); // Output: 3

3. Modularitatea: Closure-urile ajută la crearea de cod modular și reutilizabil (componente in react).


## Event Loop 
un mechanism aparte care permite ca js sa efectueze actuni non-blocante(actiuni in paralel) si sa raspunde la eventimente asincrone, chiar dara este un limbaj de programare single-threaded(pe un singur fir) -- (ca codul sa mearga mai departe in timp ce alt cod este in asteptare) 
* nu face parte din js (in chrome se foloseste v8 in nodejs v8 concepte diferite )

* este compous din:
1. call stack  - (v8) - aseaza actiunile care returneaza alte actiuni intro ordine astel incit in momentul in care ultima activune va intoarce o valoare , din stack sa dispara consecutiv si restul actiunilor(ex: cind avem functii care includ alte functii)

3. web api     - se inregistraza evenimentele asicrone intr-un spatiu separat unde se executa, apoi sunt transmise in task queue (daca setTimeout 3000, aici se asteapta 3sec apoi e trnsmis in task queue)
* aici se inregistreaza si eventListener , de ex click - cind va fi click , functia din eventListener va fi transmisa in tasck queue.
* apartine browserului spre diferenta de restul care sunt executate de js interpreter(v8)

2. task queue  -  pastreaza actiunile in ordinea sosirii lor din web api si le transmite in call stack cind este gol
* toate evenimentele din task queue vor asepta ca stack sa fie gol , doar apoi se vor adauga si ele in stack pentru a fi executate (codul sincron are prioritate)

  1. Micro task (faster) - promises. 
  2. Macro task (slower) - setTimeout, setInterval, eventsListener
* macro taskurile se vor efectua doar atunci cind toate micro tascurile vor fi efectuate

* evenimentele sincrone trec doar prin call stack , web api si task queue sunt pentru gestionarea evenimentelor asincrone

sincrone tasks -->  micro tasks --> macro task

# Event Delegation
Să presupunem că ai o listă de elemente li într-un ul:
<ul id="myList">
  <li>Element <strong>1</strong></li>
  <li>Element <strong>2</strong></li>
  <li>Element <strong>3</strong></li>
</ul>
În loc să atașezi un handler de eveniment click la fiecare li, poți folosi delegarea evenimentelor setind doar un event la elementul parinte:

document.getElementById('myList').addEventListener('click', function(event) {
    if (event.target && event.target.nodeName === 'LI') {
        console.log('Elementul click-uit:', event.target.textContent);
        window.location.href += '?' + event.target.textContent
    }
});

# Event Propagation:
- Capturing Phase: Evenimentul se deplasează de la document în jos spre elementul țintă.
    * addEventListener('event', (e)=>{}, {capture : true} ) --> pentru a captura aceasta deplasare si a executao primul rind , eventul se va exectuta de sus in jos , si nu ca deobicei de jos in sus

- Target Phase: Evenimentul este gestionat de elementul țintă.
    * event.target - elementul pe care sa facut click (=== this daca nu arrow f)
    * event.currentTarget - elementul care are event listener pentru acest event
    * event.target.nodeName - 'li'

- Bubbling Phase: Evenimentul urcă înapoi prin elementele părinte până la document.
    * stopPropagation() oprește propagarea evenimentului daca are doar un eventHandler.
    * stopImediatePropagation() oprește propagarea evenimentului daca are mai multi eventHandleri.

# Focus event  
* focus este un eventiment fara propogare ( pentru a aduga propagare folosim focusin focusout).
- 'focus' si 'blur' sunt by default inlocuite cu atributele 'required' si 'pattern' dupa HTML5. 

element.focus()
element.blur() --> metde de adaugare fortata a blur sau focus .

- unele elemente nu au focus by default , de ex div , dar putem aduga focus daca le setam atributul 'tabindex = 1'
numarul setat ca tabindex va arata ordinea obiectului care va avea focus dupa apasarea tastei tab de catre user.
- daca tabindex = 0 , va fi fara ordine , va merge de sus in jos in rind cu restul elementelor.
- daca tabindex = -1 , nu vom putea face focus decit prin js.
- document.activeElement - daca dorim sa gasim elementul cu focus in pagina prin js 



# Date() UTC
*   let currentTime = new Date();
    let specificDate = new Date(2024,7,15) //  2024 aug 15 , aug = 7 deoarece ianuarie = 0
    let dateFromString = new Date('2024-08-15T10:30:00') // da o data dupa un string

*   let now = new Date();
    console.log(now.getFullYear()); // Anul (ex: 2024)
    console.log(now.getMonth());    // Luna (0-11; ianuarie = 0)
    console.log(now.getDate());     // Ziua lunii (1-31)
    console.log(now.getHours());    // Ora (0-23)
    console.log(now.getMinutes());  // Minute (0-59)
    console.log(now.getSeconds());  // Secunde (0-59)

- UTC - Coordinated Universal Time