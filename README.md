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

part 2 : 
I made Hacker UI using pygame : 

import pygame
import random
import time
import sys

pygame.init()
WIDTH, HEIGHT = 900, 500
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("ARION :: PRO HACKER UI")

BLACK = (0, 0, 0)
GREEN = (0, 255, 0)
DARK_GREEN = (0, 150, 0)
RED = (255, 0, 0)

font_big = pygame.font.SysFont("consolas", 38)
font = pygame.font.SysFont("consolas", 24)
font_small = pygame.font.SysFont("consolas", 16)

clock = pygame.time.Clock()
class MatrixLine:
    def __init__(self):
        self.x = random.randint(0, WIDTH)
        self.y = random.randint(-HEIGHT, 0)
        self.speed = random.randint(2, 6)
        self.length = random.randint(5, 15)

    def draw(self):
        for i in range(self.length):
            char = random.choice("01#@$%")
            text = font_small.render(char, True, GREEN)
            screen.blit(text, (self.x, self.y - i * 15))
        self.y += self.speed
        if self.y > HEIGHT:
            self.y = random.randint(-100, 0)

matrix_lines = [MatrixLine() for _ in range(40)]
def draw_header():
    title = font_big.render(">>> ARION HACKER SYSTEM <<<", True, GREEN)
    screen.blit(title, (200, 20))

def draw_progress_bar(value):
    pygame.draw.rect(screen, DARK_GREEN, (50, HEIGHT - 60, 800, 20), 2)
    pygame.draw.rect(screen, GREEN, (52, HEIGHT - 58, int(7.96 * value), 16))

def glitch():
    for _ in range(5):
        x = random.randint(0, WIDTH)
        y = random.randint(0, HEIGHT)
        pygame.draw.line(screen, RED, (x, y), (x + 50, y), 1)

def typing(text, y):
    typed = ""
    for char in text:
        typed += char
        screen.fill(BLACK)
        draw_matrix()
        draw_header()
        draw_progress_bar(progress)
        draw_text(typed, y)
        glitch()
        pygame.display.update()
        time.sleep(0.03)

def draw_text(text, y):
    render = font.render(text, True, GREEN)
    screen.blit(render, (50, y))

def draw_matrix():
    for line in matrix_lines:
        line.draw()
def login_screen():
    typing("ENTER USERNAME: Your_name", 120)
    time.sleep(0.5)
    typing("ENTER PASSWORD: ********", 160)
    time.sleep(1)

def password_crack():
    y = 220
    for i in range(1, 101, 5):
        fake_pass = "".join(random.choice("ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789") for _ in range(8))
        screen.fill(BLACK)
        draw_matrix()
        draw_header()
        draw_text("CRACKING PASSWORD...", 120)
        draw_text(f"TRYING KEY: {fake_pass}", 160)
        draw_text(f"PROGRESS: {i}%", y)
        draw_progress_bar(i)
        glitch()
        pygame.display.update()
        time.sleep(0.15)

# ---------------- MAIN FLOW ----------------
lines = [
    "Initializing Neural Interface...",
    "Connecting to Secure Server...",
    "Scanning Open Ports...",
    "Injecting Control Protocol...",
    "Decrypting Secure Layers...",
    "Accessing Core Mainframe...",
    "SYSTEM OVERRIDE ENABLED",
]

progress = 0
y_pos = 100

# LOGIN
screen.fill(BLACK)
login_screen()

# PASSWORD CRACK
password_crack()
for line in lines:
    typing(line, y_pos)
    y_pos += 40
    progress += 100 // len(lines)
    time.sleep(0.5)
running = True
while running:
    screen.fill(BLACK)
    draw_matrix()
    draw_header()
    draw_progress_bar(100)

    final_text = font_big.render("ACCESS GRANTED :: WELCOME Your_Name", True, GREEN)
    screen.blit(final_text, (180, HEIGHT // 2 - 20))

    exit_text = font_small.render("Press X to Exit | your_name SYSTEM ONLINE", True, GREEN)
    screen.blit(exit_text, (330, HEIGHT // 2 + 30))

    glitch()

    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_x:
                running = False

    pygame.display.update()
    clock.tick(60)

pygame.quit()
sys.exit()
