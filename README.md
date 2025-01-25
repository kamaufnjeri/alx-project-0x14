# TMDb API Integration

This project integrates with The Movie Database (TMDb) API to provide data on movies, TV shows, and actors. The API enables applications to retrieve information such as movie details, genres, TV show episodes, and actor profiles.

---

## Table of Contents

- [Overview](#overview)
- [Authentication](#authentication)
  - [Obtain Your API Key](#obtain-your-api-key)
  - [How to Use the API Key](#how-to-use-the-api-key)
- [Endpoints](#endpoints)
  - [Movies](#movies)
  - [Search](#search)
- [Request Format](#request-format)
- [Response Examples](#response-examples)
  - [Success Responses](#success-responses)
  - [Error Responses](#error-responses)
- [Rate Limits and Best Practices](#rate-limits-and-best-practices)

---

## Overview

TMDb is a powerful API that provides:

- Movie details such as title, genres, release date, and ratings.
- TV show information including episodes and seasons.
- Actor profiles, including movies and TV shows they are associated with.
- Search capabilities across movies, TV shows, and people.

---

## Authentication

You need an API key to access the TMDb API. Follow these steps to obtain and use your API key.

### Obtain Your API Key

1. Visit [TMDb](https://www.themoviedb.org/) and log into your account.
2. Navigate to your profile > **Settings** > **API** section.
3. Request and copy your API key.

### How to Use the API Key

#### Method 1: Bearer Token

Include the API key as a Bearer token in the request header:

```http
Authorization: Bearer YOUR_API_KEY
```

#### Method 2: Query Parameter

Append the API key to your request URL:

```http
GET https://api.themoviedb.org/3/movie/550?api_key=YOUR_API_KEY
```

Replace `YOUR_API_KEY` with your actual API key.

---

## Endpoints

Here are some common TMDb API endpoints:

### Movies

Retrieve detailed information about a specific movie:

```http
GET https://api.themoviedb.org/3/movie/{movie_id}?api_key=YOUR_API_KEY
```

### Search

Search for movies, TV shows, or people:

```http
GET https://api.themoviedb.org/3/search/movie?query=QUERY&api_key=YOUR_API_KEY
```

Replace `QUERY` with your search term.

---

## Request Format

All requests must be sent over HTTPS and include the appropriate API key for authentication.

Example GET request:

```http
GET https://api.themoviedb.org/3/movie/550?api_key=YOUR_API_KEY
```

---

## Response Examples

### Success Responses

#### Movie Details

```json
{
  "id": 550,
  "title": "Fight Club",
  "overview": "A ticking-time-bomb insomniac channels primal male aggression...",
  "release_date": "1999-10-15",
  "genres": [
    { "id": 18, "name": "Drama" }
  ],
  "vote_average": 8.438
}
```

#### Search Results

```json
{
  "page": 1,
  "results": [
    { "id": 550, "title": "Fight Club", "release_date": "1999-10-15" }
  ]
}
```

### Error Responses

#### Unauthorized Access

```json
{
  "status_code": 7,
  "status_message": "Invalid API key."
}
```

#### Resource Not Found

```json
{
  "status_code": 34,
  "status_message": "The resource you requested could not be found."
}
```

---

## Rate Limits and Best Practices

### Rate Limits

- Maximum of 50 requests per second.
- Maximum of 20 connections per IP.

### Best Practices

1. **Efficient Data Retrieval**: Request only the data you need.
2. **Caching**: Cache frequently accessed data to minimize API calls.
3. **Error Handling**: Implement retry logic with exponential backoff for transient errors.
4. **Attribution**: Include TMDb's logo and provide attribution as required by their terms.
5. **Monitoring**: Regularly monitor API usage to avoid exceeding rate limits.

---

## Attribution

This project uses the TMDb API but is not endorsed or certified by TMDb. For more information, visit [TMDb](https://www.themoviedb.org/).

---

## License

This project is licensed under the MIT License.
