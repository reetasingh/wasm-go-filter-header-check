```bash


brew install envoy
brew tap tinygo-org/tools
brew install tinygo

# work on main.go

# build web-assembly
tinygo build -o ./hello.wasm -scheduler=none -target=wasi ./main.go


# work on envoy.yaml

# run envoy
envoy -c envoy.yaml -l debug

```


# curl output

output when header present -> Hello World!
output when header is not present -> request is paused

```

reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ curl localhost:8085/hello  --header "x-header1:abc" 
Hello World!reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$ 
reetasingh-ltm8:~ reetasingh$  curl localhost:8085/hello


```
when header is not present
<img width="1244" alt="Screen Shot 2021-03-23 at 20 56 10" src="https://user-images.githubusercontent.com/14129300/112252396-47687b00-8c1a-11eb-9ce7-82b299d42b51.png">

when header is present
![Uploading Screen Shot 2021-03-23 at 20.54.18.png…]()



# reference 
https://tufin.medium.com/extending-envoy-proxy-with-golang-webassembly-e51202809ba6
