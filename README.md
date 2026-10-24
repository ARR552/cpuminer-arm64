# cpuminer para Mac con chip Apple Silicon

Este repositorio no contiene código fuente. Su único contenido útil está en la sección **Releases**: un binario de [cpuminer-multi](https://github.com/tpruvot/cpuminer-multi) (`cpuminer`) compilado para macOS en procesadores Apple Silicon (M1, M2, M3, M4 y posteriores).

cpuminer-multi es un minero por CPU que soporta muchos algoritmos de proof-of-work, entre ellos sha256d (Bitcoin), scrypt (Litecoin) y x11 (Dash). Se usa en la asignatura de Blockchain para ver cómo funciona la minería proof-of-work desde un ordenador normal. No sirve para minar con beneficio: una CPU queda a años luz de un ASIC. Sirve para entender el protocolo stratum, el ajuste de dificultad y lo que ocurre entre un minero y un pool.

## Repositorio original

Este binario es una compilación sin cambios de **cpuminer-multi**, de tpruvot:

- Código fuente: https://github.com/tpruvot/cpuminer-multi
- Licencia: GPL v2

Todo el mérito es de sus autores. Este repositorio solo existe para que los alumnos no tengan que compilarlo.

## Descarga

1. Ve a la pestaña **Releases** de este repositorio.
2. Descarga el fichero `cpuminer` de la última versión.
3. Guárdalo en una carpeta, por ejemplo `~/cpuminer`.

## Primer arranque

macOS bloquea los ejecutables descargados de internet que no están firmados. Hay que quitar la marca de cuarentena y dar permiso de ejecución una sola vez:

```bash
xattr -d com.apple.quarantine ~/cpuminer/cpuminer
```

```bash
chmod +x ~/cpuminer/cpuminer
```

Comprueba que arranca:

```bash
~/cpuminer/cpuminer --version
```

## Uso

Prueba de rendimiento sin conectarse a ningún pool:

```bash
~/cpuminer/cpuminer --benchmark
```

Minar contra un pool con el protocolo stratum, sustituyendo la URL, el usuario y la contraseña por los que indique el profesor:

```bash
~/cpuminer/cpuminer -a sha256d -o stratum+tcp://POOL:PUERTO -u USUARIO -p CONTRASEÑA
```

Para otro algoritmo cambia `-a sha256d` por el que toque, por ejemplo `-a scrypt` o `-a x11`. Con `-t N` fijas el número de hilos; por defecto usa todos los núcleos. La lista completa de algoritmos y opciones:

```bash
~/cpuminer/cpuminer --help
```

Para parar, pulsa Ctrl+C.

## Compilación

El binario se ha compilado a partir del código fuente de [tpruvot/cpuminer-multi](https://github.com/tpruvot/cpuminer-multi), commit o versión `PENDIENTE`, en un Mac con Apple Silicon y las dependencias de Homebrew `automake`, `autoconf`, `libtool`, `pkg-config`, `curl`, `jansson`, `openssl` y `gmp`. No incluye modificaciones sobre el código original.

cpuminer-multi se distribuye bajo licencia GPL v2. El código fuente completo está en el repositorio original enlazado arriba.
