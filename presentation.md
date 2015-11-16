title: ECMAScript 6
author:
    name: Kamil Durkiewicz
    url: http://github.com/durkiewicz
style: presentation.css
script: script.js
output: index.html
controls: true

--
# Elm
## Functional Reactive Programming in Elm

--
# Why Java and C&#35; are bad?

--
### Sample Java code (1/2)
```
public class Person {
    private final int age;
    private final String name;
    
    public Person(final int age, final String name) {
        this.age = age;
        this.name = name;
    }
    
    public int getAge() {
        return this.age;
    }
    
    public String getName() {
        return this.name;
    }
    
    @Override
    public boolean equals(final Object o) {
        if (this == o) return true;
        if (!(o instanceof Person)) return false;
        final Person that = (Person) o;
        return Objects.equals(this.age, that.age) &&
            Objects.equals(this.name, that.name);
    }
```

--
### Sample Java code (2/2)
```    
    @Override
    public int hashCode() {
        return Objects.hash(this.age, this.name);
    }
    
    @Override
    public String toString() {
        final StringBuilder sb = new StringBuilder("{");
        sb.append("age=").append(this.age);
        sb.append(", name=").append(this.name);
        sb.append('}');
        return sb.toString();
    }
}
```

--
### Why Javascript is bad?

Yes, it is expresive.
```
var person = { name: "Kamil", age: 29 };
```
But JS developers see these messages many times a day:
- "undefined is not a function"
- "cannot read property 'name' of null"
- "object is not a function"

And they are scared to refactor. Or they waste many days to do a simple refactor. 

--
### What is Elm?

- functional programming language
- FRP approach to building browser applications
- created by Evan Czaplicki in 2012

--
### Language features

- syntax similar to Haskell...
- ...but conceptually closer to ML language family (SML, OCaml, F#)
- typing: static, strong, inferred 
- small but expressive set of language constructs
- immutability
- transpiled to JS

--
### Syntax

[http://elm-lang.org/docs/syntax](http://elm-lang.org/docs/syntax)

--
### Missing language features

- `null` / `undefined` / `NaN`
- OOP-style classes
- changing a value of anything
```
x = 1
x = 2 {- causes a compilation error -} 
```
```
p = { name = "Kamil", age = 29 }
p = { name = "Kamil Piotr", age = 29 } {- causes a compilation error -} 
```
```
p = { name = "Kamil", age = 29 }
p.name = "Kamil Piotr" {- no such syntax -}
```
--
### Signals

- A signal is a value that changes over time.
- example `Mouse.position : Signal ( Int, Int )`
- or `main : Signal Html`
- `foldp : (a -> state -> state) -> state -> Signal a -> Signal state`
- `foldp` is similar to `foldr` or to `Array.prototype.reduce` from JS 

--
### Elm architecture

- there's a separate [article](https://github.com/evancz/elm-architecture-tutorial/) about it
- very similar to React + Flux

--
### Advantages

- Much easier refactoring
- Runtime errors are rare
- Problem detection at CI can be very cheap

--
### Exercise

- let's implement a ball that can kill Mario
- [github.com/durkiewicz/mario-elm](https://github.com/durkiewicz/mario-elm)
- branch master - copy / paste from [elm-lang.org/examples/mario](http://elm-lang.org/examples/mario)
- branch mario-with-ball - proposition of a new model

--
### References

- [http://elm-lang.org](http://elm-lang.org)
- [https://github.com/rtfeldman/dreamwriter](https://github.com/rtfeldman/dreamwriter)
