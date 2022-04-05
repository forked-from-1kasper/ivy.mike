Groupoid Infinity for Arend
===========================

This is a port of Groupoid Infinity cubical base library to JetBrains Arend proof assistant.

```
\func meet (i j : I)
   => \let | p1 => \lam i j => (coe (\lam x => left = x) (path (\lam _ => left)) j @ i)
           | p2 => (path (\lam _ => path (\lam _ => left)))
       \in coe (\lam i => Path (\lam j => left = p1 i j) (path (\lam _ => left))
               (path (\lam j => p1 i j))) p2 right @ i @ j

\func connAnd {A : \Type} {a b : A} (p : a = b) (i : I) : a = p @ i
   => path (\lam j => p @ meet i j)

\func J (A : \Type) (a : A) (C : \Pi (x : A) -> a = x -> \Type)
        (d : C a (refl A a)) (x : A) (p : a = x) : C x p
   => coe (\lam i => C (p @ i) (connAnd p i)) d right
```

Credits
-------

* Maxim Sokhatsky
* Siegmentation Fault
* Sergei Stepanenko
* Tesla Ice Zhang‮
