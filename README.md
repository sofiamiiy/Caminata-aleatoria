# Caminata-aleatoria
import random
import matplotlib.pyplot as plt

def paso(p):
    if random.random() < p:
        return 1
    else:
        return -1

def caminar(n, p):
    posicion = 0
    posiciones = [posicion]
    for _ in range(n):
        posicion += paso(p)
        posiciones.append(posicion)
    return posiciones

def promedio(trayectoria):
    return sum(abs(x) for x in trayectoria) / len(trayectoria)

def regreso0(trayectoria):
    for i in range(1, len(trayectoria)):
        if trayectoria[i] == 0:
            return i
    return None 

n = 10
p = 0.5
q = 1 - p
trayectoria = caminar(n, p)
regreso = regreso0(trayectoria)

print("Número de pasos:", n)
print("Proba der (p):", p)
print("Proba izq (q):", q)
print("Pos final:", trayectoria[-1])
print("Pos max:", max(trayectoria))
print("Alejamiento max:", abs(max(trayectoria)-0))
print("Pos min:", min(trayectoria))
print("Alejamiemto min:", abs(min(trayectoria)-0))
print("Alejamiento promedio:", promedio(trayectoria))
if regreso is not None:
    print("Primer regreso a 0 en el paso:", regreso)
else:
    print("No regresó a 0")

plt.figure(figsize=(10,5))
plt.plot(trayectoria, marker='o', markersize=3)
plt.title("Caminata al azar")
plt.xlabel("Paso")
plt.ylabel("Posición")
plt.grid(True)
plt.show()
