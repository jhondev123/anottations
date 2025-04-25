O quick sort pega uma lista de elementos. pega um PIVOT que é um valor podendo ser do inicio, meio ou fim. ele vai montar duas novas listas, a primeira com os valores maiores e a segunda com os valores maiores. apartir disso ele vai chamar de forma recursiva os menores e depois os maiores, e vai montar uma lista de resultado com a seguinte sequência
```
ListaMenores + Pivot + ListaMaiores
```
Exemplo no c#
```c#
public static List<int> Order(List<int>nums)
{
	if (nums.Count <= 1)
		return nums;
	int pivot = nums[nums.Count / 2];
	List<int> newArray = new List<int>();
	List<int> minor = new List<int>();
	List<int> major = new List<int>();

	for(int intI=0;intI< nums.Count;intI++)
	{
		if (nums[intI] < pivot)
		{
			minor.Add(nums[intI]);
		}
		if (nums[intI] > pivot)
		{
			major.Add(nums[intI]);
		}
	}
	newArray.AddRange(Order(minor));
	newArray.Add(pivot);
	newArray.AddRange(Order(major));
	return newArray;
}
```