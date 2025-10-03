<h1 id="intel-msrs">Configuración de MSR's en Intel <a href="#intel-msrs">(permalink)</a></h1>

<h2 id="table-of-contents">1. Tabla de contenidos <a href="#table-of-contents">(permalink)</a></h2>

- [1. Tabla de contenidos](#table-of-contents)
- [2. Definicion de MSR's](#definicion-de-msrs)
- [3. Ejemplos](#ejemplos)
  - [3.1. MSR-POWER-CTL=0x1FCH](#power-ctl)
  - [3.2. MSR-MISC-FEATURE-CONTROL=0x1A4H](#misc-feature)
  - [3.3. IA32-MISC-ENABLE=0x1A0H](#misc-enable)
 
<h2 id="definicion-de-msrs">2. Definicion de MSR's <a href="#definicion-de-msrs">(permalink)</a></h2>

En arquitecturas modernas de procesadores, muchos parámetros de bajo nivel no están expuestos en el BIOS ni en el sistema operativo de manera directa. Estos parámetros se encuentran documentados en los datasheets y volúmenes de especificación que publica el fabricante (ej. Intel o AMD). Dichos documentos detallan el significado de cada registro, ya sea un MSR (Model Specific Register), un registro PCI, o un espacio MMIO/IO.

Cada registro contiene distintos bits de control, organizados en máscaras binarias. Estos bits habilitan, deshabilitan o modifican funciones internas del procesador y del chipset, como estados de energía, latencias de transición, políticas de reloj o comportamientos de optimización. Al comprender qué representa cada bit, es posible aplicar cambios muy precisos para ajustar el comportamiento del hardware, ya sea con fines de investigación, rendimiento o reducción de latencia.

Para trabajar con estos registros en Windows se suele emplear herramientas como [RWEverything](https://rweverything.com/)/[Chiptool](https://github.com/LuSlower/chiptool), que permiten leer, modificar y escribir directamente valores en MSRs o registros PCI/IO. El procedimiento básico siempre es el mismo:

<h2 id="ejemplos">3. Ejemplos: <a href="#ejemplos">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

<h2 id="power-ctl">3.1. MSR-POWER-CTL=0x1FCH <a href="#power-ctl">(permalink)</a></h2>

El MSR_POWER_CTL (dirección 0x1FC, decimal 508) es un registro específico de Intel extraido de "Intel® 64 and IA-32 Architectures Software Developer’s Manual, Volume 4: Model-Specific Registers" disponible en procesadores desde la 6.ª hasta la 13.ª generación, incluyendo también varias familias de Intel Xeon y Core i3. Este registro permite al usuario modificar directamente ciertos bits relacionados con control de energía y comportamiento del procesador. Su uso resulta especialmente útil en sistemas con BIOS bloqueada (BIOS locked), ya que otorga la posibilidad de aplicar cambios a nivel de sistema operativo que normalmente solo podrían configurarse desde la BIOS.

Dentro de este MSR existen distintos campos de bits configurables, cada uno con una función específica. Por ejemplo, el bit 1 (C1E Enable) habilita o deshabilita la transición del procesador al estado de bajo consumo C1. El bit 19 (Disable Energy Efficiency Optimization) permite desactivar la optimización de eficiencia energética en los estados P, afectando directamente cómo el procesador gestiona el rendimiento y el consumo. De forma similar, el bit 20 (Disable Race to Halt Optimization) controla si se permite o no la estrategia de ejecución conocida como “Race to Halt”. Estos bits son de lectura/escritura (R/W), lo que significa que se pueden manipular mediante herramientas que accedan a los MSRs (RDMSR y WRMSR).

<details>
<summary>3.1.1 Instruccion 1. </summary>
  
<img width="1080" height="906" alt="MSR_POWER_CTL= (3)" src="https://github.com/user-attachments/assets/0f1cf8bc-d5bf-4819-9f05-410fe1ed65fa" />

<details>
<summary>3.1.2. Instruccion 2. </summary>

<img width="1080" height="634" alt="MSR_POWER_CTL= (1)" src="https://github.com/user-attachments/assets/a6085ca3-d059-4472-afc4-cce5e536b0c1" />

<details>
<summary>3.1.3. Instruccion3. </summary>

<img width="1088" height="656" alt="MSR_POWER_CTL= (2)" src="https://github.com/user-attachments/assets/0e050ee5-6e7d-40ad-98e9-4f9f2c5d218d" />



