
 <img src="https://user-images.githubusercontent.com/31222514/149813300-65804694-d3ea-4e31-955d-dbc47229a82d.png" width="30%" alt="Typescript logo">
 
# Typescript

Short summary of a typescript beginner's lesson

# Why

Because it is AWESOME! 

- avoid bugs
- make code clear
- more maintainable

Not for nothing it is falvor #1

![state of javascript](https://s3.eu-west-1.amazonaws.com/cd.sseu.re/items/bLuxng8E/3af806a4-6bc9-4cd9-99f2-9916d1cfece2.jpg?v=b98886f90248690c47ab0beaa1045ae9?v=b98886f90248690c47ab0beaa1045ae9)


## Errors

1. syntax errors (`{name: "David, email: "david.rajcher@codairsseur"`)
2. Static type errors (`"Thanks for buying [object Object], we hope to see you again!"`)
3. Dynamic type errors (`Uncaught TypeError: Cannot read property 'title' of undefined`)
4. Exceptions (catching a 500 error... Typescript does not help)
5. Logical 👑 (Typescript does not help)


```javascript
const createFullName = (firstName, lastName) => {
 return `${firstName} ${lastName}`
}

createFullName({firstName: 'david', lastName: 'rajcher'})
```

## Main types

The main types will be the same as our data types:

- string
- boolean
- number
- null
- undefined

Array we define by using a type and adding a `[]` to it
- `strings[]`
- `boolean[]`

With object we can (and should) define each property

```typescript
type Pet = {
  id: number,
  name: string,
  age: number,
  friendly: boolean,
}
```

We can then expend using other types:

```typescript
type Health = {
     vaccinations: string[],
     general: numner,
     allergies: string[]
}

type Pet = {
  id: number,
  name: string,
  age: number,
  friendly: boolean,
  health: Health
}
```

And we can even expend using more exotic types:

```typescript

type Health = {
     vaccinations: Vaccine[]
}

type Vaccine = 'arvovirus' | 'distemper' | 'canine hepatitis' | 'rabies'

type status = 'active' | 'inactive' | 'pending'

type Book = {
   title: string,
   author: string,
   genere: Genere | null
}


type Dog = {name: string} & Animal & Canine
```

## Interfaces

Very similar to types but have extra features.

One extra feature is that they are extendable:

```typescript
interface Email {
    sender: string
    recipient: string
    title: string
    content: string
}

interface SecureEmail extends Email {
    secure: boolean,
    domain: 'hospital', 'private', 'pharmacy'
}
```

## Functions

```typescript
const fetchBooks = async (author, year, title, available) => {
     return await axios.get('api.articles.com', 
     {
       params: {
         auther,
         year, 
         title,
         available
      }
     }
  )    
}

fetchBooks({auther: 'Thomas Sowell'})
```

Let's add some types
```typescript
const fetchBooks = async (author: string, year: number, title: string, available: boolean) => {
     return await axios.get('api.articles.com', 
     {
       params: {
         auther,
         year, 
         title,
         publisher
      }
     }
  )    
}
```
And a return type

```typescript

interface Book {
    author: string
    year: numner
    title: string
    available: boolean
    genre: Genre
    pages: number
    difficulty: 1 | 2 | 3 | 4 | 5
}


const fetchBooks = async (author: string, year: number, title: string, available: boolean): Promise<Book[]> => {
     // code
}
```
Params as an object

```typescript
const fetchBooks = async ({
   author
   year,
   title, 
   available
}: {
   author: string
   year: string
   title: string
   available: boolean
}): Book[] => {
     // code
}
```
Let's separate the params' interface from the function
```typescript
interface Params {
   author: string
   year: string
   title: string
   available: boolean
}

interface Book {
    author: string
    year: number
    title: string
    available: boolean
    genre: Genre
    pages: number
    difficulty: 1 | 2 | 3 | 4 | 5
}

const fetchBooks = async ({
   author
   year,
   title, 
   available
}: Params): Promise<Book[]> => {
     // code
}
```
And maybe some params (or all) should not be forced
```typescript
interface Params {
   author?: string
   year?: string
   title?: string
   available?: boolean
}
```
And maybe there can be extra params
```typescript
interface Params {
   author?: string
   year?: string
   title?: string
   available?: boolean
   [key: string]: any
}
```
And lastly, we can also define functions inside interfaces
```typescript
interface Pet {
   name: string
   kind: string
   age: number
   friendly: boolean
   noise: () => string
}

const dog: Pet = {
   name: 'rocky'
   kind: 'canine',
   age: 1,
   friendly: false,
   noise: () => 'woof woof'
}

console.log(dog.noise())

```
What about functions that don't return anything?
```typescript
const submit = (form): void => {     
     setForm(form)
}
```

## any

```typescript

interface Pet {
    name: string,
    age: number
    favoriteToy: any
}
```

## Go practice

1. [Exercise: email](https://www.staging-typescript.org/play?ssl=31&ssc=11&pln=22&pc=1#code/M4UwdgJg6iA2DGB7AtiAosghgS1gCgG8AoAAhLE1QC4SAiAaTlhAE9aAaUkkLXG2gNZNWAASQQcwUAFcATgDokyDl1nSARrOzxgNYmTIArROt0kCJAC7ZLzfgCkTJAA6Jg1sAHNgHEhBDA8PwA4iCWJNLOEpYBJIhgJMbqLm4e3iTYCYhy5GEA7oiyArQkAL6cBlYg8AAWelY2dnQAKtU1uXk+7H4BQXQAYrIoJABKIJjw4Z5uwNjOVohWNSAdAeGYkCRIiMzuJLDYmphaASXlXGSyGxAo9da2IA7Se6iowCSy47CwbGVcpURSgBKIhEABm0jAk2w8RIoEgMAQKHQvHwFFQ3R4OFg3TUmm07wAvCQANoAXSB5i4SDAezksBIxNoNUslmcugA9BzxJIZAowCBOrRqfEXgFgJhPCtiQADC4kAA8zgAfAAJbAkAAkBHRIFKAEIFRyVaDKkrlYilCtLItLMsSABhRASbBSEA5AWdOLSB6WfUkGAAck+8rhkRAshINUwzmcLAWUcwADcVixsnEwOpEMcIIbjcrTQZzQBNbKBlMZSDaTAxCAkNPSEh5DbhG0faogbAVvIgEACH6hyLRWKwu0rME7WCIPKZTxagh4rQ6eTMLx20ofDRL3RGk3yhUQLtbWCYKSE2ieLQQWgFypkbWLgnyLDOPCP+CM5VUu8GT6WOQJHKP5moeSbHqewDnu+N6hsBCruEMXjKg+W7aPI9zMKURoIfEni3sBZoqih+ICPI-iBLIWH5rBZocqB+E-jKADcsHAvIxiZHgtC0ECAK0fRhZkOaAAyiApt0DaRjEEzLLI7zXEsKyfHsiBgopVSULuBb7vM8AnmetDAFg3wkMgPogNeDFFpgUafGC57avSpQcpCwAaBRhwgAA-FiuCEtqvmwKUN4AKq0u58BaOoIBGpgVlaVwzGFjSwA7CAK6IJ4eBvBKUpAixpRAA1.)
2. [Exercise: tic tac toe](https://www.staging-typescript.org/play?#code/FAFwngDgpgBAKgSwDawLwwK4DsDWWD2A7lgNwwD058A8gCLXCiSwBC+AhgE4AmM62eIqQpU4dBk2gwA4uwC2aTLgLEylGvUYAzbAGMQCfFhjcEAZwhJ2YABQBzeVABcMxwEoYAb2AwYuo2b4KAB0SPh29o7BAEYcPMFy7BA2nER8AHxePr4wnFAgGJzGAEQAPsUwANS5RMEAVvgIWDYVxR7VZcUk2QC+bvWNzcUAOlhtVTAABqMAkiAA5GYwACSeDgrBBUU9izBbWJNuwD3aegZGMJbWkQousgoANDAAHi5YGHLRUJxPYG8fX04Hm8vgQWhgNygMTi3AA2mAALqw54ImAAQlQ6FawOyvhAAAtUoQYFgoMSAKKcVKcFpwfHsEAwCzsXSwelLdhIPLsbhgGBfKDGK5gKDcNFtbq+E6+dZQ2JcOGI5Go9CyzaFUjZNX7PgwbUaviYmDFAAaFQA-MbqBUXKausdGP4sGZGbK7o5dSD+TCXLDYa0ngHjcaEQ9-cbAxHg8VQ+HipH49GEaHsvtbWaHcBTBYrLZZW5usBhZCngAGMsFrPmYv5ws1xxlp4ARkr2frCkrRdzJZgTaeACZW9Xu7XGO2oM2B0Oc9dR0A)
3. [Exercise: objects](https://www.staging-typescript.org/play?#code/FAMwrgdgxgLglgewgAigyMByBDMBzACxgE8BhAuAGwBMAnAUwgAooKaGIAaZY+7WgJTIA3sGTIGMMLRSsqdRgDoQVGPVos21ZAF4AfCLHiJ9KTNRbFAZzgQry1eqY2U+5C8W9+unTp59BRUpGPBgCZAMAVgBuIwBfASCQsNi44FBIWEQUKwRaGAAhYgBBPHomAAd6BArg7mwrKEZqWzwhUXFJaRQqmuDrPJgmJmxuACMhNw7jLvMGpogWiDwjY2QAfmQRxWwy5ABaZDGdsoFV4wAuLePd+gPkbBP6AVjxBOA0jOh4JGQQPIAtgB5Cq2bLFMboGAAWQQADc4OUAfDEe0jHAQFtkQj6DtYHl7LZqPQAB5AkBMABE0N2eERyAA4sRKMEIARsNhKJShHo-AAGNFrWYoSkASQA5CzkAB3bAwVjIOAwSmvZBxZD0ShWO4YrEo3FlCAMRQAuWsJgAekacCYigAVAIVBa4AJBTNTN1kJSAMroRZWZB4BhygCEKviGq1OsxTHO2MRigQYXUABFTNgqPYIPxaHLssgAGQFuP6xPJ2hpmAZrWKbO0XM-CCKOEIOBNQmLUnkqnYajYBHaOVqCCQ2joQjciL8oxuzoe8yU4oQYhhVrIOsN+jaMbEZDeuC0ZAp-twbTQqDHgcgbBNMOq9Wa7WGIXzkWYGr0cNvD7AIA)
