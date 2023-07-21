# Treinamento
Curso_DIO
# Menu do sistema



menu = """

[d] Depositar
[s] Sacar
[e] Extrato
[q] Sair

=> """

# Variáveis do sistema


saldo = 0
limite = 500
extrato = ""
numero_saque = 0
LIMITE_SAQUE = 3


# Função para depositar


def depositar():
    global saldo
    try:
        deposito = float(input("Digite o valor do depósito: "))
        if deposito > 0:
            saldo += deposito
            print("Depósito realizado com sucesso!")
            print(f"Novo saldo: R$ {saldo:.2f}")
        else:
            print("O valor do depósito deve ser maior que zero.")
    except ValueError:
        print("Valor de depósito inválido. Certifique-se de inserir um número válido.")


# Função para sacar


def sacar():
    global saldo, numero_saque
    if numero_saque < LIMITE_SAQUE:
        try:
            valor_saque = float(input("Digite o valor do saque: "))
            if 0 < valor_saque <= saldo and valor_saque <= limite:
                saldo -= valor_saque
                numero_saque += 1
                print(f"Saque de R$ {valor_saque:.2f} realizado com sucesso!")
                print(f"Novo saldo: R$ {saldo:.2f}")
            else:
                print("Valor de saque inválido. Certifique-se de ter saldo suficiente e respeitar o limite de saque.")
        except ValueError:
            print("Valor de saque inválido. Certifique-se de inserir um número válido.")
    else:
        print("Você atingiu o limite diário de saques.")


# Função para extrato


def exibir_extrato():
    global extrato
    if extrato:
        print("Extrato:")
        print(extrato)
    else:
        print("Extrato vazio. Nenhuma transação realizada.")


# Loop do sistema

while True:
    opcao = input(menu)

    if opcao == "d":
        print("Depósito")
        depositar()

    elif opcao == "s":
        print("Saque")
        sacar()

    elif opcao == "e":
        print("Extrato")
        exibir_extrato()
        
    elif opcao == "q":
        print("Saindo...")
        break

    else:
        print("Operação inválida, por favor selecione novamente a operação desejada.")

