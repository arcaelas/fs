<img alt="ARCAELAS LOGO" src="https://raw.githubusercontent.com/Arcaelas-Insiders-ES/dist/main/banner/dark.svg" />

# FileSystem

**FS** no posee funciones u expectativas distintas a los manejadores de archivos comunes, incluso esto se presenta como una versión **BETA** de este manejador y  ***Todos***  sus métodos son **Sícronos**.

Su implementación es sencilla:

```js
import { Directory, File } from 'arcaelas/fs'
const { Directory, File } = require("arcaelas/fs");
```


## Directory
> Conoceremos el módulo de Directory el cual administra las tareas orientadas al manejo de carpetas y algunas funciones de archivos.

---
### match(glob: string[], options: object) : string[]
> Con un patrón global o específicos, podríamos listar los archivos y directorios dentro de rutas específicas o genéricas.

```js
Directory.match("./*.js") // Al JS files in current directory
Directory.match("./**/*.js") // Al JS files in recursive directory.
```

---
### mkdir(path: string, options: [fs.MakeDirectoryOptions](https://nodejs.org/api/fs.html#fspromisesmkdirpath-options) ) : string[]
> Creación de directorios **Sync** con posibilidades recursivas.

```js
Directory.mkdir("./profiles/arcaelas/photos/")
fs.mkdir("./profiles/arcaelas/photos/", {
    recursive:true
})
```

---
### copy(globs: string[], target: string, options: object ) : object
> Copiar archivos y directorios de forma recursiva.

```js
Directory.copy("./profiles/**/photos/", "/backups/")
```

---
### move(globs: string[], target: string, options: object ) : object
> Mover archivos y directorios de forma recursiva.

```js
Directory.move("./profiles/**/photos/", "/backups/")
```

---
### rename(globs: string[], target: string, options: object ) : object
> Alias para **move()**.

```js
Directory.rename("./profiles/**/photos/", "/backups/")
```

---
### unlink(globs: string[], options: object ) : object
> Eliminar archivos y directorios de forma recursiva.

```js
Directory.unlink("./profiles/**/photos/")
Directory.unlink(["./profiles/**/photos/"])
```

## File
> El módulo de **File** administra funciones similares.

---
### unlink(glob: string[], options: object) : string[]
> Alias para **Directory.unlink**

---
### read(filename: string, options: object, cb?: function) : Buffer
> Leer archivos con un callback de forma sicrona.

```js
File.read("/config/database.json", "utf8", (err, data)=>{
    if(err) return;
    console.log( data );
})
```

---
### write(filename: string, options: object, cb?: function) : Buffer
> Escribir archivos con un callback de forma sicrona.

```js
File.write("/config/database.json", "{ \"username\":\"root\" }");
// or
File.write("/config/database.json", ()=>{
    return { username:"root" };
})
// or
File.write("/config/database.json", { username:"root" }, (err)=>{
    if(err) throw err;
    console.log("Saved");
})
```

<div style="text-align:center;margin-top:50px;">
<hr/>
<img src="https://raw.githubusercontent.com/Arcaelas-Insiders-ES/dist/main/footer/dark.svg" width="400px" style="margin:20px 0;">

> ¿Want to discuss any of my open source projects, or something else?Send me a direct message on [Instagram](https://instagram.com/arcaelas) or [Twitter](https://twitter.com/arcaelas).</br> If you already use these libraries and want to support us to continue development, you can sponsor us at [Github Sponsors](https://github.com/sponsors/arcaelas).
</div>