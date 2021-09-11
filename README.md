# 210907_sP1

## mkgit

Realice un script con las siguientes funciones:

- `mkgit -d directorio [-t titulo]`
- `mkgit --help`

Se le pasará como argumento un directorio, en caso de no existir debe crearlo. En dicho directorio iniciará un nuevo repositorio git, creará un archivo README.md donde el título será el pasado en los argumentos o en caso de no haber sido pasado como un argumento el nombre del directorio.

- En caso de que el directorio exista y no esté vacío devolverá un código de error.
- En caso de que el directorio no exista y no se pueda crear deberá retornar otro código de error.
- En caso de no poder inicializar el repositorio o fallar el intento de commit también debe retornar un código de error correspondiente.
- Se debe proveer una ayuda la cual indique el modo de uso y los posibles códigos de error a ser retornados, está ayuda será accedida mediante la opción `--help` o al utilizar el comando de forma incorrecta.

El script debe poder ser ejecutado desde cualquier directorio del sistema de este modo.

## find .jpg

Renombrar dentro del directorio `~/wiki` todos los archivos regulares con extensión `.JPG` y `.jpeg` a `.jpg`.

```bash
# Encontrar los archivos objetivo
find ./wiki -name "*.jpeg" -o -name "*.JPG"
# Dividir el procedimiento en 2 partes, primero encontrar los archivos objetivo con find y luego realizar un loop
# para renombrarlos:
for imagen in $(find ./wiki -name "*.jpeg" -o -name "*.JPG"); do
    mv $imagen ${imagen%.*}.jpg
done
```

Una vez renombrado los archivos listar los que superen los 3MB y realice una copia de estos al directorio `~/img`.

```bash
mkdir ~/img &> /dev/null; find ./wiki/ -size +3M -exec cp {} ~/img \;
```

## Backup

Describa con argumentos como sería la implementación de un buen método para realizar un "backup" de:

1. Código fuente de una aplicación en desarrollo.

```md
Un repositorio de git con un remote en github, gitlab, u otro servidor puede ser un buen modo de mantener el código seguro.
```

2. Una aplicación en producción.

```md
En el caso de una aplicación en producción, el código fuente puede estar en un repositorio, mientras que los datos variables
deben ser respaldados a un servidor remoto de otro modo. Para eso rsync puede ser una buena solución ya que transfiere solo los archivos
que se modificaron y mantiene las propiedades.
Además sería buena práctica el tener un script que genere un backup de la base de datos en caso de que exista, también transfiriendolo a un sitio seguro.
```

3. El directorio home del usuario.

```md
Para este caso rsync con la opción, `-a`, ya que puede generar un directorio espejo de un modo muy eficiente.
```
