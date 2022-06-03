[children and movies](https://www.staging-typescript.org/play?#code/JYOwLgpgTgZghgYwgAgMqmQbwFDOQTwjigC5kQBXAWwCNpkAfZAZzClAHNsBfbP0SLEQoAwgAtgAGwAmWXC1DMy6EAG0Aujz4wKIBGGAB7EMgSHdYAHJwKHMWHzip0qBBAAKBBJmuQZJzIaADQERKTk1HRQjCxsnACUcniuYBRQJl7OvgB0MFKCnt6yALwAfEl4yClpGUXZzIq5+dDuDSZlCiDZhMTIxf2hxPHZkm4cYGLI5QCsANzy3MOjIONi87zYAtDwSMgACtDMxhVwHBBklLTQWtg6egbHR1BgAEL4AIJn7gAOEIbfozIBygRzU6hCcGYSBA0k4ZBehkMozgIESOGSEFS6WQv3+o3qhme7nccBCNESHXRlWq2Mh0NhK3klWQAH5kCTsqcUABaZA0TlneJMypkdz8rnIXlwAUQeLzPCLG5bIS7AAimLgUmYFRAxCgcAefgqeAAboZgEglLF2CsNAsbptwNthMgALKGE3AFBUxBgQlW1g2jh2vBnECuMiBzjyQwTaDqsCayRWhNJ5g3O76IwmGCEqgAeW+oGz7xo5jA7s9EHcVA9XrIla9aPkwBg7NrVc5+n92VA0ggAA98zB3AAiV2nDhe5AAcXwkmWYjgcEko8SpWKyAADM3mTSTKOAJIAcgXyAA7gavMhgGBR-LkNxkBBkyhW+26xBsmHXNkqFexHcAB6KFgHcbIACp4jyIDgHiXdqUxGpkFHVBzBhbUOFcA0AEJ7wWZ9XxvNt3GFDsvWyWMxHjDUtWyXUoH1Q1kAAMhYsjP0ouMoFTOiGKY7NsjNC0IGYXsYUHYcxzgaQ4E9WQDUgEAyygcw7DXKZNy3eQEIxLED3eEB8AmThyD1A0IFkGh8DQYBolVOTgFkV0EAc+SdggPCHyfF9mG9YV9xQyx-ggfCFS0IA)

```typescript
interface Sin {
  year: number | string;
}

interface Child {
  sins: Sin[];
}

function countNaughtyChildren(children: Child[], year: number | string) {
  return children.filter((child) => {
    return child.sins.filter((sin) => sin.year === year).length > 5;
  }).length;
}

interface Person {
  age: number;
}

function sortByAge(people: Person[], ascending: Boolean) {
  return people.sort((a, b) => {
    return ascending ? a.age - b.age : b.age - a.age;
  });
}

interface Details {
  narration: {
    voices: string[];
  };
}

interface Movie {
  actors: string[];
  genre: string;
  otherDetails: Details;
}

function formOpinionAboutMovie(movie: Movie) {
  if (movie.actors.indexOf("Maggie Gyllenhaal") >= 0) {
    return "I'll watch it";
  } else if (movie.genre.match(/sci(.*)fi/i)) {
    return "Sounds great!";
  } else if (
    movie.otherDetails.narration &&
    movie.otherDetails.narration.voices.indexOf("adavid attenborough") >= 0
  ) {
    return "Anything narrated by Sir David McDavidface!";
  } else {
    return "Nope";
  }
}
```

[send email](https://www.staging-typescript.org/play?#code/FASwdgLgpgTgZgQwMZQAQCUCuAjGImoDewqqEIEANlAFyoDOEeYA5gDQmoAmU9SA-HUbMWwAL7BgEAJ4AHNAGUoYLgHUolJAHsAtlACiOhCEqoAvKgAUnMAj1Cm4dpyhGTDkR1IwceJPUEMX3wAbQBdYABKcwA+VAA3LRAuSW0wRgZlNQ1tPUNjSjolFXVNXQM3UwtLWz02VFcC+p9cfHpzVHDoszjiUjSMzBgq1AAiAAsICFl6GgB6Oe0uY3p6KCGAOjAoAHd6Uc4BiFQ9VYQWNAsAA05SAB5ZGIAJEFQAEkJaqDEAQju5x6SUj3R6lXJoCBaMjjNAAYS0yxAq3WMFQ2z2qC0mCoUAgP1Q6gA5DAoLdSPRMPJUeMELJZNIyFCafE0NIsZiwNgtAgYFw-gCYkDgQ8YgBNLGElmocBcfAIaBcVBszCoHYISCM1AklAgKU7KBQADWlGkZNQlOW0HaWjA0LQcC0lEoWh2TnehBafnoG2orAg4zEWuC-ho-0BZLusviqCQlAQqzMoxYeC4o0FwOBH09bQ2RlklmzBB6RDNwJJECGtpuGZrqEjupjcYTo0LadLtbuwhtLBiWeDG3IOLE-y7rHTtZrIr7rSQGx4fGHAvbwrmUfHtauAG5S2JIhsAFZJMCWUajSISDP-NdCkExAAyWhZ9WVqOgyBhMHa6sV-rQJIyWhwHaZBQHYYaChGsiNvG9CJvQRhOic2JQKm67CggqDjCScCJh8QyUGIcyYOkOB8Hg2BQPwjQmGYHzUQRaYAKokdgZEgBR-wIGh4GcFuQoDI6UA+loLCWKc9DnFAkTbhIwBrCUOTlPkJjWKQowANIaNQ0ijF4YyGlpUDSAAAksKxrJsuS6ZwIRkoQZAUNQdCjAAUlo2CoLIWiME4+z1POSDOQA4ri5qyJavAcqgh4eV5PmsO04CYkMaK4jsWgwIaoyoGIemkPZg5OWMAAqUBIOMqV7Lp3C8IFYwAGIwLoGCgUgxwsN59AgFBkLAeivDHN+MZaIJGSUOxMA8iAvDZbldkOTizkuZgGR6KcWqgU6Ok5ZwESRMAQA)

```typescript
interface Rubric {
  title: string;
  desc?: string;
}

type SendWelcomeEmail = (
  name: string,
  email: string,
  rubrics?: Rubric[]
) => void;

const sendWelcomeEmail: SendWelcomeEmail = (name, email, rubrics = []) => {
  const url = "https://codaisseur.news";
  const message = `
    <p>Hi ${name}!</p>

    <p>Welcome to the Codaisseur news outlet! We're
     super happy to have you onboard!</p>

    <p>You've indicated you want to receive weekly
     updates on the following ${rubrics.length} rubrics:</p>

    <div class="grid">
      ${rubrics
        .map((rubric) => {
          return `
          <div class="rubric">
            <strong>${rubric.title}</strong>
            <p>${rubric.desc}</p>
          </div>
        `;
        })
        .join("")}
    </div>

    <p>Love, your teachers and the rest of the team</p>

    <p class="small muted">
      <a href="${url}/unsubscribe?email=${email}">Unsubscribe</a>
    </p>
  `;

  console.log(message);
};

sendWelcomeEmail("Kelley", "kelley@codaisseur.com", [
  { title: "Job postings", desc: "Get updates on job postings in our network" },
  {
    title: "Tech news",
    desc: "From React gossip to the newest and coolest libraries",
  },
  { title: "Just memes really" },
]);
```

[tic tac toe](https://www.staging-typescript.org/play?#code/FAFwngDgpgBAKgSwDawLwwEQA0MwD6YDyGA3DAPTnyEAihwoksAQgPYCGATgCYzoDOITggB2AcwDaAXWllK1Og3DQYAcXYBbNDADewGDABGHHgC4YbLt30wQAV04jziFMAC+ZBgDM7IgMYgCKwiMNwI-BBI7GAAFGKaUObqWgCUujZ+wfysKAB0SKxicQm5xla5GuwQMZysAO58AHzpBgacUPaOmHi4ANQwtXW5AFasojG4GGn9GD0kNm4pI2MiEwA6IlMw-QAGGwCSIADk-DAAJDrxWrmdIm4ntg4iOynu3r4BQSGR0cVaSQkADQwAAe5hEdg0hignGBYHBkOhnDSegMCC8MD+UFKJm4EjAMhBUhgAEJUOhJiibAYQAALQYwERQBoAUU4tU4EzgtPYIBgEXYflgPNO7CQ7XY3DARigUG+UTAUG4JKm8wMbhsV2xZR4+MJxPQWpuTzVMCNtz4ZpKFvJFJwMAA-ERcOZsKQ3sBMiJBFb-moEpbUUZceYJBJJsCI5hMFJAeHMJGE9GMLH4xhE+nk1JYzZbq6cB6whEFViUvNgD9YlrgQAGWtl4BFyul8vN6swOswACMDabJa1DYr-aB3eBACZe+E2wlB9OtMCu+PJ8XfgP5kA)

```typescript
type Tile = "X" | "O"; // TODO

type Board = string[][]; // TODO

type Game = {
  board: Board;
  turn: Tile;
};

function display(game: Game) {
  console.log(
    game.board
      .map((row) => {
        return "|" + row.join(" ") + "|";
      })
      .join("\n") + `\nIt's ${game.turn}'s turn`
  );
}

function play(game: Game, x: number, y: number) {
  if (game.board[y][x] !== " ") {
    throw new Error("That space has already been played!");
  }
  game.board[y][x] = game.turn;
  game.turn = game.turn === "X" ? "O" : "X";
}

const game: Game = {
  board: [
    [" ", " ", " "],
    [" ", " ", " "],
    [" ", " ", " "],
  ],
  turn: "X",
};

display(game);

play(game, 0, 0);
display(game);

play(game, 0, 1);
display(game);

play(game, 1, 2);
display(game);

play(game, 1, 2);
display(game);
```
