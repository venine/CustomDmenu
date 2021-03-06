# CustomDmenu
Use Dmenu like your typical menu.

Clone this repo to efficiently integrate themes with i3wm by using this menu - https://www.github.com/venine/i3-colors

### Features
1. Can be made into a cascading menu.
2. Supports the adding of new commands.
3. Supports aliasing in the configuration. 
4. Seamless integration with i3-colors

### Usage
Let us first understand the structure. 
Now this can be recursive. You can imagine it as a tree.

![Structure](https://github.com/venine/CustomDmenu/blob/master/cdmenu.png?raw=true)
![Structure](https://github.com/venine/CustomDmenu/blob/master/cdmenu1eg.png?raw=true)

- `-c CATEGORY`				CATEGORY is the name of the category. It can be nested.
- `-c CATEGORY -m 'ALIAS::COMMAND'`	Alias and command in a category CATEGORY.
- `-t`					Themes installed using i3-colors. You can select and apply them spontaneously.
- `-k`					Processes generated by ps -e. The chosen one will be pkill-ed()
- `-a`					Show a menu containing all other menus. From this, you can open the other ROOT menus.

Examples
- `-c websites`						Open websites using firefox (if that is what you have set) from a menu
- `-c websites -m 'YouTube::${browser} youtube.com`       Open website using ${browser}(firefox in my case) <- Add this option but don't open the menu.

### Configuration
Run these commands or do it manually -
`mkdir ~/.config/CustomDmenu && cp config.yaml ~/.config/CustomDmenu`

How to use the config?
It is simple and intuitive.

I have included my setup. the `swapWorkspace` binary is included with i3-colors.

As you can see, this is a .yaml document, so it is easy to understand. You can nest categories all you want. Only in the case of `websites`, it will automatically *create two dmenus* for private and normal sessions with the same websites.

Under the `config` section, it is mandatory to define some aliases at least. Especially home. You have to also ignore the `aliasesReverseMapped` section because it is automatically made. 

This program also tries to obtain the *dmenu params automatically* from the *config of i3wm*. However, *if you define the params here, no params will be used from the file.*

You have to also set the path for i3-colors and i3config for the sake of convenience. If you have modularized your config after installing i3-colors, the default path is ~/.config/i3/user/default.i3.		

Also, aliases exist as ${ALIAS} as placeholders in areas where you want them to expand. 

### Requirements
1. Perl
2. Perl Modules - YAML::XS, Getopt::Std, Scalar::Util `sudo cpan YAML::XS Getopt::Std Scalar::Util`
3. i3 
4. i3-colors - if you want to use the -t flag with this program. 
5. dmenu - of course. 
