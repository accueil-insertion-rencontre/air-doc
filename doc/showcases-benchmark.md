# Benchmark des stacks JavaScript orientées **« code first »**

## 1. Principes de sélection

- **Node.js + TypeScript** côté back pour profiter de l’écosystème et du typage statique.
- **SSR/SSG** côté front afin d’obtenir un site vitrine indexable et performant.

## 2. Benchmark *Back‑end* Node.js / TS

| Framework | Perf. brute<sup>1</sup> | Typage TS | Écosystème | Points forts → faiblesses |
|-----------|------------------------|-----------|-------------|---------------------------------------------|
| **Fastify** | ~28 k req/s (≈ ×3 Express) | ✔️ | Large (plugins JWT, CORS, websockets, etc.) | Super compromis perf/plug‑ins ; HTTP/2 natif → À tout coder (auth, RBAC, etc.) |
| **Hyper Express** | ~40 k req/s (≈ ×4 Express) | ✔️ | Plus réduit | Ultra‑rapide (uWebSockets.js) → Documentation et communauté modestes |
| **NestJS** *(adapter Fastify)* | ~2 × Express | ✔️ (décorateurs) | Très mature | Architecture modulaire, DI, Swagger auto → plus verbeux qu’un micro‑framework |
| **AdonisJS v6** | ~Fastify (mesures internes) | ✔️ | Écosystème moyen | Expérience « Laravel‑like », validation intégrée → moins répandu |

<sup>1</sup> Benchmarks 2023‑12, route JSON simple, Intel i7 / Node 20. Les écarts se resserrent dès qu’on ajoute la BD.

## 3. Benchmark *Front‑end* / Méta‑frameworks JS

| Framework | Perf. runtime | SSR / SSG | Typage | Popularité 2024 | Points clés |
|-----------|--------------|-----------|--------|-----------------|-------------|
| **Next.js 14** *(React)* | Edge Runtime, streaming TTFB rapide | ✔️ (SSR, ISR) | TS natif | #1 usage pro | Énorme écosystème, App Router, Server Actions |
| **Nuxt 3** *(Vue 3)* | Nitro + Vite → très rapide | ✔️ | TS opt‑in | #2 (Vue) | Unifie CSR / SSR / ISG, learning curve douce |
| **SvelteKit 2** | Hydratation minimale | ✔️ | TS opt‑in | Satisfaction ⭐⭐⭐⭐⭐ | Bundle ultra‑léger, DX rapide |
| **Astro 5** | Zero JS par défaut, islands architecture | ✔️ | TS opt‑in | CWV 65 % pass | HTML‑first, mélange React/Vue/Svelte ; parfait pour contenu statique |
| **Angular 17** | Build & mem optimisés (‑50 %, ‑30 %) | ✔️ | TS obligatoire | #3 usage | Solution tout‑intégré, parfaite avec NestJS |
| **Remix / Qwik / Solid** | Excellent (islands/resumation) | ✔️ | TS | niche | Innovants mais écosystèmes réduits |
| **Next.js 14** *(React)* | Edge Runtime, streaming TTFB rapide | ✔️ (SSR, ISR) | TS natif | #1 usage pro | Énorme écosystème, App Router, Server Actions |
| **Nuxt 3** *(Vue 3)* | Nitro + Vite → très rapide | ✔️ | TS opt‑in | #2 (Vue) | Unifie CSR / SSR / ISG, learning curve douce |
| **SvelteKit 2** | Hydratation minimale | ✔️ | TS opt‑in | Satisfaction ⭐⭐⭐⭐⭐ | Bundle ultra‑léger, DX rapide |
| **Angular 17** | Build & mem optimisés (‑50 %, ‑30 %) | ✔️ | TS obligatoire | #3 usage | Solution tout‑intégré, parfaite avec NestJS |
| **Remix / Qwik / Solid** | Excellent (islands/resumation) | ✔️ | TS | niche | Innovants mais écosystèmes réduits |

## 4. Couples de stack recommandés

| Scénario | Back‑end | Front‑end | Pourquoi |
|----------|----------|-----------|----------|
| **Ultra‑léger & performant** | Fastify (+ Prisma / Zod) | SvelteKit 2 | Temps de réponse minimal, bundle client < 20 kB |
| **Site vitrine contenu‑first** | Fastify (+ Prisma) | Astro 5 | Zero JS par défaut, SEO/CWV excellents, markdown facile |
| **Hybride vitrine / admin** | Fastify (+ Prisma) | Astro 5 (public) + SvelteKit 2 **ou** Next.js 14 (admin) | Vitrine ultra‑rapide + dashboard interactif séparé ; monorepo simple, rewrites domaine |
| **Architecture solide & testable** | NestJS (+ Fastify) | Angular 17 | Décorateurs et DI alignés, tests intégrés, mono‑repo NX |
| **Débit HTTP maximal** | Hyper Express (+ Prisma) | SvelteKit 2 **ou** Next.js 14 | uWebSockets.js pour le back, front léger ou React selon l’équipe |
| **Full TypeScript React** | Fastify (+ tRPC) | Next.js 14 | API type‑safe bout‑en‑bout, DX React universelle |

## 5. Synthèse

- **Fastify** reste le meilleur compromis performance / simplicité ; **NestJS** ajoute une ossature robuste si l’équipe accepte plus de boilerplate.
- **Hyper Express** n’est justifié que lorsque le serveur HTTP est le véritable goulet d’étranglement.
- La solution **hybride Astro 5 + SvelteKit 2 / Next.js 14** combine une vitrine HTML‑first ultra‑rapide (SEO, Core Web Vitals) et un back‑office interactif séparé ; c’est le compromis idéal si les performances publiques sont prioritaires sans sacrifier l’ergonomie de l’admin.
- Côté front, **Next.js** domine par son écosystème, **SvelteKit** par la légèreté, **Angular 17** lorsque l’on veut une cohérence forte avec Nest.
- **Effort de développement** : Fastify (+ Prisma) demande plus de code métier mais reste abordable ; NestJS réduit ce code mais implique un démarrage plus verbeux ; l’option hybride Astro + SvelteKit/Next introduit deux toolchains à maîtriser mais garde une séparation claire des responsabilités ; Angular 17 apporte beaucoup de fonctionnalités prêtes à l’emploi mais une courbe d’apprentissage plus raide.

*Révisions futures : surveiller SvelteKit 2.1 (routing amélioré) et l’arrivée d’AdonisJS 6 stable pour de nouveaux chiffres de bench.*

