# WebAssembly written in GO and used with Envoy to check HTTP request header and do not allow request if a certain header is not present

In this, we are checking for header `x-header1` to be present. The web-assembly code is called as filter in Envoy
```bash


brew install envoy
brew tap tinygo-org/tools
brew install tinygo

# work on main.go - it has the actual logic for webassembly filter in GO

# build web-assembly
tinygo build -o ./hello.wasm -scheduler=none -target=wasi ./main.go


# work on envoy.yaml - here the custom webassembly filter is added to envoy

# run envoy
envoy -c envoy.yaml -l debug

```


# curl output




```
output when header present -> Hello World!

reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ curl localhost:8085/hello  --header "x-header1:abc" 
Hello World!reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 

output when header is not present -> request is paused

reetasingh-ltm8:~ reetasingh$  curl localhost:8085/hello




```

 # Envoy logs
 
 
when header is not present
<img width="1244" alt="Screen Shot 2021-03-23 at 20 56 10" src="https://user-images.githubusercontent.com/14129300/112252396-47687b00-8c1a-11eb-9ce7-82b299d42b51.png">

when header is present
<img width="1261" alt="Screen Shot 2021-03-23 at 20 54 18" src="https://user-images.githubusercontent.com/14129300/112252502-6f57de80-8c1a-11eb-9b3b-c9777311d779.png">





# Reference 
https://tufin.medium.com/extending-envoy-proxy-with-golang-webassembly-e51202809ba6
