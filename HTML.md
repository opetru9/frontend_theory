### HTML

# Rolul Declarației <!DOCTYPE html>
Indică faptul că documentul este în format HTML5.(e mult mai scurt a versionile anterioare unde declararea formatului era mai lunga si mai complexa)
La fel indica browserilor in ce mod sa fie redat documentul , in lipsa lui documentul poate avea un comportament straniu la afisare.

# ce este tagul meta?
Este utiliziat pentru a transmite metadate despre document HTML.
Aceste date sunt utilizate de catre browser motoare de căutare și alte servicii web
pentru a înțelege mai bine conținutul și comportamentul paginii web.
- exemple: 
* cuvinte cheie al siteului:
    <meta name="keywords" content="HTML, CSS, JavaScript, meta tag">
* autorul 
    <meta name="author" content="Numele Autorului">
* setul de caractere:
    <meta charset="UTF-8"> acesta e folosit pentru a afisa textul corect si pentru ca sitemul multilingv sa functioneze mai bine
* utf-8 este un set de caractere universal care suportă aproape toate caracterele și simbolurile din toate limbile scrise
* daca nu ar fi:
- ar putea aparea prbleme cu afisarea textului in pagina 
- probleme cu seo si accesibiliate 

2. meta name="viewport" content="width=device-width, initial-scale=1" /> - Controlează modul în care pagina web este afișată pe dispozitivele mobile
* width=device-width face ca lățimea paginii să fie egală cu lățimea ecranului dispozitivului
* initial-scale=1 setează nivelul de zoom inițial la 1, adică fără zoom. Acestea ajută la asigurarea că pagina este receptivă și bine vizibilă pe diferite dimensiuni de ecran.
* daca nu ar fi:
- siteul ar fi afisat in dimensiuni de desktop - va afisa continutul mic si greu de citit , butoanele greu de apasat , etc
- in lipsa atributului "viewport" la dispozitivele mobile se situl se va incarca mai greu deoarece acestea vor trebui să proceseze mai multe date pentru a redimensiona și afișa pagina corespunzător
- seo(search egine optimization) scazut 

3. meta name="theme-color" content="#000000" - schimba culoarea temei la mobile , acest lucru poate face ca bara de adrese la browserul mobilului sa fie negru

4. meta name="description" content="Web site created using create-react-app"  Furnizează o descriere scurtă a conținutului paginii web 
Motoarele de căutare folosesc această descriere în rezultatele căutărilor, iar rețelele sociale o pot utiliza atunci când pagina este partajată

# de ce e mai bine sa folosim tag-uri semantici in html document?
1. pentru claritatea si ordine
2. pentru cititoarele de ecrane pentru persoane cu dizabilitati
3. SEO - motoarele de cautare gasesc mai usor in rezulatul cautorilor

# difenrenta dintre section si article?
<section>: Folosit pentru a organiza conținut pe teme sau subiecte, în cadrul aceleiași pagini sau document. Este mai mult despre structura internă și organizarea conținutului.
<article>: Folosit pentru a defini conținut independent, care are sens pe cont propriu și poate fi reutilizat sau distribuit în alte contexte.
