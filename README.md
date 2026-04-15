# Launch game in fullscreen for Linux
directions if having trouble opening game while fullscreen is active in linux

## Directions

 Install devilspie2 if not already installed
```
sudo apt install devilspie2
```
 Create config directory
```
mkdir -p ~/.config/devilspie2

# Create the main config file
cat > ~/.config/devilspie2/devilspie2.lua << 'EOF'
-- Load all .lua files in this directory
scripts = {
   "opengame.lua"
}
EOF
```
make borderless rule (make sure to replace "Game Name"
```
cat > ~/.config/devilspie2/opengame.lua << 'EOF'
-- Replace "Game Name" with the exact game name
if (string.find(get_application_name(), "Game Name") or 
    string.find(get_window_class(), "GN")) then
    -- Remove fullscreen state
    set_window_fullscreen(false)
    -- Set to borderless by maximizing without decorations
    maximize()
    -- Optional: set specific geometry (x, y, width, height)
    -- set_window_geometry(0, 0, 1920, 1080)
end
EOF
```

Then run
```
pkill devilspie2
devilspie2 &
```

Then launch game
