### ce este react
- Biblioteca JS care simplifica crearea aplicatiilor facindule mai structurate mai reactive si mai simple.
- Este bazat pe componenta si pe starea ei.
- Componenta este creata rapid si usor datorita sintaxei JSX care este un amestec de html si js dar intrun final react va transforma in js. 
- Starea componentei permite rerandarea componentei la schimbarea anumitor valori. 
- Props sunt datele transmise componentelor ca atribute iar apoi utilizate in interiorul componentelor ca parametri.


# Virtual DOM 
Permite randarea componentelor rapid si economic:

* React compară noul Virtual DOM cu vechiul Virtual DOM și identifică care schimbari sau efectuat si re-randeaza doar segventa schimbata , evitind re-redereingul total al DOM-ului real.

- Minimizează numărul de actualizări directe ale DOM-ului real, reducând astfel costurile de performanță.
- Programatorii nu trebuie să se ocupe direct de manipulările DOM-ului, ceea ce face codul mai curat și mai ușor de întreținut.
- Optimizare Automată: React gestionează optimizarea actualizărilor interfeței utilizatorului, făcând aplicațiile mai rapide și mai receptive la schimbările de stare.

# Component's lifecycle methods:
Diferitele etape prin care trece o componentă de la "montare", "actualizare" și până la "demontare"

1.componentDidMount() - după ce componenta este montată 
- useEffect( ()=>{}, []) --> Se specifică un array gol ca al doilea argument pentru a rula efectul doar o singură dată, la montare.

2.componentDidUpdate() - după ce actualizarea a fost aplicată DOM-ului.
- useEffect( ()=>{}, [update]) --> Se specifică în array-ul de dependențe variabilele care, atunci când se schimbă, declanșează efectul.

3.componentWillUnmount() -  înainte de demontarea și distrugerea unei componente.
- useEffect( ()=>{ return (removeEventListener)}, []) --> poate returna o funcție de curățare care va fi apelată înainte de demontarea componentei.


# Hooks
* useState() - permite sa facem re-redenring componentei schimbint starea interna a componentei ,astfel facind pagina interactiva 

* useEffect() - prelucreaza careva schimbari a componentei si depinde de array de dependente, daca:
- useEffect( ()=>{}, [update]) - se efectuiaza cind se schimba update.
- useEffect( ()=>{}, []) - se efectuiaza doar o data la montarea componentului.
- useEffect( ()=>{}) - se efectuiaza la fieacre re-rendering a paginiii.

* useContext() - pentru a evita props drill-down , cind transmitem date direct catre componenta destinatara direct , fara intermediari care nu au nevoie de aceste date.

* useRef() - are 2 uitilizari:
1. comunicarea cu node elementul in direct (in loc de querry selector)

    let myRef = useRef()
    return <div ref={myRef}></div>

2. memorizarea unei informatii fara re-rendering, daca avem nevoie de o valoare care va trebui fi retinuta in memorie si dorim sa o folosim cit mai rapid si mai econom ne convine sa declaram variabila prin useRef() , astfel valoarea ei se va memoriza dupa schimbare si far a fi nevoie de un re-rendering care ar provoca uzul lui useState()

    let myValue = useRef(1)
    useEffect(()=>{
        document.addEventListener( scroll, ()=>{
            myValue++
        })
    },[])

* useMemo() - are 2 utilizari:
1. permite efectuarea controlata a unori functii pentru a econemosi resurse, structura e ca si la useEffect() : let memo = useMemo( function, [dependente]) ceia ce va returna function , va fi salvat in variabila 'memo' care va da rezultatul mereu cit dependentele nu se vor schimba, astfel economisint resurse --> aceasta se numeste memoizare , cind introducem o functie in interiorul use memo pentru ca ea sa se efectueze doar cind dependentelele se schimba.

*** React.memo() --> evita re-rerenderingul inutil al componentelor care nu se schimba.
    
* useCallback() 
* useReducer()

* <svg className={styles['icon-fav']}>
              <use
                href={`${process.env.PUBLIC_URL}/sprite.svg#heart`}
                xlinkHref={`${process.env.PUBLIC_URL}/sprite.svg#heart`}
              />
    </svg>  - astfel afisam o icon svg din publi folder



* sfc - simple functional component - face o componenta simpla fara date cu export 
* rafce - react arrow function export component - face o componenta simpla cu numele file cu react in ea 


*useEffect(() => {
    if (!products.list) {
        return;
    }
}, []);
- astfel putem pune o conditie a executarii lui use effect , tot ce va veni dupa return in caz ca products.list este gol fals sau undefined , nu va fi executat , functia va iesi din useEffect