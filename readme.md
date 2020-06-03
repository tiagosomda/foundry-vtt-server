# Foundry VTT Server

This is a repo with my personal set of instructions for creating a Foundry VTT server.  
I done this setup on my raspberry pi and also in Azure.  

### Setup Instructions
- manual instructions: [foundry-linux-server-setup.md](foundry-linux-server-setup.md)
- automated instructions: to be created

## Raspberry PI Setup and Learnings
The setup was very simple and it works really well.  
The only issue I had was with my home's internet upload speed.  
That caused very long loading times when switching between scenes in Foundry VTT.  
If I had a better upload speed connection, I would probably just use that instead.

## Azure Setup and Learnings
### Windows
I first did a setup with a Windows image.  
I picked a regular home version of windows and the experience was okay.  
I think the main issue was with azure throttling IO operations.

### Linux
After my raspberry pi setup, I decided to do the same, but with a linux VM in Azure.  
It worked really well!  

## I don't want to go through the trouble of doing all of this setup
There is a really good service called Forge VTT.  
It probably does a very similar setup, but you don't need to deal with any of it.  
- https://forge-vtt.com/

## About this repo:
My friend showed me something he did and that inspired me to create this repo with some instructions.

His project and reason for doing it were really cool!  
There are definitely more kids that would love to have something similar setup for them.  
Check it out :  
- website: https://thoughtarray.github.io/RowsterTowster/
- repo: https://github.com/thoughtarray/RowsterTowster
