<div align="center">
</div>

<h1 align="center">Pekora/Project X Fixed Source code</h1>
<p align="center">Pekora was a roblox revival that targeted the 2017-2021 era of roblox.</p>
<p align="center">I do not own the rights to Pekora, as Supra (🐀) and Chloe (⚠️) owned it before it shutdown in late 2025 and became Korone which shutdown earlier this year (2026). LOL!</p>
<p align="center">This source code was originally leaked by Tooble, and recovered as I had it saved to my Hard Drive.</p>
<p align="center">This is completely safe, but I do not recommend re-hosting this unless you know what your doing and know a thing or two about the ECS codebase.</p>
<p align="center">js use some better shit this SUCKS ASS.</p>
<div align="center">
    
## Prerequistes 
</div>

- Windows 10
- Knowledge
- Time
- A Domain which is 10 Characters long (for example, "roblox.com")
- <a href="https://nodejs.org/dist/v18.16.1/node-v18.16.1-x64.msi">Node.js</a>, *to run the renderer/build panel*
- <a href="https://sbp.enterprisedb.com/getfile.jsp?fileid=1258627">PostgreSQL</a>, *for the database*
- <a href="https://builds.dotnet.microsoft.com/dotnet/Sdk/6.0.412/dotnet-sdk-6.0.412-win-x64.exe">.NET 6.0</a>, *to run the website*
- <a href="https://go.dev/dl/go1.20.6.windows-amd64.msi">Go</a>, *for asset validation*
- <a href="https://github.com/redis-windows/redis-windows/releases/download/8.6.2/Redis-8.6.2-Windows-x64-cygwin-with-Service.zip">Redis Server</a> *important*



## Note
imo this source is not the best, so I suggest making your own, or using a better source.

Pekora is Skidded ECS.

# Setup

1. Create a PG user, DB, and create a file called `"config.json"` in `services/api`. Put this in it (replacing the DB, User, and Pass with your credentials):

    ```json
    {
        "knex": {
            "client": "pg",
            "connection": {
                "host": "127.0.0.1",
                "user": "postgres",
                "password": "postgres",
                "database": "db_name_here"
            }
        }
    }
    ```

2. Install nodejs, go (lang), and dotnet 6. Go into the `services/api` directory in a terminal, run:

    ```bash
    npm i
    npx knex migrate:latest
    ```

3. Go into the `services/Roblox/Roblox.Website` folder and rename `appsettings.example.json` to `appsettings.json`. Put in your DB info and any other configurable things. Also make sure to edit the "Directories" stuff (change `/home/my_username/source-code/` to the exact path of the unzipped source code, i.e. the path this README file is in).

4. Go into the `services/Roblox/Roblox.Website` folder in a terminal, and run:

    ```bash
    dotnet run
    ```

    If everything is successful, you should be able to visit the site at `http://localhost:5000/`.

5. Start up the admin service by opening a new terminal, going into the `services/admin` folder, and running:

    ```bash
    npm i
    npm run dev
    ```

6. Open `services/2016-roblox-main/docs/get-started.md` and follow the guide for setting up 2016-roblox (this is the frontend). You should change the:

    ```
    https://{0}.roblox.com{1}
    ```

    API format to:

    ```
    http://localhost:5000/apisite/{0}{1}
    ```

7. Register an account, then copy your user id and replace the `"12"` in `"OwnerUserId"` (inside appsettings) with your user id. `ctrl+c` the `dotnet run` command to close it, then run it again to start the site back up. You should now be able to go to:

    ```
    http://localhost:5000/admin/
    ```

    for admin stuff.

8. In order to upload things, you will have to start up the "asset validation service". You can do this by going into `services/AssetValidationServiceV2` in a terminal and running:

    ```bash
    go run main.go
    ```

Note that the `game-server` program will probably need a lot of edits to actually work as a game service and/or render service.

This will be improved soon dw
