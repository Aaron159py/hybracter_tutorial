# hybracter_tutorial

## Instalación de Hybracter
Es necesario crear un ambiente específico para Hybracter

```
conda create -n hybracterENV -c bioconda -c conda-forge  hybracter
```

```
conda activate hybracterENV
```

```
hybracter install
```



Cuando yo use hybracter con miniconda, faltaba una dependencia y se bugeaba a veces, por lo que reinstalarla servía en casos de errores al momento de ensamblar.

```
conda install -n hybracterENV -c bioconda porechop_abi
```


Además, había que exportar el path de dos maneras:
- Escribir esto en la screen en donde se va a realizar el ensamblaje.
- O escribir esa línea en el ~/.bash_profile y luego aplicar `source ~/.bash_profile` (esto final no es necesario si reinicio la terminal)
```
export PATH="$HOME/miniconda3/bin:$PATH"
```

---

## Uso de Hybracter
El csv debe contener las etiquetas de las lecturas. Se tiene un archivo con lecturas `illumina forward`, otras con `illumina reverse` y uno con `lecturas nanopore`.

La etiqueta va a ser el nombre que van a tener los archivos, carpetas y subcarpetas relacionadas al ensamblaje.

Como ejemplo, el csv para un ensamblaje híbrido debe tener este contenido:
`etiqueta,nanopore.fastq.gz,illumina_forward.fastq.gz,illumina_reverse.fastq.gz`

Se ejecuta el ensamblaje tanto con las lecturas brutas como con las procesadas
```
hybracter hybrid --auto -i lecturas_hy.csv -o output_lecturas_brutas_hy -t 10
```

```
hybracter hybrid --auto -i lecturas_brutas_hy.csv -o output_lecturas_brutas_hy -t 10
```
