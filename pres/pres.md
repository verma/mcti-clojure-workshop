
```clojure
(def title  "Clojure Workshop")
(def author "Uday Verma")
(def date   "Apr 3, 2015")
```




```clojure
(def a-number 100)
(def a-float  3.141592654)

(def a-string  "Hello There")
(def a-keyword :mickey-mouse)
```




```javascript
// javascript
var a = 1 + 2 + 3 + 4 + 5 + 6;
```

```clojure
;; clojure
(def a (+ 1 2 3 4 5 6))
```




```javascript
// javascript
var a = 1 * 2 * 3 * 4 * 5 * 6;
```

```clojure
;; clojure
(def a (* 1 2 3 4 5 6))
```




```clojure
(def a [1 2 3 4 5])

(def b [1 2 :stuff "string" 2.32])
```




```clojure
(def a {"first-name" "Mickey"
        "last-name"  "Mouse"})

(def b {:first-name "Mickey"
        :last-name  "Mouse"})
```




```clojure
(def a {1 "Mickey"
        2 "Mouse"})

(def b {[1 2 3] "Mickey"
        [4 5 6] "Mouse"})
```




```clojure
(def a {1 "Mickey"
        2 "Mouse"})

(def b [:this :stuff :is :out :of :control])

(count a) ;; 2
(count b) ;; 6
```




```clojure
(def a {1 "Mickey"
        2 "Mouse"})

(def b [:this :stuff :is :out :of :control])

(a 1)     ;; "Mickey"
(b 3)     ;; :out
(nth b 3) ;; :out
```




```clojure
(def a {1 "Mickey"
        2 "Mouse"})

(get a 5)               ;; nil
(get a 5 :dont-haz)     ;; :dont-haz
```




```clojure
(def a {:fname "James" :lname "Bond"})
(def b (assoc a :agency :mi-6))

=> b
{:fname "James" :lname "Bond" :agency :mi-6}

=> a
{:fname "James" :lname "Bond"}
```




```clojure
(def i-can-haz-filosofi?
     "Things are immutable in Clojure, you
     can only make new things out of old
     ones, and old ones remain unchanged")
```




```clojure
(def agent-007
    {:fname "James" :lname "Bond"
        :agency mi-6
        :address
            {:street "Many Secret Street"
             :city "London"
             :country "GB"}})
```




```clojure
(get agent-007 :agency)    ;; :mi-6
(get agent-007 :weakness)  ;; nil
(get agent-007 :weakness :none)  ;; :none
(get-in agent-007
        [:address :country])  ;; "GB"

```




```clojure
(def a-set #{:wow :such :set})

(contains? a-set :wow) ;; true
(a-set :wow) ;; wow
(a-set :not-wow) ;; nil
```




```clojure
(def a-weird-list (1 2 3) ;; ERRAR! 1 is not a function
(def a-list '(1 2 3 4))   ;; notice that '

(first a-list) ;; 1
(second a-list) ;; 2
(nth a-list 3)  ;; 4

(rest a-list) ;; (2, 3, 4)
```




```clojure
(conj [1 2 3] 3) ;; [1 2 3 3]
(conj '(1 2 3) 3) ;; (3 1 2 3)

(conj #{1 2 4} 3) ;; #{1 2 4 3}
(conj #{1 2 4} 4) ;; #{1 2 4}

(conj {:a 1} [:b 2]) ;; {:a 1 :b 2}
```




```clojure
(defn add-4 [n]
  (+ 4 n))

(add-4 3) ;; 7
(add-4 2) ;; 6
```





```clojure
(defn mul-4 [n]
  (* 4 n))

(mul-4 3) ;; 12
(mul-4 2) ;; 8
```





```clojure
(defn do-this [f n]
  (f n))

(do-this add-4 3) ;; 6
(do-this mul-4 3) ;; 12
```




```clojure
(do-this - 1) ;; -1
(do-this (fn [v]
           (+ 1 v))
         5) ;; 6
```




```clojure
(do-this #(+ 1 %) 5) ;; 6
(do-this (partial + 1) 5) ;; 6
(do-this inc 5)  ;; 6
```





```clojure
(map
  inc
  [1 2 3 4 5]) ;; [2 3 4 5 6]
(map
  str
  [1 2 3 4 5])
  ;; ["1" "2" "3" "4" "5"]
```





```clojure
(map
  (fn [v]
    (* v v v))
  [1 2 3 4 5]) ;; [1 8 27 64 125]
(map
  #(* % % %)
  [1 2 3 4 5]) ;; [1 8 27 64 125]
```





```clojure
(fn [a] (+ a 5))
#(+ % 5)

(fn [a b] (+ a b))
#(+ %1 %2)
```





```clojure
(do-this #(+ 5 %) 5) ;; 10

(do-this #(+ (- 2 %) 5) 10) ;; -3
```





```clojure
(do-this #(+ 5 %) 5) ;; 10

(do-this #(+ (- 2 %) 5) 10) ;; -3
```





```clojure
(if true
  "hello"
  "bye")        ;; "hello"
```





```clojure
(if (= 4 4)
  "equal"
  "nope, failure")   ;; "equal"
```





```clojure
(if (zero? (mod 10 2)))
  "2 divides 10"
  "nope, failure")   ;; "2 divides 10"
```




```
(loop [v 10]           ;; <-- v = 10
  (println v)
  (when (pos? v)
    (recur (dec v)))) ;; recur with dec'd v 
```





```
(loop [v (read-byte)]
  (when-not (eof? v)
    (process-byte! v)
    (recur (read-byte))))
  
```






```
(loop [] 
  (let [v (read-byte)]
    (when-not (eof? v)
        (process-byte! v)
        (recur))))
  
```




```
(doall
  (map process-byte!
    (read-bytes-from-file)))
  
```





```
(ns my-code
  (:require [quil.core :as q]))

(q/defsketch stuff
  ;; ...
  )
```
