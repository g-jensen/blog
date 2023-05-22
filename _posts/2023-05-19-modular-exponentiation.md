---
layout: post
title: "Modular Exponentiation"
date: 2023-05-19
---
Modular exponentiation refers to any expression in the form `b^e (mod n)`.

The simple way to calculate the value of this expression would be to simply calculate `b^e` and then
take that value `mod n`.

As `b` and `e` become large, calculating the value of this expression the simple way becomes very time-consuming and
can cause integer overflows even if the ending value is not large.

One way to greatly increase the speed and decrease the chance of integer overflows is to use Binary Exponentiation.
This process involves converting `e` into binary and then looping through the bits to take shortcuts.

The following implementation of Binary Exponentiation in Clojure (`mod-pow`) loops through of the bits of `e` from right to
left and is thus called Right-to-Left Binary Exponentiation:

```clojure
(defn mod-pow-next [val exponent base n]
      (if (= 1 (mod exponent 2))
        (mod (* val base) n)
        val))

(defn mod-pow [base exponent n]
      (loop [base     base
             answer   1
             exponent exponent]
            (if (zero? exponent)
              answer
              (recur (mod (* base base) n)
                     (mod-pow-next answer exponent base n)
                     (quot exponent 2)))))
```

The `(quot exponent 2)` and `(if (= 1 (mod exponent 2))` are the parts that loop through of bits of `e`

A small benchmark:
```clojure
(time (mod-pow 93 163 4))
"Elapsed time: 0.084 msecs"
=> 1
(time (mod (pow 93 163) 4))
"Elapsed time: 1.441667 msecs"
=> 1N
```

Notice that the simple way returns `1N` as opposed to `1`. This shows that it
first calculated `93^163` and then just took that `(mod 4)`. But the more sophisticated method only returns
`1` because it never actually gets to numbers high enough to have to use `BigInteger`