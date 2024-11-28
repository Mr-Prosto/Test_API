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
            var result = JsonSerializer.Deserialize<dynamic>(json);
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
