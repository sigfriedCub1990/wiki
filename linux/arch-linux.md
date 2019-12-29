# Arch Linux

## Install custom fonts

All fonts live inside `/usr/share/fonts`, this **fonts** are available to all users, to add new **fonts** only to the current user and avoid _sudoing_ do as follow:

* ```bash
  # In your user folder
  ~> mkdir -p /.local/share/fonts
  ```

* ```bash
  # Move the TTF files inside the newly created folder
  ~> cp *.ttf ~/.local/share/fonts
  ```

* ```bash
  # Refresh the system fonts cache with
  ~> fc-cache
  ~> fc-list | grep `font-name` # To check if the fonts is really installed
  ```



