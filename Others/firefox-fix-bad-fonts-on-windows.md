# Fix bad fonts rendering in Firefox on Windows

1. Open the config page by typing `about:config` in the address bar
1. Select `gfx.font_rendering.cleartype_params.rendering_mode` and change its value to `5`

## Legend

```
-1 (Firefox default)
0 (default)
1 (aliased)
2 (GDI Classic)
3 (GDI Natural)
4 (Natural)
5 (Natural Symmetric)
```
