# NET6 DateOnly Json Serialize

## Package

Update package `System.Text.Json` >= `7.0.0`

## Swagger document

### Program.cs

```csharp
services.AddSwaggerGen(c => {
	// MapType for DateOnly "2021-01-01"
	c.MapType<DateOnly>(() => new OpenApiSchema
	{
		Type = "string",
		Format = "date"
	});
});
```
