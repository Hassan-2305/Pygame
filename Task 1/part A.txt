import pygame
import random 
import time 

pygame.init()

screen = pygame.display.set_mode((800,600))

pygame.display.set_caption("click circle")
screen.fill((255,255,255))
pygame.display.update()

running = True
drawing = False
start_time = 0
click_position = (0,0)
circle_color =(0,0,0)

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.MOUSEBUTTONDOWN and event.button == 1:
            drawing = False
            start_time = time.time()
            click_position = pygame.mouse.get_pos()
            circle_color =(random.randint(0,255), random.randint(0,255), random.randint(0,255))
        elif event.type == pygame.KEYDOWN:
              if event.key == pygame.K_q:
                    screen.fill((255, 255, 255))
                    pygame.display.update()
        
        
        elif event.type == pygame.MOUSEBUTTONUP and event.button == 1:
                        drawing = True
                        duration = time.time() - start_time
                        radius = int(20+duration * 100)
                        pygame.draw.circle(screen,circle_color,click_position,radius)
                        pygame.display.update()

pygame.quit() 



            


            

        

