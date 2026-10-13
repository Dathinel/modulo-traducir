<p align="center">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://raw.githubusercontent.com/Dathinel/rodaje/main/assets/marca/rodaje.svg" alt="Logotipo de Rodaje" width="104"></a>
</p>

<h1 align="center">modulo-traducir</h1>

<p align="center">
  Módulo de IA opcional para <a href="https://github.com/Dathinel/rodaje">Rodaje</a>: traduce una pista de subtítulos a otro idioma conservando los tiempos, con Qwen3-4B-Instruct-2507 en local. Todo corre en tu equipo, sin conexión.
</p>

<p align="center">
  <a href="#licencia"><img src="https://img.shields.io/badge/c%C3%B3digo-GPLv3-E8833A?style=flat-square&labelColor=1D1D1D" alt="Código GPLv3"></a>
  <a href="https://github.com/Dathinel/modulo-traducir/releases/latest"><img src="https://img.shields.io/github/v/release/Dathinel/modulo-traducir?style=flat-square&labelColor=1D1D1D&color=E8833A&label=versi%C3%B3n" alt="Última versión"></a>
  <img src="https://img.shields.io/badge/contenido-1_funci%C3%B3n_%C2%B7_1_modelo-E8833A?style=flat-square&labelColor=1D1D1D" alt="Contenido: 1 función · 1 modelo">
  <img src="https://img.shields.io/badge/formato-.paquete-E8833A?style=flat-square&labelColor=1D1D1D" alt="Formato .paquete">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://img.shields.io/badge/para-Rodaje-E8833A?style=flat-square&labelColor=1D1D1D" alt="Para Rodaje"></a>
</p>

| Función | Qué hace |
|---|---|
| `traducir` | Traducir subtítulos conservando ids y tiempos |

Corre en: Vulkan (GPU) o CPU. Motor: llama.cpp vía LLamaSharp 0.27.0 (MIT); va autocontenido porque LLamaSharp no admite Native AOT. Rodaje lo abre como un proceso aparte y le habla por una tubería con nombre ([protocolo de módulos](https://github.com/Dathinel/rodaje/blob/main/docs/protocolo-modulos.md)); lo que devuelve es una propuesta que se aplica como un paso del historial (Ctrl+Z la deshace).

## Modelos (2,3 GB)

El `.paquete` no trae los modelos: Rodaje los baja después de instalar el módulo, comprueba su SHA-256 y los deja en `modelos\` dentro de la carpeta del módulo. Si la descarga se corta, sigue desde donde quedó.

| Id | Tamaño | Licencia | De dónde sale |
|---|---|---|---|
| `qwen3-4b-instruct-2507-q4km` | 2,3 GB | Apache-2.0 | Hugging Face `unsloth/Qwen3-4B-Instruct-2507-GGUF` @ `a06e946b` |

## Instalar en Rodaje

En Rodaje, Complementos → Instalar lo baja, comprueba la firma del catálogo y el hash, lo instala y baja sus modelos. A mano: descarga `modulo-traducir-<versión>.paquete` de las [releases](https://github.com/Dathinel/modulo-traducir/releases) y usa «Instalar desde archivo…» en Complementos; después, «Bajar modelos». Más detalles en la [guía de complementos](https://github.com/Dathinel/rodaje/blob/main/docs/guia/complementos.md).

## Código

El código fuente está en el repositorio de Rodaje, en [`modules/Rodaje.Module.Translate`](https://github.com/Dathinel/rodaje/tree/main/modules/Rodaje.Module.Translate), junto con la biblioteca del protocolo ([`src/Rodaje.Modules.Protocol`](https://github.com/Dathinel/rodaje/tree/main/src/Rodaje.Modules.Protocol)). Cada release adjunta además el código exacto con el que se compiló (`codigo-fuente-*.zip`). Se arma con:

```
powershell -NoProfile -ExecutionPolicy Bypass -File build\empaquetar-modulo.ps1 -Modulo modulo-traducir
```

| Archivo | Qué es |
|---|---|
| `paquete.json` | El manifiesto del módulo: funciones, VRAM y cada modelo con su URL, tamaño y SHA-256 |
| `LICENCIAS.md` | Licencias de las bibliotecas y los modelos |
| `LICENSE` | GPLv3 con los términos adicionales de Rodaje |

## Licencia

El código es GPL-3.0-only con los términos adicionales de Rodaje (atribución y permiso para complementos), ver `LICENSE`. Los modelos y las bibliotecas conservan la suya: ver `LICENCIAS.md`. El logotipo de Rodaje es marca de su autor ([TRADEMARK.md](https://github.com/Dathinel/rodaje/blob/main/TRADEMARK.md)).
