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

```output

[2021-03-22 21:10:51.616][2633455][info][config] [source/server/configuration_impl.cc:125] loading tracing configuration
[2021-03-22 21:10:51.616][2633455][info][config] [source/server/configuration_impl.cc:85] loading 0 static secret(s)
[2021-03-22 21:10:51.616][2633455][info][config] [source/server/configuration_impl.cc:91] loading 1 cluster(s)
[2021-03-22 21:10:51.642][2633455][info][config] [source/server/configuration_impl.cc:95] loading 1 listener(s)
[2021-03-22 21:10:51.843][2633455][info][config] [source/server/configuration_impl.cc:107] loading stats configuration
[2021-03-22 21:10:51.843][2633455][info][runtime] [source/common/runtime/runtime_impl.cc:425] RTDS has finished initialization
[2021-03-22 21:10:51.844][2633455][info][upstream] [source/common/upstream/cluster_manager_impl.cc:191] cm init: all clusters initialized
[2021-03-22 21:10:51.844][2633455][warning][main] [source/server/server.cc:609] there is no configured limit to the number of allowed active connections. Set a limit via the runtime key overload.global_downstream_max_connections
[2021-03-22 21:10:51.844][2633455][info][main] [source/server/server.cc:712] all clusters initialized. initializing init manager
[2021-03-22 21:10:51.844][2633455][info][config] [source/server/listener_manager_impl.cc:888] all dependencies initialized. starting workers
[2021-03-22 21:10:51.845][2633455][info][main] [source/server/server.cc:731] starting main dispatch loop
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: :authority: localhost:8085
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: :path: /hello
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: :method: GET
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: user-agent: curl/7.64.1
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: accept: */*
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: x-forwarded-proto: http
[2021-03-22 21:11:27.223][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: request header: x-request-id: bc133cee-5332-471a-a999-00f0eb55029d
[2021-03-22 21:11:27.236][2633486][info][wasm] [source/extensions/common/wasm/context.cc:1171] wasm log: 2 finished

```

# refercence 
https://tufin.medium.com/extending-envoy-proxy-with-golang-webassembly-e51202809ba6