# mscgen_js
*Turns text into sequence charts.*

- Uses the [mscgen][1] mini language. 
- Supports a [simplified subset of mscgen][5] for lazy bastards.
- [Demo here][2]

## Sample
This sequence chart ...

![a sample sequence chart, rendered as png](wikum/readme.png)

was made with this *mscgen* source:
``` mscgen
msc {
  a [ label="Entity A", textbgcolor="red", textcolor="white" ],
  b [ label="Entity B", textbgcolor="yellow" ],
  c [ label="Entity C", textbgcolor="blue", textcolor="yellow" ];

  a->b [ label = "ab()" ] ;
  b->c [ label = "bc(TRUE)"];
  c=>>c [ label = "process(1)" ];
  b<<=c [ label = "callback()", arcskip="1"];
  |||;
  ---  [ label = "If more to run", ID="*" ];
  a->a [ label = "next()"];
  a=>c [ label = "ac1()"];
  b<<c [ label = "cb(true)", textbgcolor="lime"];
  b->b [ label = "stalled(...)"];
  a<<b [ label = "ab() = FALSE", textcolor="red", linecolor="red"], 
  c note c [ label="Just a note ...", linecolor="green", 
            textcolor="green", textbgcolor="lime" ];
}
```

## mscgen_js and the mscgen standard
mscgen_js was made to go both ways:

- Accept all valid [mscgen][1] programs and render them correctly. 
- Have all valid mscgen programs accepted by mscgen_js accepted and rendered
  correctly by mscgen.

Moreover [ms genny][5], the simplified subset, translates to mscgen with the 
flip of a switch.

If you find proof to the contrary on any of this [tell us][6].


## Building mscgen_js yourself

See [build.md][7]

## License
This software is free software [licensed under GPLv3][3]. This means (a.o.) you _can_ use
it as part of other free software, but _not_ as part of non free software.

mscgen_js is built on various libraries, each of which have their own license (incidentally all
MIT style). In order of significance: [pegjs][12], [codemirror][13], [canvg][16], [requirejs], [jQuery][14], [amdefine]. 
Icons courtesy of Dmitry Baranovskiy [license][15].

It uses [mocha], [jshint] and [plato] to maintain some modicum of verifiable code quality and 
[make] for a build system.

## Thanks
- [Mike McTernan][1] for creating the wonderful mscgen standard, the accompanying c implementation and for 
  releasing both to the public domain (the last one under a [GPLv2][18] license to be precise).
- [David Majda][8] for cooking and maintaining the fantastic and lightning fast [PEG.js][9] parser generator.
- [Marijn Haverbeke][10] for the snazzy [CodeMirror][11] editor component.
- Gabe Lerner for the [canvg][17] library, which makes converting vector graphics to rasters like a walk in the park. 

[1]: http://www.mcternan.me.uk/mscgen
[2]: http://sverweij.github.io/mscgen_js
[3]: wikum/license.mscgen_js.md
[5]: wikum/msgenny.md
[6]: https://github.com/sverweij/mscgen_js/issues?milestone=2&state=open
[7]: wikum/build.md
[8]: http://majda.cz/en/
[9]: http://pegjs.majda.cz/
[10]: http://marijnhaverbeke.nl
[11]: http://codemirror.net
[12]: wikum/license.pegjs.md
[13]: wikum/license.codemirror.md
[14]: wikum/license.jquery.md
[15]: wikum/license.icons.md
[16]: wikum/license.canvg.md
[17]: http://code.google.com/p/canvg/
[18]: http://code.google.com/p/mscgen/source/browse/trunk/COPYING
