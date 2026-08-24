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