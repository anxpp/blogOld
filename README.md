#地址：http://anxpp.com/ 

```java
/**
 * Check whether write operations are allowed on the given Session.
 * <p>Default implementation throws an InvalidDataAccessApiUsageException in
 * case of {@code FlushMode.MANUAL}. Can be overridden in subclasses.
 * @param session current Hibernate Session
 * @throws InvalidDataAccessApiUsageException if write operations are not allowed
 * @see #setCheckWriteOperations
 * @see Session#getFlushMode()
 * @see FlushMode#MANUAL
 */
protected void checkWriteOperationAllowed(Session session) throws InvalidDataAccessApiUsageException {
	if (isCheckWriteOperations() && session.getFlushMode().lessThan(FlushMode.COMMIT)) {
		throw new InvalidDataAccessApiUsageException(
				"Write operations are not allowed in read-only mode (FlushMode.MANUAL): "+
				"Turn your Session into FlushMode.COMMIT/AUTO or remove 'readOnly' marker from transaction definition.");
	}
} 
```
```xml
<tx:advice id="txAdvice" transaction-manager="transactionManager">
	<tx:attributes>
		<tx:method name="*" propagation="REQUIRED" />
	</tx:attributes>
</tx:advice>
```
