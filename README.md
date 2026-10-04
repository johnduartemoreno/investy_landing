# investy_landing

Sitio público de Investy: `https://investyapp.com`. Una sola página estática, sin
build y sin dependencias — `index.html` con el CSS adentro.

## Por qué existe este repo y no una carpeta

- **No va en el meta-repo:** publicar con Cloudflare Pages exige darle acceso de
  lectura al repositorio, y el meta contiene los informes legales, los números de
  costos y credenciales de sandbox. No hay motivo para exponer eso por una página
  estática.
- **No va en `investy_frontend`:** ese repo es la app Flutter; un sitio estático
  adentro le ensucia el propósito y el build.

## Qué puede y qué no puede decir esta página

El texto sigue `docs/brand/encuadre-legal.md` del meta-repo, actualizado con la
investigación legal de B158. En resumen, **no** se usa: *asesor* / *asesoría*,
*recomendaciones personalizadas*, *encaja con tu perfil*, *retorno esperado*,
ni ninguna mención de bróker, custodia o cuentas segregadas. Owl se describe como
que *propone activos para practicar en el simulador y explica cada uno*.

La **leyenda del art. 2.40.1.1.2 del Decreto 2555** va en la página y no se saca.

Antes de cambiar una frase, leer esa tabla. Es la misma razón por la que hubo que
reemitir el PDF de campaña (B98, B158).

## Publicación

**Cloudflare Pages**, conectado a este
repositorio. `wrangler.toml` sólo declara `pages_build_output_dir`:
`public/` se sirve tal cual. Por eso no hay
comando de build ni framework preset (queda en *None*).

El dominio ya usa los nameservers de Cloudflare (`aron.ns.cloudflare.com`,
`nicolas.ns.cloudflare.com`). Cada push a `main` republica.

### Lo que hay que sacar al publicar

Existe un Worker viejo, **`investyapp-redirect`**, que manda `investyapp.com` y
`www.investyapp.com` al formulario de Tally. **Las rutas de un Worker se evalúan
antes que este sitio**, así que mientras existan, el dominio sigue yendo al
formulario (B166) por más que el sitio esté publicado. Hay que quitarle las rutas
—o borrarlo— en *Settings → Domains & Routes*.

## Verificar antes de publicar

```bash
cd public && python3 -m http.server 8000   # y abrir http://localhost:8000
```
