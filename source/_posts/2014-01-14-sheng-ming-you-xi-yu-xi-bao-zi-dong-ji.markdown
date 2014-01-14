---
layout: post
title: "生命游戏与细胞自动机"
date: 2013-03-10 15:25:03 +0100
comments: true
categories: 
---


"Cellular Automaton"，ein Interessante Modell, was ist benutzt in viele Felder. Ich kann diesem Konzept nicht deutlich erklaeren, Weil ich nur die Prozess verstehe, keinen weitere Benutzungen. Um mehr Informationen zu erkuendigt werden, suchen Sie es nach Wikipedia.

Aber ich finde ein Phaenomen interessant. "Cellular Automaton" war erhoben durch ein Spiel, "Conways Spiel des Leben". Die Regel ist sehr einfach verstanden. Und darunter ist die code

```
import time
from random import random

SIZE = 20

matrix = [[int(random()*2) for y in range(SIZE)] for x in range(SIZE)]

while True:
    for x in matrix:
        for y in x:
            if y: print 1,
            else: print ' ',
        print
    print '\n\n\n\n';
    time.sleep(1)
    matrix = (lambda t:
                [
                    [
                        [0,0,t[x][y],1,1][sum([t[p+x][q+y] for p, q in [(0,1),(1,0),(-1,0),(0,-1)] if (p+x in range(SIZE) and q+y in range(SIZE))])]
                        for y in range(SIZE)
                    ] for x in range(SIZE)
                ]
            )(matrix)
```

我发现这个过程竟然是收敛的，问题来了，如何制定收敛的规则呢？
