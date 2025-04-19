Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.

**Example 1:**

**Input:** nums = [2,7,11,15], target = 9
**Output:** [0,1]
**Explanation:** Because nums[0] + nums[1] == 9, we return [0, 1].

**Example 2:**

**Input:** nums = [3,2,4], target = 6
**Output:** [1,2]

**Example 3:**

**Input:** nums = [3,3], target = 6
**Output:** [0,1]

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

# Resolução
Esse leet code a forma mais comum é fazer por brute force, porém não necessariamente mais performático

com brute force:
```c#
int[] TwoSumBruteForce(int[] nums, int target)
{
    for (int i = 0; i < nums.Length; i++)
    {
        for (int j = i+1; j < nums.Length; j++)
        {
            if(nums[i] + nums[j] == target)
            {
                return [i,j];
            }
        }
    }
    return [];
}
```
Essa resolução é boa mas como mencionado não é a mais performática, ela leva muito tempo para processar por ter complexidade  [[O(n)2]]

a outra resolução possível é com um algoritmo de hashmap
```c#
int[] TwoSumResultHashmap(int[] nums, int target)
{
	// cria um hashmap do c#
    Dictionary<int,int> numsIndices = new Dictionary<int,int>();
    for (int i = 0; i < nums.Length; i++)
    {
	    // pega o primeiro valor da interação e diminui o valor que
	    // quer encontrar, assim podendo procurar se o valor que falta existe dentro do hashmap  
        int complement = target - nums[i];
        if (numsIndices.ContainsKey(complement))
        {
            return [numsIndices[complement], i];
        }
        // caso não tenha encontrado ele adiciona no hashmap
        if (!numsIndices.ContainsKey(nums[i]))
        {
            numsIndices[nums[i]] = i;
        }
    }
    return [];
}
```