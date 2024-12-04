# Joyce Chen and Katherine Li Final Project!

## Project planning: Design Doc

### Design Doc
https://docs.google.com/document/d/1waQ40CT8vVwmg2EtrsiP1IPtTGzJkQFuOkwuBFhcMmw/edit?usp=sharing

#### Introduction
- What motivates your project?

Food 🙂

#### Goal
- What do you intend to achieve with this project?

#### Inspiration/reference:
- You must have some form of reference material for your final project. Your reference may be a research paper, a blog post, some artwork, a video, another class at Penn, etc.  
- Include in your design doc links to and images of your reference material.

#### Specification:
- Outline the main features of your project.

#### Techniques:
- What are the main technical/algorithmic tools you’ll be using? Give an overview, citing specific papers/articles.

#### Design:
- How will your program fit together? Make a simple free-body diagram illustrating the pieces.

#### Timeline:
- Create a week-by-week set of milestones for each person in your group. Make sure you explicitly outline what each group member's duties will be.

Submit your Design doc as usual via pull request against this repository.
## Milestone 1: Implementation part 1 (due 11/13)

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

References:
- https://www.youtube.com/watch?v=BClgCh_w3lo
- Blast node: https://www.sidefx.com/docs/houdini/nodes/sop/blast.html
- How to make partitions different every iteration:
- https://www.reddit.com/r/Houdini/comments/1et5z2p/how_to_use_a_different_seed_for_every_iteration/
- Lot subdivision outer edges: https://www.sidefx.com/forum/xtopic/68602/?page=1#post-291672
  
<img width="696" alt="Screenshot 2024-11-14 at 12 05 31 AM" src="https://github.com/user-attachments/assets/863bdf38-0a0f-4b04-878c-267610cc7f6f">

## Milestone 2: 



## Milestone 3:


