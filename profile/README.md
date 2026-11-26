# goichi-dev

Open-source Go libraries, built around **Goichi**: a multi-protocol web API
framework.

## Goichi

One Goichi application serves REST, WebSocket, GraphQL, gRPC/ConnectRPC, MQTT
and MCP, all sharing one router, one middleware chain and one authentication
model. It also includes a reverse proxy with load balancing, health checks,
WebSocket passthrough and a layer-4 TCP proxy.

```sh
go get github.com/goichi-dev/goichi@latest
```

```go
package main

import "github.com/goichi-dev/goichi"

func main() {
	app := goichi.New(goichi.Config{})
	app.GET("/hello/:name", func(c *goichi.Context) error {
		return c.JSON(map[string]string{"hello": c.Param("name")})
	})
	app.Listen(":3000")
}
```

## Repositories

| repository | what it is |
|---|---|
| [goichi](https://github.com/goichi-dev/goichi) | The framework |
| [goichi-examples](https://github.com/goichi-dev/goichi-examples) | Runnable examples, one per protocol, plus every protocol on one port |
| [goichi-bench](https://github.com/goichi-dev/goichi-bench) | REST benchmark against fiber, gin, echo, chi and atreugo, and the regression gate for Goichi |
| [thai-lunar](https://github.com/goichi-dev/thai-lunar) | Thai lunar calendar (ปฏิทินจันทรคติไทย) for Go: Gregorian to ข้างขึ้น/ข้างแรม and back, Buddhist holy days, no dependencies |

## Performance

On the latest [goichi-bench](https://github.com/goichi-dev/goichi-bench) run,
Goichi v0.6.0 came third of six frameworks. It is 35–66% faster than gin, echo
and chi, and up to 15% slower than fiber. The benchmark explains how it
measures, how much of the result is noise, and how to reproduce it.

Everything here is MIT licensed. Goichi is at `v0.x`, so its API may still
change between minor versions.
