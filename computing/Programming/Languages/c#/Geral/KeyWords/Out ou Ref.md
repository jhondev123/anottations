# out
É usada ambas para passar valores por referência, se for out n precisa estar inicializada
```c#
public bool foo(string bar,out string error)
{
	try
	{
		return "foo" == bar;
	}
	catch (Exception e)
	{
		error = e.Message;
		return false;
	}
}

foo("foo",out string error);
if(!string.IsNullOrEmpty(error))
{
	MessageBox(error);
}
```
No exemplo ele cria a variavel error e ela vai ter valor somente se houver alguma exception no método

# ref
Passa os valores por referência, diferente do out ele precisa que a variavel esteja inicializada antes de ser passada para o método que pede um ref
```c#
public bool foo(string bar,ref string error)
{
	try
	{
		return "foo" == bar;
	}
	catch (Exception e)
	{
		error = e.Message;
		return false;
	}
}
string error;
foo("foo",ref string error);
if(!string.IsNullOrEmpty(error))
{
	MessageBox(error);
}