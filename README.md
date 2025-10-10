
---

# 🎬 MoviesDatabase API Documentation Review

> **The MoviesDatabase API** provides a powerful and easy-to-use interface to access detailed information about over **9 million movies, TV series, and episodes** — with real-time updates and flexible filtering.

---

## 🌍 API Overview

The **MoviesDatabase API** offers a comprehensive and continually updated dataset for film and television content. It’s perfect for developers building movie apps, dashboards, or entertainment-based platforms.

✨ **Key Highlights:**

* 📚 Over **9 million** titles (movies, series, and episodes)
* 🔄 **Weekly updates** for new titles
* ⭐ **Daily updates** for ratings and episode details
* 🧩 **All query parameters are optional** — simple and flexible requests
---

## 🧾 API Version

**Version:** `1.0`
*Last updated based on the latest MoviesDatabase API release.*

---

## 🔗 Available Endpoints

Each endpoint returns an object containing a **`results`** key.
Endpoints that use pagination also include: **`page`**, **`next`**, and **`entries`**.

| Endpoint                           | Description                                                                                                     |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| **`/titles`**                      | Retrieve a list of all titles (movies, shows, and episodes). Supports filters like `genre`, `year`, and `type`. |
| **`/titles/{id}`**                 | Get detailed info about a single title using its unique ID.                                                     |
| **`/titles/search`**               | Search for titles by keyword, phrase, or partial name.                                                          |
| **`/titles/episodes/{series_id}`** | Fetch all episodes of a specific series.                                                                        |
| **`/ratings/{title_id}`**          | Retrieve current rating and review statistics for a title.                                                      |
| **`/genres`**                      | Get the list of available genres supported by the API.                                                          |

---

## 📦 Request and Response Format

### 🔹 Example Request

```bash
GET https://api.moviesdatabase.com/titles?year=2025&type=movie&page=1
```

### 🔹 Example Response

```json
{
  "results": [
    {
      "id": "tt1234567",
      "title": "Example Movie",
      "year": 2023,
      "type": "movie",
      "rating": 8.1,
      "genres": ["Action", "Adventure"]
    }
  ],
  "page": 1,
  "next": 2,
  "entries": 10000
}
```

🧠 **Notes:**

* All requests are **GET** by default.
* Responses are returned in **JSON** format.
* Pagination is supported via `page` and `next` keys.

---

## 🔐 Authentication

Authentication is done through an **API key** provided in the request headers.

### Example:

```bash
GET https://api.moviesdatabase.com/titles
Headers:
  X-API-Key: your_api_key_here
```

⚠️ Without a valid API key, requests may return limited or restricted data.

---

## ⚠️ Error Handling

The API uses standard HTTP status codes for error reporting.

| Status Code | Meaning         | Description                                       |
| ----------- | --------------- | ------------------------------------------------- |
| `200`       | ✅ OK            | Request completed successfully.                   |
| `400`       | ❌ Bad Request   | The request parameters are invalid or incomplete. |
| `401`       | 🔒 Unauthorized | Missing or invalid API key.                       |
| `404`       | 🚫 Not Found    | The requested resource doesn’t exist.             |
| `500`       | 💥 Server Error | Internal issue on the API side.                   |

### Example Error Response:

```json
{
  "error": "Invalid API key provided",
  "status": 401
}
```

---

## 🚦 Usage Limits and Best Practices

* ⏱️ **Rate Limits:** The API may restrict requests per minute — check the docs for your specific limit.
* 🧠 **Use Caching:** Cache frequently requested data to reduce API load.
* 🎯 **Filter Wisely:** Use filters and pagination to avoid large responses.
* 🆕 **Stay Updated:** Visit the official documentation regularly for new features or updated endpoints.

---

