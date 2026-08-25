# Using Fetch in React Components
- One common use case is to fetch the API when the component mounts
- Look at the example below
```
import { useEffect, useState } from "react";

const Image = () => {
  const [imageURL, setImageURL] = useState(null);

  useEffect(() => {
    fetch("https://picsum.photos/v2/list", {
      headers: {
        "User-Agent": "the-odin-project"
      }
    })
    .then((response) => response.json())
    .then((response) => setImageURL(response[0].download_url))
    .catch((error) => console.error(error));
  }, []);
  return (
    imageURL && (
      <>
        <h1>An image</h1>
        <img src={imageURL} alt={"placeholder text"} />
      </>
    )
  );
};
export default Image;
```

# Including an identification header
- Sometimes, an API may require clients to identify their traffic
- You can do it by including a custom identifier header, such as a `User-Agent` or any other identifier the API owner specifies inside the request options
- It is used to prevent spamming and block malicious bots.
- Here, traffic refers to the flow of network data and HTTP requests moving from your application to the API server.
- When an API provider talks about "identifying your traffic," they mean recognizing which specific app or client is generating those incoming requests.

# Using fetch in React Components
- Whenever we are fetching data inside a component, it is best to wrap it inside `useEffect`, so it loads when the component is mounted.
- After the Usage, when component is dismounted, the API still sends data, so we have to use `controller.abort()`, so that it automatically cancels the HTTPS requests
- Like this
```
useEffect(() => {
    // 1. Create an AbortController instance
    const controller = new AbortController();

    fetch("https://api.example.com/user", {
      signal: controller.signal, // 2. Pass the signal to fetch
    })
      .then((res) => res.json())
      .then((data) => setData(data))
      .catch((err) => {
        if (err.name === "AbortError") {
          console.log("Fetch aborted on unmount!");
        }
      });

    // 3. Cleanup function runs automatically when component UNMOUNTS
    return () => {
      controller.abort(); // Immediately cancels the HTTP request
    };
  }, []);
```

# Handling Errors
- There might be situations in which API may be down or Servers may be down.
- To fix this, we have to check for "something" before the component returns JSX.
- We do it as follows
- 1st we define an error as state
```
const [error, setError] = useState(null);
```
- Then we write a code that detects error and throws it so that `catch` can catch it, before we send the JSX
```
useEffect(() => {
  fetch("https://picsum.photos/v2/list", {
    headers: {
      "User-Agent": "the-odin-project"
    }
  })
    .then((response) => {
      if (response.status >= 400) {
        throw new Error("server error");
      }
      return response.json();
    })
    .then((response) => setImageURL(response[0].download_url))
    .catch((error) => setError(error));
}, []);
```
- Then if there is an error, we return a React Fragment(things between <></>).
```
if (error) return <p>A network error was encountered</p>

return (
  imageURL && (
    <>
      <h1>An image</h1>
      <img src={imageURL} alt={"placeholder text"} />
    </>
  )
);
```
- In above code, if there is an error detected then it will return a relevant `<p>` tag and nothing else will be returned.
- Now when a bad URL is passed or the API returns an unexpected response, the page will relay that information to the user.

## Loading State
- Sometimes, the API several may take several seconds, and in meantime, the user might see a blank page, so we don't want that
- Meaning, loading prevents a blank screen.
- Here what goes
```
const Image = () => {
  const [imageURL, setImageURL] = useState(null);
  const [error, setError] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    fetch("https://picsum.photos/v2/list", {
      headers: {
        "User-Agent": "the-odin-project"
      }
    })
      .then((response) => {
        if (response.status >= 400) {
          throw new Error("server error");
        }
        return response.json();
      })
      .then((response) => setImageURL(response[0].download_url))
      .catch((error) => setError(error))
      .finally(() => setLoading(false));
  }, []);

  if (loading) return <p>Loading...</p>;
  if (error) return <p>A network error was encountered</p>;

  return (
    <>
      <h1>An image</h1>
      <img src={imageURL} alt={"placeholder text"} />
    </>
  );
};
```
- 1) Page Loads and `loading` to true, so screen immediately shows `<p>Loading..</p>`
- 2) During this time, browser sends request to server for data, and while data is being recieved, page shows, `Loading..`
- 3) Failure Occurs: The server responds with an error (e.g., a 500 server crash or no internet connection).
     - `.catch()` runs and saves the error to state.
     - `.finally()` runs and sets loading to false.
- 4) Re-render: Now that loading is false, React stops displaying "Loading...", evaluates `if (error)`, and replaces the text on screen with `<p>A network error was encountered</p>`.
- Loading is shown during the wait for the server, regardless of whether the eventual outcome is success or failure.