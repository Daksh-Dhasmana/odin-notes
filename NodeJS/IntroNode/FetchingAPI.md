# Basic Get Usage
- You use GET when you want to fetch data from a server without changing or adding anything on the database.
- 
```
async function main(){
    const response=await fetch("URL");
    const data= await response.json();
    console.log(data);
}
main().catch(console.error)
```

# Basic Post usage
- You use POST when you want to send new data to the server to be processed, saved, or acted upon.
- 
```
const body={
    name:"daksh",
    title:"books",
}
async function main(){
    const response=await fetch("URL",{
        method:"POST",
        headers:{
            'User-Agent':'undici-stream-example',
            'Content-type':'application/json'
        }
        body: JSON.stringify(body),
    });
    const data=await response.json();
    console.log(data);
}
main().catch(console.error);
```
- Headers provide metadata about the request:
  - `Content-Type: application/json` tells the receiving server that the data inside the request body is formatted as a JSON string so it knows how to parse it.
  - `User-Agent` identifies the client or library making the request.

# Customizing fetch API using undici
- Undici allows you to customize the Fetch API by providing options to the `fetch` function.