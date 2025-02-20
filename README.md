import pygame
import random
pygame.init()


class brick:
        def __init__(self,xpos, ypos):
            self.xpos = xpos
            self.ypos = ypos
            self.color = (random.randrange(100, 250),random.randrange(100, 250),random.randrange(100, 250))
            self.isDead = False
        def draw(self):
            if not self.isDead:
                pygame.draw.rect(screen, self.color,(self.xpos, self.ypos, 100, 50))

        def collide(self, ball_x, ball_y):
            if not self.isDead:
                if(ball_x + ball_size > self.xpos and
                   ball_x < self.xpos + 100 and
                   ball_y + ball_size > self.ypos and
                   ball_y < self.ypos + 50):
                   self.isDead = True
                   return true
            return False
    
# Open a new window, caption it "Pong"
screen = pygame.display.set_mode((700,500))
pygame.display.set_caption("Pong")

# heres the varaible that runs our game loop
doExit = False

# The clock will be used to control how fast the screen updates
clock = pygame.time.Clock()

#variables to hold paddle position
        #these go above game loop
p1x = 20
p1y = 440



p1Score = 0

#ball variable
bx = 350 #xposition
by = 250 #yposition
bVx = 5 #x velocity (horizontal spped)
bVy = 5 #y velocity (vertical spped)


b1 = brick(50, 50) #create a brick(you need to do this 8 more times)
b2 = brick(50, 150)
b3 = brick(250, 50)
b4 = brick(150, 300)
b5 = brick(250, 150)
b6 = brick(150, 200)
b7 = brick(50, 250)
b8 = brick(250, 250)
b9 = brick(150, 100)
while not doExit: #GAME LOOP-----------------------------------
    
    
    clock.tick(60)
    
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            doExit = True
    #-game logic------------
    keys = pygame.key.get_pressed()
    if keys[pygame.K_a]:
        p1x-=5
      
        
    if keys[pygame.K_d]:
        p1x+=5
    #ball movement
    bx += bVx
    by += bVy

#reflect ball off side walls of screen
    if bx < 0 or bx > 700:
        bVx *= -1

    if by < 0 or by > 500:
        bVy *= -1
        
    if bx < p1x + 100 and by + 20 > p1y and by + 20 < p1y + 20:
        bVx *= -1
        bVy *= -1

    #call the collision function 9 times
        
        if b1.collide(bVx, bVy):
            bvy *= -1
        if b2.collide(bVx, bVy):
            bvy *= -1
        if b3.collide(bVx, bVy):
            bvy *= -1
        if b4.collide(bVx, bVy):
            bvy *= -1
        if b5.collide(bVx, bVy):
            bvy *= -1
        if b6.collide(bVx, bVy):
            bvy *= -1
        if b7.collide(bVx, bVy):
            bvy *= -1
        if b8.collide(bVx, bVy):
            bvy *= -1
        if b9.collide(bVx, bVy):
            bvy *= -1
    #render section----------------------------
    
    screen.fill((0,0,0)) #wipe screen black
#reflect ball off side walls of screen, change score
   
    b1.draw()
    b2.draw()
    b3.draw()
    b4.draw()
    b5.draw()
    b6.draw()
    b7.draw()
    b8.draw()
    b9.draw()
    #draw a rectangle
    pygame.draw.rect(screen, (255,200,255), (p1x, p1y, 100, 20))
    pygame.draw.circle(screen,(85,255,255), (bx,by), 20)
    
    #update the screen
    pygame.display.flip()

 




pygame.quit()#when game is done 
        
        
    




        
