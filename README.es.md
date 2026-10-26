<p align="right"><sub><a href="README.md">Read in English</a></sub></p>

<p align="center">
  <img src="assets/banner-navy.svg" alt="Cristian Guerra — Senior SDET · WAR Paradigm" width="100%"/>
</p>

<p align="center">
  <a href="https://www.linkedin.com/in/criguex"><img src="https://img.shields.io/badge/LinkedIn-criguex-0A66C2?style=flat-square&logo=linkedin&logoColor=white" alt="LinkedIn"/></a>
  <img src="https://img.shields.io/badge/Vivo_en-Medellín,_Colombia_(GMT--5)-071B2B?style=flat-square" alt="Ubicación"/>
  <a href="https://wa.me/573106344106?text=Hola%20Cristian%2C%20vi%20tu%20perfil%20de%20GitHub%20y%20me%20gustar%C3%ADa%20hablar%20de%20un%20contrato%20remoto"><img src="https://img.shields.io/badge/Disponible_para-contratos_remotos-55DFBD?style=flat-square&labelColor=071B2B&logo=whatsapp&logoColor=071B2B" alt="Disponible para contratos remotos — escríbeme por WhatsApp"/></a>
</p>

## En palabras simples

Me aseguro de que el software haga lo que promete. Construyo revisiones automáticas que usan una aplicación como lo haría una persona y levantan la mano apenas algo se rompe, y las conecto al pipeline para que corran con cada cambio. Últimamente también reviso la IA: pruebo lo que construye y cómo se califica, y rompo cosas a propósito para demostrar que las revisiones de verdad lo notan.

## Tres casos

Tres proyectos, uno por tipo de trabajo. Cada uno dice el problema, qué construí, cómo comprobarlo tú mismo y qué se midió. Las cifras salen de corridas de laboratorio, no de sistemas en producción.

**1 · Automatización para un release: [restful-booker-quality-suite](https://github.com/criguex/restful-booker-quality-suite)**
- **Problema:** decidir si una API puede salir, y mantener visibles los bugs conocidos en vez de esconderlos.
- **Qué construí:** suite de API con Playwright basada en riesgo, contratos con Zod y presupuestos de latencia, en cuatro gates de CI contra una copia fija de la app en Docker.
- **Compruébalo:** `docker compose up --build -d && npm ci && npm run quality`
- **Mi parte:** una demo tratada como un release. Definí el modelo de riesgo (P0: cambios sin autorización, integridad del ciclo de la reserva, autenticación) y qué bloquea un release; dejé visibles los 8 defectos y escribí cada exclusión. Asistentes de IA escribieron el código Playwright/Zod y el reporte bajo mi dirección.
- **Medido (laboratorio):** 43 chequeos pasan en 2,0 s; 8 defectos confirmados quedan como fallos esperados, así que un arreglo pone la suite en rojo hasta que alguien lo reconoce.

**2 · Evaluar un agente de IA: [agent-eval-jev](https://github.com/criguex/agent-eval-jev)**
- **Problema:** saber cuándo un agente que usa herramientas inventa cifras o se salta un paso, sin confiar en un solo juez LLM.
- **Qué construí:** primero chequeos en código, después un juez Jev calibrado, un juez LLM solo para comparar, y un gate de CI con una franja de revisión humana.
- **Compruébalo:** `python -m agenteval evaluate && python -m agenteval gate`
- **Mi parte:** decidí qué probar, los pesos de los criterios y las reglas del umbral; un asistente de IA redactó las 60 etiquetas de referencia siguiendo mi rúbrica y yo las revisé y aprobé; asistentes de IA lo construyeron y lo corrieron bajo mi dirección.
- **Medido (laboratorio):** el evaluador coincide con las etiquetas de referencia (redactadas por IA, revisadas por mí, sin anotador independiente) en el 93,1% de 29 casos de prueba (kappa 0,86); el mismo gate deja pasar al agente v2 y frena al v1.

**3 · QA científico: [predictor-debugger](https://github.com/criguex/predictor-debugger)**
- **Problema:** comprobar si una red neuronal que predice un fluido 3D respeta la física, sin mover el arco después de ver los datos.
- **Qué construí:** un depurador físico con hipótesis y umbrales en un commit antes de cada ronda, corrido en varias máquinas.
- **Compruébalo:** `uv run --locked verify.py --saved mac` (minutos, sin descargar datos)
- **Mi parte:** orquesté las rondas: tres máquinas y sistemas operativos, versiones fijadas, publicar los fallos como fallos, una v1.0 reproducible. La IA propuso hipótesis y umbrales, que aprobé antes de cada ronda, y escribió y corrió el código.
- **Medido:** 49 hipótesis prerregistradas en cuatro rondas: 48 pasan y una (H14) falló y está publicada así; las mismas huellas en seis entornos.

## Liderazgo técnico

Lidero como contribuidor individual: defino los riesgos, los gates y las reglas, y agentes de IA hacen buena parte de la ejecución dentro de ellas. Tres casos, anonimizados:

- **Parar la producción por un falso verde.** En una línea de contenido automatizada que es mía, una auditoría mostró que la puerta de calidad de imágenes daba 90 y «aprobado» mientras rechazaba 10 de 10 planos. Paré la generación, decidí los 12 gates abiertos del plan de corrección y solo reanudé cuando la puerta volvió a medir; el arreglo y el despliegue tomaron unas 5 horas. Regla: un gate que dice OK sin evidencia es peor que no tener gate.
- **Criterios de release para 10 apps pequeñas de clientes.** Definí qué es P0 (lo que bloquea hoy o crea riesgo legal o de dinero real ahora; una función que nadie pidió nunca es P0; una afirmación falsa en la documentación es P0) y la regla de que nada sale sin smoke y E2E en verde y sin un revisor que no sea quien arregla. Una ronda de revisión, hecha por agentes de IA con ese protocolo, encontró 17 P0 y cerró 16, con unas 125 pruebas nuevas.
- **Corregir a la IA con evidencia.** Cuando un asistente de IA recalculó mi experimento público y lo llamó revisión independiente, le hice etiquetarlo como operado por IA bajo mi dirección y lo publiqué como release aparte ([repro-ia-20261026](https://github.com/criguex/predictor-debugger/releases/tag/repro-ia-20261026)). Quién ejecutó algo cambia lo que se puede afirmar.

## Sobre mí

Soy SDET senior con más de 7 años en automatización de pruebas, sobre todo en fintech y banca. Diseño frameworks de automatización desde cero, pruebo APIs y aplicaciones web de punta a punta y meto gates de calidad en el CI.

Últimamente la mayor parte de mi trabajo es **probar lo que construye la IA**: volver medibles los veredictos cuando las salidas no son deterministas, y usar asistentes de IA para diseñar y explorar pruebas más rápido mientras una persona sigue firmando.

## Proyectos destacados

Ordenados del más importante al menos importante.

### Proyectos principales · verificar resultados de ciencia e IA

| Proyecto | Qué muestra | Stack |
|---|---|---|
| **[scientific-qa-evidence](https://github.com/criguex/scientific-qa-evidence)** | Auditoría de QA independiente y reproducible de las pruebas en Lean 4 que publicó OpenAI para Navier–Stokes y Euler: reconstruidas desde el código fuente, verificadas de nuevo con dos verificadores independientes y sometidas a mutaciones a propósito. [Ver el sitio](https://criguex.github.io/scientific-qa-evidence/) | Lean 4 · Python · CI |
| **[predictor-debugger](https://github.com/criguex/predictor-debugger)** | Un depurador físico prerregistrado para una red neuronal que predice un fluido 3D: umbrales comprometidos antes de los datos, veredictos reproducidos en tres máquinas y las hipótesis que fallan también publicadas | Python · numpy · uv · CI |

### Enseñar

| Proyecto | Qué muestra | Stack |
|---|---|---|
| **[qa-automation-course](https://github.com/criguex/qa-automation-course)** | Curso interactivo y gratis de QA Automation: 35 módulos en 4 niveles, desde oráculos y Playwright hasta evaluar IA, mutation testing y QA científico, cada uno con quiz autocorregible, reto verificable y rúbrica. [Haz el curso](https://criguex.github.io/qa-automation-course/) | HTML · JavaScript · GitHub Pages |

### Evaluar IA

| Proyecto | Qué muestra | Stack |
|---|---|---|
| **[qa-eval-lab](https://github.com/criguex/qa-eval-lab)** | Pruebas de UI con Playwright **y** evaluación de LLM (DeepEval + Promptfoo) conectadas en un solo eval-gate de CI | Playwright · TypeScript · DeepEval · Promptfoo · CI |
| **[agent-eval-jev](https://github.com/criguex/agent-eval-jev)** | Evaluación de un agente de IA real que usa herramientas, con chequeos en código, un juez Jev calibrado y un juez LLM, conectada a un gate de CI | Python · Jev · LLM judge · CI |
| **[jev-ci-triage](https://github.com/criguex/jev-ci-triage)** | Clasifica cada prueba que falla en CI como regresión, inestable, ambiente, datos de prueba o desconocida: primero reglas, Jev solo para lo ambiguo; nunca vuelve a correr ni esconde una falla | TypeScript · Playwright/JUnit · Jev |
| **[playwright-jev](https://github.com/criguex/playwright-jev)** | Aserciones semánticas para Playwright Test (`toMean`, `toChoose`, `toBeScored`) con Jev, grabadas una vez y repetidas en CI | Playwright · TypeScript · Jev |
| **[jev-test-impact](https://github.com/criguex/jev-test-impact)** | Corre solo las pruebas que tocó un cambio: primero el grafo de imports y las reglas de dueños, Jev para lo ambiguo y la suite completa ante cualquier duda | TypeScript · Vitest · Playwright · Jev |
| **[laya-server](https://github.com/criguex/laya-server)** | Un juez local y gratis (el modelo Laya, en CPU) con el contrato de Jev y una cascada a la nube para los casos dudosos | Node.js · Laya · Windows |

### Probar al que prueba · mutación

| Proyecto | Qué muestra | Stack |
|---|---|---|
| **[war-paradigm](https://github.com/criguex/war-paradigm)** | WAR Paradigm: probar al que prueba. Romper la realidad a propósito (una ley física en una simulación, un paso de un flujo, una respuesta de IA) y ver si las pruebas lo notan. Experimentos ejecutables detrás de mis publicaciones | Playwright · TypeScript · CI |
| **[civica-playwright-challenge](https://github.com/criguex/civica-playwright-challenge)** | Framework con forma de producción: Page Object Model, localizadores semánticos, capa de mocks determinista, chequeos de accesibilidad, escenarios mutantes que aprenden solos | Playwright · TypeScript · GitHub Actions |

### QA de requisitos

| Proyecto | Qué muestra | Stack |
|---|---|---|
| **[spec-review-case-study](https://github.com/criguex/spec-review-case-study)** | Cómo reviso una especificación antes de que alguien construya: 19 hallazgos (números que no cuadran, costos dados como hechos, reglas que nadie podría probar), una checklist reutilizable y un script que recalcula las cifras | Markdown · Python |

### Frameworks de automatización

| Proyecto | Qué muestra | Stack |
|---|---|---|
| **[restful-booker-quality-suite](https://github.com/criguex/restful-booker-quality-suite)** | Pruebas de API con mentalidad de release para Restful Booker: ciclo de vida, autenticación, contratos con Zod y presupuestos de latencia en cuatro gates de CI, con ocho defectos confirmados que siguen visibles | Playwright · TypeScript · Zod · Docker |
| **[playwright-saucedemo-e2e](https://github.com/criguex/playwright-saucedemo-e2e)** | Suite E2E multinavegador con POM y CI en cada push | Playwright · TypeScript |
| **[karate-api-testing](https://github.com/criguex/karate-api-testing)** | Pruebas de API REST guiadas por datos, con caminos felices y de falla | Karate DSL · Java · Maven |
| **[serenity-screenplay-salesforce](https://github.com/criguex/serenity-screenplay-salesforce)** | Patrón Screenplay para flujos web de negocio con documentación viva | Serenity BDD · Java · Cucumber |
| **[selenium-cucumber-pom](https://github.com/criguex/selenium-cucumber-pom)** | Framework web clásico por capas: drivers, hooks, page objects, datos de prueba | Selenium · Java 17 · Cucumber |

## Cómo trabajo

- **Primero los flujos dorados, después los muto.** Un cambio por mutante; si la suite sigue en verde, eso es un hallazgo.
- **API primero, UI como evidencia.** Chequeos rápidos y estables en la capa de servicio; el navegador demuestra el recorrido del usuario.
- **Veredictos deterministas para sistemas no deterministas.** Pasa/falla donde la especificación lo permite, puntajes contra criterios de aceptación donde no, y la misma entrada corrida 3 veces.
- **Las reglas duras viven en el código, no en los prompts.** Hooks, gates de CI y revisiones que no se pueden olvidar.

## Herramientas

**Web y móvil:** Playwright · Selenium · Cypress · Serenity BDD (Screenplay) · Appium
**API y rendimiento:** Karate DSL · REST Assured · Postman · k6 · JMeter
**Lenguajes:** TypeScript · JavaScript · Java · SQL
**CI e infraestructura:** GitHub Actions · GitLab CI · Jenkins · Docker
**Prácticas:** BDD (Cucumber/Gherkin) · pruebas de contrato · gestión de pruebas con Jira/Xray · pruebas asistidas por IA (Claude Code, Copilot, MCP)

## Contacto

Escríbeme por [WhatsApp](https://wa.me/573106344106?text=Hola%20Cristian%2C%20vi%20tu%20perfil%20de%20GitHub%20y%20me%20gustar%C3%ADa%20hablar%20de%20un%20contrato%20remoto) o [LinkedIn](https://www.linkedin.com/in/criguex). Estoy disponible para [contratos remotos](https://wa.me/573106344106?text=Hola%20Cristian%2C%20vi%20tu%20perfil%20de%20GitHub%20y%20me%20gustar%C3%ADa%20hablar%20de%20un%20contrato%20remoto) en automatización de QA y SDET.
