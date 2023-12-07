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
'''lisp
###Condicionales

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
