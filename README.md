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

# reference 
https://tufin.medium.com/extending-envoy-proxy-with-golang-webassembly-e51202809ba6
