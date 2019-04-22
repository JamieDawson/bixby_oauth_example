I recently completed a week long Bixby Hackathon at 42 Silicon valley. My team managed to create  a music searching app that lets DJs find up songs for their genre and BPM using the Spotify API by just speaking to the phone. One of the hardest aspects of that project was trying to figure out how to correctly use OAuth so that Bixby could have permission to communicate to the Spotify API and get the JSON info from it. So I decided to create a blog post dedicated to teaching people how to apply OAuth their code. In this post, I'll provide example code (Which you'll download from Github) to apply your Client ID and Client Secret that you'll get from Spotify.

Before we begin, you'll need to download Bixby and get a Spotify account (both are free). 


<b>Step 1</b>: Go to the spotify developers page and log in. 


Step 2: Be sure you're looking at the Dashboard section of the site. The page should look something like this:
Click on the "My New App" button to create a new app. I just named the app "testing_spotify". 


Step 3: At this point you should have page that looks like the picture below. We now have our Client ID and Client Secret.


Step 4: Go to the Bixby Developer center and sign in. You should see a button to click on the top left to create a team. You can name the team whatever you want, but be sure to use an original Namespace. You most likely won't have access to the name "test_out_spotify" since I already took it. So come up with something original. 
Click the "Register Capsule" button. I'm just going to add the word "example" to it.
NOTE: remember test_out_spotify.example (or whatever you call your project). This name will be used in your code later.


Step 5: Click on the Config & Secrets button. This is where you're going to take the Client ID and Client Secret from Spotify so that your app will have access to it. Click the +add button under Secrets. Use the name "id" and apply the Spotify Client ID. Then add the name "secret" and apply the Spotify Client Secret. Be sure to hit the "save and apply" button when you click add.


Step 6: So now that you have the full name of what you'll be using (Reminder that mine is: test_out_spotify.example), we need to go back to our Spotify Developer Dashboard and update our uri. To change the uri, click on the green "edit Settings" button.
From there, we will need to add our link inside the Redirect URIs option. The format for what we have to type inside that option will look like this:
https://<your-capsule-id>.oauth.aibixby.com/auth/external/cb
Remember how my project is called test_out_spotify.example (see Step 4)? Where the "." is between test_out_spotify and example, replace it with a "-". replace <your-capsule-id> inside the above example with your project name. 
The URI should look something like this:
https://test_out_spotify-example.oauth.aibixby.com/auth/external/cb


Step 7: So now that we have all the credentials we need, lets apply them to actual code. I created a capsule that will access the Spotify API and display a track ID, a track name, and a track tempo.
Click this link to clone the example repo.


Step 8: Drag the downloaded repo into bixby.


Step 9: Go to capsule.bxb and replace it with the name you chose from step 4.


Step 10: Inside resources->base->player.endpoints.bxb, add your Client ID and Secret Client to your code from your Spotify account that you acquired in step 3.


Step 11: Compile the code and run it with the sentence "Get me 1 track at 160 beats per minute". The Bixby Simulator will prompt you to sign into Spotify. Your output should look like this once you successfully sign in.
You've now successfully used OAuth in Bixby to communicate with the Spotify API and display information pulled from the Spotify JSON file.
