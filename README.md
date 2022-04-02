from asyncore import loop
import requests
import math
import numpy

r = requests.get('https://hackersdamatrix.herokuapp.com/at3json')

lista = r.json()
lista_Completos = []
lista_N_completados = []
numero_Lista = 1
lista_quantidade = []
lista_geral = 0

#verificar quem terminou
for pessoas in lista:
    if pessoas['completed'] == True:
        lista_Completos.append(pessoas)

#ver quantos IDs tem na lista completa
for numero_repeticao in lista_Completos:
    if numero_Lista == numero_repeticao['userId']:
        numero_Lista = numero_Lista + 1

#resetar e mexer nas variaveis
numero_Lista = numero_Lista - 1
numero_Max = numero_Lista
numero_Lista = 1

numero_Lista = numero_Lista 

#vai ser para achar quantidade terminada
def adicionar_numero_tarefas():
    for cadaPessoas in lista_Completos:
        if cadaPessoas['userId'] == numero_Lista:
            lista_quantidade.append((1))

numero_anterior = 0

while numero_Lista < numero_Max + 1:
    adicionar_numero_tarefas()
    numero_total_total = sum(lista_quantidade) - numero_anterior
    print(f"Cada usuario terminou -- UserId: {numero_Lista} terminou:", numero_total_total, "tarefas.")
    numero_anterior = sum(lista_quantidade)
    lista_geral += numero_total_total
    numero_Lista = numero_Lista + 1

print(f"No total, os usuários terminaram:", lista_geral, "tarefas.")

