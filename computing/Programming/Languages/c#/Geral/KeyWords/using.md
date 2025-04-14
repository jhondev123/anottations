A keyword tem a funcionalidade de liberar recursos depois de algo ser usado. conexão com o banco de dados, acesso a arquivos
como ele faz isso. o c# disponibiliza uma interface chamada IDisposable, que possui um único método, o Dispose. esse método ele vai ser executado no final do using ou seja liberando recursos usados.
```c#
using (var arquivo = new StreamWriter("log.txt"))
{
    arquivo.WriteLine("Gravando no log...");
}
```
Como seria sem usar o using
```c#
var arquivo = new StreamWriter("log.txt");
try
{
    arquivo.WriteLine("Gravando no log...");
}
finally
{
    if (arquivo != null)
        arquivo.Dispose();
}
```

