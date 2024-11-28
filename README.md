## Исходник:
### JsonController:
```
using Microsoft.AspNetCore.Mvc;
using System.Text.Json;

namespace Test_API.Controllers
{
    [ApiController]
    [Route("[controller]")]
    public class JsonController : ControllerBase
    {
        [HttpPost]
        public IActionResult Post([FromBody] string json)
        {
            // Process the incoming JSON
            var result = JsonSerializer.Deserialize<dynamic>(json);

            // Here you would typically process the JSON and generate a response
            // For this example, we'll just return the input JSON

            return Ok(result);
        }
    }
}

```
### Program:
```
var builder = WebApplication.CreateBuilder(args);
builder.Services.AddControllers();

var app = builder.Build();

app.UseHttpsRedirection();
app.UseAuthorization();
app.MapControllers();

app.Run();
```
