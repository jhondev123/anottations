[[C SHARP]]
Usado para não bloquear a thread principal quando demanda de alguma coisa externa ao app, requisições HTTP. banco de dados ou até leitura de arquivos

# Async define um método que é assincrono
Ou seja, um método que não é para esperar ele exutar


# Await
espera a conclusão de uma task antes de continuar a execução

# Exemplo
```c#
public async Task<string> BuscarDadosAsync()
{
    using (var http = new HttpClient())
    {
        string resultado = await http.GetStringAsync("https://api.exemplo.com/dados");
        return resultado;
    }
}
```
- `await` **pausa a execução** até que a tarefa seja concluída.
- O resto do código do método **espera o resultado**, sem bloquear a thread.