# _Code challenge 28 MovieSort()_

## Challenge Summary:

## Feature Tasks

- Implement the functions sortYear, sortTitle, and inGenre in the file sort.ts.

  - Execute your tests while developing using npm run watch
  - Execute your tests in CI using npm test

- Functions:

  - sortYear
    - Arguments: movies array
    - Sorts the input array by year, in ascending order.
  - sortTitle
    - Arguments: movies array
    - Sorts the input array by title, ignoring "The " at the beginning of titles.
  - inGenre
    - Arguments: movies array, genre string
    - Filters the input array, returning only those movies who include genre.

- Extract the comparator callbacks

  - sortYear and sortTitle should both be implemented by passing a custom comparison function to the built-in sort utility.
  - Export these helper functions at the top level of your file, and call them from your sortYear and sortTitle functions.
  - Import these helper functions into your test, and write tests that verify they return the appropriate comparison values (<0, 0, or >0).

## Whiteboard Process

![](/Images/codechallenge28.png)

## Approach & Efficiency

used .sort for year and title and retirn an ordered array. When it came to genre I used .filter() and .includes().

## Solution

```javascript
export function compareYear(a: Movie, b: Movie) {
  return a.year > b.year ? 1 : b.year > a.year ? -1 : 0;
}
export function compareTitle(a: Movie, b: Movie) {
  return a.title.replace("The ", "").localeCompare(b.title.replace("The ", ""));
}

export function filterByMovieGenre(genre: string) {
  return function (a: Movie) {
    return a.genres.includes(genre);
  };
}

export function sortYear(movies: Movie[]): Movie[] {
  return movies.sort(compareYear);
}

export function sortTitle(movies: Movie[]): Movie[] {
  return movies.sort(compareTitle);
}

export function inGenre(movies: Movie[], genre: string): Movie[] {
  return movies.filter(filterByMovieGenre(genre));
}
```
