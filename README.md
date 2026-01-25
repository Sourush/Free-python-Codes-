# Free-python-Codes
part 1 : 
This python code look's illegal but its not : 
import pygame
import time
import random

pygame.init()
screen = pygame.display.set_mode((800, 400))
pygame.display.set_caption("ARION HACK SIMULATOR")

font = pygame.font.Font(None, 36)
green = (0, 255, 0)
black = (0, 0, 0)

lines = [
    "Initializing system...",
    "Connecting to server...",
    "Bypassing firewall...",
    "Accessing mainframe...",
    "Decrypting files...",
    "ACCESS GRANTED 🔥"
]

def draw_text(text, y):
    screen.fill(black)
    render = font.render(text, True, green)
    screen.blit(render, (50, y))
    pygame.display.update()

running = True
for line in lines:
    draw_text(line, 180)
    time.sleep(random.uniform(0.8, 1.5))

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

pygame.quit()
