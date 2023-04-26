[[LINUX]]

# fc-cache  

after installing new fonts either:
- globally:
    - `/usr/cache/fonts/`
- locally:
    - `~/.local/share/fonts/`

.. you have to rebuild the font cache:
- `fc-cache -fv`
    -f     force rebuild
    -v     verbose

