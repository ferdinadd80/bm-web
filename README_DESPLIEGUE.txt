========================================================================
  B&M INTELLIGENCE — SITIO WEB · INSTRUCCIONES DE DESPLIEGUE
========================================================================

CONTENIDO DE ESTE PAQUETE
-------------------------
  index.html        El sitio completo (bilingüe ES/EN, responsive, light)
  favicon.svg       Ícono del sitio
  fonts/            Fuente Geist optimizada (5 pesos, formato woff2)
  _redirects        Reglas de redirección de dominios

CÓMO EDITAR TEXTOS (para Fernando)
----------------------------------
  Abre index.html con Bloc de notas o VS Code.
  Cada texto aparece DOS veces, así:

    <span class="lang-es">Texto en español</span>
    <span class="lang-en">English text</span>

  Edita el que necesites, guarda, y vuelve a subir el archivo a
  Cloudflare (Direct Upload). Nada más.

========================================================================
  FASE 1 — PUBLICAR EL SITIO (hacer ahora)
========================================================================

DESPLIEGUE EN CLOUDFLARE PAGES (mismo flujo que bm-assets)
  1. Comprime esta carpeta en un ZIP (o usa el ZIP ya provisto)
  2. Cloudflare Dashboard -> Workers & Pages -> Create
  3. Pages -> Upload assets (Direct Upload)
  4. Project name:  bm-web
  5. Sube el ZIP -> Deploy
  6. Verifica en la URL temporal: bm-web.pages.dev

CONECTAR EL DOMINIO PRINCIPAL  bm-intelligence.com
  ⚠️ Esto NO afecta el correo de Zoho. El correo usa registros MX;
     la web usa A/CNAME. Son independientes. No se toca el correo.

  1. En el proyecto bm-web -> Custom domains -> Set up a domain
  2. Agrega:  bm-intelligence.com
  3. Agrega también:  www.bm-intelligence.com
  4. Cloudflare configura el DNS automáticamente (dominio ya en tu cuenta)
  5. Espera el certificado SSL (1-5 min)

  Resultado:
    bm-intelligence.com          -> SITIO  ✅
    www.bm-intelligence.com      -> redirige a bm-intelligence.com

========================================================================
  FASE 2 — AGREGAR bm-intelligence.com.mx (opcional, después)
========================================================================

  El sitio funciona perfecto SIN esto. Hazlo cuando quieras proteger
  también el dominio .com.mx y que redirija al .com.

  1. Cloudflare Dashboard -> Add a domain -> bm-intelligence.com.mx
  2. Cloudflare te dará 2 nameservers (ej: xxx.ns.cloudflare.com)
  3. Entra al panel donde compraste el .com.mx (Neubox)
  4. Cambia los nameservers del .com.mx por los de Cloudflare
  5. Espera la propagación (puede tardar de minutos a 24h)
  6. En Cloudflare, con el .com.mx ya activo:
     proyecto bm-web -> Custom domains -> agrega:
       bm-intelligence.com.mx
       www.bm-intelligence.com.mx
  7. El archivo _redirects ya tiene las reglas listas: ambos
     redirigirán automáticamente a bm-intelligence.com

  Resultado final (las 4 puertas, un solo destino):
    bm-intelligence.com          -> SITIO  ✅
    www.bm-intelligence.com      -> redirige
    bm-intelligence.com.mx       -> redirige
    www.bm-intelligence.com.mx   -> redirige

========================================================================
