# Development server

As per the development guidelines, all changes should be tested before pushing to production.

RonStation provides a development server allowing all maintainers to do just that. 

The server will let you test features as a player or an admin, and the server will let you select the version of the game you'd like to test out.

## Access the development server

* You will need to be a member of the RonStation organization on GitHub
* You will need to know basic knowledge of SSH (optional)

We cannot leave the development server open to the Internet. Therefore, we've opted to make the server only accessible with a VPN.
This means :

* The web server serving the game files
* The game server
* SSH

Are behind a VPN and cannot be accessed without it.

Once connected, you can join the development server on `dev.ronstation.space`.

To access the development server :

* Download our selected VPN : Tailscale. You can learn more about how Tailscale works [here](https://tailscale.com/blog/how-tailscale-works).
* Once installed, login to tailscale. Choose **sign in with GitHub** and select **Authorize Tailscale**.
* When reaching the **Select a Tailnet** page, choose **RonStation**.
* You have succesfully joined the RonStation VPN.

> [!NOTE]
> Should the procedure fail, a good idea is to close all tailscale tabs, clear cookies, and start again.

> [!IMPORTANT]
> Our tailscale instance is configured as such that all servers are unable to connect back to your computer.
> Maintainers can connect on specific port to the development server, but not the other way around.
> 
> Moreover, maintainers are only able to connect to the development server and cannot connect to other 
> maintainers. **Absolutely no exceptions will be made**.
> 
> You can verify this fact by asking a member of the Project Management Board for a copy of the configuration.

This is enough to connect your SS14 game to the development server.

> [!NOTE]
> The Tailscale client is pretty awesome, as it only routes the traffic that needs to be routed.  
> This means you could theorically keep the tailscale client running for as long as you want, even though you shouldn't.  
> But if you choose to do so, you shouldn't feel any performance issue or weird behaviour.  
> My recommendation would be to open Tailscale when you actually need it, and close it once you're done.  
> That way you can be sure that nothing odd or insecure happens.

### Connect to SSH

All maintainers are able to connect to the development server via SSH. This is particularly useful because the development server
does not use any CDN or watchdog.

Thankfully, the server comes with a script allowing maintainers to run the version of the game they'd like to test out.

### Scripts available

The main script you should use is `rebuild_server.sh`. It does the following : 
* It destroys the current instance of the server (while keeping the database)
* It rebuilds a whole new instance of the server with a set commit (you should edit the file to select which commit you'd like)
* It deploys the client release so that the game client can download it
* It unwraps the server and brings the database back into the copy
* It starts a fresh instance of the server

This process might seem overkill but it avoids all and any remnants of the previous build of the server.
Consider the build might take a good couple of minutes, so don't abuse of it.

### Fair-use policy

All maintainers are required to use the server for exactly what it was supposed to.
Nothing more.

Any violations of this policy will be considered as a demoteable offence.