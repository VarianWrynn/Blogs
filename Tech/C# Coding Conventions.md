# C# Coding Conventions



[toc]

[这里关于大括号是否要重启一行？](https://programmercarl.com/%E5%89%8D%E5%BA%8F/%E4%BB%A3%E7%A0%81%E9%A3%8E%E6%A0%BC.html#%E4%BB%A3%E7%A0%81%E8%A7%84%E8%8C%83)

Google规范是 大括号和 控制语句保持同一行的，我个人也很认可这种写法，因为可以缩短代码的行数，特别是项目中代码行数很多的情况下，这种写法是可以提高阅读代码的效率。

当然我并不是说一定要按照Google的规范来，**代码风格其实统一就行，没有严格的说谁对谁错**。



Coding conventions serve the following purposes:

- They create a consistent look to the code, so that readers can focus on content, not layout.
- They enable readers to understand the code more quickly by making assumptions based on previous experience.
- They facilitate copying, changing, and maintaining the code.
- They demonstrate C# best practices.

 Important

The guidelines in this article are used by Microsoft to develop samples and documentation. They were adopted from the [.NET Runtime, C# Coding Style](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md) guidelines. You can use them, or adapt them to your needs. The primary objectives are consistency and readability within your project, team, organization, or company source code.



## Naming conventions

There are several naming conventions to consider when writing C# code.

In the following examples, any of the guidance pertaining to elements marked `public` is also applicable when working with `protected` and `protected internal` elements, all of which are intended to be visible to external callers.



### Pascal case

Use pascal casing ("PascalCasing") when naming a `class`, `record`, or `struct`.



```csharp
public class DataService
{
}
```



```csharp
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```



```csharp
public struct ValueCoordinate
{
}
```

When naming an `interface`, use pascal casing in addition to prefixing the name with an `I`. This clearly indicates to consumers that it's an `interface`.



```csharp
public interface IWorkerQueue
{
}
```

When naming `public` members of types, such as fields, properties, events, methods, and local functions, use pascal casing.



```csharp
public class ExampleEvents
{
    // A public field, these should be used sparingly
    public bool IsValid;

    // An init-only property
    public IWorkerQueue WorkerQueue { get; init; }

    // An event
    public event Action EventProcessing;

    // Method
    public void StartEventProcessing()
    {
        // Local function
        static int CountQueueItems() => WorkerQueue.Count;
        // ...
    }
}
```

When writing positional records, use pascal casing for parameters as they're the public properties of the record.

C#Copy

```csharp
public record PhysicalAddress(
    string Street,
    string City,
    string StateOrProvince,
    string ZipCode);
```

For more information on positional records, see [Positional syntax for property definition](https://docs.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/record#positional-syntax-for-property-definition).

### Camel case

Use camel casing ("camelCasing") when naming `private` or `internal` fields, and prefix them with `_`.



```csharp
public class DataService
{
    private IWorkerQueue _workerQueue;
}
```

 **Tip**

> When editing C# code that follows these naming conventions in an IDE that supports statement completion, typing `_` will show all of the object-scoped members.
>
> When working with `static` fields that are `private` or `internal`, use the `s_` prefix and for thread static use `t_`.



```csharp
public class DataService
{
    private static IWorkerQueue s_workerQueue;

    [ThreadStatic]
    private static TimeSpan t_timeSpan;
}
```

When writing method parameters, use camel casing.

```csharp
public T SomeMethod<T>(int someNumber, bool isValid)
{
}
```

For more information on C# naming conventions, see [C# Coding Style](https://github.com/dotnet/runtime/blob/main/docs/coding-guidelines/coding-style.md).





## Reference:

1. [C# Coding Conventions-Microsoft](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)