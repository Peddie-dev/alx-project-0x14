## 🧩 API Overview  

Collection of information for **movies**, **TV shows**, and **actors**.  
Includes YouTube trailer URLs, awards, full biographies, and many other useful details.  

This API provides **complete and updated data** for over **9 million titles** (movies, series, and episodes) and **11 million actors, crew, and cast members**. It is an excellent resource for developers building applications that rely on accurate and detailed entertainment information.  

👉 **Support the developer:** [Buy Me a Coffee](https://www.buymeacoffee.com/SAdrian13)  

---

## 🔖 Version  

**MoviesDatabase API Version:** `v1`  

This version provides complete and updated data for over 9 million titles and 11 million actors, with new titles updated **weekly** and ratings/episodes updated **daily**.

## 🔗 Available Endpoints  

Below are the main endpoints provided by the **MoviesDatabase API**, along with their functions and brief descriptions:

### 🎬 Titles  
- **`/titles`** — Returns an array of titles (movies, series, episodes) based on filters or sorting parameters.  
- **`/titles/{id}`** — Fetches detailed information about a specific title using its IMDb ID.  
- **`/titles/{id}/ratings`** — Retrieves a title’s rating and total votes.  
- **`/titles/series/{id}`** — Returns episodes of a series in ascending order by episode and season.  
- **`/titles/seasons/{id}`** — Returns the total number of seasons in a specific series.  
- **`/titles/series/{id}/{season}`** — Fetches all episodes from a given season of a series.  
- **`/titles/x/upcoming`** — Lists upcoming movie and series releases.  

### 🔍 Search  
- **`/titles/search/keyword/{keyword}`** — Searches for titles using keywords.  
- **`/titles/search/title/{title}`** — Searches for titles based on full or partial titles.  
- **`/titles/search/akas/{aka}`** — Searches for titles by their alternate names (aka).  

### 🎭 Actors  
- **`/actors`** — Retrieves a list of actors based on filters and pagination.  
- **`/actors/{id}`** — Fetches detailed information about a specific actor using their IMDb ID.  

### ⚙️ Utilities  
- **`/title/utils/titleType`** — Returns available title types (e.g., movie, series, short film).  
- **`/title/utils/genres`** — Provides a list of available genres.  
- **`/title/utils/lists`** — Returns predefined collections such as “Top Rated,” “Most Popular,” and “Box Office Hits.”  

---

Each endpoint returns a JSON object containing a `results` key and may include pagination fields like `page`, `next`, and `entries` where applicable.

