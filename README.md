I recently completed a week long Bixby Hackathon at 42 Silicon valley. My team managed to create  a music searching app that lets DJs find up songs for their genre and BPM using the Spotify API by just speaking to the phone. One of the hardest aspects of that project was trying to figure out how to correctly use OAuth so that Bixby could have permission to communicate to the Spotify API and get the JSON info from it. So I decided to create a blog post dedicated to teaching people how to apply OAuth their code. In this post, I'll provide example code (Which you'll download from Github) to apply your Client ID and Client Secret that you'll get from Spotify.

Before we begin, you'll need to download Bixby and get a Spotify account (both are free). 


<b>Step 1</b>: Go to the spotify developers page and log in. 


<b>Step 2</b>: Be sure you're looking at the Dashboard section of the site. The page should look something like this:

<img width="996" alt="1" src="https://user-images.githubusercontent.com/16840579/56539598-405efc80-651b-11e9-94f1-4995aa9b19ea.png">
Click on the "My New App" button to create a new app. I just named the app "testing_spotify". 

<b>Step 3</b>: At this point you should have page that looks like the picture below. We now have our Client ID and Client Secret.

<img width="1094" alt="2" src="https://user-images.githubusercontent.com/16840579/56539604-42c15680-651b-11e9-9767-f316e406e8c6.png">

<b>Step 4:</b> Go to the Bixby Developer center and sign in. You should see a button to click on the top left to create a team. You can name the team whatever you want, but be sure to use an original Namespace. You most likely won't have access to the name "test_out_spotify" since I already took it. So come up with something original.

<img width="467" alt="3" src="https://user-images.githubusercontent.com/16840579/56539608-4523b080-651b-11e9-8a73-498aea9c2907.png">

Click the "Register Capsule" button. I'm just going to add the word "example" to it.
NOTE: remember test_out_spotify.example (or whatever you call your project). This name will be used in your code later.

<img width="471" alt="4" src="https://user-images.githubusercontent.com/16840579/56539612-46ed7400-651b-11e9-89ca-12170e9d1799.png">

<b>Step 5:</b> Click on the Config & Secrets button. This is where you're going to take the Client ID and Client Secret from Spotify so that your app will have access to it. Click the +add button under Secrets. Use the name "id" and apply the Spotify Client ID. Then add the name "secret" and apply the Spotify Client Secret. Be sure to hit the "save and apply" button when you click add.

![5](https://user-images.githubusercontent.com/16840579/56539620-4b199180-651b-11e9-8b43-bfc3302560a7.png)

<b>Step 6:</b> So now that you have the full name of what you'll be using (Reminder that mine is: test_out_spotify.example), we need to go back to our Spotify Developer Dashboard and update our uri. To change the uri, click on the green "edit Settings" button.

<img width="853" alt="6" src="https://user-images.githubusercontent.com/16840579/56539623-4d7beb80-651b-11e9-90d2-1ff2a3ff6f71.png">

From there, we will need to add our link inside the Redirect URIs option. The format for what we have to type inside that option will look like this:
https://<your-capsule-id>.oauth.aibixby.com/auth/external/cb
  
Remember how my project is called test_out_spotify.example (see Step 4)? Where the "." is between test_out_spotify and example, replace it with a "-". replace <your-capsule-id> inside the above example with your project name. 
The URI should look something like this:
https://test_out_spotify-example.oauth.aibixby.com/auth/external/cb


<b>Step 7:</b> So now that we have all the credentials we need, lets apply them to actual code. I created a capsule that will access the Spotify API and display a track ID, a track name, and a track tempo.
Click this link to clone the example repo.

<img width="556" alt="7" src="https://user-images.githubusercontent.com/16840579/56539626-4f45af00-651b-11e9-9498-ce965da25d90.png">

<b>Step 8:</b> Drag the downloaded repo into bixby.


<b>Step 9:</b> Go to capsule.bxb and replace it with the name you chose from step 4.

<img width="801" alt="8" src="https://user-images.githubusercontent.com/16840579/56539628-5076dc00-651b-11e9-866e-fbd36d8115c4.png">

<b>Step 10:</b> Inside resources->base->player.endpoints.bxb, add your Client ID and Secret Client to your code from your Spotify account that you acquired in step 3.

<img width="903" alt="9" src="https://user-images.githubusercontent.com/16840579/56539632-52409f80-651b-11e9-9ca8-29bb7692d432.png">

</b>Step 11:</b> Compile the code and run it with the sentence "Get me 1 track at 160 beats per minute". The Bixby Simulator will prompt you to sign into Spotify. Your output should look like this once you successfully sign in.

<img width="759" alt="10" src="https://user-images.githubusercontent.com/16840579/56539636-5371cc80-651b-11e9-8c7e-8feaf8d19869.png">

You've now successfully used OAuth in Bixby to communicate with the Spotify API and display information pulled from the Spotify JSON file.
