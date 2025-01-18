---
layout: ../../layouts/post.astro
title: Using Axios in React
description: Axios is a popular JavaScript library for making HTTP requests, and it's often used in React applications to fetch data from APIs. Below is a simple guide on how to set up and use Axios in React.
dateFormatted: Jan 17, 2025
---

# Using Axios in React

Axios is a popular JavaScript library for making HTTP requests, and it's often used in React applications to fetch data from APIs. Below is a simple guide on how to set up and use Axios in React.

## Step 1: Install Axios

First, you need to install Axios. Run the following command in your project directory:

```bash
npm install axios
```

## Step 2: Import Axios in Your Component

In the React component where you want to make HTTP requests, import Axios:

```javascript
import axios from 'axios';
```

## Step 3: Making a GET Request

To fetch data from an API, you can use Axios within a `useEffect` hook, which will trigger once when the component mounts:

```javascript
import React, { useState, useEffect } from 'react';
import axios from 'axios';

const DataFetcher = () => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    axios.get('https://api.example.com/data')
      .then(response => {
        setData(response.data); // Store the fetched data in state
        setLoading(false); // Set loading to false after data is fetched
      })
      .catch(err => {
        setError('Error fetching data'); // Handle errors
        setLoading(false); // Set loading to false on error
      });
  }, []); // Empty dependency array ensures the request runs once on mount

  if (loading) return <div>Loading...</div>;
  if (error) return <div>{error}</div>;

  return (
    <div>
      <h1>Fetched Data</h1>
      <pre>{JSON.stringify(data, null, 2)}</pre>
    </div>
  );
};

export default DataFetcher;
```

### Key Points:
- **GET Request**: We used `axios.get()` to fetch data.
- **useState**: We used React's state hook to store `data`, `loading`, and `error`.
- **useEffect**: Axios request is wrapped in `useEffect()` to run when the component mounts.
- **Error Handling**: Use `.catch()` to handle errors gracefully.

## Step 4: Making a POST Request

To send data to an API, you can use `axios.post()` like this:

```javascript
axios.post('https://api.example.com/submit', { key: 'value' })
  .then(response => console.log('Data submitted:', response))
  .catch(error => console.error('Error submitting data:', error));
```

That's it! Axios makes it simple to fetch or send data in your React apps.
```

