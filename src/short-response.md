# Section 2 — Short Response

Write your responses directly in this file. Follow markdown formatting guidelines. Check the rubric.md file to see how your short responses will be graded.

As a quick guide, check the following before submitting:

- [] Answered all parts of every question
- [] No typos or grammar mistakes (use grammarly!)
- [] Accurately uses relevant technical terminology
- [] Uses markdown to enhance readability (preview in VS Code with Command/Control + Shift + V)
- [] Responses are concise and easy to comprehend

---

## Question 1

In your own words, explain what does _encapsulation_ refer to? Why is this concept beneficial when programming?

Provide a code snippet to illustrate _encapsulation_.

## Response 1

`Encapsulation` is one of the pillars of object-oriented programming in which data (including behaviors) is bundled up together(interface or object). This allows the data to be accessed only in areas where you want it to be access.
for ex:

```js
const person={
  name: `Jerry`,
  age: `29`,
  speak(){
    return `Hi I'm ${this.name}!`
  }
  getAge(){
    return `I am ${this.age}!`
  }
}
```

In the code above all the instance variables and methods will only belong to the person object.

## Question 2

Explain what the `this` keyword is. Why is the `this` keyword useful?

In the code snippet below, what does `this` refer to?

```js
class Counter {
  constructor() {
    this.count = 0;
  }
  increment() {
    this.count++;
  }
}

const counterA = new Counter();
const counterB = new Counter();

counterA.increment();
counterA.increment();
counterA.increment();

counterB.increment();

console.log(counterA.count);
console.log(counterB.count);
```

## Response 2

The `this` keyword refers directly to the object that is _invoking_ the method. It is useful because it allows methods and functions to access the properties and other methods of that specific object, making the code more flexible and reusable.

In this example, `this.count = 0` can be understood as setting the `count` property on the specific `Counter` object that is created. It does not refer to the `Counter` class itself, but rather to the _instance_ of the class. Therefore, the `this` keyword is referring to the individual object created from the `Counter` class, not the class as a whole.

---

## Question 3

In your own words, explain what **polymorphism** means in OOP. Provide an example in code that demonstrates polymorphism.

## Response 3

`Polymorphism` is another pillar of OOP where different types of objects can be used in similar ways because they share the same _interface_, even if each type implements those methods differently.

ex:

```js
Class Enemy{
  constructor(name,health,attack){
    this.name =name;
    this.health = health;
    this.attack = attack;
  }
  Attack(){
    return `${this.name} dealt ${attack} damage!`;
  }
}
class Goblin extends Enemy{
  constructor(health,attack){
    super(`Goblin`,health,attack);
    this.clubPower =20;
  }
  specialMove(){
    return `${this.clubPower} damage! That club hit hard`;
  }
}
class Demon extends Enemy{
  constructor(health,attack){
    super(`Demon`,health,attack);
    this.bloodDrain
  }
  specialMove(){
    return `Ah! They drain ${this.bloodDrain}!`
  }
}
```

In this example, the `Demon `and `Goblin` classes both use the shared code from the `Enemy` class — that part is _inheritance_.

It becomes `polymorphism` because they each define their own version of the `specialMove()` method. Even though both objects expose a method with the same name, each one behaves differently. This allows you to call .`specialMove()` on any enemy type and get behavior specific to that enemy.

---

## Question 4

You're building a game where players can raise different digital pets: Cats, Dogs, and Birds. All pets have have a `name`, `energy` level, and `happiness` level and can all `sleep`. Cats have the ability to `hunt`, dogs have the ability to `chase`, and birds have the ability to `fly`.

**Part A:** Describe in words how you would use inheritance to organize these classes.

**Part B:** Explain one advantage of using inheritance here instead of creating three completely separate classes.

## Response 4

`Inheritance` is the relationship between two classes where a child class (subclass) inherits methods and properties from a parent class (superclass). This allows the child class to reuse and extend the functionality defined in the parent class. (Almost always, when a class uses the `extends` keyword, it is using inheritance.)

In this example, we create a parent class called `Animal` that sets up a constructor taking in name, energy, and happiness. This shared setup can be reused by all animals—such as a cat, dog, or bird—while still allowing each one to have its own unique ability.

```js
class Animal {
  constructor(name, energy, happiness) {
    this.name = name;
    this.energy = energy;
    this.happiness = happiness;
  }
  sleep() {
    return `${this.name} is sleeping`;
  }
}
class Cat extends Animal {
  constructor(energy, happiness) {
    super(`cat`, energy, happiness);
    this.ability = `hunt`;
  }
}
class Dog extends Animal {
  constructor(energy, happiness) {
    super(`dog`, energy, happiness);
    this.ability = `chase`;
  }
}
class Bird extends Animal {
  constructor(energy, happiness) {
    super(`bird`, energy, happiness);
    this.ability = `fly`;
  }
}
```

It is beneficial because you aren’t rewriting the same code, which follows the DRY (Don’t Repeat Yourself) principle. Instead of redeclaring the same logic over and over again, you get to reuse the code that already exists.
