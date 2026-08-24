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