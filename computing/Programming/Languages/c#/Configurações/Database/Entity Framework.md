[[Orms]]
[[Orm]]
[[C SHARP]]

Primeiro precisa criar a DB context
```
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.Logging;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using teste_tickets.Models;

namespace teste_tickets.Data
{
    public class MyDbContext : DbContext
    {
        public MyDbContext(DbContextOptions<MyDbContext> options): base(options)
        {
                
        }
        public DbSet<Employee> Employees { get; set; }
    }
}
```

Depois Precisa adicionar a Secret
```

{ 
	"ConnectionStrings": {
	"DefaultConnection": "Host=localhost;Database=Erp;Username=postgres;Password=postgres;" 
	} 
}

```

Depois configurar o Program.cs
```
using Microsoft.EntityFrameworkCore;
using Microsoft.Extensions.Configuration;
using Microsoft.Extensions.DependencyInjection;
using teste_tickets.Data;
using teste_tickets.Models;
namespace teste_tickets
{
    internal class Program
    {

        [STAThread]
        static void Main()
        {

            var builder = new ConfigurationBuilder()
                .AddUserSecrets<Program>()
                .Build(); 
            string connectionString = builder.GetConnectionString("DefaultConnection");


            ServiceCollection service = new ServiceCollection();
            service.AddDbContext<MyDbContext>(options => options.UseNpgsql(connectionString));
            ApplicationConfiguration.Initialize();
            Application.Run(new employee());
        }
    }
}
```

e para poder criar as migrations precisa ter um dbcontextfactory
```
using Microsoft.EntityFrameworkCore.Design;
using Microsoft.EntityFrameworkCore;
using System;
using System.Collections.Generic;
using System.Configuration;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace teste_tickets.Data
{
    public class MyDbContextFactory
    {
        public class ErpContextFactory : IDesignTimeDbContextFactory<MyDbContext>
        {
            public MyDbContext CreateDbContext(string[] args)
            {
                var optionsBuilder = new DbContextOptionsBuilder<MyDbContext>();
                optionsBuilder.UseNpgsql(
                    "Host=localhost;Database=teste;Username=pgsql;Password=pgsql;");
                return new MyDbContext(optionsBuilder.Options);
            }
        }
    }
}

```
