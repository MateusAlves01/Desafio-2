# Desafio-2

Explicando o que o código esta fazendo;
## Fazer a explicação por partes

Nessa primeira etapa tem uma class chama MyClass1 com duas instâncias privadas sendo: __var1 é uma lista do tipo inteiro e __var2 é uma string
#### Logo abaixo
A criação de um construtor __init é chamado quando um objeto é criado. 

Os métodos get são de acesso que retornam os valores armazenados nas variáveis. Os métodos set são métodos de modificação onde altera os valores.

```python
class MyClass1:
    __var1 : List[int]
    __var2 : str
  
    def __init__(self, var1:List[int], var2:str):
        self.__var1 = var1
        self.__var2 = var2
    
    def get_var1(self):
        return self.__var1
    
    def set_var1(self, var1:List[int]):
        self.__var1 = var1

    def get_var2(self):
        return self.__var2
    
    def set_var2(self, var2:str):
        self.__var2 = var2
```

## Segunda etapa

O method1  começa criando uma cópia da lista "__var1" do objeto que chama o método, usando o método copy() da classe list. Em seguida, essa cópia é ordenada usando o método sort() da classe list. Depois que a lista ordenada é criada, a função percorre todos os elementos da lista, começando com o segundo elemento (índice 1) até o último elemento da lista, usando um loop for e a função range(). Para cada elemento atual na lista, a função verifica se o elemento atual é igual ao elemento anterior (índice atual - 1) na lista ordenada. Se houver uma correspondência, significa que há um valor duplicado na lista original e a função retorna True.

```python
def method1(self)->bool:
        aux = self.__var1.copy()
        aux.sort()
        for i in range(1, len(aux)):
            if aux[i] == aux[i-1]:
                return True
        return False
   
```
Recebe um argumento inteiro target e retorna uma lista de dois inteiros, que são índices de elementos na lista privada "__var1" do objeto que chama o método. Esses índices correspondem a um par de números na lista que somam target. Se não houver tal par, a função retorna uma lista vazia. função enumerate() para iterar sobre cada elemento da lista privada "__var1" do objeto que chama o método.  O método verifica se o valor remaining já foi armazenado no dicionário seen. Se já tiver sido armazenado, significa que há um par de números na lista que somam target. Nesse caso, o método retorna uma lista contendo os índices do par de números encontrados: [i, seen[remaining]]

```python
def method2(self, target:int)->List[int]:
        seen = {}
        for i, value in enumerate(self.__var1): 
            remaining = target - self.__var1[i] 
           
            if remaining in seen: 
                return [i, seen[remaining]]  
            else:
                seen[value] = i 

```

O method3 recebe um objeto MyClass1 como argumento e um inteiro. Criando uma cópia da lista armazenada na variável de instância __var1 em seguida, modifica o valor de k para que esteja entre 0 e o tamanho da lista, usa um loop while para girar a lista k vezes para a direita, movendo o último elemento para o início da lista em cada iteração. O método retorna a lista girada.
```python
def method3(self, k:int)->List[int]:
        nums = self.__var1.copy()
        k = k % len(nums)
        n = len(nums)
        i = 0
        count = 0
        while count < n:
            pos = (i + k) % len(nums)
            curr = nums[pos]
            nums[pos] = nums[i]
            count += 1
            j = pos
            while j != i and count < n:
                pos = (j + k) % len(nums)
                nums[pos], curr = curr, nums[pos]
                j = pos
                count += 1
            i += 1
        return nums

```
method4 vai retornar uma lista invertida
```python
 def method4(self)->str:
        return self.__var2[::-1]

```
method5 Recebe duas listas de inteiros "x" e "y" como argumentos e retorna um número que é a mediana das duas listas combinadas ele acaba ali combinando as duas listas em Z, usando o operador de concatenação * e a sintaxe [*x, *y], que é uma maneira compacta de criar uma nova lista que contém todos os elementos de "x" e "y". Em seguida, a lista "z" é ordenada usando o método sort() da classe list.
```python
  @staticmethod
    def method5(x:List[int], y:List[int])->int:
        
        z = [*x,*y]
        z.sort()
        if len(z)%2 == 0:
            result = (z[len(z)//2] + z[len(z)//2-1])/2
            
        else:
            result = z[len(z)//2]
        
        return result

```
# Refatoração
Sempre usar descritivos nos metodos para que qualquer pessoa pessoa possa ler o código com facilidade
