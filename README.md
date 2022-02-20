
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

1. syntax errors
2. Static type errors
3. Dynamic type errors
4. Exceptions
5. Logical


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
     allergies: string[] | null
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
type vaccinations = 'arvovirus' | 'distemper' | 'canine hepatitis' | 'rabies'

type status = 'active' | 'inactive' | 'pending'
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
    author: string,
    year: numner,
    title: string,
    available: boolean,
    genre: Genre,
    pages: number.
    difficulty: 1 | 2 | 3 | 4 | 5
}


const fetchBooks = async (author: string, year: number, title: string, available: boolean): Book[] => {
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
