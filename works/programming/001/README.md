# Domino Simulation

#### 2024-02-25

Today, my dad and I created a domino simulation with [pymunk](https://www.pymunk.org/en/latest/).

We used [ChatGPT](https://chat.openai.com/) to debug it.


### Video Demo

<video src="https://creative-seohee.github.io/works/programming/001/video/domino.mp4" width="400px" controls>
</video>


### Code

#### Python

```python
import pymunk
import pymunk.pygame_util
import pygame
from pygame.locals import *
import sys

# Pygame Initialization
pygame.init()
width, height = 600, 600
screen = pygame.display.set_mode((width, height))
clock = pygame.time.Clock()
draw_options = pymunk.pygame_util.DrawOptions(screen)

# Pymunk Phsyics Space Creation
space = pymunk.Space()
space.gravity = (0, 981)  # gravity
space.iterations = 50


# Make dominos
def make_domino(space, index):
    domino_body = pymunk.Body(mass=1, moment=10)
    domino_body.position = (50 + index * 80, height - 60)
    domino_shape = pymunk.Poly.create_box(domino_body, size=(20, 100))
    domino_body.elasticity = 1
    domino_shape.friction = 1  # add friction to dominoes
    space.add(domino_body, domino_shape)
    return domino_body

for i in range(10):
    domino_body = make_domino(space, i)
    if i == 0:
        first_domino = domino_body

# Solid ground
ground = pymunk.Body(body_type=pymunk.Body.STATIC)
ground.position = (0, 0)
ground_shape = pymunk.Segment(ground, (0, height - 5), (width, height - 5), 5)
ground_shape.elasticity = 1
ground_shape.friction = 1  # add friction to ground
space.add(ground, ground_shape)


# Pushing the domino to the side
first_domino.apply_impulse_at_local_point((100, 0))

# Looping the game
running = True
while running:
    for event in pygame.event.get():
        if event.type == QUIT:
            running = False

    screen.fill((255, 255, 255))
    space.debug_draw(draw_options)

    space.step(1 / 80)
    pygame.display.flip()
    clock.tick(50)
```
