São estruturas de dados no c# que permitem armazenar e gerenciar grupos de objetos de maneira eficiente. Elas pertencem ao namespace System.Collections ou System.Collection.Generics

Elas são divididos em dois tipos
* Genéricas
* Não genéricas
	* São coleções que funcionam com objetos do tipo object, que pode precisar de casting.  exemplos: ArrayList, HashTable, Qeue, Stack
* Genéricas
	* São coleções que são safety evitando conversões desnecessárias e melhorando a perfomance, exemplos: 
		* `List<T>`
		* `Dictionary<TKey , TValue>`
		* `Qeue<T>`
		* `Stack<T>`
		* `HashSet<T>`