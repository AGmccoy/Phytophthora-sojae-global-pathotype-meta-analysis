
#### *Phytophthora sojae* pathotype database and validation analyses
#### Austin McCoy
```

#### `r format(Sys.time(), '%B %d %Y')`

```

```{r, echo=FALSE}
#loading in the packages needed for readme
library(readxl)
library(DT)
```

### Pathotype database summary table
```{r, echo=FALSE}
pathotype_summary <- read_excel("pathotype surveys data.xlsx", 
    sheet = "surveys summary")
datatable(pathotype_summary, rownames = FALSE, class = 'cell-border stripe', filter="top", options = list(pageLength = 5, scrollX=T, editable=FALSE) )
```

****

#### hagis analyses to validate the data in the database is accurate to the manuscripts. Link to each validation analysis:

****

* [Laviolette & Athow 1981: Physiologic Races of *Phytophthora megasperma* f. sp. *glycinea* in Indiana, 1973-1979](./Laviolette-1981.html)
* [Buzzell, Haas, Crawford, and Vaartaja 1977: Soybean phytophthora rot in southwersten Ontario](./Buzzell-1977.html)
* [Schmitthenner, Hobe, and Bhat 1994: *Phytophthora sojae* Races in Ohio Over a 10-year Interval](./Schmitthenner-1994.html)
* [Anderson 1980: Incidence of Phytophthora root-rot of soybeans in Essex County, Ontario in 1979](./Anderson-1980.html)
* [Anderson & Buzzell 1992: Diversity and Frequency of Races of *Phytophthora megasperma* f. sp. *glycinea* in Soybean Fields in Essex County, Ontario, 1980-1989](./Anderson-1992.html)
* [Heritage, Castles & Pierpoint 1993: Surveys of Phytophthora root and stem rot in early maturing soybean crops in southern temperate regions of Australia from 1985 to 1988](./Heritage-1993.html)
* [Barreto, Stegman de Gurfinkel, & Fortugno 1993: Races of *Phytophthora sojae* in Argentina and Reaction of Soybean Cultivars](./Barreto-1995.html)
* [Yang, Ruff, Meng and Workneh 1996: Races of *Phytophthora sojae* in Iowa Soybean Fields](./Yang-and-Nelson-1996.html)
* [Abney, Melgar, Richards, Scott, Gorgan & Young 1997: New Races of *Phytophthora sojae* with *Rps*1-d Virulence](./Abney-1997.html)
* [Kaitany, Hart & Safir 2001: Virulence Composition of *Phytophthora sojae* in Michigan](./Kaitany-2001.html)
* [Jackson, Kirkpatrick & Rupe 2004: Races of *Phytophthora sojae* in Arkansas Soybean Fields and Their Effects on Commonly Grown Soybean Cultivars](./Jackson-2004.html)
* [Mohammadi, Alizadeh, Mirabolfathi, & Safaie 2007: Changes in Racial Composition of *Phytophthora sojae* in Iran Between 1998 and 2005](./Mohammadi-2007.html)
* [Nelson, Mallik, McEwen, & Christianson 2008: Pathotypes, Distribution, and Metalaxyl Sensitivity of *Phytophthora sojae* from North Dakota](./Nelson-2008.html)
* [Robertson, Cianzio, Cerra, & Pope 2009: Within-field Pathogenic Diversity of *Phytophthora sojae* in Commercial Soybean Fields In Iowa](./Robertson-2009.html)
* [Costamilan, Clebsch, Soares, Seixas, Godoy, & Dorrance 2013: Pathogenic diversity of *Phytophthora sojae* in pathotypes from Brazil](./Costamilan-2013.html)
* [Cui, Yin, Tang, Dong, Zheng, Zhang, & Wang 2010: Distribution, Pathotypes, and Metalaxyl Sensitivity of *Phytophthora sojae* from Heilongjiang and Fujian Provinces in China](./Cui-2010.html)
* [Xue, Marchand, Chen, Zhang, Cober, & Tenuta 2015: Races of *Phytophthora sojae* in Ontario, Canada, 2010-2012](./Xue-2015.html)
* [Agustina, Marcelo, Paula, & Silvina 2017: Primer reporte de *Phytopthora sojae* y sus patotipos afectando soja en Uruguay](./Agustina-2017.html)
* [Hebb, Bradley, Mideros, Telenko, Wise, & Dorrance 2021-Illinois data only: Pathotype Complexity and Genetic Characterization of *Phytophthora sojae* Populations in Illinois, Indiana, Kentucky, and Ohio](./Hebb-2021-Illinois-only.html)
* [McCoy, Noel, Jacobs, Clouse, & Chilvers 2021: *Phytophthora sojae* pathotype distribution and fungicide sensitivity in Michgian](./McCoy-2021.html)






