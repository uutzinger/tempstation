# Contact Less Temperature Measurement Station

## Introduction and Purpose
1) To create an inexpeinsve measurement station measuring forhead temperature at a distance of 0.5 meter.  

2) To intergrate the measurement statition into a visions system that recognizes faces and reads temperature once the head is positioned inside the measurement erea.

## Sensor Design
Contactless Melexis IR thermal sensor.  

The thermal radiation is collected with a planoxcovex lens and projected on the the sensor. 

The sensors FOV will need to be optimized to match and collection angle of light which is determiend by the diameter of the lens and how far the sensor is mounted away from the lens. That distance is determined by how far away we want to object to be placed. Simple calculations using thin lens equation is below.

The sensor can be read with any microcontroller but also single board computer that has an I2C interface. The sensor operates at 3.3V.

## Optical Design

For improved radiation collection we can collect light with IR lenses. The peak emission wavelength for skin temperatre is 9.4 microns and is very low at 3 microns. Several lens materials are available for that wavelength range.

* Zinc Selenide (ZnSe):  0.6-15 micron
* Germanium (Ger): 1.7-16micron
* Silicon (SiO2): 0.25 – 3.4 micron

Plano convex lenses for CO2 laser machining have a diameter of 12 or 20mm.  
Aliexpress has 20mm diameter leases with focal lengths of 38 and 50mm.  
Edmund optics has plano convex lenses of 12mm diameter and 13, 20 and 25mm focal length.  

Thin Lens Euquation | 
--- |
![Thin Lens Equation](https://latex.codecogs.com/svg.latex?1/f&space;=&space;1/S_1&space;&plus;&space;1/S_2) 
![Thin Lens Magnification Equation](https://latex.codecogs.com/svg.latex?M&space;=&space;-&space;S_2&space;/&space;S_1)
![Lens Equation Picture](https://upload.wikimedia.org/wikipedia/commons/7/71/Lens3.svg)

If we design a system to image at 500mm (s1) and use 38mm focal length (f) the lens is mounted at 41mm (s2) from the sensor. If the lens has 20mm diameter and the sensor is mounted 41mm away from the lens, we need FOV of 27.4 degrees or more at the sensor ```atan(41/10)```.

With a ½ inch lens and a 13mm focal length, we mount the lens at 13.5mm and the FOV of the sensor needs to be at least 50 degrees.

### Distances of relevance:

The ear to ear distance  is 220-230mm, the eye pupil distance 63mm, comfortable reading of a book is at 250 (young person) and 400/500mm (old person).

At 500mm distance, the FOV to image the head width is 26 degrees. To measure temperature on a small spot on the forhead without an imaging lens, the sensor would need to have a very small FOV. For example a measurement spot of 50mm diameter at 500mm distance has a 5.5 degrees FOV. Therefore collecting light with an IR lens is more efficient.

In comparison, the IMX219 CSI camera has a 62 degrees horizontal and 49 degrees vertical FOV.

## Component Selection
### Thermal Sensor
**Melexis MLX90614ESF – XYZ**  
* X: A 5V, B 3V, D medical grade 0.1C
* Y: A single zone, C gradient compensated, 
* Z: A 90, C 35, F 10, H 12 , I 5, deg FOV  
Available options:  
AAA, ACC, ACF  
BAA, BCA, BCC, BCF ($32), BCI ($41)  
DAA ($20)  single zone , 90 deg  
DCA ($21)  gradient comp, 90 deg  
**DCC ($24)  gradient comp, 35 deg**  
DCH ($35)  gradient comp, 12 deg  
DCI ($56)  gradient comp, 5 deg  

* Received 4 x MLX90614ESF-DCC Medición de temperatura infrarroja sin contacto

**Melexis MLX90615SSG – DAA or DAG**
No data yet

### Lens

* Received 4 x WaveTopSign China PVD ZnSe Diameter 20mm, Focal Length 38.1mm For Co2 Laser Engraving Machine
