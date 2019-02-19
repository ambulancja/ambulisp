Implementacion de LISP hecha en [LDPL](https://github.com/Lartu/ldpl).

**Comandos**

- `(quote x)` devuelve x sin ejecutarlo
- `(begin x1 ... xn)` ejecuta x1, x2, ..., xn y devuelve el resultado de xn
- `(define x y)` define la variable x con el valor de y (agranda el scope)
- `(set x y)` asigna la variable x al valor de y (no agranda el scope, la variable x ya tiene que estar definida)
- `(if c1 x1 c2 x2 ... cn xn [y])` si la condición c1 es verdadera devuelve el resultado de x1, si no sigue evaluando hasta que alguna de las condiciones c1, c2, ..., cn sea verdadera. si ninguna es verdadera devuelve y. el else "y" es popcional
- `(lambda (x1 ... xn) y1 ... ym)` crea una lambda con n parametros que cuando se la llama ejecuta los comandos y1, ..., ym
- `(f x1 ... xn)` llama a la funcion f con los parametros x1, ..., xn.
- `()` es la lista vacia
- `(cons x y)` crea un cons `(x . y)`
- `(car x)` devuelve el car del cons
- `(cdr x)` devuelve el cdr del cons
- `(null x)` si es la lista vacía devuelve t sino devuelve ()
- `(eq x y)` si son iguales devuelve t sino devuelve ()
- `(print x)` muestra x.
- `(println x)` muestra x seguido de un enter

**Ejemplo**

## map.ambulisp ##

```
(define nil (quote ()))

(define map)
(set map
  (lambda (f list)
    (if (null list)
        nil
        (cons
          (f (car list))
          (map f (cdr list))))))

(println
  (map (lambda (x) (cons x x))
       (cons (quote a)
         (cons (quote b)
           (cons (quote c)
                 nil)))))
```

- ldpl ambulisp.ldpl<map.ambulisp
- ((a . a) (b . b) (c . c))
