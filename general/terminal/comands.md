# Unix Commands

El dispositivo de entrada port defecto **stdin** es el **teclado**, el dipositivo de salida estandard **stdout** es la pantalla

- 0 es para stdin
- 1 es para stdout
- 2 es para stderr (estandard error, archivo donde se escriben todos los errores)

<table>
<tr>
<th>Command</th>
<th>Used for</th>
</tr>
<tr>
<td>cd</td>
<td>Change directory</td>
</tr>
<tr>
<td>ls</td>
<td>List command used for showing the content of a directory.</td>
</tr>
<tr>
<td>rm</td>
<td>Remove command used for removing a file or a directory</td>
</tr>
<tr>
<td>mv</td>
<td>Used to move files or folders to another location</td>
</tr>
<tr>
<td>touch</td>
<td>Allows creating of a new empty file or to update a timestamp on a file</td>
</tr>
<tr>
<td>cp</td>
<td>Used to make a copy of a file or folder</td>
</tr>
<tr>
<td>mkdir</td>
<td>Make a new directory</td>
</tr>
<tr>
<td>pwd</td>
<td>Print work directory, shows the current location in the shell</td>
</tr>
<tr>
<td>cat</td>
<td>Allows reading or concatenation of a file</td>
</tr>
<tr>
<td>less</td>
<td>Displays the contents of a file one page at a time.</td>
</tr>
<tr>
<td>grep</td>
<td>Global regular expression, allows for searching contents of files or folders</td>
</tr>
<tr>
<td>cat</td>
<td>Concatenate files and print on the standard output</td>
</tr>
<tr>
<td>wc</td>
<td>Word count, print newline, word, and byte counts for each file</td>
</tr>
</table>

### Grep

Global Regular Expression Print, se usa para buscar en arvhivos y carpetas como tambien su contenido, tenga en cuenta que el comando es **case sensitive**

```bash
# Busqueda
# Suponga que tiene un archivo names.txt con nombres de personas no organizados y desea buscar por Sam

grep Sam names.txt
# Retorna lista de nombres que comienzan por Sam, ya que la S está en mayuscula

# Si desea que la búsqueda no sea case sensitive agregue la bandera (flag) -i

grep -i Sam names.txt

# Si desea una búsqueda exacta use la bandera -w

grep -w Sam names.txt

ls /bin | grep zip
```

### Pipes

Permite usar la salida de un comando como la entrada de otro

```bash
cat test.txt | wc -w
```

### Redireccionamiento

Con el redireccionamiento puede cambiar la entrada y/o salida estandard

- `<` se usa para stdin

```bash
# Cree un archivo input.txt con algo en su interior
cat < input.txt
```

- `>` se usa para stdout

```bash
ls -l > output.txt
```

- `2>` se usa para stderr
- `2>&1` imprime en stdout y en stderr

```bash
# La carpeta /bin/usr no existe
ls -l /bin/usr > error.txt
# ls: cannot access 'bin/usr/: No such fule or firectory

# Escribir stderr a un archivo
ls -l /bin/usr 2> error.txt

# Manejar el error
ls -l /bin/usr > error_output.txt 2>&1

```
