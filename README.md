# Comprehensive Guide on How to Tunnel your ROMA Localhost Frontend to a Public URL

---
## Step 1: You'll need a VPS. 

You can get from contabo.com or PQ Hosting. Contabo is cheaper, you can get a vps for as low as $5 per month, but only accept card payments and require KYC. PQ hosting however accepts crypto payment and doesn't require KYC, but more expensive and less reliable. 

## Step 2: Install ROMA on your VPS with this guide

```
https://github.com/MikeMoulder/ROMA-VPS-Guide-With-UI-UX/tree/main
```
When you get to this end of the above guide, where you're about to restart Docker containers. Come back to this guide

## Step 3: 

Create a new screen

```
screen -S roma
```

## Step 4: 

After creating a new screen, start ROMA with 

```
cd
cd ROMA
cd docker
docker compose down
docker compose up -d
```

## Step 5: 
Check if there's any error in your installation. Run the command below 

```
docker compose logs -f
```

## Step 6: 

When you something similar to this image below. 

(img)

detach the current screen with CTRL+A, then D

## Step 7: 

create a new terminal with CTRL+SHIFT+C or or click the "+" button at the top right corner of your current terminal 

## Step 8: 

In the new terminal you created... 

Download and install Cloudfared with 
```
wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
sudo dpkg -i cloudflared-linux-amd64.deb
```

Optional: Very cloudfared installation with
```
cloudflared --version
```

## Step 9: 

Create a new screen with: 
```
screen -S frontend
```

## Step 10: 

After creating a new screen, run: 
```
cloudflared tunnel --url http://localhost:3000
```
Localhost:3000 being your frontend localhost. 

This command will give you a public url for testing that you can share with friends. 

You'll get a url that looks like the image below (if you're not seeing the url, adjust the size of your terminal by dragging the top with your mouse) 

Copy the url and save it (don't open yet) 

Then, detach the current screen with CTRL+A, then D 

## Step 11:

Create a new terminal. 

Then create a new screen with: 
```
screen -S backend
```

## Step 12: 

After that, run: 
```
cloudflared tunnel --url http://localhost:5000
```
You'll get a url just like you did in in step 10. Save that also, it's important. 

Then, detach the current screen with CTRL+A, then D

## Step 13: 

Before you open the link we created in step 10 which is your frontend public url (the url you can share to the public to access the ROMA you created in your VPS) 

Open to the ROMA folder in your root. When in the ROMA folder, locate and open the Frontend Folder. 

You'll see a file named "vite.config.ts" 

Open it. It should look like this when you open it: 

(img) 

before 'ngrok.io',

add this: 
```
'.trycloudflare.com',
```

## Step 14: 

You can open/visit the url you copied in step 10. You should be able to open ROMA on any device. 

Share with your close friends or complete stranger, but be wary of rate limiting.  

You can now close your vps, and start testing ROMA. 

Goodbye. 

If you run into any problems, message me on X:_hadeelen 








