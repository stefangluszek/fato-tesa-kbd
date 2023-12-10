# fato-o-tesa

## Introducion
This repository documents my attempt at building a custom mechianical keyboard. I have been been considering switching to a split ergonomical keyboard such as the [Ergodox](https://ergodox-ez.com/) for a while now.
I hestitated, mostly because I love my current Varmillo Mechianical keyboard and I was not sure if switching back and forth between the two would be a good idea. At the end I deciced it was more about learning the process of building a custom keyboard than actually using it. So I decided to build a custom keyboard from scratch.

The requirements I had were simple, a split mechanical keyboard with the base laout as close to the ISO layout as possible to make switching back and forth as painless as possible. Why ISO? Because I use a Swedish/Norwegian keyboard which uses the ISO layout.

## The layout
I used the [Keyboard Layout Editor](http://www.keyboard-layout-editor.com/) to create the layout. It's based on the ISO 60% preset, but includes the top row with a couple of functional keys. I will explain why I needed the top row later on when we get to the PCB design.

The raw layout can be foud [here](layouts/layout.kle).

![Layout](docs/assets/fat-o-tesa-layout.png)

## Plate and the PCB
I decided to go with the sandwich design, which means that the top plate, the PCB and the bottom plate will share the same outline. One could go with doing the design directly in KiCad, but I played a bit with it and found it to be a bit cumbersome, especially when designing curves and rounded corners. So I decided to make a CAD model be the base model of the keyboard. There are many CAD tools out there, but I like the [Onshape](https://cad.onshape.com/) best, as it is web basaed and works on all platforms, yes even Linux. It's also free if all your documents are public, which is fine for this project.

I used [Keebio Plate Generator](https://plate.keeb.io/) to generate the plate DXF file based on my KLE layout. I selected the MX Opening cutout type with 0.5mm cutout fillet radius. I've tested this cutout with a 3mm acrylic plate and one switch and it seems to work fine. I imporetd the DXF file into a Sketch in Onshape Part Studio, Fixed the imported sketch entity added the board edge cuts, 2.3mm mounting holes and fixtures for tenting with m5 bolts. The model is almost fully parametric, apart from the switch cutout fillets. I was considering writing an [Onshape FeatureScript](https://cad.onshape.com/FsDoc/) that would automatically place switch and stabilizers cutouts on the sketch according to a layout defined in the KLE format, but since importing the DXF file from Keebio worked prety well, I decided to leave it for now. The downside being of course that each switch cutout is it's own sketch entity so if you end up having to modify any part of it you would have to repeat the operation for *ALL* the switches! Which won't be fun. I also tried to keep to the standard MX switch Unit size of 19.05. All the defined parameters are increments of 1/8 * 19.05 mm. This should make designing the PCB in KiCad a bit easier, as I should be able to set the grid to 1/8 * 19.05 mm and have everything align nicely.

![Plate](docs/assets/top-plate-render.png)
