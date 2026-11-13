# CLAUDE.md — El teorema de excisión

Transparencias en LaTeX/Beamer sobre el teorema de excisión en homología
singular (Universidad de Sevilla). Referencia de base: Hatcher,
*Algebraic Topology*, §2.1, pero la demostración sigue un enfoque propio
(ver «Plan»).

El tema Beamer está en `beamerteaching/` como submódulo
(https://github.com/FMuro/beamerteaching).

## Compilación

```sh
git submodule update --init --recursive
latexmk -pdf main.tex
```

Compatible con **pdfLaTeX**, **TeX Live en macOS** y **Texifier en iPad**.
No introducir dependencias que rompan ninguno de estos entornos.

## Estructura

```
main.tex          ← preámbulo, macros y ensamblaje
beamerteaching/   ← submódulo con el tema
secciones/        ← un fichero por sección, incluido con \input desde main.tex
```

Cada fichero de `secciones/` empieza con `\section{...}`.

## Plan

1. Cadenas subordinadas a un recubrimiento $\cU=\{U_i\}_{i\in I}$ con
   $X=\bigcup_i \Int U_i$: subcomplejo $C^{\cU}_\bullet(X)\subseteq C_\bullet(X)$
   de los símplices singulares con imagen en algún $U_i$.
2. Subdivisión baricéntrica de un símplice; el diámetro de cada símplice
   de la subdivisión es $\le \frac{n}{n+1}$ veces el del original.
3. Operador subdivisión $S$ en cadenas singulares; $S$ es morfismo de
   complejos y es homotópico a la identidad.
4. Teorema de las cadenas pequeñas: existe una retracción
   $\rho\colon C_\bullet(X)\to C^{\cU}_\bullet(X)$ que fija $C^{\cU}_\bullet(X)$
   y una homotopía de cadenas $D$ en $C_\bullet(X)$, $\partial D+D\partial=\id-\iota\rho$,
   que se anula sobre $C^{\cU}_\bullet(X)$.
5. Excisión y Mayer–Vietoris como consecuencias.

## Macros (main.tex)

`\N \Z \R \id \im \diam \Int \simplex{n} \Sing \cU \CU \Sd`.
No redefinir macros estándar de LaTeX (p. ej. `\int`).

## Reglas de estilo

- Español. Rigor alto; lenguaje natural, ni telegráfico ni prolijo.
- No empezar frases, párrafos, títulos ni pies de figura con símbolos
  matemáticos: anteponer un sustantivo («El operador $\Sd$…», «El punto
  $v_2$…») o reformular («Si $n=0$, …»).
- Demostraciones completas: objetivo → pasos esenciales → justificación de
  los no evidentes → conclusión explícita.
- Frames largos: `[allowframebreaks]`, nunca comprimir. **No usar `\pause`.**
- Una idea pedagógica principal por frame. PDF legible página a página.
- Énfasis: `\alert{}` con moderación; no `\emph{}` como recurso principal.
  **No usar `\boxed{}`.**
- Entornos: `theorem`, `proposition`, `lemma`, `corollary`, `definition`,
  `example`, `exercise`, `proof`, `solution`.
