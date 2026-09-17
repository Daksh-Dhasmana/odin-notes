# Basic Get Usage
- You use GET when you want to fetch data from a server without changing or adding anything on the database.
```
async function main(){
    const response=await fetch("URL");
    cont data= await response.json();
    console.log(data);
}
main().catch(console.error)
```

# Basic Post usage
- You use POST when you want to send new data to the server to be processed, saved, or acted upon.