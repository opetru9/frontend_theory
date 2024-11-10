### CSS

# css priority
1. 1.0.0.0 inline styles 
2. 0.1.0.0 id 
3. 0.0.1.0 class, pseudo-class,  atribute ( [type: text] )
4. 0.0.0.1 elemente, pseudo-elemente ( div, ::before )

* chiar daca folosesc 11 clase la selector (0.0.11.0) oricum nu va fi mai specific ca un id niciodata , un id va fi mai putin specific doar daca adaog !important la clasa

# collapsing margins 
  daca doua margini pe aceiasi axa se contrapun , se aplica doar marginea mai mare :

* <div></div>
  <div></div>
  style{div{margin: 20px 0 30px;}}--->disitanta dintre divuri va fi 30px

# adaptivity
noi folosim media requesturi pentru a face site adaptiv
* responsive design - cind micsoram browserul si siteul e eleastic , se adapteaza dupa fiecare dimensiune, pare a fi elastic
* adaptive design   -  cind siteul are 3 dimensiuni stabilite si se schimba numai cind se schimba acele dimensiuni

# position sticky
Este o combinație între relative și fixed
- sticky atunci când doriți ca un element să rămână vizibil în interiorul unui container specific, dar să se miște în restul paginii.
- fixed atunci când doriți ca un element să rămână fixat în aceeași poziție în fereastra de vizualizare, indiferent de scroll.

# css imports
* importurile in css este mai bine sa le evitam , de ex daca avem mai multe importuri intrun file care va fi transmis prin link la html , nu se va desena nimic pina nu vor veni toate importurile , in schimb daca toate importurile le facem prin link din head , totusl se va incarca in paralel marind viteza

# elemente ascunse in pagina
display : none;      ---> dipare din DOM
visibility : hidden; ---> nu se vede dar este in DOM
input type = 'hidden'---> nu se vede dar este in DOM
hight and width = 0  ---> nu se vede dar este in DOM