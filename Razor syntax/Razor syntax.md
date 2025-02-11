# Razor syntax
## intro
In `.cshtml` file, which is used for creating dynamic web pages in ASP.NET MVC (Model-View-Controller) or ASP.NET Core, 

the block `@{ //... }` will be treated as `C#` code and executed on server.

## Razor expression
### Implicit Razor expressions
Implicit Razor expressions start with `@` followed by C# code

```
<p>@DateTime.Now</p>
<p>@DateTime.IsLeapYear(2016)</p>
```

> [!NOTE]
> When using implicit Razor expressions, it must not contain whitespace,
>
> the only exceptions are
>
> + `@` followed by C# `await` keyword.
> + C# statement has a clear ending (whitespace can be intermingled).
>
> ```
> <p>@await DoSomething("hello", "world")</p>
> ```

> [!NOTE]
> Implicit expressions cannot contain C# generics
>
> since the characters inside the brackets (`<>`) are interpreted as an HTML tag. 
>
> ```
> <p>@GenericMethod<int>()</p>
> ```

### Explicit Razor expressions
Explicit Razor expressions consist of an @ symbol with balanced parenthesis.

```
<p>Last week this time: @(DateTime.Now - TimeSpan.FromDays(7))</p>
```

```
@{
    var joe = new Person("Joe", 33);
}

<p>Age@(joe.Age)</p>
```

Any content within the @() parenthesis is evaluated and rendered to the output.

## reference
[ASP.NET Razor](https://zh.wikipedia.org/zh-tw/ASP.NET_Razor)
