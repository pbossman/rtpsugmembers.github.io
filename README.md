# How to add yourself to RTPSUGMembers
### Prerequisites: This guide assume Git and PowerShell are installed. An Image of yourself 400 by 400 pixels is used.
1. We will start by forking the RTPSUGMembers repository. From the RTPSUGMembers [repo](https://github.com/RTPSUGMembers/rtpsugmembers.github.io) Click the Fork button in the top right corner.
![Fork Click](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/Capture1.PNG)
2. After the page refreshes you should notice that instead of saying:

    ![Fork1](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/fork1.PNG)

    It should now say (with RTPSUGTest being your username):

    ![Fork2](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/fork2.PNG)

    If you arent already using github pages on your account you can preview this page by changing the repository name to match your username.
    - Go to Settings
    - Change the Repository name to "(Your UserName).github.io"
    
    ![Rename Repo](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/Capture2.png)
    
    You can now point your browser to "(Your UserName).github.io" to view the page.

    ### You have officially Forked a Repo!

3. Next we will clone the repository. Any directory on your local system should work but for our example we will use C:\repo
    - Click Clone or Download and copy the http:// address provided.
    ![Clone Repo](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/Capture3.png)
    - Open PowerShell

    ```powershell
    New-Item -Type Directory C:\repo
    Set-Location C:\repo
    git clone https://github.com/RTPSUGTest/rtpsugtest.github.io.git
    #Replace URL above with URL that you copied from Github
    Set-Location C:\repo\rtpsugtest.github.io\
    #Replace rtpsugtest.github.io with your repository name
    ```

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/console1.PNG)

    If successful it should look like the above console.
    
    We have now copied the repository from Github down to our local machine. We can make changes and then push them back up.

4. Next we will create a branch. Branches are used as a place to make changes that will not break your working code in Master.

    - From the PowerShell Console run:
    `git checkout -b AddMember'

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/console2.PNG)

5. Now lets add our content and information page for ourselves in the members section of the website.
    - From the PowerShell Console in your local git folder run:
    ```powershell
    copy-item .\_members\template.md .\_members\YourName.md
    notepad .\_members\YourName.md #Mac/Linux users can use VSCode or any other text editor.
    ```
    Make sure to change 'YourName.md' to your name or something unique and identifiable.

    - In notepad replace or remove all the relevant fields. Make sure to save when you are done.
    - The Image field will be a jpg that we will add in the next step make sure the name is unique, if you dont want to use your own image you can use sample.jpg, sample2.jpg, sample3.jpg, or sample4.jpg and skip the next step.

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/notepad1.PNG)

6. Adding our image. As mentioned above you can use one of the samples. If you use your own image:
    - Please only add images of yourself
    - Images should be *appropriate*
    - Make sure the image is reasonably sized (400x400)
    - Add the image to C:\repo\rtpsugtest.github.io\assets\images\members\

7. Now we will push our changes back into git hub.

    - Go back to the PowerShell console, if you closed the console you will need to navigate back to your local repository folder.

    ```powershell
    Set-Location C:\repo\rtpsugtest.github.io\
    #Replace rtpsugtest.github.io with your repository name
    ```
    - We need to check in all of our changes
    - Commit them to our local repository
    - Push them to the remote repository (Github)

    ```powershell
        git add .
        git commit -m "John Smith added himself as a member"
        git push -u origin AddMember
    ```
    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/console3.PNG)

8. Lets see what we did. We will start by pulling our changes into Master, so that we can see them on our Github Page.
    
    - Bring up your browser and go back to your repository https://github.com/RTPSUGTest/rtpsugtest.github.io as our example.
    - It will default to the Master Branch, we need to switch branches and check our changes. You can do this by clicking the button that says "Branch: master" and then clicking the AddMember branch that we created.

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/branch1.PNG)

    - Once you have switched branches you should see the message about the most recent commit you made. You can also click into the _members folder and see the file we added. Assuming everything is good we will move to the next step.

9. In order for our Github Page to update our changes need to be a part of the Master Branch. We will do that by creating a Pull Request. This Pulls our changes from 'AddMember' into 'Master'.

    - Click the 'Pull requests' tab toward the top, then select the green 'New pull request' button.

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/pull1.PNG)

    On the next page you will select what Repository and Branch you want to update or 'Pull' changes into and what Repository and Branch you want those changes to be 'Pulled' from.

    - For the base repository select the repository you created. This should be 'UserName/username.github.io' for our example it's RTPSUGTest/rtpsugtest.github.io.

    If you chose the right repository screen will simplify from allowing both a Repository(fork) and branch to just a branch for selection.

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/pull2.PNG)

    - You now want to select the two branches 'Master' as the base and 'AddMember' as the compare.

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/pull3.PNG)

    Now the screen will give you a comparison of what changes exist between the two branches. We should see only green and the file that we added with our information. If you added an Image that will appear as well.

    - If everything checks out you can click 'Create pull request' button.

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/pull4.PNG)

    - Feel free to add a comment on the next page and click 'Create pull request' button again.

    Now you will have the opportunity to review your pull request.
    If you were submitting a pull request against a repository that you dont have permission to, someone else would need to review and merge the changes.

    - Click 'Merge pull request'

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/pull4.PNG)

    - Click 'Confirm'
    - Click 'Delete branch' slightly to the right

    ![Console](https://github.com/RTPSUGMembers/rtpsugmembers.github.io/blob/master/assets/images/readme/pull4.PNG)

    Thats it you have now done a pull request against your master branch and merged it.

    - If you browse to your github page site it should update shortly https://username.github.io/ for our example https://rtpsugtest.github.io/





