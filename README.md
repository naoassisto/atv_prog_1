# atv_prog_1

## Explicação do cod 


`BankAccountTest.cs`.

### Classe `BankAccount` - Exemplos do Código

#### Propriedades:
```csharp
public class BankAccount
{
    public string CustomerName { get; private set; }
    public double Balance { get; private set; }
    ...
}
```
- **Construtor da Classe `BankAccount`**: Inicializa uma nova instância da classe `BankAccount` com um nome de cliente e um saldo inicial.


#### Métodos:
- **Débito:**
```csharp
public void Debit(double amount)
{
    if (amount > Balance || amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }

    Balance -= amount; // Atualiza o saldo
}
```
- **Método `Debit`**: Verifica se o valor de débito é válido (não negativo e não maior que o saldo atual) antes de subtrair o valor do saldo.


- **Crédito:**
```csharp
public void Credit(double amount)
{
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }

    Balance += amount; // Atualiza o saldo
}
```
- **Método `Credit`**: Verifica se o valor de crédito é válido (não negativo) antes de adicionar o valor ao saldo.


### Classe `BankAccountTest` - Exemplos de Testes Unitários

- **Teste Unitário `Debit_WithValidAmount_UpdatesBalance`**: Configura um ambiente de teste (Arrange), executa a operação de débito (Act) e verifica se o saldo final está correto (Assert).


#### Teste de Débito:
```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Conta não debitada corretamente");
}
```

Esta estrutura abrange a inicialização de uma instância da `BankAccount` com um saldo inicial, a execução de uma operação de débito, e a verificação para assegurar que o saldo final seja o esperado após o débito.

## Mudanças no codigo

## Classe `BankAccount`

### Método `Debit`

O método `Debit` original contém um erro intencional para demonstrar a importância dos testes de unidade.

**Original:**
```csharp
public void Debit(double amount)
{
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }

    m_balance += amount; // intentionally incorrect code
}
```

<a href="https://imgur.com/JtCrN7y"><img src="https://i.imgur.com/JtCrN7y.png" title="source: imgur.com" /></a>

**Modificado:**

A mudança principal é a correção na lógica do método `Debit`, onde o saldo da conta é decrementado pelo valor do débito, refletindo a operação de débito corretamente.


```csharp
public void Debit(double amount)
{
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }

    m_balance -= amount; // Correção: o saldo é agora decrementado corretamente
}
```


<a href="https://imgur.com/histFvA"><img src="https://i.imgur.com/histFvA.png" title="source: imgur.com" /></a>




