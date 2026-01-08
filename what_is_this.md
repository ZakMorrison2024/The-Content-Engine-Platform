``` 
Engine:
--------

This engine is a custom ECS-based 2D game engine and live-game framework, designed to support:

Multiple game modes and instance types
High-performance 2D rendering
AI-driven avatars and agents
Live interaction systems (chat, polls, donations)
Streaming and platform integrations
Modular UI and HUD systems

The architecture is split into Engine Level (reusable core systems) and Game Level (game-specific logic).

Design Principles

ECS-driven architecture
Data-oriented design
Behaviour composition over inheritance
Separation of engine and game logic
Performance-first rendering
Tooling as a first-class concern

```
=============================================================
```
Structure Overview:
-------------------

Engine Level:
    - Main:
        Point of call for Engine.
        Also intiation of profiling.
    Core:
        - Context:
            Context is the primary dict for systems to connect and draw information from.
        - Engine:
            Engine is the point of call for all game states.
            It loads renderer and draw primitives and loads the rest of the goddamn system.
        - Input:
            OpenGL Input initation system.
        - Window:
            OpenGL Window system.
        - Time:
            Runs GameTime.
    Render:
        - Renderer2D:
            Renderer2D is the rendering core of the system.
        - Draw2D:
            Draw2D is the draw primitives that are vectorised, batched and sent to Renderer2D
        - Text2D:
            Draw labels and text.
        - Bitmap:
            Config Glyph upload to GPU/Renderer.
        - Textures
    Math:
        - Vector2:
            Vector 2D. X,Y
        - Vector3:
            Vector 3D. X,Y,Z
        - Math Util:
            Random Math Function.
        - Clamp:
            Clamp Math Function.
        Geometry:
            - Shape2D:
                2D collision geometry wrapper.
            - Rect:
                2D rectangles. (Pos)(Size)
            - Circle:
                2D circles.
            - Line:
                2D lines.
            - Polygon:
                2D polygons.
            - ABB/OBB:
                - 2D advanced rect collsion helpers.
            ... - add triangle.!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
    Profiling:
        - Engine Profiling Managment:
            Shows engine metrics and profiling
        - Fps:
            Shows FPS (Frames Per Second).
    Systems:
        Debug_Systems:
            - Debug Viewer:
                In-Game debug system.
                Allows graphical viewing and ingame profiling.
                Add certian controls.
            - Debug System:
                Custom profiling system.
                Print reports.                       
            - Debug Renderer:
                Debug collisions and drawing.
            Tabs:
                - Metrics_tab:
                    In-game metrics profiling. 
                - Instance_tab:
                    In-game instance table.
                - Graph_tab:
                    In-game pretty metric graphs.
                - Engine_tab:
                    In-game Engine/Context viewer.
                - Inspector_tab:
                    In-game instance selector.
                - Controls_tab:
                    In-game controls and stress test.
        Assets:
            - Asset System:
                Loads assets groups to GPU.
            - Audio System:
                Load Audio to Memory.
            - Animator:
                Frame animator for visual assets.
                Works by taking length / y for auto-framing.
        Chat:
            - Chat System:
                Online Chat System
                Offline Chat System - debug
                Organises Chat data for games.
            - Donation System:
                Collects and organises donation data from chat system.
            - Poll System:
                Collects and organises poll data from chat system.
            - Semantics System:
                Collects and determines sematic value from chat system.
        Input:
            - Control System:
                Main Control layer. 
                Mouse
                Keys
                Joypad
        Monitization:
            - Wallet:
                Engine users purse.
        Network:
            - Network System:
                HTTP network orgainsor and connector.
        Progression:
            - Player Progression System:
                Engine level progression/loyalty system.
            - Save and Load System:
                Saves and loads data for user.
            - Viewer Progression System:
                Tracks viewers loyalty.
        Cleanup:
            - Engine Clean:
                 Cleans Engine.
            - Game Clean:
                Cleans Game enviroment.
        - Global Physics System:
                I have no idea, does next to nothing, supposed to facilitate global instance game physics.
    UI:
        - UI:
            UI is the user interface abstraction layer, this holds all the utilities for buttons, sliders, icons
        - Clouds:
            Draws background clouds.
        - Marquee Banner:
            Draw Marquee banner in menu card.
    Tools:
        - Auto Asset Manifest:
            auto manifests assets for asset system.
        - Generate_id:
            Auto ID chat users.
        - Pillow:
            Advanced image helper.
        - QR:
            generates dynamic QR codes.
        - Twitch:
            Twitch scraper.
        - Youtube:
            YouTube scraper.

Game Level:
    Instances:
        - Instance:
            Primary dynamic instance class
            Controls players, avatars, items, projectiles.
        Avatar:
            - Avatar Kernels:
                Numba Kernels for collisions.
            - AvatarBatch:
                Avatar movement and collisons.
            - Boid System:
                Wave forms.
            - Cosmetics Manager:
                Avatar cosmetics control.
            - Grid:
                Game Numba Grid.
            - Pathfinding:
                Primitive and simple pathfinding.
            - Pathing:
                Basic pathing movement.
            - Warmup: (depreciated) ??????????????????????????????????????????????
            Cosmetics:
            GOAP:
                - Actions:
                    Drives GOAP intents
                - Planner:
                    Plans GOAP intents
                - Set Intent:
                    Intents
                - World State:
                    World State connector
                Behaviours:
                    - Chase:
                        Chase intent
                    - Engage:
                        Engage intent
                    - Flee:
                        Flee intent
                    - Wander:
                        Wander intent
                    ... Make more dynamic intents
        Components:
            - Render Component:
                Draw control for instances
            Avatar Components:
                - Av Health Component:
                    Avatar Health set
                - Batch Component:
                    Avatar Batch component
                - Body Component:
                    Avatar body set
                - Boid Component:
                    Avatar wave movement control component
                - Collision Component:
                    Avatar Python Collision component
                - Cosmetic Component:
                    Avatar Cosmetic component
                - Drop Component:
                    Avatar Drops
                - GOAP Component:
                    Avatar AI intent component
                - Inventory Component:
                    Avatar inventory component
                - Message Component:
                    Avatar message/dialog control
                - Pathing Component:
                    Avatar Pathing component
                - Stats Component:
                    Avatar stats
            Item Components:
                - Consumable Component:
                    Consumable function
                - Item Component:
                    Item data component
                - WeaponStats Component:
                    Weapon data component
                - WorldItem Component:
                    World Pos and effect component
            NPC Components:
                - NPC_Movement Component:
                    NPC movement
                - NPC_POS Component:
                    NPC world Position
            Player Components:
                - Input Component:
                    Player Controls
                - Pick-Up Component:
                    Player pickup mechanic
                - Player_Movement Component:
                    Player movement
                - Player_POS Component:
                    Player position reference? - is this depreciated?
                - Stats Component:
                    Player stats
                ... Some may need deleting and others added
            Static Components:
                - Loot Component:
                    Loot mechanic
                - POS Component:
                    Position reference
                - Static_Health Component:
                    static item/object/instance health
        Projectiles:
            - Base Projectile:
                Projectile controls
            Components:
                - proj_render Component: (depreciated)
                - proj_stats Component:
                    Projectice stats
                Behaviours:
                    - Arch:
                        Arch behaviour
                    - Bounce:
                        Bounce behaviour
                    - Circular:
                        Circular movement behaviour
                    - Homing:
                        Homing on target behaviour
                    - Slash:
                        Slash behaviour
                    - Straight Line:
                        straight forward behaviour
                    - Wave:
                        wave mechanic behaviour
                    - ZigZag:
                        zigzag movement behaviour
    Physics: (depreciated?)
        - Base Physics:
            set physics ECS
        Components:
            - Acceleration:
                Acceleration behaviour
            - Collision:?????????????????????????????????????????????????
                Collsion behaviour
            - Gravity:
                Gravity behaviour
    Objects:
        - Director:
            Director profiles and orcastrates instance based games
        - Loot:
            Loot designates and scales loot drops
        - Narrator:
            Narrator helps world building in roleplaying
        - Reward:
            Reward decided loot and how it should be distrubuted
        - TTS:
            TTS helps viewers have a audiotry voice
    Scripts:
        Camera:
            - Camera Manager:
                Camera manager orchastrates multiple camera instances
            Camera Component:
                - Camera
                    Camera instance
        Dialog:
            - Dialog Manager:
                Orchastrates dialog movtives
            Dialog Components:
                ... Needs dialog controls
        Events:
            - Events Base:
                - Orchastrates events
           - Events System:
                Events system
            Events Components:
                - On Game Time:
                    On game timer event
                - On Turn:
                    On Turn event
        Controls?:
            ... (note this is the ECS creator element, not in files)
        Spawn:
            - Spawn System
                primary spawn system
            - Wave Spawn System
                wave spawn system
            ...
            Components:
                Behaviours:
                    - Spawn Behaviour:
                        types of spawning
                Types:
                    - Entity types:
                        types of avatars to spawn
                    - Get Pseudo Textures:
                        debug textures class
        Triggers:
            - Trigger:
                Triggers for game or instance events
            - Trigger System:
                Controls Triggers
            Trigger Components:
                - On Enter Area:
                    Trigger on area collision
                - On Health Below:
                    Trigger if health below threshold
                - On Timer:
                    Trigger if timer exhausted
    States:
        Creator:
            ... Create creator suite
        Games:
            GS (GAME SHOWS):
                - Genie:
                    - Guessing or wishing genie
                - Trivia:
                    Trivia game
            RP (ROLEPLAYING):
                - Doctor:
                    - CC is doctor, chat are patients
            Instance Based:
                - Survival:
                    Bullet Hell Like
                - DnV:
                    Dungeons and Dragons like
                - Viewwings:
                    Lemmings like where viewers can control their lemmings
            - End Screen:
                Donation and stats screen where viewers can purchase cosmetics or items or events.
        Login:
            - Login:
                Login to Oauth
            - Login Stings:
                Translations for Login
        Menu:

            - Menu Cards:
                Cards which display games and types
            - Menu Cards Strings:
                Translations for Menu Cards
            - Menu Content:
                idk
            - Menu Credits:
                Sphinixx staff credits and assets
            - Menu Engine Settings:
                Overal Engine settings
            - Menu Form:
                Feedback form
            - Menu Game Options:
                Options for individual games
            - Menu Game Options Strings:
                translations for game options
            - Menu Join:
                join for friends multiplayer
            - Menu Player Customisation:
                player cosmetics and picture
            - Menu Start:
                intial menu screen
            - Menu Start Strings:
                translations for menu screen
            - Menu User: (???)
        MISC:
            - Closescreen:???
            - Feedback:
                Feedback fourm
            - Lang:
                Select langauge
            - Lang Strings:
                Lang translations
            - Loading:
                Loading state - precompile physics and assets
            - Loading Strings:
                Loading translations
            - Pause:
                Pause viusuals
            - Splash:
                Sphinixx mono splash
        Shop:
            - Marketplace:
                where users can buy more games or assets
        Story:
            ... Impliment story elements for sphoinixx
    Visual:
        - HUD Base:
            HUD control
        HUD Components:
            Components: 
                - UI Component:
                    HUD display orchastrator
                - UI Renderer Component:
                    HUD Draw
                - UI Value Bind:
                    HUD bridge
            PREDEFINED:
                - Abiility CoolDown:
                    - cool down
                - Dialog_bar:
                    dialog visual rep
                - Dice:
                    Dice
                - HealthBar:
                    Health bar draw
                - Inventory Slot:
                    Inventory slot draw
                - MiniMap:
                    Minimap draw
                - Notification:
                    Notifcations - ie. donations
                - Options Button:
                    options ingame
                - Timer:
                    timer visual
                - UI Icon:
                    UI icons
    World:
        Maps:
            - Map Chunck:
                This helps the renderer draw the map by making one submission for all triagles.
            City Maps:
                - City Map:
                    generic city map
                - London Map:
                    London map
                - Carnival Map:
                    Carnival map
            Draft Maps:
                ... Maps user makes
            Saved Maps:
                ... finished user made maps
            Open Maps:
                - Map Random:
                    random land map
                - Map Tundra:
                    random snow map
                - Map Moon:
                    random moon map
                - Map Mars:
                    random mars map
                - Map Desert:
                    random desert map
                - Map LavaDonut:
                    random lavadonut
                - Map Islands:
                    random islands
                
Managers:
    - Avatar Manager:
        controls avatar textures
    - Chat SnapShot:
        controls avatar chat dialog
    - Game Management:
        finds avalible games
    - Get Instance Texture:
        helper to download profile pictures
    - Map Management:
        map finder
    - On Avatar Ready:
        helper class

Util: - these are dev tools
    - Asset Manifestor:
        create manafest for assets
    - Clean:
        clean project files
    - Make Bitmap Font:
        make fonts
    - Search:
        list project files and LoC
    - Credits:
        temp txt for credits of used assets
```
=============================================================
```
Marketing:
----------

Marketing:
----------

Target Audiences:
-----------------
- Small to mid-sized streamers (500–10k concurrent viewers)
  Streamers who want highly interactive content that differentiates their channel
  without relying on external third-party tools.

- Variety & experimental streamers
  Creators running trivia nights, roleplay streams, game shows, or audience-driven
  chaos formats.

- Indie and meme-driven communities
  Viewers who enjoy collective decision-making, chaos mods, Twitch Plays–style events,
  and emergent humour.

- Content creators seeking ownership
  Streamers who want a fully integrated, brandable interactive system rather than
  fragmented tools (bots, overlays, extensions).

- Interactive experience designers
  Developers, artists, and event hosts building chat-controlled games, charity events,
  audience participation shows, or experimental formats.

CTA:
----
Primary:
- "Turn your chat into the main character."

Secondary:
- "Build live games your audience controls."
- "Make your stream a playable world."
- "Chat votes, donates, spawns, sabotages — real-time chaos."
- "The engine for the next Twitch Plays phenomenon."

Launch CTA:
- "Go live in under 5 minutes with ready-made interactive game modes."

Predictions:
------------
- Early adoption by 20–50 small streamers running novelty and test streams.
- Emergence of viral clips driven by chat sabotage, coordination, and donation-triggered chaos.
- One or more weekly streamer formats built entirely around the platform.
- Gradual positioning as a go-to tool for interactive variety streaming and live audience games.
- Long-term potential to define a new category of streamer-driven interactive entertainment.
```

