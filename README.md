#地址：http://anxpp.com/ 

```java
protected void checkWriteOperationAllowed(Session session) throws InvalidDataAccessApiUsageException {  
        if (isCheckWriteOperations() && getFlushMode() != FLUSH_EAGER && session.getFlushMode().lessThan(FlushMode.COMMIT)) {  
            throw new InvalidDataAccessApiUsageException(  
                    "Write operations are not allowed in read-only mode (FlushMode.NEVER/MANUAL): "+  
                    "Turn your Session into FlushMode.COMMIT/AUTO or remove 'readOnly' marker from transaction definition.");  
        }  
    }  
```
