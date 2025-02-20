## Simulador de Banco em Python

Este programa simula um sistema bancário simples, permitindo ao usuário realizar depósitos, saques e consultar o extrato.

### Menu de Opções

```python
menu = """
[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """
```

### Variáveis Iniciais

```python
saldo = 0
limite = 500
extrato = ""
numero_saques = 0
LIMITE_SAQUES = 3
```

### Loop Principal

```python
while True:
    opcao = input(menu)

    if opcao == "d":
        valor = float(input("Informe o valor do depósito: "))

        if valor > 0:
            saldo += valor
            extrato += f"Depósito: R$ {valor:.2f}\n"
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "s":
        valor = float(input("Informe o valor do saque: "))

        excedeu_saldo = valor > saldo
        excedeu_limite = valor > limite
        excedeu_saques = numero_saques >= LIMITE_SAQUES

        if excedeu_saldo:
            print("Operação falhou! Você não tem saldo suficiente.")
        elif excedeu_limite:
            print("Operação falhou! O valor do saque excede o limite.")
        elif excedeu_saques:
            print("Operação falhou! Número máximo de saques excedido.")
        elif valor > 0:
            saldo -= valor
            extrato += f"Saque: R$ {valor:.2f}\n"
            numero_saques += 1
        else:
            print("Operação falhou! O valor informado é inválido.")

    elif opcao == "e":
        print("\n================ EXTRATO ================")
        print("Não foram realizadas movimentações." if not extrato else extrato)
        print(f"\nSaldo: R$ {saldo:.2f}")
        print("==========================================")

    elif opcao == "q":
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")
```

### Funcionamento

1. O usuário pode escolher entre as opções de depósito (`d`), saque (`s`), extrato (`e`) ou sair (`q`).
2. O sistema controla o limite de saque diário e o número máximo de saques permitidos.
3. As transações são armazenadas e exibidas no extrato.
4. O programa só encerra quando o usuário escolhe a opção `q`.

---

Este código é útil para demonstrar conceitos básicos de programação como loops, condicionais e manipulação de strings em Python.

