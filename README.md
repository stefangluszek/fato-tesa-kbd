# fato-o-tesa

## Introducion
This repository documents my attempt at building a custom mechianical keyboard. I have been been considering switching to a split ergonomical keyboard such as the [Ergodox](https://ergodox-ez.com/) for a while now.
I hestitated, mostly because I love my current Varmillo Mechianical keyboard and I was not sure if switching back and forth between the two would be a good idea. At the end I deciced it was more about learning the process of building a custom keyboard than actually using it. So I decided to design and build my own custom mechanical keyboard.

The requirements I had were simple, a split mechanical keyboard with the base laout as close to the ISO layout as possible to make switching back and forth as painless as possible. Why ISO? Because I use a Swedish/Norwegian keyboard which uses the ISO layout.

## The layout
I used the [Keyboard Layout Editor](http://www.keyboard-layout-editor.com/) to create the layout. It's based on the ISO 60% preset, but includes the top row with a couple of functional keys. I will explain why I needed the top row later on when we get to the PCB design.

The raw layout can be foud [here](layouts/layout.kle).

![Layout](docs/assets/fat-o-tesa-layout.png)

## Plate and the PCB
I decided to go with the sandwich design, which means that the top plate, the PCB and the bottom plate will share the same outline.
The top and the bottom plates I can cut out of 3mm acrylic with the laser cutter. I could also manufacture the PCB myself, but the PCB CNC machine at the MakersLink is not ready for general use so I've decided to design the PCB in KiCAD and order it from [JLCPCB](https://jlcpcb.com/), which seems to be pretty affordable (~20USD with shipping). Because the PCB will be manufactured by a third party I've decided to base the entire design on the PCB, as I won't be able to easily modify that, and later export the PCB layout and imoprt into [Onshape](https://cad.onshape.com) for the plates design.

In KiCAD I set the grid to 1/8 * 19.05mm and layoed out all the switches on the PCB. One have to be extremly precise when placing the switches and make sure you use all the components using the "Move with reference" option, to make sure all swtiches are perfectly aligned.
Once I was happy with the placement of the switches on the PCB, I expoerted the keycaps layout to a DXF file and imported it into Onshape. In Onshape I added some constraints to makes sure, the switches were perfectly aligned. If you miss anytihg by a even as little as 0.01mm the constraints will give you an error and you will have to go back to KiCAD and fix it. Yes, I've learned that the hard way. Once I have the keycaps outlines in Onshape, I started to place the switch cutouts. After testing different cutout options on a 3mm acrylic, I've decided to use 13.8mm x 13.8mm clasic MX cutouts with no fillets and no slots for opening the switches. These cutouts resulted in the snuggest fit of the OUTEMU switches to a 3mm acrylic plate. At this point I had a KiCAD PCB design, PCB and plate CAD models in Onshape.

Link to the Onshape document: [fat-o-tesa-v1](https://cad.onshape.com/documents/4cd495c87c7dda10663811d2/w/b5d95b47f52db33ad3f41531/e/3e70d648d0571f67e1f8d256?renderMode=0&uiState=657f0b6864fd316c9ab080da)

![Top Plate](docs/assets/top-plate-render.png)

![PCB](docs/assets/pcb-render.png)

I exported the PCB outline from Onshape and imported it as Edge cuts into KiCAD. After wiring everything up the PCB design is ready for manufacturing.

![PCB](docs/assets/pcb-kicad.png)

I will wait for all the components to arrive to confirm the footprint dimensions before I order the PCBs from JLCPCB. I also need to add cutouts for the stabilizers, but I haven't received them yet, so I am not sure what the dimensions are.

