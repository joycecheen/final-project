# Joyce Chen and Katherine Li Final Project!

## Project planning: Design Doc

### Design Doc
https://docs.google.com/document/d/1waQ40CT8vVwmg2EtrsiP1IPtTGzJkQFuOkwuBFhcMmw/edit?usp=sharing

#### Introduction
- What motivates your project?

Food 🙂

#### Goal
- Develop a procedural generator in Houdini that creates 3D bento boxes with randomized layouts and food items.

#### Inspiration/reference:
![image](https://github.com/user-attachments/assets/415a4965-8016-48a6-8cc8-d39ceb2ff2a2)
![image](https://github.com/user-attachments/assets/92466a5b-820e-42c3-87ad-dbe3ccc4d4e2)


#### Specification:
A generator that creates randomized layouts for bento boxes, with ability to specify number of compartments, etc.
Procedural models of food items such as rice, vegetables, sushi, fruits, and garnishes.
Variability in food arrangement and bento box to give each bento box a unique appearance.

#### Design:
<img width="373" alt="Screenshot 2024-12-04 at 10 16 04 AM" src="https://github.com/user-attachments/assets/8fbeb1fd-ca80-427d-8e6e-2157cbc2aaa1">

## Milestone 1:

We first started by following the box stacking workflow from the buildings homework

https://github.com/user-attachments/assets/b372a8b8-b69d-4759-af01-740604cf8738

We then made our procedurally generated partitions using the Lot Subdivision node. We had a lot of issues with getting only the inside edges (partitions) to show up, but we ended up figuring it out by creating a bounding box-ish around the border to group the outside points, converted them into edges, and used group combine to only select the inner edges.

From before it was working fully:

https://github.com/user-attachments/assets/ebdb3f25-51f9-419a-b597-80a5afe1be00

Then we started inserting our food assets as basic boxes into the partitions. We sorted the partition areas and placed the rice in the biggest and the salad in the smallest. We are still in the process of placing our sashimi and roll assets, which we plan to do by modifying the building homework.

https://github.com/user-attachments/assets/0f904178-50c0-40ca-99ab-3f107c803773

Some things we want to fix in future milestones:
- Add handles on the sides
- Bevel the bottom
- Bigger bento = more partitions
- Fix divisions visible on sides
- Height of partitions not scaling with bento height
- Additional customizations(no rice/no sushi/etc.)

Enjoy us struggling ft. the world's biggest monitor:

https://github.com/user-attachments/assets/bb231604-093b-4d5a-9fcd-270ecc0513c4
  
<img width="696" alt="Screenshot 2024-11-14 at 12 05 31 AM" src="https://github.com/user-attachments/assets/863bdf38-0a0f-4b04-878c-267610cc7f6f">

## Milestone 2: 

### Creating Rice
Used scatter node to create points, and attribute randomize to randomize the normals, and then copy to points to place individual rice grains.
![Screen Recording 2024-12-04 at 9 45 58 AM](https://github.com/user-attachments/assets/d253cd2f-09e4-41c1-aa6e-1170a681614b)


### Filling Largest and Smallest Partitions
Filled largest partition with rice, and smallest partition with soup using mountain node.
![image](https://github.com/user-attachments/assets/9f31bf19-cdc7-4c7e-adba-255e05560e3b)

Placing the sushi rolls and sashimi:
- Lots of trial and error with trying to place the roll and sashimi, but we ended up using the Lot Subdivision node again to divide each partition, and then we separated these divisions into their own primitives and iterated through them with a for each loop. Within the loop we used a matchSize node to match either the roll or the sashimi to the size of the division. We randomized which roll or sashimi was placed within the switch node


## Milestone 3:

### Final Models of Sushi and Sashimi
All modeled within Houdini. Reused rice logic and used Vellum Cloth Solver node for the seaweed to wrap around sashimi.
![Screen Recording 2024-12-04 at 10 08 06 AM](https://github.com/user-attachments/assets/18138a1a-762a-4f91-b010-4f5f135467e2)

![Screenshot 2024-12-04 at 9 53 58 AM](https://github.com/user-attachments/assets/50a353f3-97ec-422f-8e6e-abecca3e4614)
![Screenshot 2024-12-04 at 9 54 09 AM](https://github.com/user-attachments/assets/8cd7b1b6-bd80-4f85-b0cc-0bb726070649)
![Screenshot 2024-12-04 at 9 54 15 AM](https://github.com/user-attachments/assets/233e67f5-7d8f-446f-9f53-1d9b01d1199a)
![Screenshot 2024-12-04 at 9 54 24 AM](https://github.com/user-attachments/assets/e3fdecd3-6da3-441d-b12e-8789f431337a)
![Screenshot 2024-12-04 at 9 54 27 AM](https://github.com/user-attachments/assets/e91941fd-6566-4a6f-b4f9-ac1da74dd9fe)
![Screenshot 2024-12-04 at 9 54 31 AM](https://github.com/user-attachments/assets/b249cc0e-1a88-473e-8cda-c3ec2a15a1ea)


### Random Coloring of Bento
Used attribute wrangle node to write a function defining color set, generating a single random index and setting points to that color index. 
![Screenshot 2024-12-04 at 10 10 01 AM](https://github.com/user-attachments/assets/b84121b9-d5aa-484a-88c0-8a9382e2e14c)

### Additional Random Toppings
Created toppings for soup and rice. For soup toppings, used a grid to scatter five kinds of toppings at random angles. For rice toppings, created three different toppings to place in center of rice randomly.
![Screenshot 2024-12-04 at 10 10 32 AM](https://github.com/user-attachments/assets/c2a50ebe-8f4e-42ca-b2c7-bea60c00e244)
![Screenshot 2024-12-04 at 10 10 54 AM](https://github.com/user-attachments/assets/35f82acb-f196-48b4-8d7e-319ad60f25e5)
![Screenshot 2024-12-04 at 10 11 09 AM](https://github.com/user-attachments/assets/84734077-068e-4e70-b55d-45ea137c4112)


Optimizations:
- Thanks to the critique, we realized the inside of our box shape from before didn’t have any faces because of how we were extruding, so we changed the logic so that the box has thickness
- Added outer box and handles and beveled the bottom to match our reference images better
- Our previous logic for rice was slowing down our file considerably, so we changed it so that we were only generating rice on the top face of the rice box and created a white box directly under so any gaps between rice pieces would still appear white
- Changed the logic so that the partitions to get the faces that we put the food geometry on are now made from the boolean of bottom face and the inner partitions so they’re exactly the same
- The density of the rice scales with the dimensions of the bento box so that it doesn’t become too sparse when the box is larger
- Rotated each sashimi piece so that its longest edge aligned with the longest edge of the sashimi box

We then prepared for our final output by adding a camera and lighting (area light, ambient light, and sky light) to match our reference images as closely as possible. 


Finally, we rendered our final images using Mantra!

References:
- https://www.youtube.com/watch?v=BClgCh_w3lo
- Blast node: https://www.sidefx.com/docs/houdini/nodes/sop/blast.html
- How to make partitions different every iteration:
- https://www.reddit.com/r/Houdini/comments/1et5z2p/how_to_use_a_different_seed_for_every_iteration/
- Lot subdivision outer edges: https://www.sidefx.com/forum/xtopic/68602/?page=1#post-291672

- https://www.youtube.com/watch?v=ewXiWafJ4PE
- https://www.youtube.com/watch?v=sO-mDdJBaVI
- https://www.sidefx.com/forum/topic/75649/?page=1#post-323614
- https://www.youtube.com/watch?v=HVFcjxk71Yo&t=49s

## Final Renders:
![untitled0001](https://github.com/user-attachments/assets/a3d129d0-20dd-48cc-b946-7e281c5f53a3)
![untitled30001](https://github.com/user-attachments/assets/9509e899-8ea1-4465-adec-a657af545ec3)
![untitled20001](https://github.com/user-attachments/assets/52dd16c6-e237-40dd-8149-46d736ab82ff)
![untitled50001](https://github.com/user-attachments/assets/d7c80140-0990-45a2-89da-790dc964f89d)


## Closing Thoughts:

Overall, we think the project went well! There was a lot of back and forth where we were trying different ways to implement parts, especially like when we were trying to get the inner edges of the lot subdivision to show up for the partitions, but that just meant we got to familiarize ourselves with more of Houdini’s functionalities! Shoutout Simon Houdini.

Did you accomplish your goals? Did you have to pivot?
- Accomplished our goal of a bento box generator
- Although we wanted our final product to be an animation originally, we struggled with figuring out what exactly to animate, so we chose to render stills instead, but we're still happy with this output!
- Things we could add in future: textures, more user control over bento box customization (choose which sushi goes where, etc.)



