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






import pygame
import random

# Inicjalizacja Pygame
pygame.init()

# Ustawienia okna gry
WIDTH, HEIGHT = 600, 400
win = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Unikaj Przeszkód")

# Kolory
WHITE = (255, 255, 255)
RED = (255, 0, 0)

# Ustawienia gracza
player_width, player_height = 50, 50
player_x, player_y = WIDTH // 2 - player_width // 2, HEIGHT - player_height - 20
player_speed = 5

# Ustawienia przeszkód
obstacle_width, obstacle_height = 50, 50
obstacle_speed = 5
obstacle_frequency = 25  # co ile klatek pojawia się nowa przeszkoda
obstacles = []

# Licznik punktów
score = 0
font = pygame.font.SysFont("Arial", 30)

clock = pygame.time.Clock()

# Główna pętla gry
running = True
while running:
    clock.tick(30)
    
    # Obsługa zdarzeń
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Ruch gracza
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and player_x > 0:
        player_x -= player_speed
    if keys[pygame.K_RIGHT] and player_x < WIDTH - player_width:
        player_x += player_speed

    # Generowanie przeszkód
    if random.randint(1, obstacle_frequency) == 1:
        obstacle_x = random.randrange(0, WIDTH - obstacle_width)
        obstacle_y = -obstacle_height
        obstacles.append([obstacle_x, obstacle_y])

    # Ruch przeszkód i sprawdzenie kolizji
    for obstacle in obstacles:
        obstacle[1] += obstacle_speed
        if obstacle[1] > HEIGHT:
            obstacles.remove(obstacle)
            score += 1
        obstacle_rect = pygame.Rect(obstacle[0], obstacle[1], obstacle_width, obstacle_height)
        player_rect = pygame.Rect(player_x, player_y, player_width, player_height)
        if player_rect.colliderect(obstacle_rect):
            running = False

    # Rysowanie wszystkiego na ekranie
    win.fill(WHITE)
    pygame.draw.rect(win, RED, (player_x, player_y, player_width, player_height))
    for obstacle in obstacles:
        pygame.draw.rect(win, RED, (obstacle[0], obstacle[1], obstacle_width, obstacle_height))
    score_text = font.render("Punkty: " + str(score), True, RED)
    win.blit(score_text, (10, 10))

    pygame.display.update()

pygame.quit()





import pygame
import random

pygame.init()

szero, wys = 600, 400
win = pygame.display.set_mode((szero, wys))
pygame.display.set_caption("Unikaj Przeszkód")
cos = 0

bialy = (255, 255, 255)
czerw = (255, 0, 0)
inny = (0,255,0)
czorny = (0,0,0)

player_szer, player_wys = 45, 65
graczPoz_x, graczPoz_y = szero // 2 - player_szer // 2, wys - player_wys - 20
player_speed = 8

przeszkoda_szer, przeszkoda_wys= 50, 50
obstacle_speed = 5
obstacle_frequency = 25  # co ile pojawia się nowa przeszkoda
obstacles = []

wynik = 0
font = pygame.font.SysFont("Arial", 30)

clock = pygame.time.Clock()

running = True
while running:
    clock.tick(30)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and graczPoz_x > 0:
        graczPoz_x -= player_speed
    if keys[pygame.K_RIGHT] and graczPoz_x < szero - player_szer:
        graczPoz_x += player_speed

    if random.randint(1, obstacle_frequency) == 1:
        obstacle_x = random.randrange(0, szero - przeszkoda_szer)
        obstacle_y = -przeszkoda_wys
        obstacles.append([obstacle_x, obstacle_y])

    for obstacle in obstacles:
        obstacle[1] += obstacle_speed
        cos=cos+1
        if cos > 240:
            obstacle_speed = obstacle_speed +1
            cos = 0
        if obstacle[1] > wys:
            obstacles.remove(obstacle)
            wynik += 1
        obstacle_rect = pygame.Rect(obstacle[0], obstacle[1], przeszkoda_szer, przeszkoda_wys)
        player_ksztal = pygame.Rect(graczPoz_x, graczPoz_y, player_szer, player_wys)
        if player_ksztal.colliderect(obstacle_rect):
            running = False

    win.fill(bialy)
    pygame.draw.rect(win, inny, (graczPoz_x, graczPoz_y, player_szer, player_wys))
    for obstacle in obstacles:
        pygame.draw.rect(win, czerw, (obstacle[0], obstacle[1], przeszkoda_szer, przeszkoda_wys))
    wynik_wypis = font.render("Punkty: " + str(wynik), True, czorny)
    win.blit(wynik_wypis, (10, 10))

    pygame.display.update()

pygame.quit()





import pygame
import random

pygame.init()

szero, wys = 600, 400
win = pygame.display.set_mode((szero, wys))
pygame.display.set_caption("Unikaj Przeszkód")
cos = 0

bialy = (255, 255, 255)
czerw = (255, 0, 0)
inny = (0,255,0)
czorny = (0,0,0)

player_szer, player_wys = 45, 65
graczPoz_x, graczPoz_y = szero // 2 - player_szer // 2, wys - player_wys - 20
player_speed = 8

przeszkoda_szer, przeszkoda_wys= 50, 50
obstacle_speed = 5
obstacle_frequency = 25  # co ile pojawia się nowa przeszkoda
obstacles = []

wynik = 0
font = pygame.font.SysFont("Arial", 30)

clock = pygame.time.Clock()

running = True
while running:
    clock.tick(30)

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and graczPoz_x > 0:
        graczPoz_x -= player_speed
    if keys[pygame.K_RIGHT] and graczPoz_x < szero - player_szer:
        graczPoz_x += player_speed

    if random.randint(1, obstacle_frequency) == 1:
        obstacle_x = random.randrange(0, szero - przeszkoda_szer)
        obstacle_y = -przeszkoda_wys
        obstacles.append([obstacle_x, obstacle_y])

    for obstacle in obstacles:
        obstacle[1] += obstacle_speed
        cos=cos+1
        if cos > 240:
            obstacle_speed = obstacle_speed +1
            cos = 0
        if obstacle[1] > wys:
            obstacles.remove(obstacle)
            wynik += 1
        obstacle_rect = pygame.Rect(obstacle[0], obstacle[1], przeszkoda_szer, przeszkoda_wys)
        player_ksztal = pygame.Rect(graczPoz_x, graczPoz_y, player_szer, player_wys)
        if player_ksztal.colliderect(obstacle_rect): #tuuuu
            running = False

    win.fill(bialy)
    pygame.draw.rect(win, inny, (graczPoz_x, graczPoz_y, player_szer, player_wys))
    for obstacle in obstacles:
        pygame.draw.rect(win, czerw, (obstacle[0], obstacle[1], przeszkoda_szer, przeszkoda_wys))
    fps = clock.get_fps()
    if fps > 30:
        fpswy = font.render("FPS: " + str(int(fps)), True, inny)
    else:
        fpswy = font.render("FPS: " + str(int(fps)), True, czerw)
    win.blit(fpswy, (470, 10))
    wynik_wypis = font.render("Punkty: " + str(wynik), True, czorny)
    win.blit(wynik_wypis, (10, 10))

    pygame.display.update()

pygame.quit()
