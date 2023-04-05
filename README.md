# Pygame
Pygame supercars game


import pygame 
import os
os.chdir(os.path.dirname(os.path.abspath(file)))
pygame.init()
screen = pygame.display.set_mode((1100, 600))
color = ("#0F83D5")
screen.fill(color)
pygame.display.flip()


def button(screen, position, text):
    font = pygame.font.SysFont("Fantasy", 100)
    text_render = font.render(text, 1, (255, 0, 0))
    x, y, w , h = text_render.get_rect()
    x, y = position
    pygame.draw.line(screen, (150, 150, 150), (x, y), (x + w , y), 5)
    pygame.draw.line(screen, (150, 150, 150), (x, y - 2), (x, y + h), 5)
    pygame.draw.line(screen, (50, 50, 50), (x, y + h), (x + w , y + h), 5)
    pygame.draw.line(screen, (50, 50, 50), (x + w , y+h), [x + w , y], 5)
    pygame.draw.rect(screen, (100, 100, 100), (x, y, w , h))
    return screen.blit(text_render, (x, y))

def start():
    (width, height) = (1100, 600)
    screen = pygame. display. set_mode((width, height))
    pygame. display. flip()
def car():
    (width, height) = (300, 300)
    bg_img = pygame.image.load("car-png-16851.png")
    bg_img = pygame.transform.scale(bg_img,(width,height))
    while True:
        screen.fill(color)
        screen.blit(bg_img,(0,0))
def menu():
    """ This is the menu that waits you to click the s key to start """
b1 = button(screen, (300, 300), "Quit")
b2 = button(screen, (500, 300), "Start")
while True:
        for event in pygame.event.get():
            if (event.type == pygame.QUIT):
                pygame.quit()
            if event.type == pygame.KEYDOWN:
                if event.key == pygame.K_ESCAPE:
                    pygame.quit()
                key_to_start = event.key == pygame.K_s or event.key == pygame.K_RIGHT or event.key == pygame.K_UP
                if key_to_start:
                    start()
            if event.type == pygame.MOUSEBUTTONDOWN:
                if b1.collidepoint(pygame.mouse.get_pos()):
                    pygame.quit()
                elif b2 .collidepoint(pygame.mouse.get_pos()):
                    start()
pygame.display.update()
pygame.quit()
 
menu()
