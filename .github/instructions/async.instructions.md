---
applyTo: "**/*.cs"
---

# Asynchronous Programming

## Async/Await
The async/await construct can accomplish most typical tasks developers face, without having to explore more complex multi-threading techniques. This pattern should be used liberally when dealing with I/O or UI interactions. When writing async code, it's important to follow best practices to avoid deadlocks and other issues.

- Prefer Async versions of IO bound operations to prevent blocking threads.
- Method signatures should be `async Task` or `async Task(T)`. 
- Async methods should have an Async suffix in their name to indicate that they are asynchronous.

## Async void

- Avoid the use of async void, when possible.
- When an exception is thrown from an async Task or async Task(T) method, that exception is captured and placed on the Task object. With async void methods, there is no Task object, so any exceptions thrown will be raised directly on the SynchronizationContext.

## Cancellation Tokens

- Cancellation tokens are a way to signal to a method that it should stop what it's doing. You can pass a cancellation token to an async method and check it periodically to see if it has been cancelled. If it has, you can stop what the method is doing and return early.
- Use cancellation tokens for async operations to allow for graceful termination
- Tokens should be provided as a parameter to any async method. The Cancellation Token should then be passed to any further async method that supports cancellation.
- Consider handling the OperationCanceledException that is thrown when the operation is cancelled. This exception should be caught and handled appropriately. This could involve cleaning up resources or notifying the user that the operation was cancelled.


```csharp
/// <summary>
/// Processes a series of items asynchronously, allowing for cancellation.
/// </summary>
/// <param name="cancellationToken">A token that can be used to cancel the operation.</param>
/// <returns>The number of items processed before cancellation, or the total number if not cancelled.</returns>
private async Task<int> ProcessItemsAsync(CancellationToken cancellationToken)
{
    int itemsProcessed = 0;

    try
    {
        // Simulate processing a series of items.
        for (int i = 0; i < 5_000; i++)
        {
            // Periodically check if the operation has been cancelled.
            cancellationToken.ThrowIfCancellationRequested();

            // Simulate some processing work.
            await Task.Delay(1_000, cancellationToken);

            itemsProcessed++;
        }
    }
    catch (OperationCanceledException)
    {
        // Handle the cancellation by logging a message or cleaning up resources if necessary.
        // Console.WriteLine("Operation was cancelled.");

        // Rethrow the exception to inform the caller that the operation was cancelled.
        //throw;
    }

    // Return the number of items processed (either completed or partially).
    return itemsProcessed;
}
```

## Web API
---
- Avoid blocking calls in ASP.NET Core applications to ensure scalability and responsiveness, blocking calls can lead to thread starvation and reduced throughput.
