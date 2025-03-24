```
class Pessoa
{
	private string idade = { get; set; }
    private string nome; // Campo privado
    // Propriedade com métodos get e set explícitos
    public string Nome
    {
        get
        {
            return nome; // Retorna o valor do campo privado
        }
        set
        {
            if (!string.IsNullOrWhiteSpace(value)) // Validação antes de definir
            {
                nome = value;
            }
            else
            {
                throw new ArgumentException("O nome não pode ser vazio ou nulo.");
            }
        }
    }
}
```