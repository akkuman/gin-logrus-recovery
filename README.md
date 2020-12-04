# gin-logrus-recovery

A gin middleware which use the logrus to recovery

# example

```golang
package main

import (
    "github.com/sirupsen/logrus"

    "github.com/gin-gonic/gin"

    ginlogrusrecovery "github.com/akkuman/gin-logrus-recovery"
    ginlogrus "github.com/toorop/gin-logrus"
)

var r *gin.Engine

// NewGinEngine create a gin engine with logrus
func NewGinEngine(logger logrus.FieldLogger) *gin.Engine {
    engine := gin.New()
    engine.Use(ginlogrus.Logger(logger), ginlogrusrecovery.Recovery(logger))
    return engine
}

func main() {
    // 日志初始化
    logger := logrus.New()

    r = NewGinEngine(logger)
    
    // some handler

    r.Run(fmt.Sprintf("0.0.0.0:8888")
}

```