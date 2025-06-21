# SHREE-GANESH-TUTORIAL-
Education for survive 
import pygame
import random

# Initialize game
pygame.init()
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Mini Shooting Game")
clock = pygame.time.Clock()

# Colors
WHITE = (255, 255, 255)
RED = (255, 0, 0)
BLUE = (0, 0, 255)
BLACK = (0, 0, 0)

# Player
player = pygame.Rect(375, 500, 50, 50)
player_speed = 5

# Bullets
bullets = []
bullet_speed = -10

# Enemies
enemies = []
enemy_speed = 2
enemy_spawn_delay = 30
enemy_timer = 0

# Game loop
running = True
while running:
    screen.fill(BLACK)
    pygame.time.delay(10)
    enemy_timer += 1

    # Events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Player movement
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and player.left > 0:
        player.x -= player_speed
    if keys[pygame.K_RIGHT] and player.right < WIDTH:
        player.x += player_speed
    if keys[pygame.K_SPACE]:
        bullets.append(pygame.Rect(player.centerx - 5, player.top, 10, 20))

    # Update bullets
    for bullet in bullets[:]:
        bullet.y += bullet_speed
        if bullet.bottom < 0:
            bullets.remove(bullet)

    # Spawn enemies
    if enemy_timer > enemy_spawn_delay:
        x_pos = random.randint(0, WIDTH - 40)
        enemies.append(pygame.Rect(x_pos, 0, 40, 40))
        enemy_timer = 0

    # Update enemies
    for enemy in enemies[:]:
        enemy.y += enemy_speed
        if enemy.top > HEIGHT:
            enemies.remove(enemy)

    # Bullet-enemy collision
    for bullet in bullets[:]:
        for enemy in enemies[:]:
            if bullet.colliderect(enemy):
                bullets.remove(bullet)
                enemies.remove(enemy)
                break

    # Draw
    pygame.draw.rect(screen, BLUE, player)
    for bullet in bullets:
        pygame.draw.rect(screen, WHITE, bullet)
    for enemy in enemies:
        pygame.draw.rect(screen, RED, enemy)

    pygame.display.update()
    clock.tick(60)

pygame.quit()import pygame
import random

# Initialize game
pygame.init()
WIDTH, HEIGHT = 800, 600
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Mini Shooting Game")
clock = pygame.time.Clock()

# Colors
WHITE = (255, 255, 255)
RED = (255, 0, 0)
BLUE = (0, 0, 255)
BLACK = (0, 0, 0)

# Player
player = pygame.Rect(375, 500, 50, 50)
player_speed = 5

# Bullets
bullets = []
bullet_speed = -10

# Enemies
enemies = []
enemy_speed = 2
enemy_spawn_delay = 30
enemy_timer = 0

# Game loop
running = True
while running:
    screen.fill(BLACK)
    pygame.time.delay(10)
    enemy_timer += 1

    # Events
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    # Player movement
    keys = pygame.key.get_pressed()
    if keys[pygame.K_LEFT] and player.left > 0:
        player.x -= player_speed
    if keys[pygame.K_RIGHT] and player.right < WIDTH:
        player.x += player_speed
    if keys[pygame.K_SPACE]:
        bullets.append(pygame.Rect(player.centerx - 5, player.top, 10, 20))

    # Update bullets
    for bullet in bullets[:]:
        bullet.y += bullet_speed
        if bullet.bottom < 0:
            bullets.remove(bullet)

    # Spawn enemies
    if enemy_timer > enemy_spawn_delay:
        x_pos = random.randint(0, WIDTH - 40)
        enemies.append(pygame.Rect(x_pos, 0, 40, 40))
        enemy_timer = 0

    # Update enemies
    for enemy in enemies[:]:
        enemy.y += enemy_speed
        if enemy.top > HEIGHT:
            enemies.remove(enemy)

    # Bullet-enemy collision
    for bullet in bullets[:]:
        for enemy in enemies[:]:
            if bullet.colliderect(enemy):
                bullets.remove(bullet)
                enemies.remove(enemy)
                break

    # Draw
    pygame.draw.rect(screen, BLUE, player)
    for bullet in bullets:
        pygame.draw.rect(screen, WHITE, bullet)
    for enemy in enemies:
        pygame.draw.rect(screen, RED, enemy)

    pygame.display.update()
    clock.tick(60)

pygame.quit()
