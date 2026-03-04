# omni_anim_people_isaacsim
Statement of the problem, In this repository, i am going to explain, how to work with animation of people in IsaacSim version 5.0.0, because onmiverse animation people extension is supported and worked, only in IsaacSim 4.2.0

Sources:
https://docs.isaacsim.omniverse.nvidia.com/4.2.0/features/warehouse_logistics/ext_omni_anim_people.html
https://www.youtube.com/watch?v=MG3uQwW3t1Q&t=256s
https://www.youtube.com/watch?v=OmXWyWGMaSY

1) Go to this web site, which supported for isaacsim 4.2.0. First of all, you need to install the extention from isaacsim, go to the windows -> extentions, and search onmi.anim.people and all anim.navi extensions. It should be installed and then, enable and autoload marked.

2) Create the ground plane, then create the mesh plane, on the left side of the interface go to transform and change the scale. This is reponsible for work zone of human actions. Also, if you don't see the mesh, which is usually is blue color. Go to the eye icon and show by the type button, here you need to activate the button NavMesh.

3) Go to the Window -> navigation -> NavMesh should to be chekcked. GO to NavMesh, there you can change the high and other values of this zone. 

4) To create the person (human), you need to go the Content in the button of the interface isaacsim. In the isaacsim forlder.
https://omniverse-content-production.s3-us-west-2.amazonaws.com/Assets/Isaac/5.0/Isaac/People/Characters/F_Business_02/ 
Around this path go. In order to open a person.

5) Bring the files of person, to the Stage (left side interface) to the World(default Prim).

6) Biped_Setup.usd 
https://omniverse-content-production.s3-us-west-2.amazonaws.com/Assets/Isaac/5.0/Isaac/People/Characters/
The same bring this file to the World.

7) <img width="1744" height="1005" alt="image" src="https://github.com/user-attachments/assets/57a35d2f-53d8-419a-8f64-ee6fd88eb20c" />
go to the extention menu, then search for the extention, which is named onmi.anim.people, and then open the folder, where is located.
Navigate to \omni\anim\people\scripts and locate the character_behavior.py file.

8) Expand each character on the stage menu and navigate until you find their SkelRoot. Example - /World/Characters/Character/male_adult_construction_01/ManRoot/male_adult_construction_01.

Select the SkelRoot of every character by holding down control and clicking on each SkelRoot. Next navigate to SkelRoot > Right Click > Add > Animation > Animation Graph and select the only available animation graph.

9) Select the SkelRoot of every character by holding down control and clicking on each SkelRoot. Select SkelRoot > Right Click > Add > Python Scripting to enable Python scripting.
<img width="2247" height="924" alt="image" src="https://github.com/user-attachments/assets/4a6530a0-438b-4e68-85b3-e92d6ed71a03" />

10) Go to the property window and in the Python Scripting property, select Add Asset and attach the character_behavior.py script.

11) Go to the VS Code, and change the code lines, some thing like that. There are you need to directly write the coordinates of goal point for human. Also, if don't know which cooridnates to write, you can create the frame and in order to trasform it and see the desired coordinates. 

if self.number_of_loop > 0:
            # Character go to original spot to form the loop
            originPos, originRot = Utils.get_character_transform(self.character)
            originAngle = Utils.convert_to_angle(originRot)
            self.commands.append(
                (None, ["GoTo", "2.37", "6.8", "0.0",  str(originAngle)])
            )
            self.commands.append(
                (None, ["GoTo", "2.83821", "-4.72656", "0.0",  str(originAngle)])
            )
            self.loop_commands = self.commands.copy()

        self.character.set_variable("Action", "None")
        carb.log_info("Initialize the character")
        return True
12) the main problem of new version isaacsim was that in windows menu, you don't see the extention icon, and you can't work with gui of this extention. So, this is solution to avoid this problem.



