[[POO]]
[[Generics]]
Exemplo no c#
```
class Product
{

}
interface IRepository<T>
{
	T Create(T pModel);
}
class ProductRepository : IRepository
{
	public Product Create(Product product)
	{
		return product;
	}

}
```


