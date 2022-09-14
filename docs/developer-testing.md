# Developer Testing

I use the phrase "developer testing" to *slightly* differentiate what we do in terms of testing as developers from what "typical" software testers do.

The biggest difference is that we **write tests as we write the code, often for things that don't even exist yet**. A software tester is usually more concerned with the "external quality" of the code - does it do the right thing.

## Quality

### Internal Quality

You wrote the code well. It is *Loosely coupled*, and *highly cohesive*.

It is *adaptable to change* because change is inevitable.

### External Quality

The *most important* point. It does what it is supposed to do. You wrote the right thing. It is meets the "Business Requirements", etc.


## Feedback Loops

We want to build development and production systems that allow us to see what is going on - good or bad - as soon as possible. 

These are "feedback loops", which is from the branch of engineering called Cybernetics.

We *intentionally* create feedback loops in our code to help us ensure we are doing the right thing.

### Inner Loop
All that stuff that happens "under our fingers" in our development environment. Instantaneous or nearly instantaneous feedback.
### Outer Loop
All that stuff that happens after we push our code to the source code repository and our build pipeline takes over.
Much slower feedback loop.

## Four Levels of Testing

### Static

Stuff like using the type system to prevent invalid states, using a strictly typed language, using `editorconfig`, or `eslint`, etc. 

e.g. In C# you can't call a method on a class that doesn't exist. You can't compile it. 

We write our code so that the inner loop will prevent *others* from creating invalid states.

This is super **inner loop**.

### Unit Testing

Testing a functional unit of code in isolation from other code. In C# that is usually a single method. 

This too is super **inner loop**.

### Integration Testing

Any time we test two or more functional units together. We are seeing how our code "integrates" with other code.

Usually involved testing against other systems (attached resources), which can include databases, networks, etc.

Sometimes this is *outer loop*, but we strive to bring as much to this in our *inner loop* as possible. More on this later in the course.

### End-To-End Testing

Often in the form of "smoke tests" - before you put the code in front of users, you have some automated (or manual) tests just to verify that it is ready for prime-time.

This is super expensive, and almost never can be complete. We rely on lower forms of test (above) a lot because of this.

Total **outer loop** stuff.


## Approaches to Writing Tests

### Test After

You write the code, you write some tests to verify that the code works now (and in the future, still works that way) according to your expectations.

## Test First

You know what you are writing, so you start with a test. It fails. When it passes you are "done". Great for ADD people. ;)

## Test-Driven Development

A form of Test-First, but implemented as a design methodology. In other words, TDD is more about *designing* code than actually "testing" it.

### TDD Form

When and if you decide to do TDD, there is a "form" you adopt. Some rules you play by. They are:

#### RED
Start with writing a meaningfully failing test.

:::tip
Meaningfully Failing here means that the test fails on the `Assert`.
:::

#### GREEN
Write *just enough* code to make the test pass. It does not need to be, nor should it be, "good" code. Just make the test pass.

This ensures that you understand the *problem* and how to solve it before you worry about the *implementation* of how *best* to do it.

#### REFACTOR

After the test is passing, make it "good". Look for duplication, look for latent abstractions, etc.

#### (Sometimes) Commit

Make a commit. 