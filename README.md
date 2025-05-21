# PC-Tuning-ES

> [!CAUTION]
> Este fork está dirigido a usuarios avanzados y no pretende ser una simple copia del proyecto original. Gran parte del contenido ha sido traducido y adaptado desde PC-Tuning para hacerlo accesible a la comunidad hispanohablante.

> [!CAUTION]
> En términos de escalado de rendimiento, el orden de impacto es: hardware > firmware (UEFI/BIOS) > sistema operativo.

> [!CAUTION]
> **NO** confíes ni aceptes ciegamente todo lo que encuentres en línea (incluida esta fuente). En su lugar, mantén una actitud crítica: valida cada afirmación mediante evidencia, investigación y pruebas comparativas (benchmarks).

> [!CAUTION]
> **NO** apliques cambios, programas o scripts aleatorios, desconocidos o sin documentación a tu sistema sin comprender enteramente qué modifican y cuál es su impacto en la seguridad, la privacidad y el rendimiento.

<h1 id="tabla-de-contenidos">1. Tabla de contenidos <a href="#tabla-de-contenidos">(permalink)</a></h1>

- [1. Tabla de Contenidos](#table-of-contents)
- [2. Introducción](#introduction)
  - [2.1. Otras Fuentes](#other-resources)
- [3. Pruebas de Rendimiento](#benchmarking)
- [4. Configuración Física](#physical-setup)
- [5. Refrigeración](#cooling)
- [6. BIOS/UEFI](#biosuefi)
  - [6.1. Estilo de Partición](#partition-style)
  - [6.2. Considerar la Versión de Windows](#consider-windows-version)
  - [6.3. Métodos de recuperación de BIOS](#bios-recovery-methods)
  - [6.4. Actualizaciones de BIOS](#bios-updates)
  - [6.5. Microcódigo de BIOS](#bios-microcode)
  - [6.6. Acceder a opciones ocultas](#accessing-hidden-options)
  - [6.7. Dispositivos innecesarios](#unnecessary-devices)
  - [6.8. Resizable Bar (ReBAR)](#resizable-bar)
  - [6.9. Hyper-Threading/Simultaneous Multithreading](#hyper-threadingsimultaneous-multithreading)
  - [6.10. Estados de Energía](#power-states)
  - [6.11. Virtualización/Modo SVM](#virtualizationsvm-mode)
  - [6.12. Ahorros de Energía](#power-saving)
  - [6.13. Módulo de Plataforma Segura (TPM)](#trusted-platform-module-tpm)
  - [6.14. Módulo de Compatibilidad (CSM)](#compatibility-support-module-csm)
  - [6.15. Arranque Seguro](#secure-boot)
  - [6.16. Inicio rápido, suspensión e hibernación](#fast-startup-standby-and-hibernate)
  - [6.17. Spread Spectrum](#spread-spectrum)
  - [6.18. Legacy usb support](#legacy-usb-support)
  - [6.19. Opciones de instalación del software](#software-installation-options)
  - [6.20. Velocidad del enlace pci para dispositivos](#pci-link-speed-for-devices)
  - [6.21. Curvas de ventilación](#fan-curves)
  - [6.22. Perfiles y copias de seguridad de BIOS](#bios-profiles-and-backups)
- [7. Configuración de puertos usb](#configure-usb-port-layout)
  - [7.1. Revisión de los puertos usb accesibles](#reviewing-accessible-usb-ports)
  - [7.2. Planificación de la Distribución](#layout-planning)
  - [7.3. Conexión de Dispositivos](#plugging-in-devices)
- [8. Configurar Periféricos](#configure-peripherals)
  - [8.1. Limpieza](#cleaning)
  - [8.2. Perfiles de Memoria Integrada](#onboard-memory-profiles)
  - [8.3. Efectos de Iluminación RGB](#rgb-lighting-effects)
  - [8.4. DPI](#dpi)
  - [8.5. Tasa de Sondeo](#report-rate)
  - [8.6. Análisis de Estabilidad del Polling](#polling-stability-analysis)
  - [8.7. Monitor](#monitor)
- [9. Estabilidad, Overclock y Rendimiento Térmico](#stability-hardware-clocking-and-thermal-performance)
  - [9.1. Sistema Operativo Temporal](#temporary-operating-system)
  - [9.2. Información General](#general-information)
  - [9.3. Corrección de Errores](#error-correction)
  - [9.4. Gestión Térmica](#thermal-management)
  - [9.5. Calibración de la Línea de Carga (LLC)](#load-line-calibration)
  - [9.6. GPU](#gpu)
  - [9.7. RAM/CPU](#ramcpu)
  - [9.8. Herramientas para pruebas de Estrés](#stress-testing-tools)
- [10. Instalar Windows](#install-windows)
  - [10.1. Particiones de Almacenamiento](#storage-partitions)
  - [10.2. ¿Qué Versión de Windows Deberías Usar?](#what-version-of-windows-should-you-use)
  - [10.3. Descargar y Preparar una ISO de Windows Oficial](#downloading-and-preparing-a-stock-windows-iso)
  - [10.4. Fuentes de ISO](#iso-sources)
  - [10.5. Preparación de la ISO](#iso-preparation)
  - [10.6. Obtener Archivos Requeridos](#fetching-required-files)
  - [10.7. Iniciar desde la ISO](#booting-into-the-iso)
- [11. Configurar Windows](#configure-windows)
  - [11.1. Configuración OOBE](#oobe-setup)
  - [11.2. Control de Cuentas de Usuario](#user-account-control)
  - [11.3. Política de Ejecución de PowerShell Sin Restricciones](#unrestricted-powershell-execution-policy)
  - [11.4. Importar Carpeta bin](#importing-bin-folder)
  - [11.5. Mitigaciones de Procesos (Windows 10 1709+)](#process-mitigations-windows-10-1709)
  - [11.6. Agregar las opciones del Registro](#merging-registry-options)
    - [11.6.1. Documentación de Opciones del Registro](#registry-options-documentation)
    - [11.6.2. Aplicación de Opciones](#applying-options)
  - [11.7. Instalación de Controladores](#installing-drivers)
  - [11.8. Opciones Específicas para Windows Server](#windows-server-specific-options-windows-server)
  - [11.9. Opciones de Privacidad (Windows 8+)](#privacy-options-windows-8)
  - [11.10. Indexación de Búsqueda](#search-indexing)
  - [11.11. Hora, Idioma y Región](#time-language-and-region)
  - [11.12. Navegador Web](#web-browser)
  - [11.13. Tareas Programadas](#scheduled-tasks)
  - [11.14. Activar Windows](#activate-windows)
  - [11.15. Limpieza de la Interfaz](#declutter-interface)
  - [11.16. Efectos Visuales](#visual-effects)
  - [11.17. Superfetch y Prefetch](#superfetch-and-prefetch)
  - [11.18. Nombre del Sistema Operativo y de la Partición](#operating-system-and-partition-name)
  - [11.19. Mostrar Iconos en la Bandeja](#show-tray-icons)
  - [11.20. Hibernación](#hibernation)
  - [11.21. Runtimes](#runtimes)
  - [11.22. Eliminación de Bloatware](#handling-bloatware)
  - [11.23. Características Opcionales](#optional-features)
    - [11.23.1. NET 3.5](#net-35)
  - [11.24. 7-Zip](#7-zip)
  - [11.25. Controlador Gráfico](#graphics-driver)
  - [11.26. MSI Afterburner](#msi-afterburner)
  - [11.27. Resoluciones de Pantalla y Modos de Escalado](#display-resolutions-and-scaling-modes)
  - [11.28. Open-Shell (Windows 8+)](#open-shell-windows-8)
  - [11.29. Spectre, Meltdown y Microcódigo del CPU](#spectre-meltdown-and-cpu-microcode)
  - [11.30. Opciones de Energía](#power-options)
  - [11.31. Process Explorer](#process-explorer)
  - [11.32. Configuración de la Gestión de Memoria (Windows 8+)](#memory-management-settings-windows-8)
  - [11.33. Opciones del Adaptador de Red](#network-adapter-options)
  - [11.34. Dispositivos de Audio](#audio-devices)
  - [11.35. Administrador de Dispositivos](#device-manager)
  - [11.36. Ahorro de Energía en Dispositivos](#device-power-saving)
  - [11.37. Sesiones de Rastreo de Eventos (ETS)](#event-trace-sessions-ets)
  - [11.38. Sistema de Archivos](#file-system)
  - [11.39. Interrupciones Señaladas por Mensaje (MSI)](#message-signaled-interrupts)
  - [11.40. Moderación de Interrupciones XHCI (IMOD)](#xhci-interrupt-moderation-imod)
  - [11.41. Panel de Control](#control-panel)
  - [11.42. Configuración de Aplicaciones](#configuring-applications)
    - [11.42.1. NVIDIA Reflex](#nvidia-reflex)
    - [11.42.2. Límite de FPS](#framerate-limit)
    - [11.42.3. Registrar Juego en Config Store](#register-game)
    - [11.42.4. Modo de Presentación](#presentation-mode)
    - [11.42.5. Modo de Juego](#game-mode)
    - [11.42.6. Reproductor Multimedia](#media-player)
    - [11.42.7. Políticas QoS](#qos-policies)
  - [11.43. Optimización en Modo Kernel (Interrupciones, DPCs y más)](#kernel-mode-scheduling-interrupts-dpcs-and-more)
    - [11.43.1. GPU y DirectX Graphics Kernel](#gpu-and-directx-graphics-kernel)
    - [11.43.2. Controlador XHCI y de Audio](#xhci-and-audio-controller)
    - [11.43.3. Tarjeta de Red](#network-interface-card)
  - [11.44. Optimización en Modo Usuario (Procesos, Hilos)](#user-mode-scheduling-processes-threads)
    - [11.44.1. Iniciar un Proceso con una Afinidad Específica](#starting-a-process-with-a-specified-affinity-mask)
    - [11.44.2. Especificar Afinidad para Procesos Activos](#specifying-an-affinity-mask-for-running-processes)
  - [11.45. CPUs Reservados (Windows 10+)](#reserved-cpu-sets-windows-10)
    - [11.45.1. Casos de Uso](#use-cases)
  - [11.46. Analizar el Visor de Eventos](#analyzing-event-viewer)
  - [11.47. Seguridad Basada en Virtualización (VBS)](#virtualization-based-security-vbs)
  - [11.48. Estados de Inactividad del CPU](#cpu-idle-states)
    - [11.48.1. Activar Estados de Inactividad (por defecto)](#enable-idle-states-default)
    - [11.48.2. Desactivar Estados de Inactividad](#disable-idle-states)
  - [11.49. Quantums de Hilo y Planificación](#thread-quantums-and-scheduling)
    - [11.49.1. Explicación de Bitmask](#bitmask-explaination)
    - [11.49.2. Valores de Win32PrioritySeparation](#win32priorityseparation-values)
  - [11.50. Frecuencia de Interrupción del Reloj (Resolución del Temporizador)](#clock-interrupt-frequency-timer-resolution)
  - [11.51. Archivo de Paginación](#paging-file)
  - [11.52. Limpieza y Mantenimiento](#cleanup-and-maintenance)

<h1 id="introduction">2. Introducción <a href="#introduction">(permalink)</a></h1>

Este recurso puede utilizarse en la medida que lo desees, pero asegúrate de prestar atención a las advertencias. El objetivo principal de este documento es aplicar un enfoque basado en evidencia para explorar prácticas de ajuste (tuning) en sistemas basados en Windows, abarcando configuraciones de hardware, sistema operativo y software, para una variedad de casos de uso. Si tu flujo de trabajo diario permite utilizar Linux, entonces úsalo: Linux ofrece mucha más flexibilidad que Windows en múltiples aspectos, especialmente para los usuarios avanzados. Este recurso está diseñado para atender a una audiencia amplia, abarcando diversos objetivos como el fortalecimiento de la seguridad y la privacidad; sin embargo, generalmente se inclina por y está orientado a obtener una ventaja competitiva en videojuegos y a la ejecución de tareas en tiempo real. Se hace especial énfasis en fomentar que los usuarios realicen los cambios por sí mismos, minimizando el uso de scripts, con el fin de asegurar la transparencia y evitar modificaciones no intencionadas en el sistema del lector.

Se recomienda al lector avanzar a través de las secciones en el orden establecido, dado que cada etapa se fundamenta en la correcta ejecución de las anteriores. Por ello, la numeración secuencial de las secciones responde a una lógica progresiva en el desarrollo del contenido.

<h2 id="other-resources">2.1. Otras fuentes <a href="#other-resources">(permalink)</a></h2>

- [BoringBoredom/PC-Optimization-Hub](https://github.com/BoringBoredom/PC-Optimization-Hub)
- [Calypto's Latency Guide](https://calypto.us)
- [djdallmann/GamingPCSetup](https://github.com/djdallmann/GamingPCSetup)
- Windows Internals, Part 1: System Architecture, Processes, Threads, Memory Management, and More
- Windows Internals, Part 2
- [WINDOWS OPTIMIZATION FOR SOFT RT V3](https://cryptpad.fr/pad/#/2/pad/view/Wik8tmQ6XC1csjmDNqmMN7dKc-Wfi26-5bOtZzegHCM/embed/)

<h1 id="benchmarking">3. Pruebas de Rendimiento <a href="#benchmarking">(permalink)</a></h1>
La evaluación comparativa es una herramienta clave para analizar de forma objetiva cómo afectan al sistema los cambios que se aplican, evitando que factores como el efecto placebo distorsionen los resultados. En este contexto, se utiliza principalmente para medir si un ajuste específico mejora el rendimiento. Es importante entender bien cómo hacer este tipo de pruebas, ya que tendrás que realizar tus propios experimentos para tomar decisiones informadas: por ejemplo, saber si un cambio provoca una caída de rendimiento o cuál es la mejor configuración para un juego. Antes de aplicar cualquier modificación, pregúntate cosas como: “¿Qué quiero lograr con esto?”, “¿Cuál es el objetivo?”, “¿Qué espero mejorar?”, “¿Qué debería cambiar si esto funciona?” y “¿Cómo puedo medir ese cambio de forma clara?”.

  

- [FrameView](https://www.nvidia.com/en-gb/geforce/technologies/frameview) - [PC Latency](https://images.nvidia.com/content/images/article/system-latency-optimization-guide/nvidia-latency-optimization-guide-pc-latency.png) en juegos que admiten [PC Latency Stats](https://www.nvidia.com/en-gb/geforce/technologies/reflex/supported-products) y intervalo entre fotogramas
- [Frame Latency Meter](https://github.com/GPUOpen-Tools/frame_latency_meter)
- [PresentMon](https://boringboredom.github.io/Frame-Time-Analysis) - Diversas métricas, incluyendo el intervalo entre fotogramas [GPU Busy](https://www.intel.com/content/www/us/en/docs/gpa/user-guide/2022-4/gpu-metrics.html). Lista completa [Aqui](https://github.com/GameTechDev/PresentMon/blob/main/README-CaptureApplication.md#metric-definitions)
- [Windows Performance Toolkit](https://learn.microsoft.com/en-us/windows-hardware/test/wpt) - Biblioteca avanzada para el análisis de rendimiento en sistemas Windows. Permite extraer datos en tiempo de ejecución sobre ISR y DPC, facilitando una inspección detallada del comportamiento del sistema a bajo nivel. [xperf](/bin/xperf-dpcisr.bat) o [xtw](https://github.com/valleyofdoom/xtw)
- [Mouse Tester](https://github.com/valleyofdoom/MouseTester) - Métricas de rendimiento del ratón, como el intervalo de sondeo, recuentos X/Y y otros datos relevantes.
- [NVIDIA Reflex Analyzer](https://www.nvidia.com/en-gb/geforce/news/reflex-latency-analyzer-360hz-g-sync-monitors) - Latencia de extremo a extremo (End-to-end latency), útil para evaluar el tiempo total de respuesta desde la entrada hasta la visualización.
- [Frame-Time-Analysis](https://boringboredom.github.io/Frame-Time-Analysis) - Análisis de datos CSV generados por las herramientas mencionadas anteriormente, incluyendo métricas clave como el percentil 1 % y 0,1 % para detectar variaciones en el rendimiento.
- [Latency Grapher](https://boringboredom.github.io/tools/latencygrapher) - Evaluación de resultados de latencia utilizando herramientas como RLA, FrameView y PresentMon para obtener una visión detallada del rendimiento gráfico y la respuesta del sistema.

<h1 id="physical-setup">4. Configuración Física <a href="#physical-setup">(permalink)</a></h1>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

- Se recomienda realizar una instalación limpia de Windows tras cualquier cambio importante de hardware, como el reemplazo de la placa base, el procesador, la plataforma o el conjunto de chips, entre otros. Esto ayuda a evitar conflictos, asegurar la compatibilidad y garantizar un rendimiento óptimo.

- Consultar este documento con el propósito de identificar los gabinetes que ofrecen el mejor flujo de aire. [Higher Airflow Cases | Calypto](https://docs.google.com/spreadsheets/d/14Kt2cAn8a7j2sGXiPGt4GcxpR3RXVcDAx9R5c2M8680/edit#gid=0)

- Evite las CPU Ryzen con múltiples CCX o CCD, ya que la comunicación entre estos módulos introduce una penalización de latencia que puede afectar negativamente al rendimiento, especialmente en tareas sensibles al tiempo de respuesta. ([1](https://calypto.us), [2](https://www.anandtech.com/show/17585/amd-zen-4-ryzen-9-7950x-and-ryzen-5-7600x-review-retaking-the-high-end/10))

- Consulte la sección [Low Latency Hardware | Calypto](https://docs.google.com/document/d/1c2-lUJq74wuYK1WrA_bIvgb89dUN0sj8-hO3vqmrau4/edit?tab=t.0#bookmark=kix.alwwrke7e395)

-Evite apretar demasiado los tornillos.

-Verifique que todos los conectores estén correctamente colocados y que ninguno esté suelto (por ejemplo, los cables de la fuente de poder).

-Desconecte dispositivos innecesarios o sin uso de su configuración, incluyendo periféricos, tiras LED o RGB, dispositivos USB, discos de almacenamiento, receptores inalámbricos, entre otros.

- Dé preferencia a los dispositivos con cable (por ejemplo, periféricos, conexión Ethernet) en lugar de los inalámbricos, ya que estos últimos suelen ofrecer un rendimiento inferior e inconsistente debido a funciones agresivas de ahorro de energía para prolongar la batería, así como a posibles interferencias y sobrecarga en la transmisión. ([1](https://www.meetion.com/a-the-impact-of-lift-off-distance-on-battery-life-with-wireless-vs-wired-gaming-mice.html), [2](https://en.wikipedia.org/wiki/2.4_GHz_radio_use), [3](https://raw.githubusercontent.com/BoringBoredom/PC-Optimization-Hub/main/content/peripherals/wireless%20overhead.png), [4](https://www.logitechg.com/en-gb/innovation/hero.html), [5](https://www.youtube.com/watch?v=Zn7WjyIvAWA))

- Se recomienda firmemente el uso de almacenamiento SSD o NVMe ([1](https://unihost.com/help/nvme-vs-ssd-vs-hdd-overview-and-comparison)) dado que los discos duros mecánicos (HDD) presentan un rendimiento deficiente y generan interferencias excesivas. ([1](https://www.howtogeek.com/165542/why-solid-state-drives-slow-down-as-you-fill-them-up)) Asegúrese de mantener siempre una cantidad suficiente de espacio libre, ya que los SSD tienden a ralentizarse a medida que se llenan. No obstante, la mayoría viene con sobreaprovisionamiento de fábrica. ([1](https://download.semiconductor.samsung.com/resources/white-paper/S190311-SAMSUNG-Memory-Over-Provisioning-White-paper.pdf), [2](https://www.techpowerup.com/ssd-specs/samsung-980-pro-1-tb.d47))

- Evalúe el estado y el rendimiento de los dispositivos de almacenamiento con herramientas como [CrystalDiskInfo](https://crystalmark.info/en/software/crystaldiskinfo) y [CrystalDiskMark](https://crystalmark.info/en/software/crystaldiskmark) para determinar si requieren mantenimiento o reemplazo.

- Revise y actualice el firmware de los dispositivos, incluidos pero no limitados a NVMe, tarjetas de red (NIC), periféricos y otros. Tenga en cuenta posibles problemas reportados en reseñas o foros relacionados con versiones específicas de firmware, si aplica.

- Instale la memoria RAM en las ranuras correctas, guiándose por el manual de la placa base. Considere también el trazado de las líneas de memoria al decidir cuántos módulos utilizar.

  - Consulte la sección [Motherboard Memory Layouts | buildzoid](https://www.youtube.com/watch?v=3vQwGGbW1AE)

- Dé preferencia a los puertos PCIe que estén conectados directamente a la CPU en lugar del chipset. Esto aplica especialmente para unidades M.2, NVMe y tarjetas gráficas (GPU). Puede verificarlo en la categoría PCIe Bus usando HWiNFO. Además, asegúrese de que todos los dispositivos PCIe estén operando bajo su especificación nominal, como por ejemplo ``x16 3.0``. ([Ejemplo](/assets/images/hwinfo-pcie-width-speed.png)). El ancho de enlace y la velocidad actuales del dispositivo deben coincidir con el máximo que este soporte. En algunos casos, como en las GPU, la velocidad del enlace puede reducirse cuando están en reposo; en tales situaciones, someta el dispositivo a carga para obtener una lectura completa.

- El IRQ sharing (compartición de interrupciones) puede causar latencia alta en las interrupciones y es una fuente común de problemas de rendimiento ([1](https://repo.zenk-security.com/Linux%20et%20systemes%20d.exploitations/Windows%20Internals%20Part%201_6th%20Edition.pdf)). Para identificar conflictos de IRQ, escriba msinfo32 en la ventana de Win+R y navegue a la sección Conflicts/Sharing. Las causas pueden deberse tanto a la configuración de hardware como de software. Para aislar posibles causas relacionadas con el hardware, habilite [Message Signaled Interrupts](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044) en el dispositivo problemático y reinicie el sistema. Si después del reinicio el dispositivo sigue compartiendo una IRQ, esto puede ser indicio de una configuración incorrecta del hardware.

- Si su placa base tiene múltiples interfaces de red integradas (NICs), considere usar aquella que admita MSI-X observandolo en [MSI Utility](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044) o [GoInterruptPolicy](https://github.com/spddl/GoInterruptPolicy) ya que es un requisito para que Receive Side Scaling (RSS) funcione correctamente ([1](https://old.reddit.com/r/intel/comments/9uc03d/the_i219v_nic_on_your_new_z390_motherboard_and)).
- Asegúrese de conectar el cable Ethernet al puerto correspondiente de la NIC deseada.
  
- Evalúe y reduzca el bufferbloat, ya que es una causa de latencia elevada y variaciones en la entrega de paquetes (jitter) en redes conmutadas por paquetes, provocada por un exceso de búfer en la red ([1](https://en.wikipedia.org/wiki/Bufferbloat), [2](https://www.bufferbloat.net/projects))

  - Consulta la sección [Waveform Bufferbloat and Internet Speed Test | Waveform](https://www.waveform.com/tools/bufferbloat)
  - Consulta la sección [What Can I Do About Bufferbloat? | Bufferbloat.net](https://www.bufferbloat.net/projects/bloat/wiki/What_can_I_do_about_Bufferbloat)
  - Consulta la sección [stoplagging.com](https://www.stoplagging.com)

- Evite encadenar cables de alimentación (daisy-chain) en cualquier parte de su configuración.

  - Consulta la sección [Installation Remark for High Power Consumption Graphics Cards | Seasonic](https://knowledge.seasonic.com/article/8-installation-remark-for-high-power-consumption-graphics-cards)

- Prefiera cables blindados y evite los innecesariamente largos, ya que ofrecen mayor protección contra interferencias. ([1](https://precmfgco.com/blog/shielded-vs-unshielded-cables))

- Asegúrese de dejar un espacio moderado entre los cables para reducir el riesgo de [coupling](https://en.wikipedia.org/wiki/Coupling_(electronics))

- Limpie el polvo de los componentes y disipadores, ya que puede provocar cortocircuitos y disminuir el flujo de aire ([1](https://www.armagard.co.uk/articles/dust-computer-killer.html)). Tenga especial cuidado con el retroceso de voltaje hacia la placa base al limpiar los ventiladores del gabinete.

- Limpie los pines de contacto y conectores de los componentes. Use aire comprimido para eliminar el polvo de las ranuras antes de instalar componentes como PCIe, NVMe, RAM, entre otros.

- Conecte el cable de video a la GPU dedicada (si está presente) en lugar de a la placa base.

- Minimice la caída de la GPU usando un soporte anti-sag o similar, para evitar dañar los contactos PCIe y la ranura.

- Tenga en cuenta que las configuraciones con múltiples monitores pueden introducir sobrecarga de procesamiento. ([1](https://www.youtube.com/watch?v=5wBxYQdN96s))

<h1 id="cooling">5. Refrigeración <a href="#cooling">(permalink)</a></h1>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

- Si planeas hacer overclock, ten en cuenta los siguientes puntos para maximizar el margen térmico y el potencial de overclock. Es importante destacar que mantener temperaturas más bajas puede influir positivamente en otros factores incluso si no realizas overclock, como el comportamiento de boost del CPU, ya que dicho algoritmo es sensible a la temperatura, entre otros aspectos.

  - Retira los paneles laterales del gabinete, ya que tienden a atrapar calor, o considera usar una configuración tipo open-bench (ten cuidado con la acumulación de polvo).
  - Realiza delid al CPU y aplica metal líquido para una mejora térmica significativa, dependiendo de la calidad del IHS ([1](https://www.youtube.com/watch?v=rUy3WcDlBXE)). También vale la pena considerar el uso de direct die y lapping, aunque es fundamental que el usuario evalúe los riesgos de llevar a cabo estos procedimientos.
  - Evita los disipadores por aire tipo torre, ya que su capacidad de enfriamiento es limitada ([1](https://www.youtube.com/watch?v=Vex9_84VpYs)) y suelen obstaculizar el flujo de aire hacia otros componentes importantes como la RAM o los VRMs.
  - Retira el disipador térmico de serie de los módulos de RAM, ya que frecuentemente atrapan calor debido a que están adheridos con espuma o pegamento ([1](https://i.imgur.com/7KvbxTv.jpg)). eemplázalos por disipadores y pads térmicos de mayor calidad, ya que la RAM sin disipación adecuada puede generar puntos calientes. Considera montar un ventilador (se recomienda uno de 140 mm) sobre la RAM utilizando bridas o adaptaciones caseras.
  - Instala un ventilador dirigido hacia los VRMs, el chipset (PCH) y otras zonas críticas con alta temperatura.
  - Sustituye los thermal pads originales si no son de buena calidad.
  - Reaplica la pasta térmica de la GPU, ya que la aplicación de fábrica suele ser deficiente. Opcionalmente, reemplaza los ventiladores de serie por otros de mayor calidad.

- Considera el uso de contact frames y monturas con desplazamiento (offset mounts) si aplica en tu plataforma.

  - Considera ver: [Investigación sobre los problemas del socket de Intel | Thermal Grizzly Contact Frame Benchmark | Gamers Nexus](https://www.youtube.com/watch?v=Ysb25vsNBQI)
  - Considera ver: [Noctua lanza monturas desplazadas para mejorar el rendimiento térmico en CPUs AMD AM5 | Noctua](https://noctua.at/en/noctua-releases-offset-mounting-for-improved-cooling-performance-on-amd-am5-processors)

- Utiliza material térmico (pasta térmica) de alta calidad y asegúrate de aplicar una cantidad adecuada.

  - Considera ver: [Las mejores pastas térmicas para CPU | Tom’s Hardware](https://www.tomshardware.com/best-picks/best-thermal-paste)

- Evalúa la distribución del contacto entre el IHS/die y la base del disipador o cold plate para garantizar una transferencia térmica óptima.

- Asegúrate de montar correctamente tu sistema de refrigeración líquida (AIO).

  - Considera ver: [Deja de hacerlo mal: cómo matar tu disipador AIO | Gamers Nexus](https://www.youtube.com/watch?v=BbGomv195sk)

- Usa ventiladores sin RGB y da preferencia a aquellos con alta presión estática, ya que elementos como los filtros de malla, radiadores, aletas de disipadores y similares obstruyen el flujo de aire.

  - Considera ver: [PC Fans | Calypto](https://docs.google.com/spreadsheets/d/1AydYHI_M6ov9a3OgVuYXhLEGps0J55LniH9htAHy2wU)

- No sobrecargues los conectores de ventilador en la placa madre, especialmente si estás usando divisores (splitters).

- Usa un disipador térmico para M.2/NVMe para reducir su temperatura ([1](https://cdn.mos.cms.futurecdn.net/mftAb4ExpeZiqVnuHrAqwf-970-80.png)) y considera colocar un ventilador encima para mejorar el enfriamiento.

<h1 id="biosuefi">6. BIOS/UEFI <a href="#biosuefi">(permalink)</a></h1>

Como regla general, asegúrate de que cualquier configuración que modifiques genere una mejora tangible en el rendimiento, y toma nota de los cambios realizados para poder revertirlos fácilmente en caso de problemas. Si estás partiendo de un sistema ya usado o con múltiples ajustes previos, se recomienda restablecer todos los valores a su estado de fábrica para empezar desde una base limpia, especialmente si sospechas que algo pudo haber quedado mal configurado desde el inicio.

<h2 id="partition-style">6.1. Estilo de Partición <a href="#partition-style">(permalink)</a></h2>

Si aún no estás utilizando el estilo de partición adecuado para tu sistema, ahora es el momento de cambiarlo, ya que algunos ajustes de esta sección dependen de ello (busca "GPT/UEFI" en esta misma sección). GPT con arranque UEFI es generalmente la opción más recomendable, ya que ofrece mejor compatibilidad y soporte moderno ([1](https://www.diskpart.com/gpt-mbr/mbr-vs-gpt-1004.html)). Puedes verificar el estilo de partición actual ejecutando ``msinfo32`` desde el cuadro de diálogo ``Win+R``. El método recomendado para convertir un disco a GPT es limpiar y convertirlo desde el instalador de Windows utilizando ``diskpart`` ([1](https://learn.microsoft.com/en-us/windows-server/storage/disk-management/change-an-mbr-disk-into-a-gpt-disk)).

- Ver también: [Cómo convertir MBR a GPT durante la instalación de Windows | MDTechVideos](https://www.youtube.com/watch?v=f81qKAJUdKc)

<h2 id="consider-windows-version">6.2. Considerar la Versión de Windows <a href="#consider-windows-version">(permalink)</a></h2>

Asimismo, considera qué versión de Windows vas a utilizar, ya que ciertos ajustes también dependen de ello  [¿Qué versión de Windows deberías usar? ](#what-version-of-windows-should-you-use) para ayudarte a decidir cuál se adapta mejor a tus necesidades.

<h2 id="bios-recovery-methods">6.3. Métodos de recuperación de BIOS <a href="#bios-recovery-methods">(permalink)</a></h2>

Modificar la BIOS siempre conlleva ciertos riesgos. Antes de hacer cambios importantes, asegúrate de conocer métodos seguros para restaurarla, como el uso de la función USB Flashback o un programador SPI como el [CH341A](https://www.techinferno.com/index.php?/topic/12230-some-guide-how-to-use-spi-programmer-ch341a), en caso de que limpiar el CMOS [1.](https://www.intel.co.uk/content/www/uk/en/support/articles/000025368/processors.html) no sea suficiente para revertir los cambios.

<h2 id="bios-updates">6.4. Actualizaciones de BIOS <a href="#bios-updates">(permalink)</a></h2>

Por último, revisa si existen actualizaciones de BIOS disponibles y lee detalladamente los registros de cambios, especialmente si se menciona una mejora en la estabilidad de la memoria u otros aspectos relevantes. No olvides consultar foros y reseñas para asegurarte de que la versión que vas a instalar no tenga problemas conocidos.

<h2 id="bios-microcode">6.5. Microcódigo de BIOS <a href="#bios-microcode">(permalink)</a></h2>

> [!WARNING]
> 🔒 Actualizar o degradar el microcódigo del procesador puede afectar negativamente la seguridad del sistema y exponerlo a vulnerabilidades. Se recomienda que el usuario evalúe cuidadosamente los riesgos de seguridad antes de modificar esta configuración.

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

En plataformas y procesadores mucho más antiguos, los parches a nivel de BIOS contra Spectre, Meltdown y otras vulnerabilidades similares podían tener un impacto considerable en el rendimiento. Sin embargo, en sistemas modernos esto ya no suele ser un factor tan determinante. La función de validación de [CPU-Z's](https://www.cpuid.com/softwares/cpu-z.html) permite visualizar la versión del microcódigo actual, y en el pasado era posible modificarlo utilizando herramientas como [MMTool](https://www.ami.com/blog/2017/10/30/what-is-mmtool). Aun así, en plataformas actuales este tipo de modificación rara vez es necesaria, y se menciona aquí únicamente con fines informativos.

<h2 id="accessing-hidden-options">6.6. Acceder a opciones ocultas <a href="#accessing-hidden-options">(permalink)</a></h2>

Los fabricantes de placas base suelen ocultar muchas configuraciones para que no estén visibles al usuario estándar. En este contexto, "desbloquear la BIOS" implica hacer visibles y accesibles estas configuraciones ocultas. La forma más sencilla de hacerlo es modificando los niveles de acceso dentro del firmware con [UEFI-Editor](https://github.com/BoringBoredom/UEFI-Editor#usage-guide) y luego flashearlo, lo cual permitirá que dichas opciones se muestren directamente en el menú UEFI. Otra opción consiste en modificar lo que ya está disponible y luego acceder a las opciones ocultas leyendo y escribiendo en la NVRAM mediante [GRUB](https://github.com/BoringBoredom/UEFI-Editor#how-to-change-hidden-settings-without-flashing-a-modded-bios) ([script generator](https://github.com/ab3lkaizen/setupvar-builder)) o [SCEWIN](https://github.com/ab3lkaizen/SCEHUB).

<h2 id="unnecessary-devices">6.7. Dispositivos innecesarios <a href="#unnecessary-devices">(permalink)</a></h2>

GComo regla general, aplica el principio de "si no lo usas, desactívalo". Si es posible, es mejor desconectar físicamente los componentes no utilizados, aunque también es válido deshabilitarlos desde la BIOS. Esto incluye, entre otros: adaptadores de red (NICs), Wi-Fi, Bluetooth, controladores de audio de alta definición (si no se usa el audio de la placa), gráficos integrados, puertos SATA, ranuras de RAM, y dispositivos integrados visibles en [USB Device Tree Viewer](https://www.uwe-sieber.de/usbtreeview_e.html) (como controladores RGB, receptores IR, etc.). Ten en cuenta que en algunas placas base el controlador de audio de alta definición puede estar vinculado al controlador USB (referencia), por lo que puede aparecer en dicho árbol como un dispositivo USB. ([1](https://www.igorslab.de/en/the-old-alc4080-on-the-new-intel-boards-demystified-and-the-differences-from-alc1220-insider)). Así que no te confundas si se encuentra en el árbol de dispositivos USB.

<h2 id="resizable-bar">6.8. Resizable Bar (ReBAR) <a href="#resizable-bar">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Consulta [este artículo](https://www.howtogeek.com/819578/what-is-resizable-bar-on-a-gpu) para obtener una visión general de qué es Resizable BAR (ReBAR). Es importante destacar que ReBAR puede provocar una pérdida de rendimiento en ciertos juegos ([1](https://www.techspot.com/review/2234-nvidia-resizable-bar)) por lo tanto, es recomendable hacer tus propias pruebas para decidir si mantenerlo habilitado.

ReBAR requiere que el sistema esté en modo BIOS UEFI con particiones GPT, además de tener activada la opción `Above 4G Decoding`  Si tu placa base no lo soporta de forma nativa, puedes considerar usar herramientas como [ReBarUEFI](https://github.com/xCuri0/ReBarUEFI)/[NvStrapsReBar](https://github.com/terminatorul/NvStrapsReBar). Para verificar si Resizable BAR está habilitado, consulta el estado desde [GPU-Z](https://www.techpowerup.com/gpuz).

<h2 id="hyper-threadingsimultaneous-multithreading">6.9. Hyper-Threading/Simultaneous Multithreading <a href="#hyper-threadingsimultaneous-multithreading">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Si tu aplicación no depende intensamente del uso de múltiples hilos por núcleo, considera desactivar [Hyper-Threading (HT)/Simultaneous Multithreading (SMT)](https://en.wikipedia.org/wiki/Hyper-threading). Esta función resulta útil en tareas altamente paralelizables como la codificación, compilación y renderizado; sin embargo, el uso de múltiples hilos por núcleo puede aumentar la contención de recursos internos del procesador y es una posible fuente de latencia e inestabilidad del sistema ([1](https://www.intel.com/content/www/us/en/developer/articles/technical/optimizing-computer-applications-for-latency-part-1-configuring-the-hardware.html)). Además, desactivar HT/SMT puede mejorar el potencial de overclocking debido a una menor generación de calor, lo cual puede traducirse en mejoras o pérdidas de rendimiento dependiendo del juego o la aplicación. Por tanto, se recomienda realizar pruebas comparativas antes de desactivarlo.

<h2 id="power-states">6.10. Estados de Energía <a href="#power-states">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Por completar.

<h2 id="virtualizationsvm-mode">6.11. Virtualización/Modo SVM <a href="#virtualizationsvm-mode">(permalink)</a></h2>

Desactiva [Virtualization/SVM Mode](https://en.wikipedia.org/wiki/Desktop_virtualization) y [Intel VT-d/AMD-Vi](https://en.wikipedia.org/wiki/X86_virtualization#I/O_MMU_virtualization_(AMD-Vi_and_Intel_VT-d)) si no utilizas máquinas virtuales, ya que estas tecnologías pueden introducir latencias adicionales en el acceso a la memoria ([1](https://web.archive.org/web/20190403122634/https://www.amd.com/system/files/TechDocs/56263-EPYC-performance-tuning-app-note.pdf)). También pueden provocar fluctuaciones en la frecuencia base del sistema (BCLK) ([1](https://linustechtips.com/topic/1479168-issue-enabling-svm-virtualization-causes-bclk-to-fluctuate-a-lot)). Puedes verificar si la virtualización está habilitada en el Administrador de Tareas, en la pestaña "Rendimiento" > CPU.

<h2 id="power-saving">6.12. Ahorros de Energía <a href="#power-saving">(permalink)</a></h2>

Las funciones de ahorro de energía no tienen cabida en sistemas que ejecutan tareas en tiempo real. Estas características pueden denominarse de diversas formas, incluyendo [ASPM (Active State Power Management)](https://en.wikipedia.org/wiki/Active_State_Power_Management) (por ejemplo, buscar *L0*, *L1*), [ALPM (Aggressive Link Power Management)](https://en.wikipedia.org/wiki/Aggressive_Link_Power_Management), Power/Clock Gating, entre otras. También pueden aparecer como "power saving". Si tienes dudas sobre una configuración específica, busca su descripción en internet para verificar si pertenece a esta categoría.

<h2 id="trusted-platform-module-tpm">6.13. Módulo de Plataforma Segura (TPM) <a href="#trusted-platform-module-tpm">(permalink)</a></h2>

> [!WARNING]
> 🔒 Desactivar el TPM (Trusted Platform Module) puede comprometer la seguridad del sistema. Evalúa cuidadosamente los riesgos antes de modificar esta opción.

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Desactiva el TPM si estás priorizando rendimiento de baja latencia. Este módulo puede generar interrupciones del tipo System Management Interrupts (SMIs) ([1](https://youtu.be/X72LgcMpM9k?si=A5Kl5NmU5f1WzZP4&t=2060)) estas son interrupciones hardware de máxima prioridad que no pueden desactivarse, cuando ocurren, obligan al CPU a pausar instantáneamente todas sus operaciones, incluso las del sistema operativo ([1](https://wiki.linuxfoundation.org/realtime/documentation/howto/debugging/smi-latency/smi)). Sin embargo, en Windows 11 algunos sistemas antitrampas como Vanguard (Valorant), FACEIT o THE FINALS requieren que el TPM esté activado. Para verificar su estado, presiona ``Win+R`` escribe ``tpm.msc``y presiona Enter.

<h2 id="compatibility-support-module-csm">6.14. Módulo de Compatibilidad (CSM) <a href="#compatibility-support-module-csm">(permalink)</a></h2>

El modo MBR/Legacy requiere que el Compatibility Support Module (CSM) esté habilitado. Generalmente, basta con activar solo los OpROM de almacenamiento y PCIe, aunque puedes habilitar todos si no estás seguro. Desactiva el CSM si estás usando GPT/UEFI, excepto en el caso de Windows 7 GPT/UEFI, que requiere CSM y OpROMs a menos que uses [uefiseven](https://github.com/manatails/uefiseven). Recuerda que ReBAR también requiere que el CSM esté deshabilitado.

<h2 id="secure-boot">6.15. Secure Boot <a href="#secure-boot">(permalink)</a></h2>

> [!WARNING]
> 🔒 Desactivar el arranque seguro (Secure Boot) puede comprometer la seguridad del sistema. Evalúa los riesgos antes de hacerlo.

En Windows 11, algunos sistemas antitrampas (Vanguard, FACEIT, THE FINALS) requieren que el arranque seguro esté activado. Si alguna herramienta booteable falla por culpa del arranque seguro, se recomienda desactivarlo temporalmente en lugar de modificar certificados o claves, ya que esto puede ocasionar problemas adicionales. Para comprobar si está habilitado, abre ``msinfo32`` desde ``Win+R`` y revisa el valor de “Arranque seguro”.

<h2 id="fast-startup-standby-and-hibernate">6.16. Inicio rápido, suspensión e hibernación <a href="#fast-startup-standby-and-hibernate">(permalink)</a></h2>

Este apartado depende de la preferencia personal, percepción y experiencia del usuario. Algunas personas prefieren no usar funciones como el inicio rápido (Fast Startup), suspensión y hibernación, ya que pueden provocar problemas inesperados ([explicación](https://www.youtube.com/watch?v=OBGxt8zhbRk)), y en su lugar optan por realizar arranques limpios que no reutilizan estados previos del núcleo y del software. Esto limita los estados de energía del sistema a S0 (encendido) y S5 (apagado suave). Puedes aprender más sobre los estados de energía del sistema en [este enlace oficial de Microsoft](https://learn.microsoft.com/en-us/windows/win32/power/system-power-states) y [esta referencia técnica.](https://www.sciencedirect.com/topics/computer-science/sleeping-state). En la BIOS, estas opciones suelen denominarse Fast Startup, Suspend to RAM, S-States (*S1*, *S2*, *S3*, *S4*, *S5*), standby, o similares. Puedes verificar los estados de suspensión disponibles en tu sistema ejecutando el siguiente comando  ``powercfg /a`` en el CMD:

Windows también ofrece una opción para deshabilitar el inicio rápido y la hibernación, además de eliminar el archivo ``C:\hiberfil.sys``:

```bat
powercfg /h off
```

<h2 id="spread-spectrum">6.17. Spread Spectrum <a href="#spread-spectrum">(permalink)</a></h2>

Desactiva el Spread Spectrum ([más información aqui](https://en.wikipedia.org/wiki/Spread_spectrum#Effect)) y asegúrate de que la frecuencia del BCLK esté lo más cercana posible al valor deseado (por ejemplo, 100 MHz en lugar de 99.97 MHz), lo cual puedes verificar con [CPU-Z](https://www.cpuid.com/softwares/cpu-z.html). Sin embargo, esto depende en gran medida del sistema y la placa base.

<h2 id="legacy-usb-support">6.18. Legacy USB Support <a href="#legacy-usb-support">(permalink)</a></h2>

Desactiva el Legacy USB Support, ya que puede hacer que el sistema entre en System Management Mode (SMM) mediante System Management Interrupts (SMIs) ([1](https://patents.google.com/patent/US6067589), [2](https://www.kernel.org/doc/Documentation/x86/usb-legacy-support.txt)) que son interrupciones de hardware de alta prioridad no enmascarables que hacen que la CPU suspenda inmediatamente todas las demás actividades, incluido el sistema operativo ([1](https://wiki.linuxfoundation.org/realtime/documentation/howto/debugging/smi-latency/smi)). Es posible que necesites activarlo para instalar un nuevo sistema operativo, acceder a la BIOS o usar dispositivos USB en algunos casos.

<h2 id="software-installation-options">6.19. Opciones de instalación del software <a href="#software-installation-options">(permalink)</a></h2>

Si existen opciones relacionadas con instalación de software (por ejemplo, ASUS Armoury Crate), desactívalas. Este tipo de software suele clasificarse como bloatware y puede evitarse sin problemas. Están presentes en distintas BIOS como las de ([ASUS](https://www.asus.com/support/faq/1043788), [Gigabyte](https://old.reddit.com/r/gigabyte/comments/106d9ns/gigabyte_control_center_prompt_to_install_every/ja0gc6l), [MSI](https://old.reddit.com/r/MSI_Gaming/comments/14s7so7/how_to_disable_autoinstall_of_msi_center/l6zoigh), [ASRock](https://old.reddit.com/r/ASRock/comments/1bxf8jt/asrock_auto_driver_install_app/kyc904r)).

<h2 id="pci-link-speed-for-devices">6.20. Velocidad del enlace pci para dispositivos <a href="#pci-link-speed-for-devices">(permalink)</a></h2>

Configura la velocidad de enlace PCIe al valor máximo soportado, como por ejemplo Gen ``Gen 4.0``. Esto puede estar representado como gigatransferencias por segundo (GT/s) ([1](https://en.wikipedia.org/wiki/PCI_Express#Comparison_table)). Esto ayuda a evitar comportamientos inesperados y problemas.

<h2 id="fan-curves">6.21. Curvas de ventilación <a href="#fan-curves">(permalink)</a></h2>

Para maximizar el potencial de refrigeración, configura las curvas de ventilador ([ejemplo](https://imgur.com/a/2UDYXp0)) o ajusta una velocidad estática alta aceptable en cuanto a ruido. Si usas un sistema AIO, configura la bomba a velocidad máxima.

<h2 id="bios-profiles-and-backups">6.22. Perfiles y copias de seguridad de BIOS <a href="#bios-profiles-and-backups">(permalink)</a></h2>

Haz una copia de seguridad del BIOS guardando la configuración actual en un perfil o exportándola a un almacenamiento local, ya que limpiar el CMOS eliminará toda la configuración si necesitas hacerlo (por ejemplo, durante el overclocking).

En mi experiencia con varias placas base, cargar un perfil guardado no siempre restaura correctamente ciertos ajustes después de limpiar el CMOS. Recomiendo volcar la NVRAM utilizando una herramienta como  [SCEWIN](https://github.com/ab3lkaizen/SCEHUB), de forma que al restaurar un perfil, puedas volver a hacer un volcado de NVRAM y compararlo con el exportado previamente usando una herramienta de comparación de texto como el complemento ComparePlus de [Notepad++ Compare plugin](https://sourceforge.net/projects/npp-compare) o [Visual Studio Code](https://code.visualstudio.com/download).

<h1 id="configure-usb-port-layout">7. Configuración de puertos usb <a href="#configure-usb-port-layout">(permalink)</a></h1>

<h2 id="reviewing-accessible-usb-ports">7.1. Revisión de los puertos usb accesibles <a href="#reviewing-accessible-usb-ports">(permalink)</a></h2>

Primero, familiarízate con qué puertos USB físicos corresponden a cada controlador USB, ya que algunos puertos mostrados en [USB Device Tree Viewer](https://www.uwe-sieber.de/usbtreeview_e.html) podrían no ser accesibles físicamente. Se recomienda conectar un dispositivo a cada puerto accesible del sistema, como los del panel I/O de la placa base y los del panel frontal, y luego anotar a qué controlador y puerto corresponde cada uno en USB Device Tree Viewer.

<h2 id="layout-planning">7.2. Planificación de la Distribución <a href="#layout-planning">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Luego, planifica y decide a qué controladores USB deseas conectar tus dispositivos, pero no los conectes todavía. En cuanto a qué controladores USB usar, eso queda a tu criterio. Si tienes más de un controlador USB, puedes aislar dispositivos como el ratón, teclado y dispositivos de audio en otro controlador USB, ya que tienen el potencial de interferir con la consistencia del polling ([1](https://forums.blurbusters.com/viewtopic.php?f=10&t=7618#p58449)). Se pueden obtener más controladores USB utilizando tarjetas de expansión PCIe o conectores USB 2.0 y 3.0 externos en la placa base. Siempre verifica esta información con [USB Device Tree Viewer](https://www.uwe-sieber.de/usbtreeview_e.html). Los sistemas Ryzen disponen de un controlador USB conectado directamente al CPU ([1](https://hexus.net/tech/features/mainboard/131789-amd-ryzen-3000-supporting-x570-chipset-examined)) el cual puede identificarse en la categoría PCIe Bus en [HWiNFO](https://www.hwinfo.com). Suele ser el controlador USB conectado a un ``Internal PCIe Bridge to bus`` el cual también está etiquetado con la arquitectura del CPU ([1](/assets/images/ryzen-cpu-usb-controller.png)).

<h2 id="plugging-in-devices">7.3. Conexión de Dispositivos <a href="#plugging-in-devices">(permalink)</a></h2>

Por último, conecta los dispositivos a los puertos y controladores USB que decidiste usar. En cualquier caso, considera utilizar primero los puertos que estén más cercanos a la raíz del árbol del hub del controlador USB. Además, también se recomienda evitar los hubs internos ([1](/assets/images/usb-hub-internal-headers.png)).

<h1 id="configure-peripherals">8. Configurar Periféricos <a href="#configure-peripherals">(permalink)</a></h1>

<h2 id="cleaning">8.1. Limpieza <a href="#cleaning">(permalink)</a></h2>

Utiliza con cuidado un [soplador de aire](https://www.amazon.com/s?k=air+dust+blower) para eliminar suciedad y residuos del lente del sensor del ratón sin dañarlo.

<h2 id="onboard-memory-profiles">8.2. Perfiles de Memoria Integrada <a href="#onboard-memory-profiles">(permalink)</a></h2>

La mayoría de los periféricos modernos como ratones y teclados admiten perfiles con memoria integrada. Configúralos antes de configurar el sistema operativo, ya que así evitarás tener que instalar software innecesario como Razer Synapse para modificar los ajustes más adelante. Se abordarán más adelante los detalles sobre cómo separar entornos sin bloatware y con bloatware mediante arranque dual. Alternativamente, puedes limitar el uso del software con bloat a un USB con Windows de arranque ([Windows To Go](https://www.youtube.com/watch?v=w34x1kBZN6c)).

<h2 id="rgb-lighting-effects">8.3. Efectos de Iluminación RGB <a href="#rgb-lighting-effects">(permalink)</a></h2>

Las especificaciones USB 2.0/3.0 están limitadas a 0.5 A y 0.9 A respectivamente ([1](https://en.wikipedia.org/wiki/USB)) y la iluminación RGB consume energía innecesaria. Apaga los efectos de iluminación o retira el LED del periférico, ya que ejecutar efectos/animaciones RGB puede afectar gravemente al microcontrolador (MCU), introduciendo demoras en otros procesos ([1](https://wooting.io/post/what-influences-keyboard-speed), [2](https://www.techpowerup.com/review/endgame-gear-xm1-rgb/5.html#:~:text=tracking%20quality%20takes%20a%20hit%20as%20soon%20as%20RGB%20is%20enabled), [3](https://www.techpowerup.com/review/roccat-kone-pro-air/5.html#:~:text=after%20having%20disabled%20all%20RGB%20lighting,%20these%20outliers%20disappeared%20entirely)).

<h2 id="dpi">8.4. DPI <a href="#dpi">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Un DPI más alto en el sensor reduce la latencia y ayuda a saturar los sondeos con datos de movimiento ([1](https://www.youtube.com/watch?v=6AoRfv9W110), [2](https://www.youtube.com/watch?v=mwf_F2VboFQ&t=458s), [3](https://www.youtube.com/watch?v=imYBTj2RXFs&t=275s)). Evita la reducción de jitter (por ejemplo, reducción de DPI) y el [sensor smoothing](https://old.reddit.com/r/MouseReview/comments/5haxn4/sensor_smoothing) que puede activarse con valores de DPI más altos.  Si tu juego utiliza entrada sin procesar (raw input) puedes reducir la velocidad del puntero en Windows para compensar la sensibilidad de un DPI más alto [calculadora](https://boringboredom.github.io/tools/winsenscalculator) De lo contrario, deja el control deslizante en su posición predeterminada, ya que el escalado puede afectar negativamente la entrada. Una forma de saber si una aplicación usa entrada sin procesar es espiar las llamadas a la API raw input con [API Monitor](http://www.rohitab.com/apimonitor) o verificar si la opción de “mejorar la precisión del puntero” tiene algún efecto en el juego. Si aún tienes dudas, deja el control deslizante en la posición predeterminada.

<h2 id="report-rate">8.5. Tasa de Sondeo <a href="#report-rate">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Tasas de sondeo más altas (polling rate) reducen jitter y latencia ([1](https://www.youtube.com/watch?app=desktop&v=djCLZ6qEVuA), [2](https://www.youtube.com/watch?v=mwf_F2VboFQ&t=458s), [3](https://www.youtube.com/watch?v=mwf_F2VboFQ&t=618s)). Sin embargo, tasas de sondeo elevadas pueden afectar negativamente el rendimiento dependiendo del hardware y la configuración general, así que ajusta según sea necesario.

<h2 id="polling-stability-analysis">8.6. Análisis de Estabilidad del Polling <a href="#polling-stability-analysis">(permalink)</a></h2>

Utiliza [Mouse Tester](https://github.com/valleyofdoom/MouseTester) para verificar si cada sondeo contiene datos. Por ejemplo, si el intervalo sube a 2 ms (500 Hz) o más desde 1 ms (1 kHz), esto no es un comportamiento esperado y es problemático. Esto puede deberse a múltiples variables, como el propio dispositivo (por ejemplo, sensor defectuoso), cable, problemas de alimentación, hardware, sistema operativo, entre otros. Puede que necesites reducir o desactivar la moderación de interrupciones USB utilizando el script [XHCI-IMOD-Interval.ps1](/bin/XHCI-IMOD-Interval.ps1), especialmente si hay múltiples dispositivos generando interrupciones en el mismo controlador USB o si las interrupciones del ratón se generan a una frecuencia igual o superior al intervalo IMOD predeterminado durante el benchmark, lo cual activa la moderación IMOD.

<h2 id="monitor">8.7. Monitor <a href="#monitor">(permalink)</a></h2>

Opcionalmente, restablece tu monitor a la configuración de fábrica y reconfigúralo en caso de que haya algo mal configurado desde el inicio. La tecnología Overdrive/AMA reduce la latencia ([1](https://twitter.com/CaIypto/status/1464236780190851078)) sin embargo, esto puede venir acompañado de un exceso de compensación (overshoot). Además, puedes intentar calibrarlo. Opcionalmente, haz overclock al monitor con  [Custom Resolution Utility](https://www.monitortests.com/forum/Thread-Custom-Resolution-Utility-CRU) y realiza pruebas de [frame skipping](https://www.testufo.com/frameskipping). Apunta a una frecuencia de actualización entera real como 60.00 Hz o 240.00 Hz, y no valores como 59.94 o 239.76.

- Ver: [Can You Calibrate a Monitor WITHOUT a Colorimeter? | techless](https://www.youtube.com/watch?v=avJTz1JhkR4)

<h1 id="stability-hardware-clocking-and-thermal-performance">9. Estabilidad, Overclock y Rendimiento Térmico <a href="#stability-hardware-clocking-and-thermal-performance">(permalink)</a></h1>

Asegúrate de que todo tu hardware sea estable antes de configurar un nuevo sistema operativo, ya que un hardware inestable puede causar fallos, corrupción de datos, menor rendimiento o incluso daños indirectos irreversibles en el hardware. La eficacia de las herramientas de prueba de estabilidad varía entre sí, por lo cual es importante usar una variedad de ellas durante suficiente tiempo (una lista no exhaustiva de herramientas recomendadas se incluye más abajo).

<h2 id="temporary-operating-system">9.1. Sistema Operativo Temporal <a href="#temporary-operating-system">(permalink)</a></h2>

Es altamente recomendable configurar un arranque dual temporal con una instalación limpia de Windows o usar un USB booteable con Windows ([Windows To Go](https://www.youtube.com/watch?v=w34x1kBZN6c)) para evitar corromper tu sistema principal mientras realizas pruebas de estrés y overclock. Para las pruebas de memoria, esto también permite que el test use más RAM, ya que no estará ocupada por bloatware potencial en tu instalación actual. El modo seguro también puede servir como entorno de prueba mínimo, pero cierto software puede no funcionar.

<h2 id="general-information">9.2. Información General <a href="#general-information">(permalink)</a></h2>

- Verifica y valida los cambios dentro del software para evitar resultados y comportamientos inesperados (por ejemplo, frecuencia, voltajes, timings).

- Guarda un perfil de BIOS antes de cada cambio cuando hagas overclock, como al modificar frecuencia o timings de CPU/RAM, para no perder el progreso si necesitas hacer un clear CMOS. Consulta la sección [Perfiles y copias de seguridad del BIOS](#bios-profiles-and-backups) sobre cómo restaurar correctamente la configuración.

- Al hacer overclock, puede que necesites aumentar los límites de potencia si se superan los valores predeterminados.

- Utiliza [HWiNFO](https://www.hwinfo.com) para monitorear los sensores del sistema. Un mayor intervalo de sondeo puede ayudar a identificar picos súbitos, aunque no transitorios en escala de microsegundos. Evita ejecutarlo mientras haces benchmarks, ya que puede afectar la fiabilidad de los resultados.

- Un solo error o cuelgue ya es demasiado. Monitorea los errores WHEA con el contador de errores de [HWiNFO](https://www.hwinfo.com) o crea un filtro en el Visor de Eventos.

- Supervisa voltajes donde sea aplicable para evitar sobrevoltajes.

- Hay incontables factores que influyen en la estabilidad, como la temperatura, la entrega de energía, la calidad general del hardware, la lotería del silicio y más.

<h2 id="error-correction">9.3. Corrección de Errores <a href="#error-correction">(permalink)</a></h2>

El overclocking no garantiza mejor rendimiento, especialmente si entran en juego mecanismos como la corrección de errores. Verifica si los cambios que estás haciendo escalan positivamente mediante una metodología de benchmarking sistemática.

<h2 id="thermal-management">9.4. Gestión Térmica <a href="#thermal-management">(permalink)</a></h2>

Evita el thermal throttling a toda costa. Recuerda que la temperatura ambiente aumenta durante el verano. Realiza underclock intencionalmente si tu sistema de refrigeración es inadecuado. Un componente térmicamente estable con menor frecuencia es preferible a uno que se acelera térmicamente a mayor frecuencia/voltaje. Para aplicar estrés térmico adicional al afinar componentes (como CPU, RAM, GPU), considera apagar ventiladores de gabinete/RAM, reducir las RPM o generar más calor (por ejemplo, cargando la GPU, usando calefactores) durante las pruebas de estrés.

- Ver: [Estabilidad del overclock de RAM y gestión térmica | buildzoid](https://www.youtube.com/watch?v=iCD0ih4qzHw)

<h2 id="load-line-calibration">9.5. Calibración de la Línea de Carga (LLC) <a href="#load-line-calibration">(permalink)</a></h2>

Esta no es una recomendación de qué modo de LLC usar, sino que se proporciona solo con fines informativos.

- Ver: [VRM Load-Line Visualized | ElmorLabs](https://elmorlabs.com/2019-09-05/vrm-load-line-visualized)
- Ver: [Vdroop setting and it’s impact on CPU operation | xDevs](https://xdevs.com/guide/e399ocg/#vdroop)
- Ver: [Why Vdroop is good for overclocking and taking a look at Gigabyte's Override Vcore mode | buildzoid](https://www.youtube.com/watch?v=zqvNkh4TVw8)

<h2 id="gpu">9.6. GPU <a href="#gpu">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Cuando hagas overclock a la GPU, puede que necesites flashear un BIOS con mayor límite de potencia o elevar manualmente dichos límites.

- En sistemas NVIDIA, asegúrate de desactivar ``CUDA - Force P2 State`` con [NVIDIA Profile Inspector](https://github.com/Orbmu2k/nvidiaProfileInspector) para evitar que la memoria baje de frecuencia durante pruebas de estrés ([1](/assets/images/cuda-force-p2-state-analysis.png))
- Ver: [A Slightly Better Way To Overclock and Tweak Your Nvidia GPU | Cancerogeno](https://docs.google.com/document/d/14ma-_Os3rNzio85yBemD-YSpF_1z75mZJz1UdzmW8GE/edit)
- Ver: [LunarPSD/NvidiaOverclocking](https://github.com/LunarPSD/NvidiaOverclocking/blob/main/Nvidia%20Overclocking.md)

<h2 id="ramcpu">9.7. RAM/CPU <a href="#ramcpu">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

- Asegúrate de que tu CPU puede hacer boost correctamente antes de comenzar, en caso de que hayas desactivado opciones como SpeedStep y Speed Shift, las cuales pueden impedir que el procesador supere su frecuencia base.

- Configura manualmente la frecuencia y los timings de la RAM para obtener una mejora de rendimiento significativa ([1](https://kingfaris.co.uk/blog/intel-ram-oc-impact)). XMP no ajusta muchos de los timings, ni garantiza estabilidad.

  - Consulta la [Eden’s DDR4 guide](https://web.archive.org/web/20231211232729/https://cdn.discordapp.com/attachments/328891236918493184/1172922515962724444/DDR4_Guide_V1.2.1.pdf)
  - Consulta [KoTbelowall/INTEL-DDR4-RAM-OC-GUIDE-by-KoT](https://github.com/KoTbelowall/INTEL-DDR4-RAM-OC-GUIDE-by-KoT)
  - Consulta [integralfx/MemTestHelper](https://github.com/integralfx/MemTestHelper/blob/oc-guide/DDR4%20OC%20Guide.md)

- Configura frecuencias y voltajes estáticos para todos los núcleos del CPU. Las variaciones en las frecuencias del hardware pueden introducir jitter debido al proceso de transiciones de frecuencia. [Precision Boost Overdrive](https://www.amd.com/en/support/kb/faq/cpu-pb2) para CPUs Ryzen es una alternativa a frecuencias y voltajes estáticos, y a menudo se recomienda.

- Los dos puntos anteriores se afectan mutuamente en términos de estabilidad, lo cual significa que tu overclock de RAM puede volverse inestable después de ajustar la CPU, por lo que deberás ejecutar pruebas de estrés nuevamente y ajustar los parámetros del CPU si es necesario.

<h2 id="stress-testing-tools">9.8. Herramientas para pruebas de Estrés <a href="#stress-testing-tools">(permalink)</a></h2>

- [StresKit]((https://github.com/valleyofdoom/StresKit)) (bootable)

- Linpack

  - [StresKit](https://github.com/valleyofdoom/StresKit)'s Linpack
  - [Linpack-Extended](https://github.com/BoringBoredom/Linpack-Extended)
  - [Linpack Xtreme Bootable](https://www.techpowerup.com/download/linpack-xtreme)
  - Utiliza diferentes tamaños de memoria durante las pruebas
  - Los residuales deben coincidir; de lo contrario, puede ser señal de inestabilidad
  - La variación de GFLOP debe ser mínima
    
- [Prime95](https://www.mersenne.org/download)

- [FIRESTARTER](https://github.com/tud-zih-energy/FIRESTARTER)

- [y-cruncher](http://www.numberworld.org/y-cruncher)

- [Memory Testing Software](https://github.com/integralfx/MemTestHelper/blob/oc-guide/DDR4%20OC%20Guide.md#memory-testing-software)

  - [HCI](https://hcidesign.com/memtest)
  - [MemTest86](https://www.memtest86.com) (bootable)
  - [MemTest86+](https://memtest.org) (bootable)

- [UNIGINE Superposition](https://benchmark.unigine.com/superposition)

- [OCCT](https://www.ocbase.com)

- [memtest_vulkan](https://github.com/GpuZelenograd/memtest_vulkan)

<h1 id="install-windows">10. Instalar Windows <a href="#install-windows">(permalink)</a></h1>

<h2 id="storage-partitions">10.1. Particiones de Almacenamiento <a href="#storage-partitions">(permalink)</a></h2>

Configura un sistema con [multi-boot](https://en.wikipedia.org/wiki/Multi-booting) para mantener entornos separados para trabajo/bloatware y juegos, asegurando que el entorno para juegos permanezca libre de software innecesario. Esto permite mantener limpia la partición de juegos sin sacrificar la usabilidad general. Para lograrlo, reduce el tamaño de un volumen en el Administrador de discos ([1](https://docs.microsoft.com/en-us/windows-server/storage/disk-management/shrink-a-basic-volume)) para crear espacio no asignado donde instalar el nuevo sistema operativo.

<h2 id="what-version-of-windows-should-you-use">10.2. ¿Qué Versión de Windows Deberías Usar? <a href="#what-version-of-windows-should-you-use">(permalink)</a></h2>

Esta sección contiene puntos importantes a considerar recopilados a lo largo de los años sobre versiones de Windows, compatibilidad y funciones exclusivas:

- Las versiones antiguas de Windows carecen de soporte para anticheats (debido a la falta de actualizaciones de seguridad tras el fin del soporte), controladores (comúnmente GPU y NIC) y aplicaciones en general, por lo que algunos usuarios se ven forzados a usar versiones más recientes. Consulta la siguiente tabla para conocer la versión mínima requerida para instalar controladores en ciertas GPUs. Sujeto a cambios.

    |GPU|Versión mínima de Windows|
    |---|---|
    |NVIDIA 10 Series y versiones inferiores | Compatible con casi todas las versiones de Windows|
    |NVIDIA 16, 20 series|Win7, Win8, Win10 1709+|
    |NVIDIA 30 series|Win7, Win10 1803+|
    |NVIDIA 40 series|Win10 1803+|
    |AMD|Consulte la página de soporte del controlador|

- Windows Server no tiene soporte para muchas NICs de consumo. Los métodos alternativos como  [este](https://github.com/loopback-kr/Intel-I219-V-for-Windows-Server) suelen interferir con anticheats debido a certificados de firma no válidos.

- Los drivers NVIDIA DCH son compatibles a partir de Windows 10 1803+ ([1](https://nvidia.custhelp.com/app/answers/detail/a_id/4777/~/nvidia-dch%2Fstandard-display-drivers-for-windows-10-faq))

- Durante la reproducción de contenido multimedia exclusivamente en Windows 10 1709, el [Multimedia Class Scheduler Service](https://learn.microsoft.com/en-us/windows/win32/procthread/multimedia-class-scheduler-service) eleva la resolución del temporizador a 0.5ms, lo que limita el control respecto a la resolución solicitada.

- Windows 10 1809+ es requerido para trazado de rayos (Ray Tracing) en GPUs NVIDIA

- Microsoft implementó una frecuencia fija de 10 MHz para QueryPerformanceFrequency en Windows 10 1809+

- Windows 10 1903+ tiene un planificador actualizado para CPUs Ryzen con múltiples CCX ([1](https://i.redd.it/y8nxtm08um331.png))

- DirectStorage requiere Windows 10 1909+, pero según un artículo, los juegos que se ejecutan en Windows 11 se benefician aún más gracias a optimizaciones en la nueva pila de almacenamiento ([1](https://devblogs.microsoft.com/directx/directstorage-developer-preview-now-available))

- Windows 10 2004+ es requerido para [Hardware Accelerated GPU Scheduling](https://devblogs.microsoft.com/directx/hardware-accelerated-gpu-scheduling) la cual es necesaria para la generación de cuadros con DLSS ([1](https://developer.nvidia.com/rtx/streamline/get-started))

- A partir de Windows 10 2004+, los procesos que aumentan la resolución del temporizador ya no afectan la resolución global ([1](https://learn.microsoft.com/en-us/windows/win32/api/timeapi/nf-timeapi-timebeginperiod), [2](https://randomascii.wordpress.com/2020/10/04/windows-timer-resolution-the-great-rule-change))  Ahora se gestiona por proceso, lo que significa que los procesos que no solicitan explícitamente una resolución más alta no la obtienen y se atienden con menos frecuencia. Esto se desarrolló aún más en Windows 11: no se garantiza una mayor resolución al proceso llamante si su ventana está minimizada o no visible ([1](https://learn.microsoft.com/en-us/windows/win32/api/timeapi/nf-timeapi-timebeginperiod)). Microsoft añadió la posibilidad de restaurar el comportamiento global en Windows Server 2022+ y Windows 11+ mediante una entrada en el registro ([1](https://randomascii.wordpress.com/2020/10/04/windows-timer-resolution-the-great-rule-change)) No es posible restaurar esta implementación en Windows 10 versiones 2004–22H2.

- Windows 11+ tiene un planificador actualizado para CPUs Intel de 12ª generación en adelante ([1](https://www.anandtech.com/show/16959/intel-innovation-alder-lake-november-4th/3)), pero el comportamiento se puede replicar manualmente con políticas de afinidad en cualquier versión de Windows como se explica en secciones posteriores.

- Windows 11+ limita la frecuencia de mensajes de ventana de los procesos en segundo plano ([1](https://blogs.windows.com/windowsdeveloper/2023/05/26/delivering-delightful-performance-for-more-than-one-billion-users-worldwide))

- Windows 11 es un requisito mínimo para [Cross Adapter Scan-Out](https://videocardz.com/newz/microsoft-cross-adapter-scan-out-caso-delivers-16-fps-increse-on-laptops-without-dgpu-igpu-mux-switch) ([1](https://devblogs.microsoft.com/directx/optimizing-hybrid-laptop-performance-with-cross-adapter-scan-out-caso))

- Se puede establecer ``AllowTelemetry`` en 0 en ediciones de Windows Server ([1](https://admx.help/?Category=Windows_10_2016&Policy=Microsoft.Policies.DataCollection::AllowTelemetry))

<h2 id="downloading-and-preparing-a-stock-windows-iso">10.3. Descargar y Preparar una ISO de Windows Oficial <a href="#downloading-and-preparing-a-stock-windows-iso">(permalink)</a></h2>

Para instalar Windows, es necesario crear un medio de instalación utilizando un archivo ISO. Una vez descargadas las ISOs, asegúrate de verificar sus hashes con las fuentes oficiales para comprobar que son auténticas y no están corruptas. Usa el comando ``certutil -hashfile <archivo>`` n CMD para obtener los hashes del archivo.

Asegúrate de descargar una ISO que contenga una edición con soporte para directivas de grupo, ya que varias de estas directivas se configurarán en pasos posteriores. A veces, puedes obtener ISOs con ediciones específicas ausentes, así que ten cuidado. A continuación se muestra una lista de ediciones recomendadas:

- Ediciones cliente: Professional
- Ediciones servidor: Standard (Desktop Experience)

<h2 id="iso-sources">10.4. ISO Sources <a href="#iso-sources">(permalink)</a></h2>

- [os.click](https://os.click)
- [New Download Links](https://docs.google.com/spreadsheets/d/1zTF5uRJKfZ3ziLxAZHh47kF85ja34_OFB5C5bVSPumk)
- [Adguard File List](https://files.rg-adguard.net)
- [Microsoft Software Download Listing](https://massgrave.dev/msdl)
- [Fido](https://github.com/pbatard/Fido)
- [UUP dump](https://uupdump.net)

<h2 id="iso-preparation">10.5. ISO Preparation <a href="#iso-preparation">(permalink)</a></h2>

<details>
<summary>Windows 7</summary>

Si estás configurando Windows 7, recomiendo usar la ISO ``en_windows_7_professional_with_sp1_x64_dvd_u_676939.iso`` ISO ([Adguard hashes](https://files.rg-adguard.net/file/11ad6502-c2aa-261c-8c3f-c81477b21dd2?lang=en-us)). Además, no podrás iniciar la ISO en hardware moderno sin integrar los drivers y actualizaciones necesarios, lo cual se puede lograr utilizando herramientas como [NTLite](https://www.ntlite.com) ([instructions](https://winraid.level1techs.com/t/guide-integration-of-drivers-into-a-win7-11-image/30793)) o DISM en línea de comandos ([instructions](/docs/image-customization.md)). Sin embargo, NTLite es más fácil de usar. Normalmente, solo se requiere integrar drivers de [NVMe](https://winraid.level1techs.com/t/recommended-ahci-raid-and-nvme-drivers/28310) y [USB](https://winraid.level1techs.com/t/usb-3-0-3-1-drivers-original-and-modded/30871) para poder iniciar el sistema desde la ISO. Asegúrate de integrar también los drivers en Windows Setup, de lo contrario podrías tener problemas para detectar almacenamiento o usar dispositivos USB, a menos que planees instalar la ISO con DISM como se describe en la sección [Iniciando desde la ISO](#booting-into-the-iso)  ya que este método omite por completo el instalador tradicional de Windows y el archivo ``boot.wim``. Para encontrar drivers compatibles con tu dispositivo, busca aquellos que soporten el HWID de tu dispositivo ([1](/assets/images/device-hwid-example.png)). Si no puedes encontrar un driver USB para tu HWID, intenta integrar el [generic USB driver](https://forums.mydigitallife.net/threads/usb-3-xhci-driver-stack-for-windows-7.81934) y la actualización ``KB2864202``. A continuación, se presenta una tabla de actualizaciones recomendadas para integrar a la ISO.

|Knowledge Base (KB) ID|Notes|
|---|---|
|KB4490628|Servicing Stack Update|
|KB4474419|SHA-2 Code Signing Update|
|KB2670838|Platform Update and DirectX 11.1|
|KB2990941|NVMe Support (<https://files.soupcan.tech/KB2990941-NVMe-Hotfix/Windows6.1-KB2990941-x64.msu>)|
|KB3087873|NVMe Support and Language Pack Hotfix|
|KB2864202|KMDF Update (required for USB 3/XHCI driver stack)|
|KB4534314|Easy anticheat Support|
|KB3191566|WMF 5.1 (<https://www.microsoft.com/en-us/download/details.aspx?id=54616>)|

Si tienes problemas con el instalador de Windows al usar un dispositivo USB a pesar de haber integrado drivers y actualizaciones en el ``boot.wim``,  puedes usar el instalador moderno de Windows para instalar tu ISO de Windows 7 colocando el archivo ``intall.wim`` de Windows 7 en la carpeta ``sources`` de un medio USB de instalación de Windows 10. Asegúrate de que los idiomas de ambas ISOs coincidan. Este método ha resuelto problemas para otras personas, ya que el instalador moderno de Windows incluye componentes necesarios para ejecutarse en hardware moderno y ofrece mayor compatibilidad.
</details>

<details>
<summary>Windows 8.1</summary>

Si estás configurando Windows 8.1, recomiendo usar la ISO ``en_windows_8_1_x64_dvd_2707217.iso`` ([Adguard hashes](https://files.rg-adguard.net/file/406e60db-4275-7bf8-616f-56e88d9e0a4a?lang=en-us)). Además, a continuación se presenta una tabla con actualizaciones recomendadas que puedes integrar en la ISO utilizando herramientas como [NTLite](https://www.ntlite.com) ([instrucciones](https://winraid.level1techs.com/t/guide-integration-of-drivers-into-a-win7-11-image/30793)) .

|Knowledge Base (KB) ID|Notes|
|---|---|
|KB2919442|Servicing Stack Update|
|KB2999226|Universal C Runtime|
|KB2919355|Cumulative Update|
|KB3191566|WMF 5.1 (<https://www.microsoft.com/en-us/download/details.aspx?id=54616>)|

</details>

<details>
<summary>Windows 10+</summary>

No se requieren pasos adicionales para las versiones de Windows 10 en adelante. Puedes integrar las actualizaciones más recientes, pero esto no es necesario si planeas mantener Windows Update habilitado después de iniciar desde la ISO. Además, las ISOs creadas usando UUP Dump ya incluyen las actualizaciones más recientes, siempre que construyas la última versión. Esto puede hacerse con [NTLite](https://www.ntlite.com) ([instrucciones](https://winraid.level1techs.com/t/guide-integration-of-drivers-into-a-win7-11-image/30793)) o DISM en línea de comandos ([instructions](/docs/image-customization.md))), aunque NTLite es más fácil de usar.
</details>

> [!IMPORTANTE]
> La presencia de claves OEM puede forzar la instalación de ediciones específicas de Windows (por ejemplo, Home), lo cual se explica en la sección [Descargar y Preparar una ISO de Windows Oficial](#downloading-and-preparing-a-stock-windows-iso). Para evitar esto, puedes personalizar los archivos ``EI.cfg`` y ``PID.txt`` ([instrucciones](https://www.youtube.com/watch?v=R3yM3AV6q-8)) o eliminar todas las ediciones excepto la que deseas instalar usando [NTLite](https://www.ntlite.com) o DISM en CLI ([instrucciones](/docs/image-customization.md)), NTLite es más fácil de usar.

<h2 id="fetching-required-files">10.6. Obtener Archivos Requeridos <a href="#fetching-required-files">(permalink)</a></h2>

Antes de instalar Windows hay dos prerrequisitos principales. Estos pueden hacerse más adelante si puedes obtenerlos desde otro sistema, pero se recomienda tenerlos preparados con anticipación. Guárdalos en un dispositivo de almacenamiento USB u otro medio accesible sin conexión tras la instalación de Windows, ya que no estarás conectado a Internet durante los primeros pasos.

1. Descarga el driver de tu tarjeta de red (NIC), ya que puede no venir incluido con Windows y será necesario para conectarte a la red.
2. La carpeta ``bin`` de este repositorio, que puede descargarse [here](https://github.com/valleyofdoom/PC-Tuning/archive/refs/heads/main.zip)

<h2 id="booting-into-the-iso">10.7. Iniciar desde la ISO <a href="#booting-into-the-iso">(permalink)</a></h2>

Esta sección cubre cómo iniciar desde la ISO descargada y preparada previamente. Para los próximos pasos, deberás desconectar el cable Ethernet y asegurarte de no estar conectado a Internet durante el proceso de instalación. Esto permitirá omitir el inicio de sesión obligatorio de Microsoft durante OOBE, permitiendo el uso de una cuenta local y evitando la instalación de actualizaciones y controladores no deseados. Existen dos formas principales de instalar Windows: mediante un dispositivo USB o utilizando DISM (sin almacenamiento USB). Ambos métodos son válidos. Si deseas eliminar tu sistema operativo actual y borrar todo el disco, deberás instalar usando USB, ya que el segundo método requiere arranque dual.

<details>
<summary>Option 1 -  Install using USB storage</summary>

- Descarga [Ventoy](https://github.com/ventoy/Ventoy/releases) y ejecuta ``Ventoy2Disk.exe``. En el menú de opciones selecciona el estilo de partición correcto y desactiva el soporte de Secure Boot. Puedes determinar el estilo actual de partición escribiendo``msinfo32`` en ``Win+R`` Finalmente, selecciona tu dispositivo USB y haz clic en instalar.

- Mueve tu ISO de Windows al almacenamiento USB desde el Explorador de archivos y arranca desde el USB en modo UEFI.

- En Windows 10 24H2 o superior, usa la versión anterior del instalador ([1](https://schneegans.de/windows/no-8.3/24h2.png)).

- Evita que el instalador de Windows reinicie automáticamente para que los nombres 8dot3 puedan ser eliminados correctamente, como se explica en los próximos pasos. Presiona ``Shift+F10`` para abrir CMD y escribe ``setup /NoReboot``. Continúa con la instalación, pero no reinicies al final.

- Si Secure Boot está activado, desactívalo temporalmente durante la instalación. Arranca desde Ventoy en tu USB usando BIOS y selecciona tu ISO de Windows. Continúa con la instalación normalmente. Una vez finalizada, puedes volver a activar Secure Boot si lo desactivaste temporalmente.

- Al instalar Windows 8 desde USB, puede que se te pida una clave. Usa la clave genérica ``GCRJD-8NW9H-F2CDX-CCM8D-9D6T9`` para omitir este paso. Esto no activa Windows.

- Al instalar Windows 11 desde USB, puedes encontrar restricciones por requisitos del sistema. Para omitir los chequeos, presiona ``Shift+F10`` para abrir CMD, luego escribe ``regedit`` y añade las claves de registro correspondientes.

    ```
    [HKEY_LOCAL_MACHINE\SYSTEM\Setup\LabConfig]
    "BypassTPMCheck"=dword:00000001
    "BypassRAMCheck"=dword:00000001
    "BypassSecureBootCheck"=dword:00000001
    ```

- Después de que los archivos hayan sido copiados a la nueva partición y antes de reiniciar, puedes evitar la creación y eliminar los nombres de archivo en formato 8.3 en el volumen donde se instaló Windows, lo cual mejora el rendimiento y la seguridad ([1](https://web.archive.org/web/20200217151754/https://ttcshelbyville.wordpress.com/2018/12/02/should-you-disable-8dot3-for-performance-and-security)). Este paso debe hacerse ahora (antes de iniciar por primera vez), de lo contrario puede generar errores de acceso a archivos, como se explica [aquí](https://schneegans.de/windows/no-8.3).

  - Presiona ``Shift+F10`` para abrir CMD.

  - Determina la letra de la unidad donde se instaló Windows escribiendo ``diskpart``, luego ``list volume``  y determina la letra correcta (será un volumen de arranque relativamente grande). Escribe ``exit`` para salir del mismo.

  - Desactiva la creación de nombres 8.3. Reemplaza ``<letra de unidad>`` por la correspondiente (por ejemplo, ``D:``)

    ```bat
    fsutil 8dot3name set <letra de unidad> 1
    ```

  - Elimina los nombres de archivo 8.3 existentes. Reemplaza ``<letra de unidad>`` por la correspondiente (por ejemplo, ``D:``)

    ```bat
    fsutil 8dot3name strip /s /f <letra de unidad>
    ```

  - Escribe  ``wpeutil reboot`` para salir del instalador de Windows y reiniciar el sistema.

</details>

<details>
<summary>Opción 2 – Instalar usando DISM Apply-Image (sin almacenamiento USB)

- Como este método requiere especificar una partición existente para aplicar la ISO, crea una nueva partición [reduciendo un volumen](https://docs.microsoft.com/en-us/windows-server/storage/disk-management/shrink-a-basic-volume) si aún no lo has hecho. Luego asigna una letra de unidad al nuevo espacio no asignado creado.

- Extrae la ISO si es necesario, y ejecuta el siguiente comando para aplicar la imagen a una partición dada. Sustituye ``<ruta\al\wim>`` por la ruta al archivo ``install.wim`` o ``install.esd`` (ubicado en la carpeta ``sources`` de la ISO extraída

  - Lista todas las ediciones disponibles y sus respectivos índices.

      ```bat
      DISM /Get-WimInfo /WimFile:<path\to\wim>
      ```

  - Aplica la imagen reemplazando ``<índice>`` por el índice de la edición deseada y ``<letra de unidad>`` por la letra de unidad asignada en el paso anterior donde se montará la imagen (por ejemplo, índice ``1`` y unidad ``D:``)

      ```bat
      DISM /Apply-Image /ImageFile:<ruta\al\wim> /Index:<índice> /ApplyDir:<letra de unidad>
      ```

- Crea la entrada de arranque con el siguiente comando. Sustituye ``<windir>`` por la ruta al directorio ``Windows`` montado (por ejemplo ``D:\Windows``)

    ```bat
    bcdboot <windir>
    ```

- Después de que se hayan copiado los archivos a la nueva partición y antes de reiniciar, puedes evitar la creación y eliminar los nombres de archivo existentes con formato 8.3 (8 caracteres + 3 de extensión) en el volumen donde se acaba de instalar Windows. Esto mejora el rendimiento y la seguridad ([1](https://web.archive.org/web/20200217151754/https://ttcshelbyville.wordpress.com/2018/12/02/should-you-disable-8dot3-for-performance-and-security)). Este paso debe realizarse antes de arrancar Windows para evitar errores de acceso a archivos, como se explica [aqui](https://schneegans.de/windows/no-8.3).

  - Para deshabilitar la creación de nombres de archivo 8.3, reemplaza ``<letra de unidad>`` con la correcta (por ejemplo. ``D:``). Si el comando falla porque la creación global de nombres 8.3 está desactivada, primero ejecuta ``fsutil 8dot3name set 2``, , luego el comando inferior, y finalmente vuelve a desactivarlo globalmente con ``fsutil 8dot3name set 1``. Esto solo es necesario si aparece un error.

    ```bat
    fsutil 8dot3name set <drive letter> 1
    ```

  - Para eliminar los nombres 8.3 existentes. Sustituye ``<drive letter>`` por la correcta (por ejemplo, ``D:``)

    ```bat
    fsutil 8dot3name strip /s /f <drive letter>
    ```

- El proceso de instalación finalizará tras reiniciar el sistema.

</details>

<h1 id="configure-windows">11. Configurar Windows <a href="#configure-windows">(permalink)</a></h1>

<h2 id="oobe-setup">11.1 Configuración OOBE <a href="#oobe-setup">(permalink)</a></h2>

- Windows Server puede forzarte a introducir una contraseña, la cual puede eliminarse opcionalmente en pasos posteriores.
  
- Si estás configurando Windows 11, presiona ``Shift+F10`` para abrir CMD, luego escribe ``regedit`` para abrir el editor del registro y agrega la siguiente entrada de registro. Esto permitirá continuar sin conexión a Internet desbloqueando la opción de ``continue with limited setup`` , como se muestra en los videos de ejemplo. Esto elimina el requisito de iniciar sesión con una cuenta Microsoft, lo cual desaconsejo por motivos de privacidad en general. Después de aplicar la entrada del registro, escribe ``shutdown /r /t 0`` en CMD para reiniciar.

    ```
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\OOBE]
    "BypassNRO"=dword:00000001
    ```

- See [assets/videos/oobe-windows7-example.mp4](/assets/videos/oobe-windows7-example.mp4)
- See [assets/videos/oobe-windows8-example.mp4](/assets/videos/oobe-windows8-example.mp4)
- See [assets/videos/oobe-windows10+-example.mp4](/assets/videos/oobe-windows10+-example.mp4)

<h2 id="user-account-control">11.2. Control de Cuentas de Usuario <a href="#user-account-control">(permalink)</a></h2>

Establece el nivel de notificación de Control de Cuentas de Usuario (UAC) a “Notificar siempre” (el nivel más alto) escribiendo ``useraccountcontrolsettings`` en ``Win+R``.  Esto reduce el riesgo de que un programa malicioso eluda el UAC, algo que puede ocurrir con la configuración predeterminada ([1](https://devblogs.microsoft.com/oldnewthing/20160816-00/?p=94105), [2](https://github.com/hfiref0x/UACME#system-requirements)).

<h2 id="unrestricted-powershell-execution-policy">11.3. Política de Ejecución de PowerShell Sin Restricciones <a href="#unrestricted-powershell-execution-policy">(permalink)</a></h2>

> [!ADVERTENCIA]
> 🔒 Establecer la política de ejecución de PowerShell en “Unrestricted” puede afectar negativamente a la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con esta modificación. Como alternativa, se puede usar ``-ExecutionPolicy Bypass`` al iniciar una instancia de PowerShell en lugar de configurar la política globalmente..

Este ajuste es necesario para ejecutar los scripts del repositorio. Abre PowerShell como administrador e introduce el siguiente comando.

```powershell
Set-ExecutionPolicy Unrestricted
```

<h2 id="importing-bin-folder">11.4. Importar Carpeta bin <a href="#importing-bin-folder">(permalink)</a></h2>

Mueve la carpeta ``bin`` que descargaste antes de instalar Windows a la unidad ``C:`` , tal como se detalla en la sección [Obtener los archivos requeridos](#fetching-required-files). Si no la has descargado aún, deberás obtenerla desde otro sistema ya que todavía no tienes acceso a la red. La ruta completa debe ser ``C:\bin``.

<h2 id="process-mitigations-windows-10-1709">11.5. Mitigaciones de Procesos (Windows 10 1709+) <a href="#process-mitigations-windows-10-1709">(permalink)</a></h2>

> [!ADVERTENCIA]
> 🔒 Desactivar las mitigaciones de procesos puede impactar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con esta modificación.

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([Instrucciones aquí.](#benchmarking)).

Existen varias mitigaciones a nivel del sistema operativo ([1](https://learn.microsoft.com/en-us/powershell/module/processmitigations/set-processmitigation?view=windowsserver2019-ps#-disable)) que están habilitadas por defecto y que pueden impactar el rendimiento. Si se desea, estas pueden deshabilitarse desde la página de "Protección contra vulnerabilidades" de Windows Defender. Debe quedar claro que deshabilitar mitigaciones reduce la seguridad. Este paso se realiza ahora ya que, si decides desactivar Windows Defender en los siguientes pasos, la interfaz ya no estará accesible; sin embargo, pueden ser activadas o desactivadas mediante los comandos [Get-ProcessMitigation](https://learn.microsoft.com/en-us/powershell/module/processmitigations/get-processmitigation?view=windowsserver2022-ps) y [Set-ProcessMitigation](https://learn.microsoft.com/en-us/powershell/module/processmitigations/set-processmitigation?view=windowsserver2019-ps) en PowerShell. Algunos programas pueden requerir que las mitigaciones estén habilitadas y fallarán si se deshabilitan, por lo tanto, procede con precaución.

<h2 id="merging-registry-options">11.6. Merging Registry Options <a href="#merging-registry-options">(permalink)</a></h2>

> [!ADVERTENCIA]
> 🔒 Algunos cambios descritos en la siguiente tabla pueden afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos asociados antes de modificar una configuración específica.

Los ajustes del registro se aplican mediante el script ``apply-registry.ps1``. En cuanto a qué opciones se aplican, estas se detallan en la tabla a continuación, la cual puede personalizarse editando el archivo ``C:\bin\registry-options.json`` con un editor de texto y configurando las propiedades como ``true`` o ``false``. Puedes respaldar este archivo para no tener que modificarlo tras cada reinstalación de Windows.

<h3 id="registry-options-documentation">11.6.1. Documentación de Opciones del Registro <a href="#registry-options-documentation">(permalink)</a></h3>

> [!IMPORTANTE]
> Actualmente, el script no revierte opciones si se ejecuta nuevamente. Por ejemplo, si el script fue ejecutado con una opción en ``true``, luego ejecutarlo con dicha opción en  ``false``  no revertirá los cambios ya realizados, ya que el script no lleva registro del estado anterior de las claves del registro asociadas a la opción. Esta funcionalidad puede añadirse en el futuro, pero por ahora, usa el argumento ``-get_option_keys <option>`` con el script para obtener todas las claves relacionadas y revertirlas manualmente si es necesario.

|Opción|Motivo|Notas|Valor por defecto|
|---|---|---|---|
|``disable windows update``|1. 1. Reducir la carga del CPU<br><br>2. Obtener un control más preciso sobre la característica en cuestió|🔒 Un valor de ``true`` puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con modificar esta configuración<br><br>Deshabilitar Windows Update está incluido en las recomendaciones de Microsoft para configurar dispositivos para rendimiento en tiempo real ([1](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)). Alternativamente, se pueden deshabilitar solo las actualizaciones automáticas en lugar de deshabilitar completamente Windows Update, logrando el mismo efecto en cuanto a reducción de carga de CPU, pero aún siendo posible actualizar Windows configurando ``disable windows update`` en ``false`` y ``disable automatic windows updates`` en ``true``. Se sabe que los procesos de Windows Update utilizan muchos recursos de CPU y memoria. Deshabilitar Windows Update rompe la Microsoft Store, sin embargo, puedes descargar e instalar paquetes Appx directamente ([instructions](https://superuser.com/questions/1721755/is-there-a-way-to-install-microsoft-store-exclusive-apps-without-store))|``false``|
|``disable automatic windows updates``|1. Reducir la carga del CPU<br><br>2. Obtener un control más preciso sobre la característica en cuestión|🔒 Un valor de ``true`` puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con modificar esta configuración<br><br>Evita la descarga e instalación automática de actualizaciones de Windows en lugar de deshabilitar completamente Windows Update y permite verificar actualizaciones manualmente de vez en cuando. Las actualizaciones pueden ocurrir en momentos inoportunos, lo que lleva a un uso excesivo de CPU y memoria en intervalos aleatorios, además de interrumpir apagados en ciertos casos. Esta opción es sobrescrita si ``disable windows update`` está configurado como ``true``. <br><br>Esta opción no afecta a las actualizaciones mayores (upgrades), que pueden ser controladas usando directivas de grupo ([instructions](https://www.tenforums.com/tutorials/159624-how-specify-target-feature-update-version-windows-10-a.html)). Sin embargo, estás limitado a evitar actualizaciones hasta que la versión especificada alcance su fin de soporte|``true``|
|``disable driver installation via windows update``|1. Reducir la carga del CPU<br><br>2. Obtener un control más preciso sobre la característica en cuestión|Evita que se instalen controladores desactualizados, vulnerables y potencialmente de bajo rendimiento mediante Windows Update. Se recomienda instalar manualmente solo la versión mínima necesaria para tu sistema (ya que el instalador completo a menudo incluye bloatware que se ejecuta constantemente en segundo plano) junto con la versión más reciente directamente desde el sitio del fabricante, como se describe en la sección [Installing Drivers](#installing-drivers). Esta opción se sobrescribe si ``disable windows update`` está en ``true``|``true``|
|``disable automatic store app updates``|1. Reducir la carga del CPU<br><br>2. Obtener un control más preciso sobre la característica en cuestión|🔒 Un valor de ``true`` puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con modificar esta configuración<br><br>Evita la descarga e instalación automática de actualizaciones de aplicaciones de la tienda en comparación con deshabilitar completamente las actualizaciones, lo cual no es deseable si el objetivo es reducir la carga de CPU. En su lugar, verifica manualmente las actualizaciones de aplicaciones de vez en cuando|``true``|
|``disable windows defender``|1. Reducir la carga del CPU<br><br>2. Prevenir problemas con la CPU entrando al estado C-State 0 ([1](https://www.techpowerup.com/295877/windows-defender-can-significantly-impact-intel-cpu-performance-we-have-the-fix))|🔒 Un valor de ``true`` puede afectar negativamente la seguridad. Los usuarios deben evaluar el riesgo de seguridad al modificar esta configuración<br><br>Esta opción desactiva completamente Windows Defender. En su lugar, realiza escaneos frecuentes, utiliza un navegador endurecido con [uBlock Origin](https://ublockorigin.com),  mantén activado el UAC y prefiere software gratuito, de código abierto y de buena reputación. Evita software propietario cuando sea posible y asegúrate de analizar archivos y ejecutables con [VirusTotal](https://www.virustotal.com/gui/home/upload) antes de abrirlos|``true``|
|``disable gamebarpresencewriter``|1. Reducir la carga del CPU|Este proceso se ejecuta constantemente en segundo plano y no es necesario para que funcionen Game Mode o Game Bar, según mis pruebas|``true``|
|``disable background apps``|1. RReducir la carga del CPU|Evita que las aplicaciones se ejecuten en segundo plano. Las aplicaciones en segundo plano se desactivan mediante directivas ya que esta opción no está disponible en la interfaz de Windows 11|``true``|
|``disable transparency effects``|1. Reducir la carga del CPU  ([1](/assets/images/transparency-effects-benchmark.png))|Desactiva los efectos de transparencia|``true``|
|``disable notifications network usage``|1. Mitigar la telemetría y conexiones hacia Microsoft ([1](https://learn.microsoft.com/en-gb/windows/privacy/manage-connections-from-windows-operating-system-components-to-microsoft-services#10-live-tiles))|N/A|``true``|
|``disable windows marking file attachments with information about their zone of origin``|1. Reducir o desactivar funciones intrusivas|🔒 Un valor de ``true`` puede afectar negativamente la seguridad. Los usuarios deben evaluar el riesgo de seguridad asociado con modificar esta configuración<br><br>Evita [esta](https://www.tenforums.com/tutorials/85418-how-disable-downloaded-files-being-blocked-windows.html) dvertencia de seguridad intrusiva ya que los archivos descargados requieren ser desbloqueados constantemente. Sin embargo, esto puede afectar la seguridad ya que el usuario no será notificado sobre archivos bloqueados mediante una advertencia de seguridad ([1](https://www.tenforums.com/tutorials/85418-how-disable-downloaded-files-being-blocked-windows.html))|``true``|
|``disable malicious software removal tool updates``|1. Obtener un control más preciso sobre la función en cuestión|🔒 Un valor de ``true`` puede afectar negativamente la seguridad. Los usuarios deben evaluar el riesgo de seguridad asociado con modificar esta configuració.g<br><br>Evita que Windows ofrezca la Herramienta de eliminación de software malintencionado a través de Windows Update.|``true``|
|``disable sticky keys``|1. Reducir o desactivar funciones intrusivas|Desactiva el mensaje ¿*Deseas activar las teclas especiales*? al presionar repetidamente la tecla ``Shift``. Muy intrusivo en aplicaciones que utilizan esta tecla para controles, como los videojuegos.|``true``|
|``disable pointer acceleration``|1. Reducir o desactivar funciones intrusivas|Garantiza una respuesta 1:1 del ratón en juegos que no utilizan eventos de entrada directa (raw input) y en el escritorio.|``true``|
|``disable fast startup``|1. Reducir o desactivar funciones intrusivas|Interfiere con el apagado real del sistema (no entra en estado S5), lo que puede provocar comportamientos inesperados ([1](https://www.youtube.com/watch?v=OBGxt8zhbRk)). Consulta la sección [Inicio rápido, suspensión e hibernación](#fast-startup-standby-and-hibernate) para más detalles. Aunque se puede forzar un apagado completo manteniendo presionada la tecla ``Shift`` al hacer clic en ``Apagar``, esto puede olvidarse fácilmente.|``true``|
|``disable customer experience improvement program``|1. Mitigar la telemetría y conexiones hacia Microsoft ([1](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/jj618322(v=ws.11)))|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable windows error reporting``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable clipboard history``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable activity feed``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable advertising id``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable autoplay``|1. Mitigar riesgos de seguridad|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable cloud content``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``mitigate web-based search info``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable sending inking and typing data to microsoft``|1. Mitigar la telemetría y conexiones hacia Microsoft|Recomendado por [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies)|``true``|
|``disable automatic maintenance``|1. Obtener un control más preciso sobre la función en cuestión|Maintenance tasks can be viewed by typing ``Get-ScheduledTask \| ? {$_.Settings.MaintenanceSettings}`` in PowerShell|``true``|
|``disable remote assistance``|1. Mitigar riesgos de seguridad|N/A|``true``|
|``disable sign-in and lock last interactive user after a restart``|1. Mitigar riesgos de seguridad ([1](https://web.archive.org/web/20241125194814/https://stigviewer.com/stig/windows_server_2012_2012_r2_member_server/2014-06-30/finding/V-43245))|N/A|``true``|
|``show file extensions``|1. Mitigar riesgos de seguridad ([1](https://www.youtube.com/watch?v=nYdS3FIu3rI))|N/A |``true``|
|``disable widgets``|1. Mitigar riesgos de seguridad ([1](https://www.youtube.com/watch?v=m9d-fXl3Z8k))|N/A|``true``|
|``disable telemetry``|1. Mitigar la telemetría y conexiones hacia Microsoft|N/A|``true``|
|``disable retrieval of online tips and help in the immersive control panel``|1. Mitigar la telemetría y conexiones hacia Microsoft|N/A|``true``|
|``disable typing insights``|1. Mitigar la telemetría y conexiones hacia Microsoft|N/A|``true``|
|``disable suggestions in the search box and in search home``|1. Mitigar la telemetría y conexiones hacia Microsoft<br><br>2. Reducir o desactivar funciones intrusivas|N/A|``true``|
|``disable computer is out of support message``|1. Reducir o desactivar funciones intrusivas|Desactiva [este mensaje](https://support.microsoft.com/en-us/topic/you-received-a-notification-your-windows-7-pc-is-out-of-support-3278599f-9613-5cc1-e0ee-4f81f623adcf) intrusivo. No relevante en versiones modernas de Windows.|``true``|
|``disable fault tolerant heap``|1. Obtener un control más preciso sobre la función en cuestión|Evita que Windows aplique mitigaciones automáticamente a nivel de aplicación para prevenir futuros bloqueos ([1](https://learn.microsoft.com/en-us/windows/win32/win7appqual/fault-tolerant-heap)), lo cual puede generar problemas ([1](https://www.mak.com/mak-one/support/help/knowledge/performance-issues-caused-by-the-fault-tolerant-heap-windows))|``true``|

<h3 id="applying-options">11.6.2. Applying Options <a href="#applying-options">(permalink)</a></h3>

- Abre PowerShell como administrador e introduce el siguiente comando. Si el comando falla, intenta desactivar la protección contra manipulaciones (Tamper Protection) (Windows 10 1909+) y la protección en tiempo real en Windows Defender. Si eso no funciona, reinicia y vuelve a ejecutar el comando. Si nada de lo anterior funciona, intenta ejecutar el comando en modo seguro. Si prefieres no ejecutar ningún script, existe la opción de crear manualmente un archivo de registro con las claves que necesites, tal como se explica en [/docs/registry-opts.md](/docs/registry-opts.md). Este documento contiene todas las claves que se fusionarían al usar el script.

    ```powershell
    C:\bin\apply-registry.ps1
    ```

- Asegúrate de que el script imprima un mensaje de “aplicado correctamente” en la consola; si no lo hace, significa que las claves del registro no se fusionaron con éxito.

- Después, y solo después de reiniciar, puedes establecer una conexión a internet, ya que las políticas de Windows Update surtirán efecto. Esta es la principal razón por la que no se recomienda conectar a internet antes de este punto.
  
> [!NOTE]
> A los mantenedores y colaboradores: las funciones y opciones deben ser probadas tal como se listan en la tabla anterior. Es inevitable que se requieran más pasos para lograr el mismo objetivo a medida que el sistema operativo reciba actualizaciones o mejoras (por ejemplo, mantener manualmente una lista de servicios relacionados con la desactivación de Windows Defender).).

<h2 id="installing-drivers">11.7. Installing Drivers <a href="#installing-drivers">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

- No se recomienda instalar controladores a través de Windows Update, ya que pueden estar desactualizados en comparación con los proporcionados por el fabricante. Las actualizaciones de controladores mediante Windows Update deben ser bloqueadas si la opción ``disable driver installation via windows update`` fue establecida en ``true`` en la sección [Merging Registry Options](#merging-registry-options)

- Consulta [Chipset Device "Drivers" (= INF files) | Fernando](https://winraid.level1techs.com/t/intel-chipset-device-drivers-inf-files/30920)

- Los controladores gráficos se instalarán en la sección [Graphics Driver](#graphics-driver), por lo tanto, no los instales en esta etapa.

- Puedes encontrar controladores buscando los que sean compatibles con el HWID de tu dispositivo. Consulta [media/device-hwid-example.png](/assets/images/find-driver-key-example.png) para saber cómo encontrar el HWID en el Administrador de dispositivos para un dispositivo dado.

- Intenta obtener el controlador en su forma INF para poder instalarlo desde el Administrador de dispositivos, ya que los instaladores ejecutables suelen incluir software no deseado junto con el controlador. A veces es posible extraer el ejecutable del instalador con 7-Zip.

- Se recomienda actualizar e instalar lo siguiente:

  - Controlador del adaptador de red (NIC). Si no tienes acceso a internet en esta etapa, necesitarás descargar el controlador desde otro dispositivo o usar un arranque dual, ya que podría no estar incluido en Windows.

  - Controladores de [USB](https://winraid.level1techs.com/t/usb-3-0-3-1-drivers-original-and-modded/30871) y [NVMe](https://winraid.level1techs.com/t/recommended-ahci-raid-and-nvme-drivers/28310) (si estás configurando Windows 7, es posible que ambos ya se hayan integrado en la sección [Downloading and Preparing a Stock Windows ISO](#downloading-and-preparing-a-stock-windows-iso))

  - [SATA](https://winraid.level1techs.com/t/recommended-ahci-raid-and-nvme-drivers/28310) (necesario en Windows 7, ya que el controlador estándar no admite interrupciones señaladas por mensajes - MSI)

- Puedes instalar otros controladores necesarios con [Snappy Driver Installer Origin](https://www.snappy-driver-installer.org)

<h2 id="windows-server-specific-options-windows-server">11.8. Opciones específicas de Windows Server (Windows Server) <a href="#windows-server-specific-options-windows-server">(permalink)</a></h2>

- Para habilitar Wi-Fi, ve a ``Manage`` -> ``Add Roles and Features`` en el panel de ``Server Manager`` y habilita ``Wireless LAN Service``.

- En Server Manager, ve a ``Manage -> Server Manager Properties`` y habilita la opción para evitar que Server Manager se inicie automáticamente

- Establece el tipo de inicio de los servicios ``Windows Audio`` y ``Windows Audio Endpoint Builder`` en automático escribiendo ``services.msc`` en ``Win+R``

- Navega a ``Computer Configuration -> Windows Settings -> Security Settings -> Account Policies -> Password Policy`` escribiendo ``gpedit.msc`` en ``Win+R`` y desactiva la opción ``Password must meet complexity requirements``

  - Abre CMD y escribe ``gpupdate /force`` para aplicar los cambios inmediatamente

- Navega a ``Computer Configuration -> Administrative Templates -> System`` escribiendo ``gpedit.msc`` en ``Win+R`` y desactiva ``Display Shutdown Event Tracker`` para eliminar el mensaje de apagado
- 
- Para eliminar la contraseña del usuario, introduce tu contraseña actual y deja en blanco los campos de nueva contraseña y confirmación en ``User Accounts`` escribiendo ``control userpasswords`` en ``Win+R``

<h2 id="privacy-options-windows-8">11.9. Privacy Options (Windows 8+) <a href="#privacy-options-windows-8">(permalink)</a></h2>

Desactiva todos los permisos innecesarios en la sección ``Privacy`` presionando ``Win+I``.

<h2 id="search-indexing">11.10. Search Indexing <a href="#search-indexing">(permalink)</a></h2>

Ciertos directorios del sistema de archivos se indexan para las funciones de búsqueda de Windows, los cuales pueden visualizarse escribiendo ``control srchadmin.dll`` en ``Win+R``.  La indexación ocurre periódicamente en segundo plano y suele generar una sobrecarga notable en la CPU, lo cual puede verse con Process Explorer como se describe en la sección [Process Explorer](#process-explorer). Por lo tanto, es preferible deshabilitar la indexación de búsqueda globalmente desactivando el servicio ``Windows Search`` Abre CMD como administrador e introduce el siguiente comando:

  ```bat
  reg add "HKLM\SYSTEM\CurrentControlSet\Services\WSearch" /v "Start" /t REG_DWORD /d "4" /f
  ```

> [!IMPORTANT]
> Para evitar errores inesperados y problemas debidos a dependencias de servicios, evalúa los otros servicios que dependen del servicio que deseas deshabilitar. Esto puede hacerse abriendo CMD como administrador y escribiendo ``sc EnumDepend <service>`` , lo cual describe los servicios que dependen del servicio que deseas deshabilitar. Estos servicios también deben ser deshabilitados para evitar errores de dependencia. Si no puedes deshabilitarlos (por ejemplo, porque los necesitas), entonces no tienes más opción que dejar habilitado el servicio que querías deshabilitar inicialmente.

<h2 id="time-language-and-region">11.11. Time, Language and Region <a href="#time-language-and-region">(permalink)</a></h2>

- Configura las opciones escribiendo ``intl.cpl`` y ``timedate.cpl`` en ``Win+R``

- Solo Windows 10 en adelante:

  - Configura las opciones en ``Time & Language`` presionando ``Win+I``

    - Si planeas usar exclusivamente un solo idioma y una sola distribución de teclado, asegúrate de que así sea para que no tengas que alternar la barra de idiomas con atajos que pueden activarse accidentalmente.

- Asegúrate de que la hora del sistema esté sincronizada y sea correcta.

<h2 id="web-browser">11.12. Web Browser <a href="#web-browser">(permalink)</a></h2>

Configura el navegador de tu preferencia.

- Ver: [privacytests.org](https://privacytests.org)

- Ver: [Desktop Browsers | Privacy Guides](https://www.privacyguides.org/en/desktop-browsers)

<h2 id="scheduled-tasks">11.13. Scheduled Tasks <a href="#scheduled-tasks">(permalink)</a></h2>

Windows incluye varias tareas programadas que pueden evaluarse utilizando [TaskSchedulerView](https://www.nirsoft.net/utils/task_scheduler_view.html). Evaluarlas ayuda a tener un control más fino sobre qué se ejecuta silenciosamente en el sistema, ya sea relacionado con actualizaciones, telemetría, Defender y más. Considera las columnas ``Last Run``, ``Next Run`` y ``Triggers`` para evaluar si vale la pena deshabilitar la tarea en cuestión.

<h2 id="activate-windows">11.14. Activate Windows <a href="#activate-windows">(permalink)</a></h2>

Utiliza los comandos siguientes para activar Windows usando tu clave de licencia si no tienes una vinculada al HWID. Asegúrate de que la activación fue exitosa verificando el estado de activación en las propiedades del sistema. Abre CMD como administrador y escribe los comandos correspondientes.

 
```bat
slmgr /ipk <license key>
```

```bat
slmgr /ato
```

<h2 id="declutter-interface">11.15. Declutter Interface <a href="#declutter-interface">(permalink)</a></h2>

Desactiva las funciones en la barra de tareas y desancla accesos directos y tiles del menú de inicio y barra de tareas. Esto es cuestión de preferencia personal.

<h2 id="visual-effects">11.16. Visual Effects <a href="#visual-effects">(permalink)</a></h2>

Las opciones de efectos visuales pueden accederse escribiendo ``sysdm.cpl`` en ``Win+R``.  Este menú permite deshabilitar animaciones de interfaz, lo cual contribuye a una mayor sensación de respuesta en la interacción con Windows. En Windows 7 se podía deshabilitar la composición del escritorio directamente aquí, pero ya no está disponible en Windows 8+. El resto de las opciones son personales.

<h2 id="superfetch-and-prefetch">11.17. Superfetch and Prefetch <a href="#superfetch-and-prefetch">(permalink)</a></h2>

Si no hay un disco duro mecánico (HDD) en el sistema, entonces se pueden deshabilitar Superfetch y Prefetch con el siguiente comando en CMD. Deshabilitar SysMain es parte de las recomendaciones de Microsoft para configurar dispositivos con rendimiento en tiempo real ([1](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)) ), la carpeta ``C:\Windows\Prefetch`` ya no debería llenarse de archivos.

  ```bat
  reg add "HKLM\SYSTEM\CurrentControlSet\Services\SysMain" /v "Start" /t REG_DWORD /d "4" /f
  ```

> [!IMPORTANT]
> Para evitar errores inesperados debidos a dependencias de servicios, evalúa qué servicios dependen de aquel que deseas deshabilitar. Esto puede hacerse escribiendo ``sc EnumDepend <service>`` en CMD como administrador. Si no puedes deshabilitarlos (porque los necesitas), entonces deberás dejar habilitado el servicio original.

<h2 id="operating-system-and-partition-name">11.18. Operating System and Partition Name <a href="#operating-system-and-partition-name">(permalink)</a></h2>

Configura el nombre del sistema operativo y de la partición de la unidad. Se recomienda establecer un nombre significativo o único como ``W10 22H2`` Trabajo o ``W10 22H2`` Juegos para mayor claridad al usar arranque dual o múltiples discos. Abre CMD como administrador e introduce los comandos necesarios.

  ```bat
  bcdedit /set {current} description "OS_NAME" 
  ```

  ```bat
  label C: OS_NAME
  ```

<h2 id="show-tray-icons">11.19. Show Tray Icons <a href="#show-tray-icons">(permalink)</a></h2>

Recomiendo habilitar la opción ``Always show all icons in the notification area`` para una mejor gestión de procesos. Ocultar iconos en la bandeja puede considerarse parcialmente un riesgo de seguridad, ya que podrías no notar programas maliciosos o no deseados ejecutándose en segundo plano.

<h2 id="hibernation">11.20. Hibernation <a href="#hibernation">(permalink)</a></h2>

Windows tiene una opción para desactivar el inicio rápido, la hibernación y eliminar ``C:\hiberfil.sys``. Se recomienda apagar completamente en lugar de guardar el estado de software en disco. Abre CMD como administrador e introduce el comando correspondiente.

```bat
powercfg /h off
```

<h2 id="runtimes">11.21. Runtimes <a href="#runtimes">(permalink)</a></h2>

Estos runtimes son dependencias comunes para una gran cantidad de aplicaciones. Normalmente los instaladores de aplicaciones instalan automáticamente sus dependencias, pero esto no siempre ocurre con aplicaciones standalone.

- [Visual C++ Redistributable](https://github.com/abbodi1406/vcredist)
- [.NET 3.5](https://woshub.com/how-to-install-net-framework-3-5-on-windows) (dependencia menos común, las instrucciones incluyen métodos de instalación offline y online)
- [.NET 4.8](https://dotnet.microsoft.com/en-us/download/dotnet-framework/net48) (incluido en Windows 10 1909+)
- [WebView](https://developer.microsoft.com/en-us/microsoft-edge/webview2)
- [DirectX](https://www.microsoft.com/en-gb/download/details.aspx?id=8109) (los lanzadores de juegos suelen instalar esto en segundo plano)

<h2 id="handling-bloatware">11.22. Handling Bloatware <a href="#handling-bloatware">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Desaconsejo fuertemente el uso de scripts de desbloat o la eliminación de componentes más allá del bloatware real como Candy Crush o cualquier otro software preinstalado que venga con Windows actualmente, ya que podrías romper el sistema operativo. Puede argumentarse que eliminar estas aplicaciones no aporta beneficio de rendimiento si no se ejecutan activamente en segundo plano, lo cual puede verificarse en el Administrador de Tareas. Para adoptar el enfoque de solo eliminar o deshabilitar lo que realmente se ejecuta en segundo plano, configura Process Explorer como se describe en la sección [Process Explorer](#process-explorer) y ordena los procesos por ``Context Switch Delta`` o ``Cycles Delta`` para evaluar qué se puede quitar. La velocidad de actualización puede modificarse en ``View -> Update Speed`` según tu tolerancia.

- [AppxPackagesManager](https://github.com/valleyofdoom/AppxPackagesManager) puede usarse para desinstalar paquetes Appx que vienen con Windows. Recomiendo conservar ``Microsoft.WindowsStore`` (Microsoft Store) (Microsoft Store) como mínimo para poder descargar aplicaciones más adelante. Los paquetes Appx también pueden instalarse sin la Microsoft Store ([1](https://superuser.com/questions/1721755/is-there-a-way-to-install-microsoft-store-exclusive-apps-without-store)). Si eliminaste la Microsoft Store por error, puede restaurarse con ``wsreset -i``

- Recomiendo encarecidamente eliminar OneDrive por razones de privacidad. Si necesitas usarlo, accede mediante el navegador. Para eliminar OneDrive, abre CMD como administrador e introduce el comando correspondiente.

    ```bat
    for %a in ("SysWOW64" "System32") do (if exist "%windir%\%~a\OneDriveSetup.exe" ("%windir%\%~a\OneDriveSetup.exe" /uninstall)) && reg delete "HKCU\SOFTWARE\Microsoft\Windows\CurrentVersion\Explorer\Desktop\NameSpace\{018D5C66-4533-4307-9B53-224DE2ED1FE6}" /f
    ```

- Deshabilitar (no desinstalar) el navegador Chromium Microsoft Edge implica los pasos siguientes. El navegador debe deshabilitarse en lugar de desinstalarse para conservar el runtime de WebView.

  - En la configuración de Microsoft Edge, desactiva las opciones de inicio como las siguientes. Esto evita que se cree una entrada de ejecución automática cada vez que se inicie ``msedge.exe``, incluso si la eliminas posteriormente con Autoruns:

    - ``Startup boost``
    - ``Continue running background extensions and apps when Microsoft Edge is closed``

  - Descarga [Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns), navega a la sección ``Everything`` y busca *`edge`*. Desactiva todos los elementos que aparezcan en los resultados filtrados.

  - Abre CMD e introduce el comando necesario para eliminar todos los accesos directos relacionados.

      ```bat
      for /f "delims=" %a in ('where /r C:\ *edge.lnk*') do (del /f /q "%a")
      ```

- Windows 10+ solamente:

  - En el menú de inicio, *desinstala* cualquier enlace residual de aplicaciones. Ten en cuenta que estas aplicaciones no están realmente instaladas, solo se instalan si haces clic en ellas, así que no lo hagas por accidente.

  - Desinstala el bloatware desde la sección de aplicaciones en el panel de control inmersivo presionando  ``Win+I`` (también puede gestionarse con [AppxPackagesManager](https://github.com/valleyofdoom/AppxPackagesManager))
  - En la sección ``Optional features`` del panel de control inmersivo, puedes desinstalar todo lo que no necesites si lo deseas.

- Si Windows Defender fue deshabilitado en la sección [Merging Registry Options](#merging-registry-options) estableciendo ``disable windows defender`` a ``true``, ``smartscreen.exe`` ignora la clave de registro que controla si se ejecuta en segundo plano de forma persistente en versiones recientes de Windows. Por esta razón, abre CMD como TrustedInstaller con ``C:\bin\MinSudo.exe --TrustedInstaller --Privileged`` e introduce el comando necesario para evitar que se ejecute en segundo plano.

    ```bat
    taskkill /f /im smartscreen.exe > nul 2>&1 & ren C:\Windows\System32\smartscreen.exe smartscreen.exee
    ```

- Puedes usar el Administrador de Tareas para comprobar si hay bloatware residual ejecutándose en segundo plano.

<h2 id="optional-features">11.23. Optional Features <a href="#optional-features">(permalink)</a></h2>

Las funciones opcionales se pueden acceder escribiendo ``OptionalFeatures`` en ``Win+R``. Habilita o desactiva funciones que necesites o no necesites. Si Windows Update está deshabilitado, probablemente no podrás instalar funciones desde esta ventana y, en su lugar, deberás instalar un paquete sin conexión usando DISM. En Windows Server, esto se puede acceder mediante el panel de Server Manager navegando a ``Manage -> Remove Roles and Features``.

<h3 id="net-35">11.23.1. NET 3.5 <a href="#net-35">(permalink)</a></h3>

Algunas aplicaciones aún utilizan el runtime de .NET 3.5, por lo que se recomienda instalarlo por si acaso. Como se mencionó anteriormente, no podrás instalarlo desde la ventana de Funciones Opcionales si Windows Update está desactivado, pero sí puedes hacerlo usando un paquete sin conexión.

Para usar el paquete sin conexión, descarga y extrae una ISO de Windows (por ejemplo en ``C:\EXTRACTED_ISO``) y abre CMD como administrador. Sustituye ``C:\EXTRACTED_ISO\sources\sxs`` por la ruta correcta a la carpeta ``\sources\sxs`` en la ISO que extrajiste y ejecuta el siguiente comando:

```bat
DISM /Online /Enable-Feature /FeatureName:NetFx3 /LimitAccess /Source:"C:\EXTRACTED_ISO\sources\sxs"
```

<h2 id="7-zip">11.24. 7-Zip <a href="#7-zip">(permalink)</a></h2>

Descarga e instala [7-Zip](https://www.7-zip.org). Abre ``C:\Program Files\7-Zip\7zFM.exe`` , luego navega a ``Tools -> Options`` y asocia 7-Zip con todas las extensiones de archivo haciendo clic en el botón ``+``. Puede que necesites hacer clic dos veces para sobrescribir asociaciones existentes.

<h2 id="graphics-driver">11.25. Graphics Driver <a href="#graphics-driver">(permalink)</a></h2>

- Ver: [docs/configure-nvidia.md](/docs/configure-nvidia.md)
- Ver: [docs/configure-amd.md](/docs/configure-amd.md)

<h2 id="msi-afterburner">11.26. MSI Afterburner <a href="#msi-afterburner">(permalink)</a></h2>

Si usas  [MSI Afterburner](https://www.msi.com/Landing/afterburner/graphics-cards), descárgalo e instálalo ahora.

- Se recomienda configurar una velocidad de ventilador estática, ya que usar la función de curva de ventilador requiere que el programa esté ejecutándose continuamente. Sin embargo, depende de ti si prefieres usar la curva o no.

- Para cargar automáticamente el perfil 1 (como ejemplo) al arrancar Windows, se puede usar el siguiente comando con el Programador de tareas ([1](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Asegúrate de colocar comillas si hay espacios en la ruta. Verifica que todo funcione correctamente tras reiniciar el sistema. Debes habilitar la opción ``Run with highest privileges`` si se requieren privilegios de administrador.

    ```bat
    "C:\Program Files (x86)\MSI Afterburner\MSIAfterburner.exe" /Profile1 /Q
    ```

<h2 id="display-resolutions-and-scaling-modes">11.27. Display Resolutions and Scaling Modes <a href="#display-resolutions-and-scaling-modes">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Si encontraste una sobreaceleración (overclock) estable para tu pantalla en secciones anteriores usando  [Custom Resolution Utility](https://www.monitortests.com/forum/Thread-Custom-Resolution-Utility-CRU), puedes aplicarla ahora.

- Normalmente, tienes la opción de realizar el escalado en la GPU o en la pantalla. La resolución nativa no requiere escalado, lo que resulta en escalado de identidad (sin escalado). Además, el escalado de identidad vuelve obsoletas la mayoría de las opciones de escalado en el panel de control de la GPU. Si estás usando una resolución no nativa, se puede argumentar que es preferible el escalado en la pantalla debido a menor procesamiento por parte de la GPU.

- Apunta a una tasa de refresco realmente entera como 60.00/240.00, no 59.94/239.76.

- Existen múltiples formas de lograr el mismo resultado respecto al escalado por GPU o pantalla. Consulta la tabla en el siguiente enlace para ver escenarios de ejemplo:

  - Ver: [¿Qué es el escalado de identidad y cómo puedes usarlo?](/docs/research.md#8-what-is-identity-scaling-and-how-can-you-use-it)

  - Opcionalmente, puedes usar [QueryDisplayScaling](https://github.com/valleyofdoom/QueryDisplayScaling) para consultar el modo de escalado actual.

- En sistemas con GPU NVIDIA, asegúrate de que la opción ``Display`` esté disponible en el ajuste ``Perform scaling on`` Si no está disponible, determina qué cambio en CRU provoca que deje de estar accesible mediante prueba y error. Esto se puede lograr ejecutando ``reset.exe`` para restaurar la configuración predeterminada y luego volver a configurar CRU. Después de cada cambio, ejecuta ``restart64.exe`` y comprueba si la opción sigue estando disponible.

- Asegúrate de que tu resolución esté configurada correctamente escribiendo ``rundll32.exe display.dll,ShowAdapterSettings`` en ``Win+R``

<h2 id="open-shell-windows-8">11.28. Open-Shell (Windows 8+) <a href="#open-shell-windows-8">(permalink)</a></h2>

Open-Shell es una alternativa FOSS al menú de inicio de Windows..

- Descarga e instala [Open-Shell](https://github.com/Open-Shell/Open-Shell-Menu). Solo instala el componente ``Open-Shell Menu``

- Configuraciones:

  - General Behavior

    - Check for Windows updates on shutdown - Desactivar

- Solo para Windows 8:

  - Abre ``"C:\Program Files\Open-Shell\Start Menu Settings.lnk"``, habilita ``Show all settings`` y navega a la sección de Configuración de Windows 8, luego establece ``Disable active corners`` en ``All``

<h2 id="spectre-meltdown-and-cpu-microcode">11.29. Spectre, Meltdown and CPU Microcode <a href="#spectre-meltdown-and-cpu-microcode">(permalink)</a></h2>

> [!WARNING]
> 🔒 Desactivar Spectre y Meltdown puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con la modificación de esta configuración.

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Desactivar Spectre y Meltdown es una técnica de mejora de rendimiento conocida desde hace tiempo por muchos entusiastas; sin embargo, con plataformas más recientes y arquitecturas modernas, puede producirse una regresión de rendimiento ([1](https://www.phoronix.com/review/amd-zen4-spectrev2)). Por esta razón, deben realizarse pruebas exhaustivas para determinar cómo se ve afectado el rendimiento y si éste escala de forma positiva, negativa o si no se ve afectado en absoluto. Su estado puede modificarse utilizando la herramienta [InSpectre](https://www.grc.com/inspectre.htm) y/o renombrando las DLLs de microcódigo dentro del sistema operativo, dependiendo de si existe una discrepancia entre las versiones de microcódigo del sistema operativo y de la BIOS ([1](https://superuser.com/a/895447), [2](https://support.mozilla.org/en-US/kb/microcode-update)). Es importante tener en cuenta que las versiones del microcódigo están sujetas a cambios con las actualizaciones de Windows.

<details>
<summary>Instrucciones para renombrar DLLs</summary>

Abre CMD como TrustedInstaller con el siguiente comando: ``C:\bin\MinSudo.exe --TrustedInstaller --Privileged`` Luego, introduce el comando correspondiente a tu CPU para eliminar las actualizaciones de microcódigo. Para revertir los cambios, simplemente intercambia los nombres de los archivos para restaurar la DLL original..

```
ren C:\Windows\System32\mcupdate_GenuineIntel.dll mcupdate_GenuineIntel.dlll
```

```
ren C:\Windows\System32\mcupdate_AuthenticAMD.dll mcupdate_AuthenticAMD.dlll
```

</details>

Meltdown does not affect the AMD architecture ([1](https://www.theverge.com/2018/1/3/16844630/intel-processor-security-flaw-bug-kernel-windows-linux), [2](https://www.phoronix.com/news/x86-PTI-Initial-Gaming-Tests), [3](https://lkml.org/lkml/2018/1/3/425)) and is required for a minority of anticheats (FACEIT).

Use [InSpectre](https://www.grc.com/inspectre.htm) and [CPU-Z's](https://www.cpuid.com/softwares/cpu-z.html) validation feature to check the status or version before and after a reboot to verify expected behavior.

<h2 id="power-options">11.30. Power Options <a href="#power-options">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Open CMD and enter the commands below.

- Set the active power scheme to High performance

    ```bat
    powercfg /setactive 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

- Remove the Balanced power scheme

    ```bat
    powercfg /delete 381b4222-f694-41f0-9685-ff5bb260df2e
    ```

- Remove the Power Saver power scheme

    ```bat
    powercfg /delete a1841308-3541-4fab-bc81-f71556f20b4a
    ```

- USB 3 Link Power Management - Off

    ```bat
    powercfg /setacvalueindex scheme_current 2a737441-1930-4402-8d77-b2bebba308a3 d4e98f31-5ffe-4ce1-be31-1b38b384c009 0
    ```

- USB Selective Suspend - Disabled

    ```bat
    powercfg /setacvalueindex scheme_current 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0
    ```

- Processor performance core parking min cores - 100

    - CPU parking is disabled by default in the High Performance power scheme ([1](https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/hardware/power/power-performance-tuning#using-power-plans-in-windows-server)). However on Windows 11+ with modern CPUs, parking is overridden and enabled. Users can determine whether CPUs are parked by typing ``resmon`` in ``Win+R``. Apart from parking intended to be a power saving feature, videos such as [this](https://www.youtube.com/watch?v=2yOYfT_r0xI) and [this](https://www.youtube.com/watch?v=gyg7Gm7aN2A) explain that it is the desired behavior for correct thread scheduling which is probably fine for the average user, but they do not account for the latency penalty of unparking cores (as with C-State transitions) along with kernel-mode activity (interrupts, DPCs). In terms of per-CPU scheduling, you can easily achieve the same outcome by managing per-CPU load manually (e.g. pin the real-time application to a [single CCX/CCD](https://hwbusters.com/cpu/amd-ryzen-9-7950x3d-cpu-review-performance-thermals-power-analysis/2) or P-Cores) by configuring affinities with the advantage being no overhead from chipset drivers and Xbox processes constantly running in the background forcing unnecessary context switches. See the [Per-CPU Scheduling](#per-cpu-scheduling) section for more information

        ```bat
        powercfg /setacvalueindex scheme_current 54533251-82be-4824-96c1-47b60b740d00 0cc5b647-c1df-4637-891a-dec35c318583 100
        ```

        ```bat
        powercfg /setacvalueindex scheme_current 54533251-82be-4824-96c1-47b60b740d00 0cc5b647-c1df-4637-891a-dec35c318584 100
        ```
        
        - Processor performance time check interval - 5000

    - There are a handful of ntoskrnl power management DPCs that are scheduled at a periodic interval to re-evaluate P-States and parked cores. With a static CPU frequency and core parking disabled, these checks become obsolete thus unnecessary DPCs get scheduled. The ``Processor performance time check interval`` setting controls how often these checks are taken place so increasing the setting's value can reduce CPU overhead as significantly fewer DPCs are scheduled. For reference and at the time of checking, the Power Saver, Balanced, High performance power schemes have a default value of 200, 15 and 15 respectively. 5000 is the maximum accepted value. Of course, if a dynamic CPU frequency is used (e.g. Precision Boost Overdrive, Turbo Boost) and parking is enabled, the effects of increasing this value should be evaluated as cores may not be able to boost their frequency in response to workloads as the OS is evaluating the current scenario less often

        <table style="text-align: center;">
            <tr>
                <td rowspan="2">DPC Function</td>
                <td colspan="3">Average DPC Rate</td>
                <td colspan="3">Total DPCs</td>
            </tr>
            <tr>
                <td>15</td>
                <td>200</td>
                <td>5000</td>
                <td>15</td>
                <td>200</td>
                <td>5000</td>
            </tr>
            <tr>
                <td>ntoskrnl!PpmPerfAction</td>
                <td>15.45Hz</td>
                <td>3.07Hz</td>
                <td>N/A</td>
                <td>311</td>
                <td>60</td>
                <td>1</td>
            </tr>
            <tr>
                <td>ntoskrnl!PpmCheckRun</td>
                <td>12.99Hz</td>
                <td>2.29Hz</td>
                <td>N/A</td>
                <td>262</td>
                <td>46</td>
                <td>1</td>
            </tr>
            <tr>
                <td>ntoskrnl!PpmCheckPeriodicStart</td>
                <td>60.39Hz</td>
                <td>4.99Hz</td>
                <td>0.2Hz</td>
                <td>1213</td>
                <td>100</td>
                <td>4</td>
            </tr>
        </table>

        ```bat
        powercfg /setacvalueindex scheme_current 54533251-82be-4824-96c1-47b60b740d00 4d2b0152-7d5c-498b-88e2-34345392a2c5 5000
        ```

- Set the active scheme as the current scheme

    ```bat
    powercfg /setactive scheme_current
    ```

<h2 id="process-explorer">11.31. Process Explorer <a href="#process-explorer">(permalink)</a></h2>

Task Manager lacks several useful metrics compared to a tool such as Process Explorer. On Windows 8+, Task Manager reports CPU utility in % which provides misleading CPU utilization details ([1](https://aaron-margosis.medium.com/task-managers-cpu-numbers-are-all-but-meaningless-2d165b421e43)). On the other hand, Windows 7's Task Manager and Process Explorer report time-based busy utilization. This also explains as to why disabling idle states within the OS results in 100% CPU utilization in Task Manager.

- Download and extract [Process Explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)

- Copy ``procexp64.exe`` into a safe directory such as ``C:\Windows`` and open it

- Navigate to ``Options`` and select ``Replace Task Manager``. Optionally configure the following:

  - Confirm Kill

  - Allow Only One Instance

  - Always On Top (helpful for when applications crash and UI becomes unresponsive)

  - Enable the following columns for granular resource measurement metrics

    - Context Switch Delta (Process Performance)

    - CPU Cycles Delta (Process Performance)

    - Delta Reads (Process I/O)

    - Delta Writes (Process I/O)

    - Delta Other (Process I/O)

  - Enable the ``VirusTotal`` column

<h2 id="memory-management-settings-windows-8">11.32. Memory Management Settings (Windows 8+) <a href="#memory-management-settings-windows-8">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

- Open PowerShell and enter the command below to review memory management options

    ```powershell
    Get-MMAgent
    ```

- Optionally use the command below as an example to disable a given setting. If you left Superfetch and Prefetch enabled in section [Superfetch and Prefetch](#superfetch-and-prefetch), then you likely want the prefetching related features enabled

    ```powershell
    Disable-MMAgent -MemoryCompression
    ```

<h2 id="network-adapter-options">11.33. Network Adapter Options <a href="#network-adapter-options">(permalink)</a></h2>

- Open ``Network Connections`` by typing ``ncpa.cpl`` in ``Win+R``

- Disable any unused network adapters then right-click your main one then select ``Properties``

- Disable ``NetBIOS over TCP/IP`` for all network adapters in ``Internet Protocol Version 4 (TCP/IPv4) -> Properties -> General -> Advanced -> WINS`` to prevent unnecessary system listening, typically on ports 137-139 which can be verified in a network monitoring tool such as [TCPView](https://learn.microsoft.com/en-us/sysinternals/downloads/tcpview) or [Wirehshark](https://www.wireshark.org). For future reference, this option has to be changed for newly installed network adapters

- Optionally configure DNS settings

  - See [DNS Resolvers - Recommended Providers | Privacy Guides](https://www.privacyguides.org/en/dns)

<h2 id="audio-devices">11.34. Audio Devices <a href="#audio-devices">(permalink)</a></h2>

- The sound control panel can be opened by typing ``mmsys.cpl`` in ``Win+R``

- Disable unused Playback and Recording devices

- I would recommend avoid using audio enhancements as they appear to marginally waste resources ([1](/assets/images/audio%20enhancements-benchmark.png))

- Optionally set the option in the communications tab to ``Do nothing`` to prevent automatic adjustment of audio levels between audio sources as this is an annoyance for the majority of users ([1](https://multimedia.easeus.com/ai-article/windows-audio-ducking.html), [2](https://superuser.com/questions/1147371/how-can-i-disable-automatic-windows-7-8-10-audio-ducking))

- Minimize the size of the audio buffer with [LowAudioLatency](https://github.com/spddl/LowAudioLatency) or on your DAC ([1](https://www.youtube.com/watch?v=JTuZvRF-OgE&t=464s)). Beware of audio dropouts due to the CPU not being able to keep up under load

<h2 id="device-manager">11.35. Device Manager <a href="#device-manager">(permalink)</a></h2>

- Open Device Manager by typing ``devmgmt.msc`` in ``Win+R``

- Navigate to ``View -> Devices by type``

  - In the ``Disk drives`` category, you can disable write-cache buffer flushing on all drives in the ``Properties -> Policies`` section if your system has a backup power supply or is not prone to power failures to prevent data loss
  - In the ``Network adapters`` category, navigate to ``Properties -> Advanced`` and disable any power-saving features

- Navigate to ``View -> Devices by connection``

  - Disable any PCIe, SATA, NVMe and XHCI controllers and USB hubs with nothing connected to them
  - Disable every device that isn't the GPU on the same PCIe port as the GPU as long as you don't need them

- Navigate to ``View -> Resources by connection``

  - Disable any unneeded devices that are using an IRQ or I/O resources, always ask if unsure and take your time on this step
  - If there are multiple entries of the same devices and you are unsure which one is in use, refer back to the tree structure in ``View -> Devices by connection``. This is because a single device can use many resources (e.g. IRQs). You can also use [MSI Utility](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044) to check for duplicate and unneeded devices in case you accidentally miss any with the cluttered Device Manager tree structure

- Optionally use [DeviceCleanup](https://www.uwe-sieber.de/files/DeviceCleanup.zip) to remove hidden devices

<h2 id="device-power-saving">11.36. Device Power-Saving <a href="#device-power-saving">(permalink)</a></h2>

Open PowerShell and enter the command below to disable the ``Allow the computer to turn off this device to save power`` option for all applicable devices in Device Manager.

Re-plugging devices may cause this option to re-enable so either avoid doing so, run this command again each time or place it in a script and run it at system startup as a precautionary measure with Task Scheduler ([instructions](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Ensure to wrap any paths with quotes if there are spaces in them. Ensure to verify whether everything is working correctly after a system restart. You need to enable the ``Run with highest privileges`` option if administrator privileges are required. For PowerShell scripts, set the program to start to ``PowerShell`` and the arguments to the path of the script (e.g. ``C:\device-power-saving.ps1``).

```powershell
Get-WmiObject MSPower_DeviceEnable -Namespace root\wmi | ForEach-Object { $_.enable = $false; $_.psbase.put(); }
```

<h2 id="event-trace-sessions-ets">11.37. Event Trace Sessions (ETS) <a href="#event-trace-sessions-ets">(permalink)</a></h2>

This section outlines instructions to mass-toggle the majority of Event Trace Sessions which can be viewed by typing ``perfmon`` in ``Win+R`` then navigating to ``Data Collector Sets -> Event Trace Sessions``. Programs that rely on event tracers will not be able to log data until the required sessions are restored (e.g. Windows Event Logging) which is the purpose of creating two registry files to toggle between them. Open CMD as administrator and enter the commands below to build the registry files in the ``C:\`` directory. These registry files must be run with Trusted Installer (use [NSudo](https://github.com/M2TeamArchived/NSudo/releases/latest)) to prevent permission errors.

- ``ets-enable.reg``

    ```bat
    reg export "HKLM\SYSTEM\CurrentControlSet\Control\WMI\Autologger" "C:\ets-enable.reg"
    ```

- ``ets-disable.reg``

    ```bat
    >> "C:\ets-disable.reg" echo Windows Registry Editor Version 5.00 && >> "C:\ets-disable.reg" echo. && >> "C:\ets-disable.reg" echo [-HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger]
    ```

<h2 id="file-system">11.38. File System <a href="#file-system">(permalink)</a></h2>

Open CMD as administrator and enter the commands below.

- Disable the creation of 8.3 character-length file names on FAT and NTFS-formatted volumes which aids performance and security ([1](https://web.archive.org/web/20200217151754/https://ttcshelbyville.wordpress.com/2018/12/02/should-you-disable-8dot3-for-performance-and-security))

  - Disable the creation of 8.3 character-length file names

    ```bat
    fsutil 8dot3name set 1
    ```

  - If the steps carried out in section [Booting Into the ISO](#booting-into-the-iso) to strip 8dot3 names was followed correctly, the command below should display a value close to 0 for "total 8dot3 names found"

    ```bat
    fsutil 8dot3name scan /s C:
    ```

- Disable updates to the Last Access Time stamp on each directory when directories are listed on an NTFS volume. Disabling the Last Access Time feature improves the speed of file and directory access ([1](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-behavior#remarks)). Beware that this may affect backup and remote storage programs as per the official remarks ([1](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-behavior#remarks))

    ```bat
    fsutil behavior set disablelastaccess 1
    ```

<h2 id="message-signaled-interrupts">11.39. Message Signaled Interrupts <a href="#message-signaled-interrupts">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Message signaled interrupts (MSIs) are faster than traditional line-based interrupts and may also resolve the issue of shared interrupts which are often the cause of high interrupt latency and stability ([1](https://repo.zenk-security.com/Linux%20et%20systemes%20d.exploitations/Windows%20Internals%20Part%201_6th%20Edition.pdf)).

- Download and open [MSI Utility](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044) or [GoInterruptPolicy](https://github.com/spddl/GoInterruptPolicy)

- MSIs can be enabled on devices that support it. It is worth noting that it may be in the developer's intention to not enable MSIs in the driver INF file hence MSIs will be disabled by default once the driver is installed. Namely, NVIDIA seems to selectively enable MSIs depending on the GPU architecture ([1](https://www.nvidia.com/en-us/geforce/forums/game-ready-drivers/13/528356)). Exercise with due care and carry out tests to determine whether changes result in positive performance scaling

  - You will BSOD if you enable MSIs for the stock Windows 7 SATA driver which you should have already updated as mentioned in section [Installing Drivers](#installing-drivers)

- To verify whether a device is utilizing MSIs, restart your PC and check whether the given device has a negative IRQ in MSI Utility

- Although this step may have been caried out in an earlier section to rule out the hardware-related causes of IRQ sharing, the software-related causes of potential IRQ sharing can be assessed now by confirming that there is no IRQ sharing on your system by typing ``msinfo32`` in ``Win+R`` then navigating to the ``Conflicts/Sharing`` section

  - If the ``System timer`` device and ``High precision event timer`` are sharing IRQ 0, a solution to this is to disable the parent device's driver of ``System timer`` which is ``PCI standard ISA bridge``. This can be accomplished with the command below. It is important to note that disabling ``msisadrv`` breaks the keyboard on mobile devices

    ```bat
    reg add "HKLM\SYSTEM\CurrentControlSet\Services\msisadrv" /v "Start" /t REG_DWORD /d "4" /f
    ```

> [!IMPORTANT]
> To prevent unexpected breakage and problems due to service dependency errors, assess the other services that depend on the service you want to disable. This can be done by opening CMD as administrator then typing ``sc EnumDepend <service>`` which describes the services that rely on the service you want to disable. These services should be disabled to avoid dependency errors. If you can't disable them (e.g. because you need them), then you have no choice but to leave the service you wanted to disable initially enabled.

<h2 id="xhci-interrupt-moderation-imod">11.40. XHCI Interrupt Moderation (IMOD) <a href="#xhci-interrupt-moderation-imod">(permalink)</a></h2>

On most systems, Windows 7 uses an IMOD interval of 1ms whereas recent versions of Windows use 0.05ms (50us) unless specified by the installed USB driver. This means that after an interrupt has been generated, the XHCI controller waits (buffer period) for the specified interval for more data to arrive before generating another interrupt which reduces CPU utilization but potentially results in data from a given device being supplied at an inconsistent rate in the event of expecting data from other devices within the buffer period that are connected to the same XHCI controller.

For example, a mouse with a 1kHz polling rate will report data every 1ms. While only moving the mouse with an IMOD interval of 1ms, interrupt moderation will not be taking place because interrupts are being generated at a rate less than or equal to the specified interval. Realistically while playing a fast-paced game, you will easily surpass 1000 interrupts/s with keyboard and audio interaction while moving the mouse hence there will be a loss of information because you will be expecting data within the waiting period from either devices. Although this is unlikely with an IMOD interval of 0.05ms (50us), it can still happen.

As an example, 1ms IMOD interval with an 8kHz mouse is already problematic because you are expecting data every 0.125ms which is significantly greater than the specified interval which results in a major bottleneck ([1](https://www.overclock.net/threads/usb-polling-precision.1550666/page-61#post-28576466)).

- See [How to persistently disable XHCI Interrupt Moderation | BoringBoredom](https://github.com/BoringBoredom/PC-Optimization-Hub/blob/main/content/xhci%20imod/xhci%20imod.md)

- Microsoft Vulnerable Driver Blocklist may need to be disabled with the command below in order to load the [RWEverything](http://rweverything.com) driver however some in-game anticheats do not adhere to disabling the blocklist so you will need to test whether this is the case (e.g. game refuses to launch)

    ```bat
    reg add "HKLM\SYSTEM\CurrentControlSet\Control\CI\Config" /v "VulnerableDriverBlocklistEnable" /t REG_DWORD /d "0" /f
    ```

- In some cases, the interrupter index can change after a reboot meaning the address will become invalid if it is hard-coded. To work around this, you can simply disable IMOD for all interrupters by placing the [XHCI-IMOD-Interval.ps1](/bin/XHCI-IMOD-Interval.ps1) script somewhere safe and launching it at startup with Task Scheduler ([instructions](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Ensure to wrap any paths with quotes if there are spaces in them. Ensure to verify whether everything is working correctly after a system restart. You need to enable the ``Run with highest privileges`` option if administrator privileges are required. For PowerShell scripts, set the program to start to ``PowerShell`` and the arguments to the path of the script (e.g. ``C:\XHCI-IMOD-Interval.ps1``)

  ```bat
  PowerShell C:\XHCI-IMOD-Interval.ps1
  ```

- To determine whether changing the IMOD interval is taking effect, you can temporarily set the interval to ``0xFA00`` (62.5Hz). If the mouse cursor is visibly stuttering upon movement, then the changes are successfully taking effect

<h2 id="control-panel">11.41. Control Panel <a href="#control-panel">(permalink)</a></h2>

It isn't a bad idea to skim through both the legacy and immersive control panel to ensure nothing is misconfigured.

<h2 id="configuring-applications">11.42. Configuring Applications <a href="#configuring-applications">(permalink)</a></h2>

- Install any programs and applications that you use (including games) to prepare us for the next steps

- If applicable, favor portable editions of programs as installers tend to leave bloatware behind even after uninstalling them however, this can be circumvented by using programs such as [Bulk-Crap-Uninstaller](https://github.com/Klocman/Bulk-Crap-Uninstaller)

<h3 id="nvidia-reflex">11.42.1. NVIDIA Reflex <a href="#nvidia-reflex">(permalink)</a></h3>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

[NVIDIA Reflex](https://www.nvidia.com/en-us/geforce/news/reflex-low-latency-platform) minimizes queued frames in the GPU render queue by dynamically adjusting the framerate in GPU-intensive gaming scenarios and can be enabled in-game if the developer has added support for it. Although this minimizes latency, it acts as a dynamic framerate limiter and can result in minor stuttering or frametime variance. For this reason, I would recommend extensively benchmarking this rather than blindly enabling it in your chosen games.

- See [NVIDIA Reflex Low Latency - How It Works & Why You Want To Use It | Battle(non)sense](https://www.youtube.com/watch?v=QzmoLJwS6eQ)

<h3 id="framerate-limit">11.42.2. Framerate Limit <a href="#framerate-limit">(permalink)</a></h3>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

- If you cap your framerate, ensure to set it at a multiple of your monitor refresh rate ([calculator](https://boringboredom.github.io/tools/fpscapcalculator)) to prevent frame mistiming and a rolling tearline ([1](https://www.youtube.com/watch?v=_73gFgNrYVQ), [2](https://github.com/BoringBoredom/PC-Optimization-Hub/blob/main/content/peripherals/mistiming/mistiming.md)). Reducing your refresh rate to avoid mismatching is also applicable ([instructions](https://forums.blurbusters.com/viewtopic.php?t=8946)). Other options include Variable Refresh Rate

- Ensure that the GPU isn't fully utilized as lower GPU utilization reduces system latency ([1](https://www.youtube.com/watch?v=8ZRuFaFZh5M&t=859s), [2](https://www.youtube.com/watch?v=7CKnJ5ujL_Q))

- Capping your framerate with [RTSS](https://www.guru3d.com/files-details/rtss-rivatuner-statistics-server-download.html) instead of the in-game limiter will result in consistent frame pacing and a smoother experience as it utilizes busy-wait which offers higher precision than 100% passive-waiting but at the cost of noticeably higher latency and potentially greater CPU overhead ([1](https://www.youtube.com/watch?t=377&v=T2ENf9cigSk), [2](https://en.wikipedia.org/wiki/Busy_waiting)). Disabling the ``Enable dedicated encoder server service`` setting prevents ``EncoderServer.exe`` from running

<h3 id="register-game">11.42.3. Register Game in Config Store <a href="#register-game">(permalink)</a></h3>

Ensure that Xbox Game Bar acknowledges the game that you are running or have installed. If not, open Game Bar by pressing ``Win+G`` and enabling ``Remember this is a game`` while it is open. This also ensures that Game Mode functions properly if you choose to use it.

<h3 id="presentation-mode">11.42.4. Presentation Mode <a href="#presentation-mode">(permalink)</a></h3>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

This is not a recommendation of what presentation mode to use and is instead, here for informative purposes.

- Always verify whether your game is using the desired presentation mode with PresentMon ([instructions](https://boringboredom.github.io/Frame-Time-Analysis))

- You can experiment and benchmark different presentation modes to assess which you prefer

  - See [Presentation Model | Special K Wiki](https://wiki.special-k.info/en/Presentation_Model)

- If there are no results after searching for the application's binary name in ``HKCU\SYSTEM\GameConfigStore`` within registry, you may need to register the game by pressing ``Win+G`` and enabling ``Remember this is a game`` while it is open. Check whether the entry has been created under the aforementioned registry key once completed

- If you want to use the ``Hardware: Legacy Flip`` presentation mode, tick the ``Disable fullscreen optimizations`` checkbox. If that doesn't work, try running the commands below in CMD and reboot. These registry keys are typically accessed by the game and Windows upon launch

    ```bat
    reg add "HKCU\SYSTEM\GameConfigStore" /v "GameDVR_DXGIHonorFSEWindowsCompatible" /t REG_DWORD /d "1" /f
    ```

    ```bat
    reg add "HKCU\SYSTEM\GameConfigStore" /v "GameDVR_FSEBehavior" /t REG_DWORD /d "2" /f
    ```

- If you are stuck with ``Hardware Composed: Independent Flip`` and would like to use another presentation mode, try running the command below to disable MPOs in CMD and reboot

    ```bat
    reg add "HKLM\SOFTWARE\Microsoft\Windows\Dwm" /v "OverlayTestMode" /t REG_DWORD /d "5" /f
    ```

<h3 id="game-mode">11.42.5. Game Mode <a href="#game-mode">(permalink)</a></h3>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Game Mode prevents Windows Update running and certain notifications from being pushed to the user ([1](https://support.xbox.com/en-GB/help/games-apps/game-setup-and-play/use-game-mode-gaming-on-pc)).

It is worth noting that Game Mode can intefere with process and thread priority boosts depending on the value of PsPrioritySeparation as explained in section [Thread Quantums and Scheduling](#thread-quantums-and-scheduling). This is evident by replicating the listening to thread priority boosts experiment in Windows Internals using Performance Monitor and the thread current priority performance counter. For this reason, you can experiment with Game Mode enabled and disabled.

<h3 id="media-player">11.42.6. Media Player <a href="#media-player">(permalink)</a></h3>

- [mpv](https://mpv.io) or [mpv.net](https://github.com/stax76/mpv.net)
- [mpc-hc](https://mpc-hc.org) ([updated fork](https://github.com/clsid2/mpc-hc))
- [VLC](https://www.videolan.org)

<h3 id="qos-policies">11.42.7. QoS Policies <a href="#qos-policies">(permalink)</a></h3>

Depending on your network and router configuration, QoS policies can be set in Windows to prioritize packets of an application.

- See [assets/images/dscp-46-qos-policy.png](/assets/images/dscp-46-qos-policy.png)

  - See [DSCP and Precedence Values | Cisco](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus1000/sw/4_0/qos/configuration/guide/nexus1000v_qos/qos_6dscp_val.pdf)

  - See [The QoS Expedited Forwarding (EF) Model | Network World](https://www.networkworld.com/article/761413/the-qos-expedited-forwarding-ef-model.html)

- See [How Can You Verify Whether a DSCP QoS Policy Is Working?](/docs/research.md#2-how-can-you-verify-whether-a-dscp-qos-policy-is-working)

- Microsoft recommend the registry entry below to ensure packets are correctly tagged with the DSCP value, especially when more than one network adapter is present or the policy is used outside a domain ([1](https://learn.microsoft.com/en-us/skypeforbusiness/manage/network-management/qos/configuring-port-ranges-for-your-skype-clients))

  ```bat
  reg add "HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\QoS" /v "Do not use NLA" /t REG_SZ /d "1" /f
  ```

<h2 id="kernel-mode-scheduling-interrupts-dpcs-and-more">11.43. Kernel-Mode Scheduling (Interrupts, DPCs and more) <a href="#kernel-mode-scheduling-interrupts-dpcs-and-more">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Windows schedules interrupts and DPCs on CPU 0 for several kernel-mode modules by default. In any case, scheduling many tasks on a single CPU can introduce additional overhead and increased jitter due to them competing for CPU time. To alleviate this, affinities can be configured to isolate given modules from disturbances including servicing time-sensitive modules on underutilized CPUs instead of clumping everything on a single CPU.

- Use the xperf DPC/ISR report generated by the [xperf-dpcisr.bat](/bin/xperf-dpcisr.bat) script or [xtw](https://github.com/valleyofdoom/xtw) to analyze which CPUs kernel-mode modules are being serviced on. You can not manage affinities if you do not know what is running and which CPU(s) they are running on to begin with. The same concept applies to user-mode threads. Additionally, verify whether interrupt affinity policies are performing as expected by analyzing per-CPU usage for the module in question while the device is busy

- Additionally, core-to-core-latency benchmarks can assist with decision-making in terms of affinity management

  - See [CXWorld/MicroBenchX](https://github.com/CXWorld/MicroBenchX)

- Ensure that the corresponding DPC for an ISR is processed on the same CPU ([example](/assets/images/isr-dpc-same-core.png)). Additional overhead can be introduced if they are processed on different CPUs due to increased inter-processor communication and interfering with cache coherence

- Use [Microsoft Interrupt Affinity Tool](https://www.techpowerup.com/download/microsoft-interrupt-affinity-tool) or [GoInterruptPolicy](https://github.com/spddl/GoInterruptPolicy) to configure driver affinities. The device can be identified by cross-checking the ``Location`` in the ``Properties -> General`` section of a device in Device Manager

<h3 id="gpu-and-directx-graphics-kernel">11.43.1. GPU and DirectX Graphics Kernel <a href="#gpu-and-directx-graphics-kernel">(permalink)</a></h3>

[AutoGpuAffinity](https://github.com/valleyofdoom/AutoGpuAffinity) can be used to benchmark the most performant CPUs that the GPU-related modules are assigned to. Configure the ``custom_cpus`` option in the config file if applicable. This option is useful for selecting a certain set of cores to benchmark such as P-Cores or a specific CCX/CCD.

<h3 id="xhci-and-audio-controller">11.43.2. XHCI and Audio Controller <a href="#xhci-and-audio-controller">(permalink)</a></h3>

The XHCI and audio controller related modules generate a substantial amount of interrupts upon interaction respective of the relevant device. Isolating the related modules to an underutilized CPU is beneficial for reducing contention.

<h3 id="network-interface-card">11.43.3. Network Interface Card <a href="#network-interface-card">(permalink)</a></h3>

The NIC must support MSI-X for Receive Side Scaling to function properly ([1](https://old.reddit.com/r/intel/comments/9uc03d/the_i219v_nic_on_your_new_z390_motherboard_and)). In most cases, RSS base CPU is enough to migrate DPCs and ISRs for the NIC driver which eliminates the need for an interrupt affinity policy. However, if you are having trouble migrating either to other CPUs, try configuring both.

Keep in mind that the amount of RSS queues determines the amount of consecutive CPUs that the network driver is scheduled on. For example, the driver will be scheduled on CPU 2/3/4/5 (2/4/6/8 with HT/SMT enabled) if RSS base CPU is set to 2 along with 4 RSS queues configured.

- See [How many RSS Queues do you need?](/docs/research.md#4-how-many-rss-queues-do-you-need)

- See [Receive Side Scaling (RSS) Configuration](https://github.com/Duckleeng/TweakCollection#receive-side-scaling-rss-configuration)

<h2 id="user-mode-scheduling-processes-threads">11.44. User-Mode Scheduling (Processes, Threads) <a href="#user-mode-scheduling-processes-threads">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

There are several methods to set affinities for processes. One of which is Task Manager but only persists until the process is closed. A more popular and permanent solution is [Process Lasso](https://bitsum.com) which allows the configuration to be saved however, a process must run continually in the background which introduces minor overhead. To work around this, you can simply launch the application with a specified CPU affinity which eliminates the requirement of programs such as Process Lasso for affinity management at the expense of usability.

- Use the [CPU Affinity Mask Calculator](https://bitsum.com/tools/cpu-affinity-calculator) to determine the desired hexal affinity bitmask

- In some cases, process can be protected so specifying the affinity may fail. To work around this, you can try specifying the affinity for the parent processes which will cause the child process to inherit the affinity when spawned. As an example, a game launcher is usually the parent process of a game. [Process Explorer's](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer) process tree can be used to identify parent and child processes

  - [Process Hacker](https://processhacker.sourceforge.io) and [WindowsD](https://github.com/katlogic/WindowsD) can bypass several process-level protections through exploits but is not advised as they interfere with anticheats

- It may be worth benchmarking the performance scaling of your application against core count as it may behave differently due to poor scheduling implementations from the application and/or OS. In some cases, it is possible that the application may perform better with fewer cores assigned to it via an affinity mask ([1](https://developer.nvidia.com/blog/limiting-cpu-threads-for-better-game-performance)). This will also give you a rough idea as to how many cores you can reserve. In other cases, it can severely harm performance as there is a potential for the game to create more worker threads than CPUs due to the game only considering the amount of physical cores available hence, it is vital that performance scaling is measured

<h3 id="starting-a-process-with-a-specified-affinity-mask">11.44.1. Starting a Process with a Specified Affinity Mask <a href="#starting-a-process-with-a-specified-affinity-mask">(permalink)</a></h3>

The command below starts ``notepad.exe`` with an affinity of CPU 1 and CPU 2 as an example which will reflect in Task Manager. This command can be placed in a batch script for easy access and must be used each time to start the desired application with the specified affinity.

```bat
start /affinity 0x6 notepad.exe
```

<h3 id="specifying-an-affinity-mask-for-running-processes">11.44.2. Specifying an Affinity Mask for Running Processes <a href="#specifying-an-affinity-mask-for-running-processes">(permalink)</a></h3>

Sometimes, the processes that you would like to set an affinity mask to are already running, so the previous command is not applicable here. As a random example, the command below sets the affinity mask of the ``svchost.exe`` and ``audiodg.exe`` processes to CPU 3. Use this example to create a PowerShell script then have it run at startup using Task Scheduler ([instructions](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Ensure to wrap any paths with quotes if there are spaces in them. Ensure to verify whether everything is working correctly after a system restart. You need to enable the ``Run with highest privileges`` option if administrator privileges are required. For PowerShell scripts, set the program to start to ``PowerShell`` and the arguments to the path of the script (e.g. ``C:\process-affinities.ps1``).

```powershell
Get-Process @("svchost", "audiodg") -ErrorAction SilentlyContinue | ForEach-Object { $_.ProcessorAffinity=0x8 }
```

<h2 id="reserved-cpu-sets-windows-10">11.45. Reserved CPU Sets (Windows 10+) <a href="#reserved-cpu-sets-windows-10">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

[ReservedCpuSets](https://github.com/valleyofdoom/ReservedCpuSets) can be used to prevent Windows routing ISRs, DPCs and scheduling other threads on specific CPUs. Isolating modules from user and kernel-level disturbances helps reduce contention, jitter and allows time-sensitive modules to get the CPU time they require.

- As mentioned in section [User-Mode Scheduling (Processes, Threads)](#user-mode-scheduling-processes-threads), you should determine how well or poorly your application's performance scales with core count to give you a rough idea as to how many cores you can afford to reserve

- As interrupt affinity policies, process and thread affinities have higher precedence, you can use this hand in hand with user-defined affinities to go a step further and ensure that nothing except what you assigned to specific CPUs will be scheduled on those CPUs

- Ensure that you have enough cores to run your real-time application on and aren't reserving too many CPUs to the point where isolating modules does not yield real-time performance

- As CPU sets are considered soft policies, the configuration isn't guaranteed. A CPU-intensive process such as a stress-test will utilize the reserved cores if required

> [!IMPORTANT]
> Unexpected behavior occurs when a process affinity is set to both reserved and unreserved CPUs. Ensure to set the affinity to either reserved or unreserved CPUs, not a combination of both.

<h3 id="use-cases">11.45.1. Use Cases <a href="#use-cases">(permalink)</a></h3>

- Hinting to the OS to schedule tasks on a group of CPUs. An example of this with modern platforms could be reserving E-Cores (efficiency cores) or either CCX/CCDs so that tasks are scheduled on P-Cores (performance cores) or other CCX/CCDs by default. With this approach, you can explicitly enforce background and unimportant tasks to be scheduled on the reserved CPUs. Note that this is purely an example and the logic can be flipped, but some latency-sensitive processes and modules are protected so affinity policies may fail which is a major limitation. There are several possibilities and trade-offs to consider. Note that performance can degrade when reserving E-Cores or other CCX/CCDs as applications may make use of them. Therefore, it is vital that you measure performance scaling when reserving cores whether it be one, a few or a set of CPUs. Another way of severly degrading performance by reserving E-Cores or CCX/CCDs is that the scheduler or applications can specifically target reserved cores for work to be scheduled on them as the ``RealTime`` field is set to 1 in the [SYSTEM_CPU_SET_INFORMATION](https://learn.microsoft.com/en-us/windows/win32/api/winnt/ns-winnt-system_cpu_set_information) struct

- Reserving CPUs that have specific modules assigned to be scheduled on them

<h2 id="analyzing-event-viewer">11.46. Analyzing Event Viewer <a href="#analyzing-event-viewer">(permalink)</a></h2>

This step isn't required, but can help to justify unexplained performance issues or issues in general. Ensure that there are no errors present on Event Viewer by typing ``eventvwr.msc`` in ``Win+R`` as anything you may have changed to your operating system could lead to internal errors or exceptions being thrown periodically.

- Merge the ``ets-enable.reg`` file that was generated in section [Event Trace Sessions (ETS)](#event-trace-sessions-ets) if applicable as it is required for event logging

<h2 id="virtualization-based-security-vbs">11.47. Virtualization Based Security (VBS) <a href="#virtualization-based-security-vbs">(permalink)</a></h2>

Virtualization Based Security negatively impacts performance ([1](https://www.tomshardware.com/news/windows-11-gaming-benchmarks-performance-vbs-hvci-security)) and in some cases, it is enabled by default. Its status can be determined by typing ``msinfo32`` in ``Win+R`` and can be disabled ([1](https://www.tomshardware.com/how-to/disable-vbs-windows-11), [2](https://support.microsoft.com/en-us/windows/options-to-optimize-gaming-performance-in-windows-11-a255f612-2949-4373-a566-ff6f3f474613)) if required. On the other hand, [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies/) recommend keeping it enabled. VBS should be disabled when virtualization is disabled in BIOS, so be careful of VBS being enabled if you enable virtualization in BIOS for future reference.

<h2 id="cpu-idle-states">11.48. CPU Idle States <a href="#cpu-idle-states">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

Disabling idle states forces C-State 0, which can be seen in [HWiNFO](https://www.hwinfo.com), and is in Microsoft's recommendations for configuring devices for real-time performance ([1](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)). Forcing C-State 0 mitigates the undesirable delay to execute new instructions on a CPU that has entered a deeper power-saving state at the expense of higher temperatures and power consumption. Therefore, I would recommend keeping idle states enabled for the majority of readers as other problems can occur due to these side effects (e.g. throttling, power issues). The CPU temperature should not increase to the point of thermal throttling because you should have already assessed that in section [Stability, Hardware Clocking and Thermal Performance](#stability-hardware-clocking-and-thermal-performance).

If a static CPU frequency is not set, the effects of forcing C-State 0 should be assessed in terms of frequency boosting behavior. For example, you certainly wouldn't want to disable idle states when relying on Precision Boost Overdrive (PBO), Turbo Boost or similar features. Avoid disabling idle states with Hyper-Threading/Simultaneous Multithreading enabled as single-threaded performance is usually negatively impacted.

<h3 id="enable-idle-states-default">11.48.1. Enable Idle States (default) <a href="#enable-idle-states-default">(permalink)</a></h3>

```bat
powercfg /setacvalueindex scheme_current sub_processor 5d76a2ca-e8c0-402f-a133-2158492d58ad 0 && powercfg /setactive scheme_current
```

<h3 id="disable-idle-states">11.48.2. Disable Idle States <a href="#disable-idle-states">(permalink)</a></h3>

```bat
powercfg /setacvalueindex scheme_current sub_processor 5d76a2ca-e8c0-402f-a133-2158492d58ad 1 && powercfg /setactive scheme_current
```

<h2 id="thread-quantums-and-scheduling">11.49. Thread Quantums and Scheduling <a href="#thread-quantums-and-scheduling">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

A quantum is the time designated for which a thread can execute before the scheduler evaluates whether another thread with the same priority is scheduled to execute. If a thread finishes its quantum and no other threads at its priority level are ready to execute, the scheduler allows the thread to continue running for an additional quantum. The quantum can be controlled with the registry key below, in addition to defining how much time of the quantum is allocated to background and foreground threads. The value is represented as a 6-bit bitmask such that each of the three pairs of bits determine the quantum's characteristics and distribution of time between background and foreground threads. By default, it is set to ``0x2`` which corresponds to ``0b000010`` and has different meanings on client and server editions as explained shortly.

```
[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\PriorityControl]
"Win32PrioritySeparation"=dword:00000002
```

<h3 id="bitmask-explaination">11.49.1. Bitmask Explaination <a href="#bitmask-explaination">(permalink)</a></h3>

- The leftmost bit pair (**XX**YYZZ) determine the quantum length. This is represented by ``PspForegroundQuantum``

  |Value|Description|
  |---|---|
  |00/11|Short Intervals (Windows Client), Long Intervals (Windows Server)|
  |01|Long Intervals|
  |10|Short Intervals|

- The middle bit pair (XX**YY**ZZ) determine whether the quantum length is variable or fixed. If a fixed-length quantum is used, then the rightmost bit pair is ignored as the ratio that determines the time allocated to background and foreground threads within the quantum is fixed. This is represented by ``PspForegroundQuantum``

  |Value|Description|
  |---|---|
  |00/11|Variable-length (Windows Client), Fixed-length (Windows Server)|
  |01|Variable-length|
  |10|Fixed-length|

- The rightmost bit pair (XXYY**ZZ**) determine the ratio of time in the quantum allocated to background and foreground threads in which, foreground threads can be allocated up to three times as much processor time than background threads. As mentioned previously, this can only be configured with variable-length quantums. This is represented by ``PsPrioritySeparation``

  |Value|Description|
  |---|---|
  |00|1:1|
  |01|2:1|
  |10/11|3:1|

- Using the information above, the default value of ``0x2`` corresponds to short, variable-length, 3:1 on Windows Client and long, fixed-length, 3:1 on Windows Server

<h3 id="win32priorityseparation-values">11.49.2. Win32PrioritySeparation Values <a href="#win32priorityseparation-values">(permalink)</a></h3>

The table below consists of all possible values that are consistent between client and server editions of Windows as ``00`` or ``11`` were not used in **XXYY**ZZ of the bitmask which have different meanings on client and server editions. Any value not specified in the table is identical to one that is stated in the table as explained [here](/docs/research.md#5-ambiguous-win32priorityseparation-values-explained), hence the values in the table are the only ones that should be used for simplicity.

Although a foreground boost can not be used when using a fixed length interval in terms of the quantum, PsPrioritySeparation still changes, and another thread priority boosting mechanism just happens to use the value of it so in reality, a fixed 3:1 quantum should have a perceivable difference compared to a fixed 1:1 quantum. See the paragraph below from Windows Internals.

> As will be described shortly, whenever a thread in the foreground process completes a wait operation on
a kernel object, the kernel boosts its current (not base) priority by the current value of
PsPrioritySeparation. (The windowing system is responsible for determining which process is
considered to be in the foreground.) As described earlier in this chapter in the section “Controlling the
quantum,” PsPrioritySeparation reflects the quantum-table index used to select quantums for the
threads of foreground applications. However, in this case, it is being used as a priority boost value.

For the majority of readers, I would simply recommend leaving it at default. Although, a mixture of the quantum length and foreground/background time allocation ratio can influence how often a thread switches context depending on whether thread's runtime exceeds its allocated time in the quantum as described previously hence you can benchmark whether it influences performance in your chosen applications if desired. If you are using Windows Server on a desktop system, the value can be set to ``0x26`` which mimics the same behavior as ``0x2`` does on Windows Client editions.

|**Hexadecimal**|**Decimal**|**Binary**|**Interval**|**Length**|**PsPrioSep**|
|---|---|---|---|---|---|
|0x14|20|0b010100|Long|Variable|0|
|0x15|21|0b010101|Long|Variable|1|
|0x16|22|0b010110|Long|Variable|2|
|0x18|24|0b011000|Long|Fixed|0|
|0x19|25|0b011001|Long|Fixed|1|
|0x1A|26|0b011010|Long|Fixed|2|
|0x24|36|0b100100|Short|Variable|0|
|0x25|37|0b100101|Short|Variable|1|
|0x26|38|0b100110|Short|Variable|2|
|0x28|40|0b101000|Short|Fixed|0|
|0x29|41|0b101001|Short|Fixed|1|
|0x2A|42|0b101010|Short|Fixed|2|

<h2 id="clock-interrupt-frequency-timer-resolution">11.50. Clock Interrupt Frequency (Timer Resolution) <a href="#clock-interrupt-frequency-timer-resolution">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

The clock interrupt frequency is the rate at which the system's hardware clock generates interrupts which allow the scheduler to perform various tasks such as timekeeping. On most systems by default, the minimum frequency is 64Hz, meaning that a clock interrupt is generated every 15.625ms. A lower frequency results in reduced CPU overhead and power consumption due to fewer interrupts but reduces timing precision and results in potentially less responsive multitasking. The maximum frequency is 2kHz, meaning that a clock interrupt is generated every 0.5ms. A higher frequency results in higher timing precision, potentially higher multitasking responsiveness but increases CPU overhead and power consumption. The minimum, current and maximum resolutions can be viewed in [ClockRes](https://learn.microsoft.com/en-us/sysinternals/downloads/clockres).

Applications that require higher precision than the default resolution of 15.625ms are able to raise the clock interrupt frequency through functions such as [timeBeginPeriod](https://learn.microsoft.com/en-us/windows/win32/api/timeapi/nf-timeapi-timebeginperiod) and [NtSetTimerResolution](http://undocumented.ntinternals.net/index.html?page=UserMode%2FUndocumented%20Functions%2FTime%2FNtSetTimerResolution.html) in which, these scenarios typically consist of multimedia playback, gaming, VoIP activity and more which can be seen by running an energy trace ([instructions](https://support.microsoft.com/en-gb/topic/guided-help-get-a-detailed-power-efficiency-diagnostics-report-for-your-computer-in-windows-7-3f6ce138-fc04-7648-089a-854bcf332810)) during runtime. The precision of features that rely on sleep-related functions to pace events are directly influenced by the clock interrupt frequency ([1](https://randomascii.wordpress.com/wp-content/uploads/2020/10/image-5.png)). Using [Sleep](https://learn.microsoft.com/en-us/windows/win32/api/synchapi/nf-synchapi-sleep) as an example, ``Sleep(n)`` should sleep for n milliseconds in actuality and not n plus/minus an arbitrary value otherwise, it can result in unexpected and inconsistent event pacing which is not ideal for features such as sleep-based framerate limiters. Note that this is an example and many real-world applications do not rely specifically on the ``Sleep`` function for event pacing. A typical value that developers appears to raise the resolution to is 1ms which means that the application can maintain a pace of events within a resolution of 1ms. In very rare cases, developers may not raise the resolution at all while their application relies on it for event pacing precision leading to breakage, but this is not common and may be applicable to some obscure programs such as lesser-known games.

The implementation of timer resolution changed in Windows 10 2004+ such that the calling process raising the resolution does not affect the system on a global level meaning, process A raising the resolution to 1ms does not affect process B at the default 15.625ms resolution unlike before. This is a great change in and of itself because it reduces overhead as other processes such as idle background processes don't get serviced by the scheduler often and the calling process receives higher precision as needed. However as an end-user, this results in limitations when wanting to leverage higher resolutions such as 0.5ms.  Given that games are not open-source to modify the code along with anticheat limitations preventing DLL injection or binary patching to raise the resolution beyond 1ms the per-process way, the only other option is to resort to the global behavior which is applicable with the registry key below on Windows Server and Windows 11+ as explained in depth [here](/docs/research.md#6-fixing-timing-precision-in-windows-after-the-great-rule-change).

```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\kernel]
"GlobalTimerResolutionRequests"=dword:00000001
```

This provides the ability to raise the resolution in a separate process which in turn, results in the desired application such as a game receiving higher precision. However as mentioned previously, the per-process implantation reduces overhead which is no longer the case when the global behavior is restored and background processes are also serviced unnecessarily often. [RTSS](https://www.guru3d.com/download/rtss-rivatuner-statistics-server-download) is an alternative method for framerate limiting and utilizes hybrid-wait which results in greater precision while eliminating the need for restoring the global behavior.

A higher resolution results in higher precision, but in some cases, the maximum supported resolution of 0.5ms provides less precision than something slightly lower such as 0.507ms ([1](/docs/research.md#7-micro-adjusting-timer-resolution-for-higher-precision)). Therefore, it is sensible to determine what calling resolution provides the highest precision (the lowest deltas) in the [MeasureSleep](https://github.com/valleyofdoom/TimerResolution) program while requesting different resolutions with the [SetTimerResolution](https://github.com/valleyofdoom/TimerResolution) program. This should be carried out under load as idle benchmarks may be misleading. The [micro-adjust-benchmark.ps1](https://github.com/valleyofdoom/TimerResolution) script can be used to automate the process.

To conclude my view on the topic, I recommend favoring the per-process (non-global) implementation where applicable as it reduces overhead and instead use [RTSS](https://www.guru3d.com/download/rtss-rivatuner-statistics-server-download) for precise framerate limiting. It is worth noting that it can introduce noticeably higher latency ([1](https://www.youtube.com/watch?t=377&v=T2ENf9cigSk), [2](https://en.wikipedia.org/wiki/Busy_waiting)) therefore I recommend comparing and benchmarking it against micro-adjusting the requested resolution for higher precision with the global behavior. It is possible that frametime stability is unaffected by raising the resolution beyond 1ms due to improvements in the in-game framerate limiter which in that case, no action is required. The primary point I want to convey is to compare all available options, with a preference of using the per-process behavior which is the default on Windows 10 2004+ if you find that raising the resolution further has little to no impact.

<h2 id="paging-file">11.51. Paging File <a href="#paging-file">(permalink)</a></h2>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instructions](#benchmarking)).

For most readers, I would recommend keeping the paging file enabled which is the default state. There is an argument that it is preferable to disable it if you have enough RAM for your applications as it reduces I/O overhead and that system memory is faster than disk however, many users have reported in-game stuttering in specific games with the paging file disabled despite being nowhere near maximum RAM load. Windows appears to allocate the page file to secondary drives sometimes which can be problematic if one of the drives is a HDD. This can be resolved by allocating the page file to an SSD and its size to "system managed size" then deallocating it on other drives.

<h2 id="cleanup-and-maintenance">11.52. Cleanup and Maintenance <a href="#cleanup-and-maintenance">(permalink)</a></h2>

It isn't a bad idea to revisit this step every so often. Setting a reminder to do so can be helpful in maintaining a clean system.

- Updates

  - Windows Update - if ``disable automatic windows updates`` was set to ``true`` in section [Merging Registry Options](#merging-registry-options), you need to manually check for updates

  - Runtimes - as outlined in section [Runtimes](#runtimes)

  - Microsoft Store Apps - if ``disable automatic store app updates`` was set to ``true`` in section [Merging Registry Options](#merging-registry-options), you need to manually check for updates

- Uninstall unwanted programs with [Bulk-Crap-Uninstaller](https://github.com/Klocman/Bulk-Crap-Uninstaller) and [AppxPackagesManager](https://github.com/valleyofdoom/AppxPackagesManager)

- Use [Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns) to remove any unwanted programs from launching at startup and check it often, especially after installing a program

- Configure Disk Cleanup

  - Open CMD and enter the command below, tick all the boxes except ``DirectX Shader Cache`` then press ``OK``

      ```bat
      cleanmgr /sageset:0
      ```

  - Run Disk Cleanup

      ```bat
      cleanmgr /sagerun:0
      ```

- Some locations you may want to review for residual files

  - ``"C:\ProgramData\Microsoft\Windows\Start Menu\Programs"`` - start menu shortcuts (don't delete windows-related shortcuts)
  - ``C:\Windows\Prefetch`` - prefetch files (this folder should not be populated when superfetch is disabled)
  - ``C:\Windows\SoftwareDistribution`` - Windows Update download cache
  - ``C:\Windows\Temp`` - temporary files
  - ``"%userprofile%"`` - residual junk
  - ``"%userprofile%\AppData\Local\Temp"`` - temporary files
  - ``"%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"`` - start menu shortcuts (don't delete windows-related shortcuts)
  - User directories - e.g. Downloads, Documents, Pictures, Music, Videos, Desktop

- Optionally clean the WinSxS folder to reduce the size of it ([1](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/clean-up-the-winsxs-folder?view=windows-11)) with the command below in CMD. Note that this can be a lengthy process

    ```bat
    DISM /Online /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

- Optionally delete obsolete system restore points in the ``System Protection`` tab by typing ``sysdm.cpl`` in ``Win+R``. It can be disabled completely if you don't use it

- If ``disable automatic maintenance`` was set to ``true`` in section [Merging Registry Options](#merging-registry-options), you need to manually trim your SSDs or defrag your HDDs as this is a task executed during automatic maintenance
