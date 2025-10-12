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

## 📦 Request and Response Format  

This section explains the structure of a typical request and its corresponding response when interacting with the **MoviesDatabase API**.

### 🔹 Request Format  

All endpoints are accessible via HTTPS and return JSON data.  
Query parameters are **optional** and can be customized to refine results.

#### Example Request  
**Get Movie Details by IMDb ID**
```http
GET /titles/tt1234567?info=base_info
```

## 🔐 Authentication  

To access the **MoviesDatabase API**, all requests must be authenticated using an **API key**.  
This key ensures that only authorized users can interact with the API and helps monitor usage for rate limiting and security purposes.

### 🔹 How to Authenticate  

Each request must include the API key in the **headers** section.  
Without this key, your request will return an **authentication error (HTTP 401 Unauthorized)**.

#### Example Header:
```http
GET /titles/tt1234567 HTTP/1.1
Host: moviesdatabase.example.com
X-API-KEY: your_api_key_here
Accept: application/json
```

## ⚠️ Error Handling  

The **MoviesDatabase API** provides clear and consistent error responses to help developers identify and resolve issues quickly.  
Errors are returned in standard **JSON format**, along with an appropriate HTTP status code.

---

### 🔹 Common Error Responses  

| Status Code | Error Type | Description | Possible Fix |
|--------------|-------------|-------------|---------------|
| **400 Bad Request** | Invalid Request | The request syntax or parameters are incorrect. | Check query parameters and request format. |
| **401 Unauthorized** | Authentication Error | Missing or invalid API key. | Include a valid API key in the request headers. |
| **403 Forbidden** | Permission Denied | The API key doesn’t have access to this resource. | Verify API key permissions or request access. |
| **404 Not Found** | Resource Missing | The requested resource (title, actor, etc.) was not found. | Ensure the IMDb ID or endpoint path is correct. |
| **429 Too Many Requests** | Rate Limit Exceeded | Too many requests were made in a short time. | Wait before making more requests or upgrade your plan. |
| **500 Internal Server Error** | Server Error | An unexpected error occurred on the API server. | Retry the request later or contact support. |

---

### 🔹 Example Error Response  

When an error occurs, the API returns a JSON response similar to this:

```json
{
  "status": "error",
  "statusCode": 404,
  "message": "Title not found for the given IMDb ID."
}
```

## 📈 Usage Limits and Best Practices  

The **MoviesDatabase API** enforces certain usage limits to ensure fair access for all developers and to maintain server performance.  
Understanding these limits and following best practices will help you use the API efficiently and avoid request restrictions.

---

### 🔹 Usage Limits  

| Limit Type | Description | Recommendation |
|-------------|-------------|----------------|
| **Rate Limit** | Maximum of **100 requests per minute** per API key. | Use request batching or caching to minimize repetitive calls. |
| **Concurrent Requests** | Up to **5 simultaneous requests** allowed per user. | Queue requests when working with large datasets. |
| **Data Size Limit** | Maximum response size of **1 MB per request**. | Use pagination (`limit` and `page` parameters) for large queries. |
| **API Key Quota** | Each free-tier key supports up to **10,000 requests per day**. | Upgrade your plan for higher daily limits if necessary. |

---

### 🔹 Best Practices for Efficient API Use  

- ⚡ **Use Pagination:** Always include `limit` and `page` parameters to reduce load and avoid hitting rate limits.  
- 🗂️ **Cache Responses:** Cache frequently accessed data (e.g., popular titles) to minimize repeated requests.  
- 🕒 **Implement Rate Limit Handling:** Detect `429 Too Many Requests` responses and delay subsequent calls accordingly.  
- 🔒 **Secure Your API Key:** Never expose your API key in public repositories or client-side code. Use environment variables.  
- 📄 **Filter Results:** Use optional query parameters (e.g., `genre`, `year`, `titleType`) to fetch only the data you need.  
- 🧩 **Handle Errors Gracefully:** Implement error handling for unexpected API or network issues to maintain a smooth user experience.  
- 🔁 **Automate Updates:** For frequently changing data like ratings or new releases, schedule periodic API syncs instead of manual refreshes.  

---

### 🔹 Example Rate Limit Handling in Code  

```javascript
async function fetchMovieData(url, headers) {
  try {
    const response = await fetch(url, { headers });

    if (response.status === 429) {
      console.warn("Rate limit exceeded. Retrying after delay...");
      await new Promise(resolve => setTimeout(resolve, 60000)); // Wait 1 minute
      return fetchMovieData(url, headers); // Retry
    }

    if (!response.ok) throw new Error(`Error ${response.status}: ${response.statusText}`);

    return await response.json();
  } catch (error) {
    console.error("API request failed:", error.message);
  }
}
```



