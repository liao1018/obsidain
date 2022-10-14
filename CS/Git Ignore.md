#cs #git

# Ignore file
```gitignore
.obsidian/workspace
.obsidian/workspace.js
.obsidian/*.js
```

# Ignore folder
```gitignore
.obsidian/*/
.obsidian/plugins/
```

# Ignore except some files
```gitignore
.obsidian/*/
!.obsidian/plugins/
```

# Example
```gitignore
# To exclude workspace cache
.obsidian/workspace

# To exclude all folder except plugin
.obsidian/*/
!.obsidian/plugins/

# To exclude all .json except a few file
.obsidian/*.json
!.obsidian/community-plugins.json
!.obsidian/hotkeys.json
```
