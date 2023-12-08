# Prolog

## Ejemplos en Lisp

### Funciones
```lisp
(defun letras ()
  (format t "Ingresa una letra minúscula: ")
  (let ((letra (read)))
    (cond
      ((member letra '(a e i o u)) (format t "La letra a es una vocal. ~a" letra))
      ((member letra '(y)) (format t "La letra a es una semivocal. ~a" letra))
      (t (format t "La letra a es una consonante. ~a" letra)))))

(defun letras_when ()
  (format t "Ingresa una letra minúscula: ")
  (let ((letra (read)))
    (when (member letra '(a e i o u))
      (format t "La letra es minuscula. ~a" letra))
    (when (member letra '(y))
      (format t "La letra es una semivocal. ~a" letra))
    (when (not (member letra '(a e i o u y)))
      (format t "La letra es una consonante. ~a" letra)))))

(defun factorial (x)
    (if (= x 0)
        1
        (* x (factorial (- x 1))))
)

(defun fibo (n)
    (if (< n 2)
        n
        (+ (fibo (- n 1)) (fibo (- n 2))))
)

(defun recorre (lista)
    (format t "~A-> ~% " (car lista))
    (if lista
        (recorre (cdr lista))
    )
)

(defvar *calcular_area_cuadrado*
    (lambda (lado)
        (* lado lado))
)

(defvar *calcular_area_cubo*
    (lambda (altura)
        (let ((lado (read)))
            (* (funcall *calcular_area_cuadrado* lado) altura)))
)
```
### Condicionales


```lisp
(format t "Ingresa la longitud de los lados: ")
(setq lado (read))
(format t "Ingresa la longitud de la altura: ")
(setq altura (read))
(format t "El área del cuadrado es: ~A ~%" (funcall *calcular_area_cuadrado* lado))
(format t "El volumen del cubo es: ~A" (funcall *calcular_area_cubo* altura))
(defvar *number-was-odd* nil)
(if (oddp 5)
    (progn (setf *number-was-odd* t)
       'odd-number)
    'even-number)

(when (oddp 5)
  (setf *number-is-odd* t)
  'odd-number)

(unless (oddp 4)
  (setf *number-is-odd* nil)
  'even-number)

(defvar *x* 20)
(cond
  ((= x 0) (print "x es igual a 0"))
  ((> x 0) (print "x es mayor que 0"))
  ((< x 0) (print "x es menor que 0"))
  (t (print "Esta es la acción predeterminada")))

(setq dia-de-la-semana 'martes)

(case dia-de-la-semana
    (lunes (print "Hoy es lunes."))
    (martes (print "Hoy es martes."))
    (miércoles (print "Hoy es miércoles."))
    (otherwise (print "Día desconocido.")))
```

### CAR CDR
```lisp
(quote (+ 2 3))
'(+ 2 3)

(setq 'a '(1 2 3 4))
(car a)
(cdr a)
(cddr a)
(cdddr a)

(setq b '((1 2 3 4 5) a b c))
(caar b)
(car b)
(cdr b)

(setq c '(1 2 3 4 (a b c) (d e f)))
(car c)
(caar (cddddr c))
(caar (cddddr (cdr c)))
(car (cdr (cdr c)))
```

```prolog
(Cabeza|Cola) = (1 2 3 4).
(a b c) = (X Y Z).
```
### Arbol genealogico
```prolog
padre(Luis, Farid).
padre(Luis, Jessa).
madre(Ale, Farid).
madre(Ale, Jessa).

madre(Ale, Roberto).
hermano(Roberto, José).
abuelo(Baldomero, José).

madre(María, Ale).
abuela(María, Farid).
abuela(Isaura, Farid).

tia(Lulú, Farid).
tía(Lulú, Jessa).
```
### Sistema Maestro (1D)
```prolog
%padres
madrede(anne,harry).
padrede(rob,harry).
madrede(karen,liam).
padrede(geoff,liam).
madrede(maura,niall).
padrede(bobby,niall).
madrede(johanna,louis).
padrede(mark,louis).
madrede(trisha,zayn).
padrede(yaser,zayn).

%hermanos
hermanade(gemma,harry).
hermanade(ruth,liam).
hermanade(nicola,liam).
hermanade(georgia,louis).
hermanade(lottie,louis).
hermanade(felicite,louis).
hermanade(phoebe,louis).
hermanade(daisy,louis).
hermanade(doris,louis).
hermanode(ernest,louis).
hermanode(greg,niall).
hermanade(safaa,zayn).
hermanade(doniya,zayn).
hermanade(waliyha,zayn).

%origen
provienede(harry,holmes_chappel).
provienede(louis,doncaster).
provienede(niall,mullingar).
provienede(zayn,bradford).
provienede(liam,wolverhampton).

%signo
signode(liam,virgo).
signode(niall,virgo).
signode(harry,acuario).
signode(louis,capricornio).
signode(zayn,capricornio).

%discos
discode(one_direction,txf,2010).
discode(one_direction,uan,2011).
discode(one_direction,tmh,2012).
discode(one_direction,mm,2013).
discode(one_direction,four,2014).
discode(one_direction,mitam,2015).
discode(harry,hs,2017).
discode(harry,fl,2019).
discode(harry,hh,2022).
discode(liam,lp1,2019).
discode(louis,walls,2020).
discode(louis,fitf,2022).
discode(niall,flicker,2017).
discode(niall,hw,2020).
discode(niall,theshow,2023).

%parejas_que_me_gustaban
exnoviade(kendall,harry).
exnoviade(taylor,harry).
exnoviade(daniellep,liam).
exnoviade(sophia,liam).
exnoviade(eleanor,louis).
exnoviade(danielle,louis).
exnoviade(hailee,niall).
exnoviade(barbara,niall).
exnoviade(perrie,zayn).
exnoviade(rebecca,zayn).

%con_quien_se_quedaron
noviade(cheryl,liam).
noviade(brianna,louis).
noviade(amelia,niall).
noviade(gigi,zayn).
noviade(olivia,harry).

%sus_bebes_bonitos
hijode(freddie,louis).
hijode(bear,liam).
hijade(khai,zayn).

miembrode(harry,one_direction).
miembrode(liam,one_direction).
miembrode(niall,one_direction).
miembrode(louis,one_direction).


% regla para saber si es miembro
es_miembro(X):- miembrode(X,Y).

% regla para saber quien es madre de quien 
es_madre(X,Y):- madrede(X,Y).

% regla para saber quien es padre de quien 
es_padre(X,Y):- padrede(X,Y).

% regla para saber quien anduvo con quien
ex_novia(X,Y):- exnoviade(X,Y).

% regla de con quien quedaron al final
es_novia(X,Y):- noviade(X,Y).

% regla para saber quien tiene disco
disco_de_quien(X):- discode(X,,).

% muestra el artista y el año que saco disco
disco_cuando(X,Y):- discode(X,,Y), disco_de_quien(,_,_Y).

% regla para saber quién sacó qué disco en un año específico
disco_en_ano(X, Y, Z) :- discode(X, Y, Z),discode(X,_,Z).

% quien tiene uno bebe juntos
tienen_hijo_juntos(X,Y):- madrede(X,Hijo),padrede(Y,Hijo).

% quien es del mismo signo
signo_compatible(X,Y):-signode(X,signo),signode(Y,signo),
X \= Y. % para que sean diferentes los datos.

% para encontrar la ciudad natal de cada uno
ciudad_natal(X, Ciudad) :- miembrode(X, one_direction), provienede(X, Ciudad).

% para saber si son de la misma familia
misma_familia(X, Y) :- hermanos(X, Y) ; madre(X, Y) ; madre(Y, X) ; noviade(X, Y) ; noviade(Y, X) ; hijode(X, Y) ; hijode(Y, X).
```

### Relaciones Paperas
```prolog
% Hechos sobre los síntomas de las paperas
sintoma(dolor_y_endurecimiento_glandula_parotida).
sintoma(fiebre, 40).
sintoma(dolor_de_cabeza).
sintoma(dolores_musculares).
sintoma(negacion_a_comer).
sintoma(cansancio).
sintoma(dolor_o_sensibilidad_alrededor_hinchazon).
sintoma(aparicion_sintomas, 3-7).
sintoma(lobulo_oreja_elevado).

% Hechos sobre las complicaciones de las paperas
complicacion(meningoencefalitis).
complicacion(orquitis).
complicacion(epididimitis).
complicacion(oforitis).
complicacion(nefritis).
complicacion(miocarditis).
complicacion(artritis).
complicacion(encefalitis).
complicacion(meningitis).
complicacion(perdida_auditiva).
complicacion(pancreatitis).
complicacion(aborto_espontaneo).

% Prevenciones de las paperas
prevencion(vacunacion_infancia, primera_dosis, 15_meses).
prevencion(vacunacion_infancia, refuerzo, 6_anios).

% Tratamientos de las paperas
tratamiento(descanso).
tratamiento(analgesicos_sint_receta, ibuprofeno).
tratamiento(analgesicos_sint_receta, acetaminofen).
tratamiento(aplicar_pano_frio_tibio_glandulas_salivales_hinchadas).
tratamiento(beber_mucholiquido, 6-8_vasos_dia).
tratamiento(evitar_alimentos_citricos).
tratamiento(recuperacion, 3-10_dias).
```
