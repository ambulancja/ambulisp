## Ambulisp 🚑

LISP Interpreter written in [LDPL](https://github.com/Lartu/ldpl).

### Commands

- `(quote x)` returns `x` without executing it.
- `(begin x1 ... xn)` executes `x1`, `x2`, ..., `xn` and returns the result of `xn`.
- `(define x y)` defines the variable `x` with the value of `y` enlarging the scope.
- `(set x y)` sets the value of `x` to the value of `y` without enlarging the scope, the variable `x` already has to be defined. 
- `(if c1 x1 c2 x2 ... cn xn [y])` if the condition `c1` is true, returns the result of `x1`. If it is not, it keeps evaluating until any of the conditions `c1`, `c2`, ..., `cn` are true. If none of these return true, it returns `y`. The `[y]` part is optional.
- `(lambda (x1 ... xn) y1 ... ym)` creates a lambda with n parameters that when called executes the commands `y1`, ..., `yn`.
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
