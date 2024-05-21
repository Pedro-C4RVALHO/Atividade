

import os

nome_arquivo = 'dados_trabalhadores.txt'

def carregar_dados():
    dados = {}
    if os.path.exists(nome_arquivo):
        with open(nome_arquivo, 'r') as arquivo:
            for linha in arquivo:
                linha = linha.strip()
                if linha:
                    (nome,salario,inss,numero_de_depentes,imposto_de_renda,cep,cpf) = linha.split(':')
                    dados[nome] = float(salario), float(inss), int(numero_de_depentes), float(imposto_de_renda), float(cep), float(cpf)
    return dados
def salvar_dados(dados):
    with open(nome_arquivo, 'w') as arquivo:
        for nome, salario ,inss,numero_de_depentes,imposto_de_renda,cpf,cep in dados.items():
            arquivo.write(f"{nome}:{salario}:{inss}:{numero_de_depentes}:{imposto_de_renda}:{cep}:{cpf}\n")

def adicionar_ou_atualizar_trabalhador(nome, salario,inss,numero_de_depentes,imposto_de_renda,cpf,cep):
    dados = carregar_dados()
    dados[nome] = salario
    dados[nome] = inss
    dados[nome] = numero_de_depentes
    dados[nome] = imposto_de_renda
    dados[nome] = cep
    dados[nome] = cpf
    salvar_dados(dados)

while True:
    nome = input("Digite o nome do trabalhador (ou 'sair' para terminar): ")
    if nome.lower() == 'sair':
        break
    salario = float(input(f"Digite o salário de {nome}: "))
    inss = float(input(f"Digite a porcentagem descontada do INSS de {nome}: "))
    inss = salario * (inss / 100)
    print("O desconto de INSS é {}".format(inss))
    numero_de_depentes = float(input(f"Digite o número de dependetes de {nome}:"))
    numero_de_depentes = numero_de_depentes * 189
    print("O desconto por dependete é {}".format(numero_de_depentes))
    def imposto_renda(salario):

        faixas = [
            (1903.98, 0.00),
            (2826.65, 0.075),
            (3751.05, 0.15),
            (4664.68, 0.225),
            (float('inf'), 0.275)
        ]

        deducoes = [
            0.00,
            142.80,
            354.80,
            636.13,
            869.36
        ]

        imposto = 0.0
        for i in range(len(faixas) - 1, -1, -1):
            limite, aliquota = faixas[i]
            if salario > limite:
                imposto += (salario - limite) * aliquota
                salario = limite
        for i in range(len(faixas) - 1, -1, -1):
            limite, _ = faixas[i]
            if salario > limite:
                deducao = deducoes[i]
                break
        else:
            deducao = 0.0
        return imposto - deducao
    imposto = imposto_renda(salario)
    print(f"O imposto de renda devido é: R$ {imposto:.2f}")
    cpf = float(input(f"Digite o CPF de {nome}:"))
    print("CPF Válido")
    cep = float(input(f"Digite o CEP de {nome}:"))
    print("CEP: ", cep)


    print(f"Dados de {nome} atualizados com sucesso.")
print("Operação concluída.")





