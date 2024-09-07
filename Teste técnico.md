1) Observe o trecho de código abaixo: int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA);
Ao final do processamento, qual será o valor da variável SOMA?

int INDICE = 13, SOMA = 0, K = 0;
Enquanto K < INDICE faça { K = K + 1; SOMA = SOMA + K; }
Imprimir(SOMA);


2) Dado a sequência de Fibonacci, onde se inicia por 0 e 1 e o próximo valor sempre será a soma dos 2 valores anteriores (exemplo: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34...), escreva um programa na linguagem que desejar onde, informado um número, ele calcule a sequência de Fibonacci e retorne uma mensagem avisando se o número informado pertence ou não a sequência.

IMPORTANTE: Esse número pode ser informado através de qualquer entrada de sua preferência ou pode ser previamente definido no código;
def pertence_a_fibonacci(numero):
    """Verifica se um número pertence à sequência de Fibonacci."""
    if numero < 0:
        return False

    # Inicializa os primeiros dois números da sequência
    a, b = 0, 1
    
    # Caso especial onde o número é 0 ou 1
    if numero == a or numero == b:
        return True

    # Calcula a sequência de Fibonacci até encontrar o número ou ultrapassar
    while b < numero:
        a, b = b, a + b
        
    return b == numero

# Opção 1: Entrada pelo usuário
entrada = int(input("Digite um número para verificar se pertence à sequência de Fibonacci: "))

# Opção 2: Número definido previamente (descomente para usar)
# entrada = 21

# Verifica se o número pertence à sequência de Fibonacci
if pertence_a_fibonacci(entrada):
    print(f"O número {entrada} pertence à sequência de Fibonacci.")
else:
    print(f"O número {entrada} não pertence à sequência de Fibonacci.")


3) Dado um vetor que guarda o valor de faturamento diário de uma distribuidora, faça um programa, na linguagem que desejar, que calcule e retorne:
• O menor valor de faturamento ocorrido em um dia do mês;
• O maior valor de faturamento ocorrido em um dia do mês;
• Número de dias no mês em que o valor de faturamento diário foi superior à média mensal.
import json

def calcular_estatisticas(faturamentos):
    """Calcula o menor e maior valor de faturamento e o número de dias acima da média mensal."""
    # Filtra os valores de faturamento válidos (ignorando nulos)
    faturamentos_validos = [f for f in faturamentos if f is not None]
    
    if not faturamentos_validos:
        return None, None, 0

    # Menor e maior valor de faturamento
    menor_faturamento = min(faturamentos_validos)
    maior_faturamento = max(faturamentos_validos)
    
    # Média mensal de faturamento
    media_mensal = sum(faturamentos_validos) / len(faturamentos_validos)
    
    # Número de dias com faturamento acima da média mensal
    dias_acima_da_media = sum(1 for faturamento in faturamentos_validos if faturamento > media_mensal)
    
    return menor_faturamento, maior_faturamento, dias_acima_da_media

# Ler dados do arquivo JSON
with open('faturamento.json', 'r') as file:
    data = json.load(file)

faturamentos_diarios = data['faturamentos']

# Calcular as estatísticas
menor, maior, dias_acima = calcular_estatisticas(faturamentos_diarios)

# Exibir os resultados
print(f"Menor valor de faturamento: R${menor:.2f}")
print(f"Maior valor de faturamento: R${maior:.2f}")
print(f"Número de dias com faturamento acima da média mensal: {dias_acima}")



4) Dado o valor de faturamento mensal de uma distribuidora, detalhado por estado:
• SP – R$67.836,43
• RJ – R$36.678,66
• MG – R$29.229,88
• ES – R$27.165,48
• Outros – R$19.849,53

def calcular_percentuais(faturamentos):
    """Calcula o percentual de representação de cada estado no faturamento total."""
    # Calcula o faturamento total
    total_faturamento = sum(faturamentos.values())
    
    # Calcula o percentual de cada estado
    percentuais = {}
    for estado, valor in faturamentos.items():
        percentual = (valor / total_faturamento) * 100
        percentuais[estado] = percentual
    
    return percentuais, total_faturamento

# Dados de faturamento por estado
faturamentos_estado = {
    "SP": 67836.43,
    "RJ": 36678.66,
    "MG": 29229.88,
    "ES": 27165.48,
    "Outros": 19849.53
}

# Calcula percentuais e total
percentuais, total = calcular_percentuais(faturamentos_estado)

# Exibe os resultados
print(f"Faturamento total: R${total:.2f}")
for estado, percentual in percentuais.items():
    print(f"{estado}: {percentual:.2f}%")



5) Escreva um programa que inverta os caracteres de um string.

IMPORTANTE:
a) Essa string pode ser informada através de qualquer entrada de sua preferência ou pode ser previamente definida no código;
b) Evite usar funções prontas, como, por exemplo, reverse;

def inverter_string(s):
    """Inverte os caracteres de uma string."""
    # Inicializa uma string vazia para armazenar o resultado
    resultado = ""
    
    # Percorre a string de trás para frente e adiciona cada caractere ao resultado
    for i in range(len(s) - 1, -1, -1):
        resultado += s[i]
    
    return resultado

# Opção 1: Entrada pelo usuário
entrada = input("Digite uma string para inverter: ")

# Opção 2: String definida previamente (descomente para usar)
# entrada = "exemplo"

# Inverte a string e exibe o resultado
string_invertida = inverter_string(entrada)
print(f"String invertida: {string_invertida}")

