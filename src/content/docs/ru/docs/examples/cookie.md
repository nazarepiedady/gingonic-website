---
title: "Установка и получение cookie"
черновик: false
---

cookieの設定と取得

```go
import (
    "fmt"

    "github.com/gin-gonic/gin"
)

func main() {

    router := gin.Default()

    router.GET("/cookie", func(c *gin.Context) {

        cookie, err := c.Cookie("gin_cookie")

        if err != nil {
            cookie = "NotSet"
            c.SetCookie("gin_cookie", "test", 3600, "/", "localhost", false, true)
        }

        fmt.Printf("Cookie value: %s \n", cookie)
    })

    router.Run()
}
```

Delete cookie by set max age to -1.

```go
c.SetCookie("gin_cookie", "test", -1, "/", "localhost", false, true)
```
