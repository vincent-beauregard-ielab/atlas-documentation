# V0 Specifications / components

## Use cases

### 0 main // Researcher access to environmental rasters

#### Description



#### Interface

* R Atlas

#### Expected bahaviour

* FIlter by spatial extent

### 1 // Insertion of rasters

#### Description



#### Interface



#### Expected bahaviour



## Components

### Storage Server

### Interface / API

## Data requirements

### Data sources



1. **Variables** Données climatique **Source** World clim **Interface** Package R, (autres ?) **Format** GeoTIFF **Intégrées JR** Oui
2. **Variables** Couverture sol, topographie (ruguosité?) **Source** Earth Env **Interface** Site web **Format** GeoTIFF **Intégrées JR** Oui
3. **Variables** Type de sol, couverture forestière, land cover
4. **Source** À définir **Interface** Site web **Format** GeoTIFF **Intégrées JR** Oui
5. **Variables** Scénarios climatique

* Land cover
* Environment variables
  * 3 layers
  * Precipit, t min, t max
  * Linked to original files
* Biovars
  * 19 layers
  * From dismo [(cran package source, ](https://cran.r-project.org/web/packages/dismo/dismo.pdf)[variables description)](https://www.worldclim.org/data/bioclim.html)
  * Linked to environmentals variables catacolg

####



