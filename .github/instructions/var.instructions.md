---
applyTo: "**/*.cs"
---

# Rules for var usage

The rules should be consistent with the team's coding standards and between different agent contexts, but here are some general guidelines:

Use `var` when the type is obvious from the right-hand side, if the type is clear from context, `var` removes noise:
```
var customer = new Customer();
var orders = new List<Order>();
var amount = 10m;
```

Use `var` when the type is irrelevant to the reader. Sometimes the _intent_ matters more than the actual type and explicit typing adds no value
```
// return type is known via method name
var items = GetItems();  
var tuple = GetData();
```

Use `var` when the type is painfully verbose. This is especially true with generics, collections or nested types:
```
var lookup = new Dictionary<string, List<Customer>>();
```

Use `var` when necessary with LINQ or anonymous types. Although sometimes it's preferred to make IQueryable explicit, see below.
**Materializing a LINQ IQueryable into a collection is a common gotcha when working with ef core and dbcontext.**


## When not to use var

Do not use it when the type is not obvious from the right-hand side
```
var result = DoMagic();   // What type is result? 
```

This hurts readability because the type is important to understand the code.
Prefer:
```
CustomerData result = DoMagic();
```

When the literal doesn’t tell you the intended type, some numeric literals are ambiguous:
```
var x = 1;     // int? 
var y = 1.0;   // double?
```

The same goes for characters/strings:
```
var value = '\n';  // char? maybe someone thinks it's string 
```

When it obscures collection types
```
var customers = GetCustomers();
```

If you don’t know whether it's:

* a `List<Customer>`
* an `IQueryable<Customer>`
* an `IEnumerable<Customer>`
* a `Customer[]`
* a custom collection

If you're working with interfaces, inheritance, or any type of casting, then don't make the type ambiguous, type it out.
