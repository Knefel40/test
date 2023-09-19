zmienna = 10
print(zmienna)
print(type(zmienna))
print(print.__doc__)
#komentarz jednoliniowy

"""
komentarz wieloliniowy
taki o tego benc
"""
print(zmienna == 20)
logiczna = True #wartosc logiczna z wielkiej litery
reszta = 10%6
czescCalkowita = 10//6 #czesc calkowita z dzielenia

#wczytywanie z klawiatury
slowo = input("Podaj slowo ")
print("wpisano "+slowo)
print(slowo[2]) #wpisuje od 2 znaku (czyli cos = s)
print(slowo[-2]) #wpisuje od końca numeracja od -1
print(slowo[2:5]) #poczatek przedzialu wchodzi ostatnie nie wchodzi (tu 5 znak)
print(slowo[:5]) #od poczatku do 5 znaku
print(slowo[5:]) #od 5 do konca
print(slowo[5::2]) #co który znak
print(slowo[::-1]) #slowo od tylu

zmienna = int(input("podaj liczbe "))

if zmienna<0:
    print(zmienna,"ujemna") #wciecia bardzo istotne
elif zmienna > 0:
    print(zmienna,"dodatnia")
else:
    print(zmienna,"jest zerem")

for litera in slowo:
    print(litera, end="*", flush=True)
print()
for i in range(10):
    print(i, end=", ") #od 0 do 9
print()
for i in range(2,10):
    print(i, end=", ") #od 2 do 9

print()
for i in range(-5,10,3):
    print(i, end=", ")

print()
for i in range(10,-10,-2):
    print(i, end=", ")


#wszystkie liczby dwucyfrowe dodatnie parzyste

print()
for i in range(10,100,2):
    print(i, end=", ")


print()
liczba = int(input("podaj zero "))
while liczba != 0:
    liczba = int(input("Podaj jednak zero "))

print()
import random
liczba = random.randint(1,100) #poczatek i koniec wchodza
print(liczba)
