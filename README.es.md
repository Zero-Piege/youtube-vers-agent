# youtube-vers-agent

Una habilidad de Claude Code que transforma tutoriales de YouTube en habilidades de Claude Code mediante verificación dual-fuente (Claude local + Gemini) y cruzamiento de especificaciones.

## Descripción

Esta habilidad convierte el contenido de tutoriales de YouTube en habilidades de Claude Code estructuradas mediante:
1. Extraer conceptos clave y procedimientos de las transcripciones de video
2. Verificar información a través de validación dual-fuente (video + documentación)
3. Crear archivos SKILL.md correctamente formateados siguiendo las convenciones de Claude Code
4. Garantizar precisión y completitud mediante referencias cruzadas

## Cuándo usar

Utiliza esta habilidad cuando deseas:
- Convertir contenido educativo de YouTube en habilidades de Claude Code reutilizables
- Crear habilidades basadas en videos tutoriales sobre herramientas de desarrollo, frameworks o metodologías
- Garantizar la precisión de las habilidades mediante verificación contra documentación oficial
- Construir una biblioteca de habilidades verificadas a partir de recursos de aprendizaje en video

## Flujo de la habilidad

### 1. Fase de análisis de video
- Procesar video de YouTube usando la habilidad watch para extraer transcripción y fotogramas clave
- Identificar temas principales, procedimientos y ejemplos de código presentados
- Estructurar objetivos y resultados de aprendizaje

### 2. Verificación dual-fuente
- Para cada concepto/procedimiento clave, consultar documentación oficial usando habilidades context7-mcp o find-docs
- Cruzar contenido de video con fuentes autoritativas
- Anotar cualquier discrepancia o diferencia de versión
- Verificar que los ejemplos de código funcionen como se demostró

### 3. Creación de habilidad
- Generar archivo SKILL.md correctamente formateado siguiendo convenciones de Claude Code
- Incluir descripción clara, directrices de uso y flujo de trabajo paso a paso
- Referenciar tanto la fuente de video como las fuentes de documentación usadas para verificación
- Añadir recomendaciones de herramientas apropiadas basadas en procedimientos verificados

### 4. Aseguramiento de calidad
- Probar ejemplos de código o procedimientos mencionados
- Validar que la habilidad siga estándares de formato de habilidades de Claude Code
- Asegurar que la habilidad proporcione orientación accionable y verificable

## Salida

Produce un archivo SKILL.md completo en el directorio apropiado .claude/skills/ que:
- Define claramente el propósito y aplicabilidad de la habilidad
- Proporciona directrices de uso específicas
- Describe un flujo de trabajo verificable
- Referencia las fuentes usadas para verificación dual-fuente
- Sigue las convenciones de habilidades de Claude Code

## Herramientas requeridas

- watch: Para procesar contenido de videos de YouTube
- context7-mcp o find-docs: Para verificación dual-fuente contra documentación oficial
- Bash: Para operaciones de archivos y creación de habilidades

## Instalación

1. Clona este repositorio:
   ```bash
   git clone https://github.com/Zero-Piege/youtube-vers-agent
   ```

2. Copia la habilidad a tu directorio de habilidades de Claude Code:
   ```bash
   cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
   ```

3. Recarga plugins:
   ```bash
   /reload-plugins
   ```

## Uso

Después de instalación, puedes usar la habilidad proporcionando una URL de YouTube y especificando qué quieres construir:

```
/youtube-vers-agent [URL de YouTube] [qué extraer] [qué construir]
```

Ejemplo:
```
/youtube-vers-agent https://youtu.be/zke3bTtvmLo Todo el proyecto Una habilidad de Claude Code
```

## Ejemplo de uso

Transformar un tutorial de YouTube sobre creación de componentes React en una habilidad de Claude Code:
1. Usa la habilidad watch para extraer transcripción de video y puntos clave
2. Usa context7-mcp para verificar patrones de creación de componentes React contra documentación oficial de React
3. Crea SKILL.md con procedimientos verificados para crear componentes React en Claude Code
4. Incluye referencias tanto al tutorial de YouTube como a la documentación de React usada

## Estándares de verificación

Todas las habilidades creadas deben:
- Referenciar al menos dos fuentes independientes (video + documentación)
- Incluir pasos específicos y accionables
- Proveer directrices de uso claras
- Seguir el formato establecido de habilidades de Claude Code
- Contener procedimientos verificables que puedan ser probados

## Licencia

Licencia MIT - ver archivo [LICENSE](LICENSE) para detalles.