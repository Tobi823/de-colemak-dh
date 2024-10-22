# Colemak-DH DE

Today, KDE does not offer any Colemak-DH keyboard layouts for German users.
I adapted https://gitlab.com/jungganz/eurkey-colemak-mod-dh for my needs.

# Installation on Linux

Copy this to /usr/share/X11/xkb/rules/base.extras.xml 
```
        <variant>
          <configItem>
            <name>de-cmk-dh-ansi</name>
            <description>German (Colemak-DH, ANSI)</description>
          </configItem>
        </variant>
        <variant>
          <configItem>
            <name>de-cmk-dh-iso</name>
            <description>German (Colemak-DH, ISO)</description>
          </configItem>
        </variant>
```

(see _usr_share_X11_xkb_rules_base.extras.xml after line 157 for reference)

Copy this to /usr/share/X11/xkb/rules/evdev.extras.xml:
```
        <variant>
          <configItem>
            <name>de-cmk-dh-ansi</name>
            <description>German (Colemak-DH, ANSI)</description>
          </configItem>
        </variant>
        <variant>
          <configItem>
            <name>de-cmk-dh-iso</name>
            <description>German (Colemak-DH, ISO)</description>
          </configItem>
        </variant>
```

(see _usr_share_X11_xkb_rules_base.extras.xml after line 158 for reference)

Copy this to /usr/share/X11/xkb/symbols/de:
```
partial alphanumeric_keys modifier_keys 
xkb_symbols "de-cmk-dh-ansi"  {

        include "de(basic)"
        name[Group1] = "German (Colemak-DH, ANSI)";

        key <AD01> { [              q,                 Q,                   at,               Agrave ] };
        key <AD02> { [              w,                 W,               aacute,               Aacute ] };
        key <AD03> { [              f,                 F,                U0133,                U0132 ] };
        key <AD04> { [              p,                 P,               igrave,               Igrave ] };
        key <AD05> { [              b,                 B,               iacute,               Iacute ] };
        key <AD06> { [              j,                 J,               ugrave,               Ugrave ] };
        key <AD07> { [              l,                 L,               uacute,               Uacute ] };
        key <AD08> { [              u,                 U,           udiaeresis,           Udiaeresis ] };
        key <AD09> { [              y,                 Y,           ydiaeresis,           Ydiaeresis ] };
        key <AD10> { [     odiaeresis,        Odiaeresis,      dead_doublecute,        dead_belowdot ] };

        key <AC02> { [              r,                 R,                aring,                Aring ] };
        key <AC03> { [              s,                 S,               ssharp,                U1E9E ] };
        key <AC04> { [              t,                 T,                thorn,                Thorn ] };
        key <AC05> { [              g,                 G,               egrave,               Egrave ] };
        key <AC06> { [              m,                 M,               eacute,               Eacute ] };
        key <AC07> { [              n,                 N,               ntilde,               Ntilde ] };
        key <AC08> { [              e,                 E,           ediaeresis,           Ediaeresis ] };
        key <AC09> { [              i,                 I,           idiaeresis,           Idiaeresis ] };
        key <AC10> { [              o,                 O,           odiaeresis,           Odiaeresis ] };

        key <AB01> { [              x,                 X,                   ae,                   AE ] };
        key <AB02> { [              c,                 C,             ccedilla,             Ccedilla ] };
        key <AB03> { [              d,                 D,              dstroke,              Dstroke ] };
        key <AB04> { [              v,                 V,                   oe,                   OE ] };
        key <AB05> { [              z,                 Z,               yacute,               Yacute ] };
        key <AB06> { [              k,                 K,           dead_greek,           squareroot ] };
        key <AB07> { [              h,                 H,               oslash,               Oslash ] };
};

partial alphanumeric_keys modifier_keys 
xkb_symbols "de-cmk-dh-iso"  {
        
        include "de(de-cmk-dh-ansi)"
        name[Group1] = "German (Colemak-DH, ISO)";

        key <AB05> { [           less,           greater,                  bar,                dagger ] }; //change AB05 to LSGT
        key <LSGT> { [              z,                 Z,               yacute,               Yacute ] };
};
```

(see _usr_share_X11_xkb_symbols_de after line 39 for reference)

After that:
- `setxkbmap de -variant de-cmk-dh-ansi` or `setxkbmap de -variant de-cmk-dh-iso` https://gitlab.com/jungganz/eurkey-colemak-mod-dh/-/issues/3
- Logout or restart
- Go to the KDE settings Keyboard > Keyboard > Layouts > Add > German > Select one of the Colemak variants
- Maybe manually set `LayoutList=de` in ~/.config/kxkbrc https://discuss.kde.org/t/cannot-select-keyboard-layout/18313

Tested on KDE Wayland.

Feel free to open an issue if you know how to better include custom keyboard layouts with 
modifying system configuration files.
