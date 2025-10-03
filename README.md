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
  - [6.6.1 Model-Specific Registers](#model-specific-registers)
  - [6.6.2 Datasheet, MMIO, IO, PCI](#datasheet)
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
  - [6.18. Legacy USB Support](#legacy-usb-support)
  - [6.19. Opciones de instalación del software](#software-installation-options)
  - [6.20. Velocidad del enlace PCI para dispositivos](#pci-link-speed-for-devices)
  - [6.21. Curvas de ventilación](#fan-curves)
  - [6.22. Perfiles y copias de seguridad de BIOS](#bios-profiles-and-backups)
- [7. Configuración de puertos USB](#configure-usb-port-layout)
  - [7.1. Revisión de los puertos USB accesibles](#reviewing-accessible-usb-ports)
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
  - [10.4. Fuentes de ISO's](#iso-sources)
  - [10.5. Preparación de la ISO](#iso-preparation)
  - [10.6. Obtener Archivos Requeridos](#fetching-required-files)
  - [10.7. Iniciar desde la ISO](#booting-into-the-iso)
- [11. Configurar Windows](#configure-windows)
  - [11.1. Configuración OOBE](#oobe-setup)
  - [11.2. Control de Cuentas de Usuario](#user-account-control)
  - [11.3. Política de Ejecución de PowerShell Sin Restricciones](#unrestricted-powershell-execution-policy)
  - [11.4. Importar Carpeta bin](#importing-bin-folder)
  - [11.5. Mitigaciones de Procesos (Windows 10 1709+)](#process-mitigations-windows-10-1709)
  - [11.6. Ajustar opciones en el registro](#merging-registry-options)
    - [11.6.1. Documentación de Opciones del Registro](#registry-options-documentation)
    - [11.6.2. Aplicar ajustes](#applying-options)
  - [11.7. Instalación de Drivers](#installing-drivers)
  - [11.8. Opciones Específicas para Windows Server](#windows-server-specific-options-windows-server)
  - [11.9. Opciones de Privacidad (Windows 8+)](#privacy-options-windows-8)
  - [11.10. Indexación de Búsqueda](#search-indexing)
  - [11.11. Hora, Idioma y Región](#time-language-and-region)
  - [11.12. Navegador Web](#web-browser)
  - [11.13. Scheduled Tasks](#scheduled-tasks)
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
  - [11.25. Drivers Gráficos](#graphics-driver)
  - [11.26. MSI Afterburner](#msi-afterburner)
  - [11.27. Resoluciones de Pantalla y Modos de Escalado](#display-resolutions-and-scaling-modes)
  - [11.28. Open-Shell (Windows 8+)](#open-shell-windows-8)
  - [11.29. Spectre, Meltdown y Microcódigo del CPU](#spectre-meltdown-and-cpu-microcode)
  - [11.30. Opciones de Energía](#power-options)
  - [11.31. Process Explorer](#process-explorer)
  - [11.32. Configuración de la Gestión de Memoria (Windows 8+)](#memory-management-settings-windows-8)
  - [11.33. Opciones del Adaptador de Ethernet](#network-adapter-options)
  - [11.34. Dispositivos de Audio](#audio-devices)
  - [11.35. Administrador de Dispositivos](#device-manager)
  - [11.36. Ahorro de Energía en Dispositivos](#device-power-saving)
  - [11.37. Sesiones de Rastreo de Eventos (ETS)](#event-trace-sessions-ets)
  - [11.38. Sistema de Archivos](#file-system)
  - [11.39. Interrupciones Señaladas por Mensaje (MSI)](#message-signaled-interrupts)
  - [11.40. Multimedia Class Scheduler Service (MMCSS)](#mmcss)
  - [11.41. Moderación de Interrupciones XHCI (IMOD)](#xhci-interrupt-moderation-imod)
  - [11.42. Panel de Control](#control-panel)
  - [11.43. Configuración de Aplicaciones](#configuring-applications)
    - [11.43.1. NVIDIA Reflex](#nvidia-reflex)
    - [11.43.2. Límite de FPS](#framerate-limit)
    - [11.43.3. Registrar Juego en Config Store](#register-game)
    - [11.43.4. Modo de Presentación](#presentation-mode)
    - [11.43.5. Modo de Juego](#game-mode)
    - [11.43.6. Reproductor Multimedia](#media-player)
    - [11.43.7. Políticas QoS](#qos-policies)
  - [11.44. Optimización en Modo Kernel (Interrupciones, DPCs y más)](#kernel-mode-scheduling-interrupts-dpcs-and-more)
    - [11.44.1. GPU y DirectX Graphics Kernel](#gpu-and-directx-graphics-kernel)
    - [11.44.2. Controlador XHCI y de Audio](#xhci-and-audio-controller)
    - [11.44.3. Tarjeta de Red](#network-interface-card)
  - [11.45. Optimización en Modo Usuario (Procesos, Hilos)](#user-mode-scheduling-processes-threads)
    - [11.45.1. Iniciar un Proceso con una Afinidad Específica](#starting-a-process-with-a-specified-affinity-mask)
    - [11.45.2. Especificar Afinidad para Procesos Activos](#specifying-an-affinity-mask-for-running-processes)
  - [11.46. CPUs Reservados (Windows 10+)](#reserved-cpu-sets-windows-10)
    - [11.46.1. Casos de Uso](#use-cases)
  - [11.47. Analizar el Visor de Eventos](#analyzing-event-viewer)
  - [11.48. Seguridad Basada en Virtualización (VBS)](#virtualization-based-security-vbs)
  - [11.49. Estados de Inactividad del CPU](#cpu-idle-states)
    - [11.49.1. Activar Estados de Inactividad (por defecto)](#enable-idle-states-default)
    - [11.49.2. Desactivar Estados de Inactividad](#disable-idle-states)
  - [11.50. Quantums de Hilo y Planificación](#thread-quantums-and-scheduling)
    - [11.50.1. Explicación de Bitmask](#bitmask-explaination)
    - [11.50.2. Valores de Win32PrioritySeparation](#win32priorityseparation-values)
  - [11.51. Frecuencia de Interrupción del Reloj (Resolución del Temporizador)](#clock-interrupt-frequency-timer-resolution)
  - [11.52. Archivo de Paginación](#paging-file)
  - [11.53. Limpieza y Mantenimiento](#cleanup-and-maintenance)

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
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

- Si planeas hacer overclock, ten en cuenta los siguientes puntos para maximizar el margen térmico y el potencial de overclock. Es importante destacar que mantener temperaturas más bajas puede influir positivamente en otros factores incluso si no realizas overclock, como el comportamiento de boost del CPU, ya que dicho algoritmo es sensible a la temperatura, entre otros aspectos.
- **AiO (Refrigeracion Liquida)**
- 💧 Un "AiO"/Refrigeración Líquida es un sistema líquido de enfriamiento, el cual incluye una bomba, un radiador, y tubos pre llenados con refrigerante. Está diseñado para remover el calor de nuestra CPU y disipar el mismo, para luego pasarlo por el radiador.
- Una Refrigeración Líquida se debe colocar adecuadamente para que tenga un funcionamiento eficiente. A continuación podrá usted ver el siguiente esquema, acerca de las formas adecuadas de colocar un enfriamiento líquido.([2](https://imgur.com/a/Ec6UNDT))
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
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

En plataformas y procesadores mucho más antiguos, los parches a nivel de BIOS contra Spectre, Meltdown y otras vulnerabilidades similares podían tener un impacto considerable en el rendimiento. Sin embargo, en sistemas modernos esto ya no suele ser un factor tan determinante. La función de validación de [CPU-Z's](https://www.cpuid.com/softwares/cpu-z.html) permite visualizar la versión del microcódigo actual, y en el pasado era posible modificarlo utilizando herramientas como [MMTool](https://www.ami.com/blog/2017/10/30/what-is-mmtool). Aun así, en plataformas actuales este tipo de modificación rara vez es necesaria, y se menciona aquí únicamente con fines informativos.

<h2 id="accessing-hidden-options">6.6. Acceder a opciones ocultas <a href="#accessing-hidden-options">(permalink)</a></h2>

Los fabricantes de placas base suelen ocultar muchas configuraciones para que no estén visibles al usuario estándar. En este contexto, "desbloquear la BIOS" implica hacer visibles y accesibles estas configuraciones ocultas. La forma más sencilla de hacerlo es modificando los niveles de acceso dentro del firmware con [UEFI-Editor](https://github.com/BoringBoredom/UEFI-Editor#usage-guide) y luego flashearlo, lo cual permitirá que dichas opciones se muestren directamente en el menú UEFI. Otra opción consiste en modificar lo que ya está disponible y luego acceder a las opciones ocultas leyendo y escribiendo en la NVRAM mediante [GRUB](https://github.com/BoringBoredom/UEFI-Editor#how-to-change-hidden-settings-without-flashing-a-modded-bios) ([script generator](https://github.com/ab3lkaizen/setupvar-builder)) o [SCEWIN](https://github.com/ab3lkaizen/SCEHUB) con [SCEWIN-GUI](https://github.com/eskezje/SCEWIN-GUI).

<h2 id="model-specific-registers">6.6.1. Model-Specific Registers (MSR) <a href="#model-specific-registers">(permalink)</a></h2>

Un Model-Specific Register [MSR](https://en.wikipedia.org/wiki/Model-specific_register) es un registro especial y particular del diseño de cada procesador (x86) que no forma parte de los registros generales de propósito común. Estos registros permiten funciones de control avanzadas del CPU, como monitoreo de rendimiento, activación o desactivación de características específicas, trazas de ejecución o ajustes internos del procesador.

Su acceso se hace mediante instrucciones privilegiadas (RDMSR para leer y WRMSR para escribir), lo cual significa que solo el sistema operativo (o código con los permisos adecuados) puede manipularlos.

<h2 id="datasheet">6.6.2. Datasheet, MMIO, IO, PCI. <a href="#datasheet">(permalink)</a></h2>

El [Datasheet](https://en.wikipedia.org/wiki/Datasheet) de un procesador o chipset describe en detalle la disposición de registros accesibles mediante distintos mecanismos como MMIO (Memory-Mapped I/O), espacio PCI o puertos de E/S (I/O ports). Estos registros contienen campos y bits que controlan aspectos fundamentales del hardware, como la administración de energía, la latencia de buses, la gestión de interrupciones o el comportamiento de controladores integrados. Al modificar de forma precisa estos bits, es posible ajustar parámetros de bajo nivel que influyen directamente en el rendimiento y la respuesta del sistema.

El acceso a estos registros se realiza a través de herramientas o instrucciones específicas que permiten leer y escribir en direcciones determinadas, siguiendo siempre la documentación oficial del datasheet. Esto garantiza que los cambios aplicados no sean arbitrarios, sino informados y consistentes con la arquitectura del dispositivo. Un uso cuidadoso de esta información permite optimizar el hardware para escenarios concretos —como reducir latencia, mejorar la eficiencia de comunicación en buses o desactivar funciones innecesarias—, manteniendo un balance entre rendimiento y estabilidad.

<h2 id="unnecessary-devices">6.7. Dispositivos innecesarios <a href="#unnecessary-devices">(permalink)</a></h2>

Como regla general, aplica el principio de "si no lo usas, desactívalo". Si es posible, es mejor desconectar físicamente los componentes no utilizados, aunque también es válido deshabilitarlos desde la BIOS. Esto incluye, entre otros: adaptadores de red (NICs), Wi-Fi, Bluetooth, controladores de audio de alta definición (si no se usa el audio de la placa), gráficos integrados, puertos SATA, ranuras de RAM, y dispositivos integrados visibles en [USB Device Tree Viewer](https://www.uwe-sieber.de/usbtreeview_e.html) (como controladores RGB, receptores IR, etc.). Ten en cuenta que en algunas placas base el controlador de audio de alta definición puede estar vinculado al controlador USB (referencia), por lo que puede aparecer en dicho árbol como un dispositivo USB. ([1](https://www.igorslab.de/en/the-old-alc4080-on-the-new-intel-boards-demystified-and-the-differences-from-alc1220-insider)). Así que no te confundas si se encuentra en el árbol de dispositivos USB.

<h2 id="resizable-bar">6.8. Resizable Bar (ReBAR) <a href="#resizable-bar">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Consulta [este artículo](https://www.howtogeek.com/819578/what-is-resizable-bar-on-a-gpu) para obtener una visión general de qué es Resizable BAR (ReBAR). Es importante destacar que ReBAR puede provocar una pérdida de rendimiento en ciertos juegos ([1](https://www.techspot.com/review/2234-nvidia-resizable-bar)) por lo tanto, es recomendable hacer tus propias pruebas para decidir si mantenerlo habilitado.

ReBAR requiere que el sistema esté en modo BIOS UEFI con particiones GPT, además de tener activada la opción `Above 4G Decoding`  Si tu placa base no lo soporta de forma nativa, puedes considerar usar herramientas como [ReBarUEFI](https://github.com/xCuri0/ReBarUEFI)/[NvStrapsReBar](https://github.com/terminatorul/NvStrapsReBar). Para verificar si Resizable BAR está habilitado, consulta el estado desde [GPU-Z](https://www.techpowerup.com/gpuz).

<h2 id="hyper-threadingsimultaneous-multithreading">6.9. Hyper-Threading/Simultaneous Multithreading <a href="#hyper-threadingsimultaneous-multithreading">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Si tu aplicación no depende intensamente del uso de múltiples hilos por núcleo, considera desactivar [Hyper-Threading (HT)/Simultaneous Multithreading (SMT)](https://en.wikipedia.org/wiki/Hyper-threading). Esta función resulta útil en tareas altamente paralelizables como la codificación, compilación y renderizado; sin embargo, el uso de múltiples hilos por núcleo puede aumentar la contención de recursos internos del procesador y es una posible fuente de latencia e inestabilidad del sistema ([1](https://www.intel.com/content/www/us/en/developer/articles/technical/optimizing-computer-applications-for-latency-part-1-configuring-the-hardware.html)). Además, desactivar HT/SMT puede mejorar el potencial de overclocking debido a una menor generación de calor, lo cual puede traducirse en mejoras o pérdidas de rendimiento dependiendo del juego o la aplicación. Por tanto, se recomienda realizar pruebas comparativas antes de desactivarlo.

<h2 id="power-states">6.10. Estados de Energía <a href="#power-states">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Por completar.

<h2 id="virtualizationsvm-mode">6.11. Virtualización/Modo SVM <a href="#virtualizationsvm-mode">(permalink)</a></h2>

Desactiva [Virtualization/SVM Mode](https://en.wikipedia.org/wiki/Desktop_virtualization) y [Intel VT-d/AMD-Vi](https://en.wikipedia.org/wiki/X86_virtualization#I/O_MMU_virtualization_(AMD-Vi_and_Intel_VT-d)) si no utilizas máquinas virtuales, ya que estas tecnologías pueden introducir latencias adicionales en el acceso a la memoria ([1](https://web.archive.org/web/20190403122634/https://www.amd.com/system/files/TechDocs/56263-EPYC-performance-tuning-app-note.pdf)). También pueden provocar fluctuaciones en la frecuencia base del sistema (BCLK) ([1](https://linustechtips.com/topic/1479168-issue-enabling-svm-virtualization-causes-bclk-to-fluctuate-a-lot)). Puedes verificar si la virtualización está habilitada en el Administrador de Tareas, en la pestaña "Rendimiento" > CPU.

<h2 id="power-saving">6.12. Ahorros de Energía <a href="#power-saving">(permalink)</a></h2>

Las funciones de ahorro de energía no tienen cabida en sistemas que ejecutan tareas en tiempo real. Estas características pueden denominarse de diversas formas, incluyendo [ASPM (Active State Power Management)](https://en.wikipedia.org/wiki/Active_State_Power_Management) (por ejemplo, buscar *L0*, *L1*), [ALPM (Aggressive Link Power Management)](https://en.wikipedia.org/wiki/Aggressive_Link_Power_Management), Power/Clock Gating, entre otras. También pueden aparecer como "power saving". Si tienes dudas sobre una configuración específica, busca su descripción en internet para verificar si pertenece a esta categoría.

<h2 id="trusted-platform-module-tpm">6.13. Módulo de Plataforma Segura (TPM) <a href="#trusted-platform-module-tpm">(permalink)</a></h2>

> [!WARNING]
> 🔒 Desactivar el TPM (Trusted Platform Module) puede comprometer la seguridad del sistema. Evalúa cuidadosamente los riesgos antes de modificar esta opción.

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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

<h2 id="pci-link-speed-for-devices">6.20. Velocidad del enlace pci <a href="#pci-link-speed-for-devices">(permalink)</a></h2>

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
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

En cuanto a qué controladores USB usar, eso queda a tu criterio. Si tienes más de un controlador USB, puedes aislar dispositivos como el ratón, teclado y dispositivos de audio en otro controlador USB, ya que tienen el potencial de interferir con la consistencia del polling ([1](https://forums.blurbusters.com/viewtopic.php?f=10&t=7618#p58449)). Se pueden obtener más controladores USB utilizando tarjetas de expansión PCIe o conectores USB 2.0 y 3.0 externos en la placa base. Siempre verifica esta información con [USB Device Tree Viewer](https://www.uwe-sieber.de/usbtreeview_e.html). Los sistemas Ryzen disponen de un controlador USB conectado directamente al CPU ([1](https://hexus.net/tech/features/mainboard/131789-amd-ryzen-3000-supporting-x570-chipset-examined)) el cual puede identificarse en la categoría PCIe Bus en [HWiNFO](https://www.hwinfo.com). Suele ser el controlador USB conectado a un ``Internal PCIe Bridge to bus`` el cual también está etiquetado con la arquitectura del CPU ([1](/assets/images/ryzen-cpu-usb-controller.png)).

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
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Un DPI más alto en el sensor reduce la latencia y ayuda a saturar los sondeos con datos de movimiento ([1](https://www.youtube.com/watch?v=6AoRfv9W110), [2](https://www.youtube.com/watch?v=mwf_F2VboFQ&t=458s), [3](https://www.youtube.com/watch?v=imYBTj2RXFs&t=275s)). Evita la reducción de jitter (por ejemplo, reducción de DPI) y el [sensor smoothing](https://old.reddit.com/r/MouseReview/comments/5haxn4/sensor_smoothing) que puede activarse con valores de DPI más altos.  Si tu juego utiliza entrada sin procesar (raw input) puedes reducir la velocidad del puntero en Windows para compensar la sensibilidad de un DPI más alto [calculadora](https://boringboredom.github.io/tools/winsenscalculator) De lo contrario, deja el control deslizante en su posición predeterminada, ya que el escalado puede afectar negativamente la entrada. Una forma de saber si una aplicación usa entrada sin procesar es espiar las llamadas a la API raw input con [API Monitor](http://www.rohitab.com/apimonitor) o verificar si la opción de “mejorar la precisión del puntero” tiene algún efecto en el juego. Si aún tienes dudas, deja el control deslizante en la posición predeterminada.

<h2 id="report-rate">8.5. Tasa de Sondeo <a href="#report-rate">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Cuando hagas overclock a la GPU, puede que necesites flashear un BIOS con mayor límite de potencia o elevar manualmente dichos límites.

- En sistemas NVIDIA, asegúrate de desactivar ``CUDA - Force P2 State`` con [NVIDIA Profile Inspector](https://github.com/Orbmu2k/nvidiaProfileInspector) para evitar que la memoria baje de frecuencia durante pruebas de estrés ([1](/assets/images/cuda-force-p2-state-analysis.png))
- Ver: [A Slightly Better Way To Overclock and Tweak Your Nvidia GPU | Cancerogeno](https://docs.google.com/document/d/14ma-_Os3rNzio85yBemD-YSpF_1z75mZJz1UdzmW8GE/edit)
- Ver: [LunarPSD/NvidiaOverclocking](https://github.com/LunarPSD/NvidiaOverclocking/blob/main/Nvidia%20Overclocking.md)

<h2 id="ramcpu">9.7. RAM/CPU <a href="#ramcpu">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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
    |NVIDIA 50 series|Win10 1809+|
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

- Windows 11+ tiene un scheduler actualizado para CPUs Intel de 12ª generación en adelante ([1](https://www.anandtech.com/show/16959/intel-innovation-alder-lake-november-4th/3)), pero el comportamiento se puede replicar manualmente con políticas de afinidad en cualquier versión de Windows como se explica en secciones posteriores.

- Windows 11+ limita el polling rate de los procesos en segundo plano ([1](https://blogs.windows.com/windowsdeveloper/2023/05/26/delivering-delightful-performance-for-more-than-one-billion-users-worldwide))

- Windows 11 es un requisito mínimo para [Cross Adapter Scan-Out](https://videocardz.com/newz/microsoft-cross-adapter-scan-out-caso-delivers-16-fps-increse-on-laptops-without-dgpu-igpu-mux-switch) ([1](https://devblogs.microsoft.com/directx/optimizing-hybrid-laptop-performance-with-cross-adapter-scan-out-caso))

- Se puede establecer ``AllowTelemetry`` en 0 en ediciones de Windows Server ([1](https://admx.help/?Category=Windows_10_2016&Policy=Microsoft.Policies.DataCollection::AllowTelemetry))

- A partir de Windows 10 2004, el kit de controladores de Windows incluye un módulo de extensión de clase de adaptador de red ([NetAdapterCx](https://learn.microsoft.com/en-us/windows-hardware/drivers/netcx/)), A partir de Windows 11 24h2+, UMDF NetAdapterCx permite a los controladores de adaptadores de red ejecutarse en modo usuario.
 - Se trata de una sustitución de NDIS (Internet Adapter Driver) por un controlador compatible con NetAdapter Class Extension, que tiene algunas ventajas sobre el antiguo.

También se han introducido los siguientes cambios en 24h2:
- Actualización de WDDM a la versión 3.2 ([1](https://learn.microsoft.com/en-us/windows-hardware/drivers/what-s-new-in-driver-development#display-and-graphics-drivers)).
- Se ha eliminado la conexión con el CPD del controlador de la GPU del flujo de entrada (función GetRawInputData), lo que tiene un efecto positivo en los resultados finales.
- Utiliza dos flujos de entrada en DWM en lugar de tres (23h2).

<h2 id="downloading-and-preparing-a-stock-windows-iso">10.3. Descargar y Preparar una ISO de Windows Oficial <a href="#downloading-and-preparing-a-stock-windows-iso">(permalink)</a></h2>

Para instalar Windows, es necesario crear un medio de instalación utilizando un archivo ISO. Una vez descargadas las ISOs, asegúrate de verificar sus hashes con las fuentes oficiales para comprobar que son auténticas y no están corruptas. Usa el comando ``certutil -hashfile <archivo>`` en el CMD para obtener los hashes del archivo.

Asegúrate de descargar una ISO que contenga una edición con soporte para directivas de grupo, ya que varias de estas directivas se configurarán en pasos posteriores. A veces, puedes obtener ISOs con ediciones específicas ausentes, así que ten cuidado. A continuación se muestra una lista de ediciones recomendadas:

- Ediciones cliente: Professional
- Ediciones servidor: Standard (Desktop Experience)

<h2 id="iso-sources">10.4. Links de las ISO's <a href="#iso-sources">(permalink)</a></h2>

- [os.click](https://os.click)
- [New Download Links](https://docs.google.com/spreadsheets/d/1zTF5uRJKfZ3ziLxAZHh47kF85ja34_OFB5C5bVSPumk)
- [Adguard File List](https://files.rg-adguard.net)
- [Microsoft Software Download Listing](https://massgrave.dev/msdl)
- [Fido](https://github.com/pbatard/Fido)
- [UUP dump](https://uupdump.net)

<h2 id="iso-preparation">10.5. Preparacion de la ISO <a href="#iso-preparation">(permalink)</a></h2>

<details>
<summary>Windows 7</summary>

Si estás configurando Windows 7, recomiendo usar la ISO ``en_windows_7_professional_with_sp1_x64_dvd_u_676939.iso`` ISO ([Adguard hashes](https://files.rg-adguard.net/file/11ad6502-c2aa-261c-8c3f-c81477b21dd2?lang=en-us)). Además, no podrás iniciar la ISO en hardware moderno sin integrar los drivers y actualizaciones necesarios, lo cual se puede lograr utilizando herramientas como [NTLite](https://www.ntlite.com) ([instrucciones](https://winraid.level1techs.com/t/guide-integration-of-drivers-into-a-win7-11-image/30793)) o DISM en línea de comandos ([instrucciones](/docs/image-customization.md)). Sin embargo, NTLite es más fácil de usar. Normalmente, solo se requiere integrar drivers de [NVMe](https://winraid.level1techs.com/t/recommended-ahci-raid-and-nvme-drivers/28310) y [USB](https://winraid.level1techs.com/t/usb-3-0-3-1-drivers-original-and-modded/30871) para poder iniciar el sistema desde la ISO. Asegúrate de integrar también los drivers en Windows Setup, de lo contrario podrías tener problemas para detectar almacenamiento o usar dispositivos USB, a menos que planees instalar la ISO con DISM como se describe en la sección [Iniciando desde la ISO](#booting-into-the-iso)  ya que este método omite por completo el instalador tradicional de Windows y el archivo ``boot.wim``. Para encontrar drivers compatibles con tu dispositivo, busca aquellos que soporten el HWID de tu dispositivo ([1](/assets/images/device-hwid-example.png)). Si no puedes encontrar un driver USB para tu HWID, intenta integrar el [generic USB driver](https://forums.mydigitallife.net/threads/usb-3-xhci-driver-stack-for-windows-7.81934) y la actualización ``KB2864202``. A continuación, se presenta una tabla de actualizaciones recomendadas para integrar a la ISO.

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

No se requieren pasos adicionales para las versiones de Windows 10 en adelante. Puedes integrar las actualizaciones más recientes, pero esto no es necesario si planeas mantener Windows Update habilitado después de iniciar desde la ISO. Además, las ISOs creadas usando UUP Dump ya incluyen las actualizaciones más recientes, siempre que construyas la última versión. Esto puede hacerse con [NTLite](https://www.ntlite.com) ([instrucciones](https://winraid.level1techs.com/t/guide-integration-of-drivers-into-a-win7-11-image/30793)) o DISM en línea de comandos ([instrucciones](/docs/image-customization.md))), aunque NTLite es más fácil de usar.
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

<h2 id="importing-bin-folder">11.4. Importar Carpeta Bin <a href="#importing-bin-folder">(permalink)</a></h2>

Mueve la carpeta ``bin`` que descargaste antes de instalar Windows a la unidad ``C:`` , tal como se detalla en la sección [Obtener los archivos requeridos](#fetching-required-files). Si no la has descargado aún, deberás obtenerla desde otro sistema ya que todavía no tienes acceso a la red. La ruta completa debe ser ``C:\bin``.

<h2 id="process-mitigations-windows-10-1709">11.5. Mitigaciones de Procesos (Windows 10 1709+) <a href="#process-mitigations-windows-10-1709">(permalink)</a></h2>

> [!ADVERTENCIA]
> 🔒 Desactivar las mitigaciones de procesos puede impactar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con esta modificación.

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Existen varias mitigaciones a nivel del sistema operativo ([1](https://learn.microsoft.com/en-us/powershell/module/processmitigations/set-processmitigation?view=windowsserver2019-ps#-disable)) que están habilitadas por defecto y que pueden impactar el rendimiento. Si se desea, estas pueden deshabilitarse desde la página de "Protección contra vulnerabilidades" de Windows Defender. Debe quedar claro que deshabilitar mitigaciones reduce la seguridad. Este paso se realiza ahora ya que, si decides desactivar Windows Defender en los siguientes pasos, la interfaz ya no estará accesible; sin embargo, pueden ser activadas o desactivadas mediante los comandos [Get-ProcessMitigation](https://learn.microsoft.com/en-us/powershell/module/processmitigations/get-processmitigation?view=windowsserver2022-ps) y [Set-ProcessMitigation](https://learn.microsoft.com/en-us/powershell/module/processmitigations/set-processmitigation?view=windowsserver2019-ps) en PowerShell. Algunos programas pueden requerir que las mitigaciones estén habilitadas y fallarán si se deshabilitan, por lo tanto, procede con precaución.

<h2 id="merging-registry-options">11.6. Ajustar opciones en el registro <a href="#merging-registry-options">(permalink)</a></h2>

> [!ADVERTENCIA]
> 🔒 Algunos cambios descritos en la siguiente tabla pueden afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos asociados antes de modificar una configuración específica.

Los ajustes del registro se aplican mediante el script ``apply-registry.ps1``. En cuanto a qué opciones se aplican, estas se detallan en la tabla a continuación, la cual puede personalizarse editando el archivo ``C:\bin\registry-options.json`` con un editor de texto y configurando las propiedades como ``true`` o ``false``. Puedes respaldar este archivo para no tener que modificarlo tras cada reinstalación de Windows.

<h3 id="registry-options-documentation">11.6.1. Documentación de los cambios en el Registro <a href="#registry-options-documentation">(permalink)</a></h3>

> [!IMPORTANTE]
> Actualmente, el script no revierte opciones si se ejecuta nuevamente. Por ejemplo, si el script fue ejecutado con una opción en ``true``, luego ejecutarlo con dicha opción en  ``false``  no revertirá los cambios ya realizados, ya que el script no lleva registro del estado anterior de las claves del registro asociadas a la opción. Esta funcionalidad puede añadirse en el futuro, pero por ahora, usa el argumento ``-get_option_keys <option>`` con el script para obtener todas las claves relacionadas y revertirlas manualmente si es necesario.

|Opción|Motivo|Notas|Valor por defecto|
|---|---|---|---|
|``disable windows update``|1. 1. Reducir la carga del CPU<br><br>2. Obtener un control más preciso sobre la característica en cuestió|🔒 Un valor de ``true`` puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con modificar esta configuración<br><br>Deshabilitar Windows Update está incluido en las recomendaciones de Microsoft para configurar dispositivos para rendimiento en tiempo real ([1](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)). Alternativamente, se pueden deshabilitar solo las actualizaciones automáticas en lugar de deshabilitar completamente Windows Update, logrando el mismo efecto en cuanto a reducción de carga de CPU, pero aún siendo posible actualizar Windows configurando ``disable windows update`` en ``false`` y ``disable automatic windows updates`` en ``true``. Se sabe que los procesos de Windows Update utilizan muchos recursos de CPU y memoria. Deshabilitar Windows Update rompe la Microsoft Store, sin embargo, puedes descargar e instalar paquetes Appx directamente ([instrucciones](https://superuser.com/questions/1721755/is-there-a-way-to-install-microsoft-store-exclusive-apps-without-store))|``false``|
|``disable automatic windows updates``|1. Reducir la carga del CPU<br><br>2. Obtener un control más preciso sobre la característica en cuestión|🔒 Un valor de ``true`` puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con modificar esta configuración<br><br>Evita la descarga e instalación automática de actualizaciones de Windows en lugar de deshabilitar completamente Windows Update y permite verificar actualizaciones manualmente de vez en cuando. Las actualizaciones pueden ocurrir en momentos inoportunos, lo que lleva a un uso excesivo de CPU y memoria en intervalos aleatorios, además de interrumpir apagados en ciertos casos. Esta opción es sobrescrita si ``disable windows update`` está configurado como ``true``. <br><br>Esta opción no afecta a las actualizaciones mayores (upgrades), que pueden ser controladas usando directivas de grupo ([instrucciones](https://www.tenforums.com/tutorials/159624-how-specify-target-feature-update-version-windows-10-a.html)). Sin embargo, estás limitado a evitar actualizaciones hasta que la versión especificada alcance su fin de soporte|``true``|
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

<h3 id="applying-options">11.6.2. Aplicar ajustes <a href="#applying-options">(permalink)</a></h3>

- Abre PowerShell como administrador e introduce el siguiente comando. Si el comando falla, intenta desactivar la protección contra manipulaciones (Tamper Protection) (Windows 10 1909+) y la protección en tiempo real en Windows Defender. Si eso no funciona, reinicia y vuelve a ejecutar el comando. Si nada de lo anterior funciona, intenta ejecutar el comando en modo seguro. Si prefieres no ejecutar ningún script, existe la opción de crear manualmente un archivo de registro con las claves que necesites, tal como se explica en [/docs/registry-opts.md](/docs/registry-opts.md). Este documento contiene todas las claves que se fusionarían al usar el script.

    ```powershell
    C:\bin\apply-registry.ps1
    ```

- Asegúrate de que el script imprima un mensaje de “aplicado correctamente” en la consola; si no lo hace, significa que las claves del registro no se fusionaron con éxito.

- Después, y solo después de reiniciar, puedes establecer una conexión a internet, ya que las políticas de Windows Update surtirán efecto. Esta es la principal razón por la que no se recomienda conectar a internet antes de este punto.
  
> [!NOTE]
> A los mantenedores y colaboradores: las funciones y opciones deben ser probadas tal como se listan en la tabla anterior. Es inevitable que se requieran más pasos para lograr el mismo objetivo a medida que el sistema operativo reciba actualizaciones o mejoras (por ejemplo, mantener manualmente una lista de servicios relacionados con la desactivación de Windows Defender).).

<h2 id="installing-drivers">11.7. Instalación de Drivers <a href="#installing-drivers">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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

<h2 id="privacy-options-windows-8">11.9. Opciones de Privacidad (Windows 8+) <a href="#privacy-options-windows-8">(permalink)</a></h2>

Desactiva todos los permisos innecesarios en la sección ``Privacy`` presionando ``Win+I``.

<h2 id="search-indexing">11.10. Indexación de Búsqueda <a href="#search-indexing">(permalink)</a></h2>

Ciertos directorios del sistema de archivos se indexan para las funciones de búsqueda de Windows, los cuales pueden visualizarse escribiendo ``control srchadmin.dll`` en ``Win+R``.  La indexación ocurre periódicamente en segundo plano y suele generar una sobrecarga notable en la CPU, lo cual puede verse con Process Explorer como se describe en la sección [Process Explorer](#process-explorer). Por lo tanto, es preferible deshabilitar la indexación de búsqueda globalmente desactivando el servicio ``Windows Search`` Abre CMD como administrador e introduce el siguiente comando:

  ```bat
  reg add "HKLM\SYSTEM\CurrentControlSet\Services\WSearch" /v "Start" /t REG_DWORD /d "4" /f
  ```

> [!IMPORTANT]
> Para evitar errores inesperados y problemas debidos a dependencias de servicios, evalúa los otros servicios que dependen del servicio que deseas deshabilitar. Esto puede hacerse abriendo CMD como administrador y escribiendo ``sc EnumDepend <service>`` , lo cual describe los servicios que dependen del servicio que deseas deshabilitar. Estos servicios también deben ser deshabilitados para evitar errores de dependencia. Si no puedes deshabilitarlos (por ejemplo, porque los necesitas), entonces no tienes más opción que dejar habilitado el servicio que querías deshabilitar inicialmente.

<h2 id="time-language-and-region">11.11. Hora, Idioma y Región <a href="#time-language-and-region">(permalink)</a></h2>

- Configura las opciones escribiendo ``intl.cpl`` y ``timedate.cpl`` en ``Win+R``

- Solo Windows 10 en adelante:

  - Configura las opciones en ``Time & Language`` presionando ``Win+I``

    - Se recomienda mantener los ajustes en inglés, ya que muchos parámetros se conservan en su idioma original dentro de la guía para garantizar compatibilidad universal.
  
    - Si planeas usar exclusivamente un solo idioma y una sola distribución de teclado, asegúrate de que así sea para que no tengas que alternar la barra de idiomas con atajos que pueden activarse accidentalmente.

- Asegúrate de que la hora del sistema esté sincronizada y sea correcta.

<h2 id="web-browser">11.12. Navegador Web <a href="#web-browser">(permalink)</a></h2>

Configura el navegador de tu preferencia.

- Ver: [privacytests.org](https://privacytests.org)

- Ver: [Desktop Browsers | Privacy Guides](https://www.privacyguides.org/en/desktop-browsers)

<h2 id="scheduled-tasks">11.13. Scheduled Tasks <a href="#scheduled-tasks">(permalink)</a></h2>

Windows incluye varias tareas programadas que pueden evaluarse utilizando [TaskSchedulerView](https://www.nirsoft.net/utils/task_scheduler_view.html). Evaluarlas ayuda a tener un control más fino sobre qué se ejecuta silenciosamente en el sistema, ya sea relacionado con actualizaciones, telemetría, Defender y más. Considera las columnas ``Last Run``, ``Next Run`` y ``Triggers`` para evaluar si vale la pena deshabilitar la tarea en cuestión.

<h2 id="activate-windows">11.14. Activar Windows <a href="#activate-windows">(permalink)</a></h2>

Utiliza los comandos siguientes para activar Windows usando tu clave de licencia si no tienes una vinculada al HWID. Asegúrate de que la activación fue exitosa verificando el estado de activación en las propiedades del sistema. Abre CMD como administrador y escribe los comandos correspondientes.

 
```bat
slmgr /ipk <license key>
```

```bat
slmgr /ato
```

<h2 id="declutter-interface">11.15. Limpieza de la Interfaz <a href="#declutter-interface">(permalink)</a></h2>

Desactiva las funciones en la barra de tareas y desancla accesos directos y tiles del menú de inicio y barra de tareas. Esto es cuestión de preferencia personal.

<h2 id="visual-effects">11.16. Efectos Visuales <a href="#visual-effects">(permalink)</a></h2>

Las opciones de efectos visuales pueden accederse escribiendo ``sysdm.cpl`` en ``Win+R``.  Este menú permite deshabilitar animaciones de interfaz, lo cual contribuye a una mayor sensación de respuesta en la interacción con Windows. En Windows 7 se podía deshabilitar la composición del escritorio directamente aquí, pero ya no está disponible en Windows 8+. El resto de las opciones son personales.

<h2 id="superfetch-and-prefetch">11.17. Superfetch y Prefetch <a href="#superfetch-and-prefetch">(permalink)</a></h2>

Si no hay un disco duro mecánico (HDD) en el sistema, entonces se pueden deshabilitar Superfetch y Prefetch con el siguiente comando en CMD. Deshabilitar SysMain es parte de las recomendaciones de Microsoft para configurar dispositivos con rendimiento en tiempo real ([1](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)) ), la carpeta ``C:\Windows\Prefetch`` ya no debería llenarse de archivos.

  ```bat
  reg add "HKLM\SYSTEM\CurrentControlSet\Services\SysMain" /v "Start" /t REG_DWORD /d "4" /f
  ```

> [!IMPORTANT]
> Para evitar errores inesperados debidos a dependencias de servicios, evalúa qué servicios dependen de aquel que deseas deshabilitar. Esto puede hacerse escribiendo ``sc EnumDepend <service>`` en CMD como administrador. Si no puedes deshabilitarlos (porque los necesitas), entonces deberás dejar habilitado el servicio original.

<h2 id="operating-system-and-partition-name">11.18. Nombre del Sistema Operativo y de la Partición <a href="#operating-system-and-partition-name">(permalink)</a></h2>

Configura el nombre del sistema operativo y de la partición de la unidad. Se recomienda establecer un nombre significativo o único como ``W10 22H2`` Trabajo o ``W10 22H2`` Juegos para mayor claridad al usar arranque dual o múltiples discos. Abre CMD como administrador e introduce los comandos necesarios.

  ```bat
  bcdedit /set {current} description "OS_NAME" 
  ```

  ```bat
  label C: OS_NAME
  ```

<h2 id="show-tray-icons">11.19. Mostrar Iconos en la Bandeja <a href="#show-tray-icons">(permalink)</a></h2>

Recomiendo habilitar la opción ``Always show all icons in the notification area`` para una mejor gestión de procesos. Ocultar iconos en la bandeja puede considerarse parcialmente un riesgo de seguridad, ya que podrías no notar programas maliciosos o no deseados ejecutándose en segundo plano.

<h2 id="hibernation">11.20. Hibernación <a href="#hibernation">(permalink)</a></h2>

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

<h2 id="handling-bloatware">11.22. Eliminación de Bloatware <a href="#handling-bloatware">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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

<h2 id="optional-features">11.23. Características Opcionales <a href="#optional-features">(permalink)</a></h2>

Las funciones opcionales se pueden acceder escribiendo ``OptionalFeatures`` en ``Win+R``. Habilita o desactiva funciones que necesites o no necesites. Si Windows Update está deshabilitado, probablemente no podrás instalar funciones desde esta ventana y, en su lugar, deberás instalar un paquete sin conexión usando DISM. En Windows Server, esto se puede acceder mediante el panel de Server Manager navegando a ``Manage -> Remove Roles and Features``.

<h3 id="net-35">11.23.1. NET 3.5 <a href="#net-35">(permalink)</a></h3>

Algunas aplicaciones aún utilizan el runtime de .NET 3.5, por lo que se recomienda instalarlo por si acaso. Como se mencionó anteriormente, no podrás instalarlo desde la ventana de Funciones Opcionales si Windows Update está desactivado, pero sí puedes hacerlo usando un paquete sin conexión.

Para usar el paquete sin conexión, descarga y extrae una ISO de Windows (por ejemplo en ``C:\EXTRACTED_ISO``) y abre CMD como administrador. Sustituye ``C:\EXTRACTED_ISO\sources\sxs`` por la ruta correcta a la carpeta ``\sources\sxs`` en la ISO que extrajiste y ejecuta el siguiente comando:

```bat
DISM /Online /Enable-Feature /FeatureName:NetFx3 /LimitAccess /Source:"C:\EXTRACTED_ISO\sources\sxs"
```

<h2 id="7-zip">11.24. 7-Zip <a href="#7-zip">(permalink)</a></h2>

Descarga e instala [7-Zip](https://www.7-zip.org). Abre ``C:\Program Files\7-Zip\7zFM.exe`` , luego navega a ``Tools -> Options`` y asocia 7-Zip con todas las extensiones de archivo haciendo clic en el botón ``+``. Puede que necesites hacer clic dos veces para sobrescribir asociaciones existentes.

<h2 id="graphics-driver">11.25. Drivers Gráficos <a href="#graphics-driver">(permalink)</a></h2>

- Ver: [docs/configure-nvidia.md](/docs/configure-nvidia.md)
- Ver: [docs/configure-amd.md](/docs/configure-amd.md)

<h2 id="msi-afterburner">11.26. MSI Afterburner <a href="#msi-afterburner">(permalink)</a></h2>

Si usas  [MSI Afterburner](https://www.msi.com/Landing/afterburner/graphics-cards), descárgalo e instálalo ahora.

- Se recomienda configurar una velocidad de ventilador estática, ya que usar la función de curva de ventilador requiere que el programa esté ejecutándose continuamente. Sin embargo, depende de ti si prefieres usar la curva o no.

- Para cargar automáticamente el perfil 1 (como ejemplo) al arrancar Windows, se puede usar el siguiente comando con el Programador de tareas ([1](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Asegúrate de colocar comillas si hay espacios en la ruta. Verifica que todo funcione correctamente tras reiniciar el sistema. Debes habilitar la opción ``Run with highest privileges`` si se requieren privilegios de administrador.

    ```bat
    "C:\Program Files (x86)\MSI Afterburner\MSIAfterburner.exe" /Profile1 /Q
    ```

<h2 id="display-resolutions-and-scaling-modes">11.27. Resoluciones de Pantalla y Modos de Escalado <a href="#display-resolutions-and-scaling-modes">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

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

<h2 id="spectre-meltdown-and-cpu-microcode">11.29. Spectre, Meltdown y Microcódigos del CPU <a href="#spectre-meltdown-and-cpu-microcode">(permalink)</a></h2>

> [!WARNING]
> 🔒 Desactivar Spectre y Meltdown puede afectar negativamente la seguridad y exponer el sistema a vulnerabilidades. Los usuarios deben evaluar los riesgos de seguridad asociados con la modificación de esta configuración.

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Desactivar Spectre y Meltdown es una técnica de mejora de rendimiento conocida desde hace tiempo por muchos entusiastas; sin embargo, con plataformas más recientes y arquitecturas modernas, puede producirse una regresión de rendimiento ([1](https://www.phoronix.com/review/amd-zen4-spectrev2)). Por esta razón, deben realizarse pruebas exhaustivas para determinar cómo se ve afectado el rendimiento y si éste escala de forma positiva, negativa o si no se ve afectado en absoluto. Su estado puede modificarse utilizando la herramienta [InSpectre](https://www.grc.com/inspectre.htm) y/o renombrando las DLLs de microcódigo dentro del sistema operativo, dependiendo de si existe una discrepancia entre las versiones de microcódigo del sistema operativo y de la BIOS ([1](https://superuser.com/a/895447), [2](https://support.mozilla.org/en-US/kb/microcode-update)). Es importante tener en cuenta que las versiones del microcódigo están sujetas a cambios con las actualizaciones de Windows.

<details>
<summary>instrucciones para renombrar DLLs</summary>

Abre CMD como TrustedInstaller con el siguiente comando: ``C:\bin\MinSudo.exe --TrustedInstaller --Privileged`` Luego, introduce el comando correspondiente a tu CPU para eliminar las actualizaciones de microcódigo. Para revertir los cambios, simplemente intercambia los nombres de los archivos para restaurar la DLL original..

```
ren C:\Windows\System32\mcupdate_GenuineIntel.dll mcupdate_GenuineIntel.dlll
```

```
ren C:\Windows\System32\mcupdate_AuthenticAMD.dll mcupdate_AuthenticAMD.dlll
```

</details>

Meltdown no afecta a la arquitectura AMD ([1](https://www.theverge.com/2018/1/3/16844630/intel-processor-security-flaw-bug-kernel-windows-linux), [2](https://www.phoronix.com/news/x86-PTI-Initial-Gaming-Tests), [3](https://lkml.org/lkml/2018/1/3/425)) y solo es requerido por una minoría de anticheats (como FACEIT).

Utiliza [InSpectre](https://www.grc.com/inspectre.htm) y la función de validación de [CPU-Z's](https://www.cpuid.com/softwares/cpu-z.html) para comprobar el estado o versión antes y después de un reinicio y así verificar el comportamiento esperado.

<h2 id="power-options">11.30. Opciones de Energía <a href="#power-options">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Abre CMD e introduce los siguientes comandos:

- Establecer el plan de energía activo como Alto rendimiento

    ```bat
    powercfg /setactive 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c
    ```

- Eliminar el plan de energía Equilibrado

    ```bat
    powercfg /delete 381b4222-f694-41f0-9685-ff5bb260df2e
    ```

- Eliminar el plan de energía Ahorro de energía

    ```bat
    powercfg /delete a1841308-3541-4fab-bc81-f71556f20b4a
    ```

- Desactivar la Gestión de energía del enlace USB 3
    ```bat
    powercfg /setacvalueindex scheme_current 2a737441-1930-4402-8d77-b2bebba308a3 d4e98f31-5ffe-4ce1-be31-1b38b384c009 0
    ```

- Desactivar Suspensión selectiva de USB

    ```bat
    powercfg /setacvalueindex scheme_current 2a737441-1930-4402-8d77-b2bebba308a3 48e6b7a6-50f5-4782-a5d4-53bb8f07e226 0
    ```

- Establecer "Processor performance core parking min cores" en 100

    - El "CPU parking" está desactivado por defecto en el plan de energía de alto rendimiento ([1](https://learn.microsoft.com/en-us/windows-server/administration/performance-tuning/hardware/power/power-performance-tuning#using-power-plans-in-windows-server)). Sin embargo, en Windows 11+ con CPUs modernas, el sistema puede forzar el aparcamiento de núcleos (parking) incluso con dicho plan. Puedes verificar si hay núcleos aparcados escribiendo ``resmon`` en ``Win+R``. Aunque el aparcamiento de núcleos está diseñado como una función de ahorro energético, algunos vídeos como [este](https://www.youtube.com/watch?v=2yOYfT_r0xI) y [este otro](https://www.youtube.com/watch?v=gyg7Gm7aN2A) explican que se trata de un comportamiento deseado para una correcta planificación de hilos. Esto puede estar bien para el usuario promedio, pero no consideran la penalización de latencia al desactivar el aparcamiento (como ocurre con las transiciones de C-State), además de la actividad en modo kernel (interrupciones, DPCs). En términos de planificación por CPU, puedes lograr el mismo resultado gestionando manualmente la carga por núcleo (por ejemplo, asignar la aplicación en tiempo real a un [unico CCX/CCD](https://hwbusters.com/cpu/amd-ryzen-9-7950x3d-cpu-review-performance-thermals-power-analysis/2) o solo a núcleos de alto rendimiento - P-Cores). Esto evita la sobrecarga causada por controladores del chipset y procesos como Xbox que generan conmutaciones de contexto innecesarias. Consulta la sección [Per-CPU Scheduling](#per-cpu-scheduling) para más detalles.

        ```bat
        powercfg /setacvalueindex scheme_current 54533251-82be-4824-96c1-47b60b740d00 0cc5b647-c1df-4637-891a-dec35c318583 100
        ```

        ```bat
        powercfg /setacvalueindex scheme_current 54533251-82be-4824-96c1-47b60b740d00 0cc5b647-c1df-4637-891a-dec35c318584 100
        ```
        
        - Establecer "Processor performance time check interval" en 5000

    - Existen varios DPCs del núcleo (ntoskrnl) relacionados con la gestión de energía que se programan periódicamente para re-evaluar los estados P (P-States) y los núcleos aparcados. Si se utiliza una frecuencia de CPU estática y el aparcamiento está desactivado, estas evaluaciones se vuelven innecesarias. El ajuste Processor performance time check interval controla cada cuánto se realiza esta evaluación. Aumentar su valor puede reducir la sobrecarga en la CPU, ya que se programan muchos menos DPCs.Por referencia, en el momento de redactar esto, los valores por defecto son:
    Ahorro de energía: 200
    Equilibrado: 15
    Alto rendimiento: 15
    El valor máximo permitido es 5000.
    Si usas frecuencias dinámicas (ej. Precision Boost, Turbo Boost) y el aparcamiento está activado, deberías evaluar el impacto de este ajuste, ya que la CPU podría no subir de frecuencia con suficiente rapidez.

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

- Establece el plan de energía actual como el plan activo

    ```bat
    powercfg /setactive scheme_current
    ```

<h2 id="process-explorer">11.31. Process Explorer <a href="#process-explorer">(permalink)</a></h2>

El Administrador de tareas de Windows carece de muchas métricas útiles en comparación con una herramienta como Process Explorer. A partir de Windows 8, el Administrador de tareas muestra el uso de CPU como porcentaje, lo cual puede llevar a interpretaciones erróneas ([1](https://aaron-margosis.medium.com/task-managers-cpu-numbers-are-all-but-meaningless-2d165b421e43)). En cambio, el Administrador de tareas de Windows 7 y Process Explorer informan el uso basado en tiempo de actividad, lo que explica por qué al desactivar los estados inactivos (C-States), la CPU aparece al 100% de uso.

- Descarga y extrae [Process Explorer](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer)

- Copia ``procexp64.exe`` a una carpeta segura como ``C:\Windows`` y abrelo 

- Ve a ``Options`` y selecciona ``Replace Task Manager``. Opcionalmente configura:

  - Confirmar cierre de procesos (``Confirm Kill``)

  - Permitir solo una instancia (Allow Only One Instance)

  - Siempre visible (Always On Top) — útil si una app se cuelga

  - Activa las siguientes columnas para una medición más granular:
    
    - Context Switch Delta (rendimiento del proceso)

    - CPU Cycles Delta (Process Performance)

    - CPU Cycles Delta (rendimiento del proceso)
     
    - Delta Reads (E/S del proceso)
  
    - Delta Writes (E/S del proceso)

    - Delta Other (E/S del proceso

   - Habilita la columna VirusTotal para escaneo de procesos sospechosos

<h2 id="memory-management-settings-windows-8">11.32. Configuración de la Gestión de Memoria (Windows 8+) <a href="#memory-management-settings-windows-8">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

- Abre PowerShell e ingresa el siguiente comando para revisar las opciones de administración de memoria.

    ```powershell
    Get-MMAgent
    ```

- Opcionalmente, utiliza el siguiente comando como ejemplo para deshabilitar una configuración específica. Si dejaste activado Superfetch y Prefetch en la sección [Superfetch and Prefetch](#superfetch-and-prefetch), entonces probablemente querrás que las características relacionadas con el prefetching sigan habilitadas.

    ```powershell
    Disable-MMAgent -MemoryCompression
    ```

<h2 id="network-adapter-options">11.33. Opciones del Adaptador de Red <a href="#network-adapter-options">(permalink)</a></h2>

- Abre ``Network Connections`` escribiendo ``ncpa.cpl`` en ``Win+R``

- Desactiva cualquier adaptador de red que no uses, luego haz clic derecho en el principal y selecciona  ``Properties``

- Desactiva ``NetBIOS over TCP/IP`` para todos los adaptadores de red en ``Internet Protocol Version 4 (TCP/IPv4) -> Properties -> General -> Advanced -> WINS`` para evitar escucha innecesaria del sistema, típicamente en los puertos 137-139, lo cual puede verificarse en herramientas de monitoreo de red como [TCPView](https://learn.microsoft.com/en-us/sysinternals/downloads/tcpview) o [Wirehshark](https://www.wireshark.org). Para referencia futura, esta opción debe cambiarse para cada adaptador de red recién instalado.

- Desactivar todas las opciones de ahorro de energía en la sección ``Advanced``.

  - Lista de posibles parámetros:

            ```
                Disabled Advanced EEE
                Energy Efficient Ethernet (EEE)
                Gigabit Ethernet
                Gigabit Lite
                Power Saving Mode
                Reduce Speed on Power Down
                Selective Suspend
                Ultra Low Power Mode
                System Idle Power Saver
            ```

- Opcionalmente configura los ajustes de DNS.

  - Consulta: [DNS Resolvers - Recommended Providers | Privacy Guides](https://www.privacyguides.org/en/dns)

- Opcionalmente leer esta guía con una cantidad grande de ajustes sobre adaptadores de Ethernet:
 
  Ver: [NIC / AFD / NDIS / TCPIP strings/dwords (ENG)]([(https://cryptpad.fr/pad/#/2/pad/view/IvUHErBqvbDs9lPOAUkUixP2zplJFGYAC99V8vcJkbM/embed/))

<h2 id="audio-devices">11.34. Dispositivos de Audio <a href="#audio-devices">(permalink)</a></h2>

- El panel de control de sonido se puede abrir escribiendo ``mmsys.cpl`` en ``Win+R``

- Desactiva los dispositivos de Reproducción y Grabación que no uses.

- Se recomienda evitar el uso de mejoras de audio ya que parecen consumir recursos marginalmente ([1](/assets/images/audio%20enhancements-benchmark.png))

- Opcionalmente, en la pestaña de comunicaciones, establece la opción en ``Do nothing`` para evitar el ajuste automático de los niveles de audio entre fuentes, lo cual suele ser una molestia para la mayoría de los usuarios ([1](https://multimedia.easeus.com/ai-article/windows-audio-ducking.html), [2](https://superuser.com/questions/1147371/how-can-i-disable-automatic-windows-7-8-10-audio-ducking))

- Minimiza el tamaño del búfer de audio con [LowAudioLatency](https://github.com/spddl/LowAudioLatency) o en tu DAC ([1](https://www.youtube.com/watch?v=JTuZvRF-OgE&t=464s)). Cuidado con las caídas de audio si el CPU no puede mantenerse al día bajo carga.

<h2 id="device-manager">11.35. Administrador de Dispositivos <a href="#device-manager">(permalink)</a></h2>

- Abre el Administrador de Dispositivos escribiendo ``devmgmt.msc`` en ``Win+R``

- Navega a ``View -> Devices by type``

  - En la categoría ``Disk drives``, puedes desactivar la opción de vaciado del búfer de caché de escritura en todas las unidades en ``Properties -> Policies`` si tu sistema tiene una fuente de energía de respaldo o no es propenso a fallos eléctricos, para evitar pérdida de datos.
    
  - En la categoría ``Network adapters`` , navega a ``Properties -> Advanced`` y desactiva cualquier opción de ahorro de energía.

- Navega a ``View -> Devices by connection``

  - Desactiva cualquier controlador PCIe, SATA, NVMe y XHCI así como concentradores USB que no tengan nada conectado
  - Desactiva cualquier dispositivo que no sea la GPU que comparta el mismo puerto PCIe que la GPU, siempre que no los necesites.

- Navega a ``View -> Resources by connection``

  - Desactiva cualquier dispositivo innecesario que esté utilizando un recurso IRQ o de E/S. Siempre pregunta si tienes dudas y tómate tu tiempo en este paso.
  - Si hay múltiples entradas del mismo dispositivo y no estás seguro de cuál está en uso, vuelve a consultar la estructura en árbol en ``View -> Devices by connection``. Esto se debe a que un solo dispositivo puede usar varios recursos (por ejemplo, IRQs). También puedes usar [MSI Utility](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044) para verificar dispositivos duplicados o innecesarios en caso de que pases alguno por alto en la vista desordenada del Administrador de Dispositivos.
- Opcionalmente usa [DeviceCleanup](https://www.uwe-sieber.de/files/DeviceCleanup.zip) para eliminar dispositivos ocultos.

<h2 id="device-power-saving">11.36. Ahorro de Energía en Dispositivos <a href="#device-power-saving">(permalink)</a></h2>

Abre PowerShell e ingresa el siguiente comando para desactivar la opción ``Allow the computer to turn off this device to save power`` para todos los dispositivos aplicables en el Administrador de Dispositivos..

Reconectar dispositivos puede hacer que esta opción se vuelva a habilitar, así que evita hacerlo, vuelve a ejecutar este comando cada vez, o colócalo en un script que se ejecute al inicio del sistema usando el Programador de Tareas ([instrucciones](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Asegúrate de colocar entre comillas cualquier ruta con espacios. Verifica que todo funcione correctamente tras reiniciar el sistema. Debes habilitar la opción ``Run with highest privileges`` si se requieren privilegios de administrador. Para scripts de PowerShell, establece el programa a iniciar como ``PowerShell`` y los argumentos como la ruta del script (por ejemplo: (e.g. ``C:\device-power-saving.ps1``).

```powershell
Get-WmiObject MSPower_DeviceEnable -Namespace root\wmi | ForEach-Object { $_.enable = $false; $_.psbase.put(); }
```

<h2 id="event-trace-sessions-ets">11.37. Sesiones de Rastreo de Eventos (ETS) <a href="#event-trace-sessions-ets">(permalink)</a></h2>

Esta sección describe instrucciones para desactivar la mayoría de las Event Trace Sessions, que se pueden ver escribiendo ``perfmon`` en ``Win+R`` y navegando a ``Data Collector Sets -> Event Trace Sessions``. Los programas que dependen de trazadores de eventos no podrán registrar datos hasta que se restauren las sesiones requeridas (por ejemplo, el registro de eventos de Windows), por lo que se crean dos archivos de registro para alternar entre ellos. Abre CMD como administrador e ingresa los comandos a continuación para crear los archivos de registro en el directorio ``C:\`` Estos archivos deben ejecutarse como Trusted Installer (usa [NSudo](https://github.com/M2TeamArchived/NSudo/releases/latest)) para evitar errores de permisos.

- ``ets-enable.reg``

    ```bat
    reg export "HKLM\SYSTEM\CurrentControlSet\Control\WMI\Autologger" "C:\ets-enable.reg"
    ```

- ``ets-disable.reg``

    ```bat
    >> "C:\ets-disable.reg" echo Windows Registry Editor Version 5.00 && >> "C:\ets-disable.reg" echo. && >> "C:\ets-disable.reg" echo [-HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\WMI\Autologger]
    ```

<h2 id="file-system">11.38. Sistema de Archivos <a href="#file-system">(permalink)</a></h2>

Abre CMD como administrador e ingresa los comandos a continuación.

- Desactiva la creación de nombres de archivo con longitud de 8.3 caracteres en volúmenes con formato FAT y NTFS, lo cual mejora el rendimiento y la seguridad ([1](https://web.archive.org/web/20200217151754/https://ttcshelbyville.wordpress.com/2018/12/02/should-you-disable-8dot3-for-performance-and-security))

  - Desactiva la creación de nombres de archivo 8.3

    ```bat
    fsutil 8dot3name set 1
    ```

  - Si se realizaron correctamente los pasos descritos en la sección [Booting Into the ISO](#booting-into-the-iso) para eliminar los nombres 8dot3, el comando a continuación debería mostrar un valor cercano a 0 para "total 8dot3 names found"

    ```bat
    fsutil 8dot3name scan /s C:
    ```

- Desactiva las actualizaciones de la marca de tiempo de Último Acceso en cada directorio cuando se listan directorios en un volumen NTFS. Desactivar esta característica mejora la velocidad de acceso a archivos y directorios ([1](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-behavior#remarks)). Ten en cuenta que esto puede afectar a programas de respaldo y almacenamiento remoto según los comentarios oficiales ([1](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/fsutil-behavior#remarks))

    ```bat
    fsutil behavior set disablelastaccess 1
    ```

<h2 id="message-signaled-interrupts">11.39. Message Signaled Interrupts <a href="#message-signaled-interrupts">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Los Message Signaled Interrupts (MSIs) son más rápidos que las interrupciones tradicionales basadas en línea y también pueden resolver el problema de interrupciones compartidas, que suelen ser la causa de alta latencia de interrupciones y problemas de estabilidad ([1](https://repo.zenk-security.com/Linux%20et%20systemes%20d.exploitations/Windows%20Internals%20Part%201_6th%20Edition.pdf)).

- Descarga y abre [MSI Utility](https://forums.guru3d.com/threads/windows-line-based-vs-message-signaled-based-interrupts-msi-tool.378044) o [GoInterruptPolicy](https://github.com/spddl/GoInterruptPolicy)

- Se pueden habilitar los MSIs en dispositivos que los soportan. Es importante notar que puede ser intencional por parte del desarrollador no habilitar MSIs en el archivo INF del controlador, por lo que estarán deshabilitados por defecto una vez instalado el driver. Por ejemplo, NVIDIA parece habilitar MSIs selectivamente dependiendo de la arquitectura de la GPU ([1](https://www.nvidia.com/en-us/geforce/forums/game-ready-drivers/13/528356)). Actúa con precaución y realiza pruebas para determinar si los cambios resultan en una mejora de rendimiento.

  - Sufrirás una pantalla azul (BSOD) si habilitas MSIs para el controlador SATA por defecto de Windows 7, el cual ya deberías haber actualizado según lo mencionado en la sección [Installing Drivers](#installing-drivers).

- Para verificar si un dispositivo está utilizando MSIs, reinicia tu PC y comprueba si el dispositivo tiene un IRQ negativo en MSI Utility.

- Aunque este paso puede haberse realizado en una sección anterior para descartar causas relacionadas con hardware en la compartición de IRQs, ahora pueden evaluarse las causas relacionadas con software confirmando que no hay IRQs compartidas en tu sistema escribiendo ``msinfo32`` en ``Win+R`` y navegando a la sección ``Conflicts/Sharing``.

  - Si el dispositivo ``System timer`` y ``High precision event timer`` comparten el IRQ 0, una solución es desactivar el controlador del dispositivo padre de ``System timer`` que es ``PCI standard ISA bridge``. Esto puede hacerse con el siguiente comando. Es importante notar que desactivar ``msisadrv`` rompe el teclado en dispositivos móviles.

    ```bat
    reg add "HKLM\SYSTEM\CurrentControlSet\Services\msisadrv" /v "Start" /t REG_DWORD /d "4" /f
    ```

<h2 id="mmcss">11.40. Multimedia Class Scheduler Service (MMCSS) <a href="#mmcss)">(permalink)</a></h2> 

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

[MMCSS](https://learn.microsoft.com/en-us/windows/win32/procthread/multimedia-class-scheduler-service) (Multimedia Class Scheduler Service) es el servicio de Windows que permite a aplicaciones multimedia (audio, captura, reproducción, juegos, aplicaciones “Pro Audio”) obtener acceso prioritario a la CPU sin bloquear por completo el resto del sistema. Las apps “se registran” con MMCSS mediante funciones del sistema (por ejemplo AvSetMmThreadCharacteristics) para indicar qué hilo está realizando trabajo de baja latencia, y el servicio ajusta prioridades y cuotas para favorecer tareas sensibles al tiempo. Esto ayuda a reducir “glitches” y dropouts en audio y mejorar la respuesta de sistemas en tiempo real, pero hay límites y configuraciones en el registro (por ejemplo SystemResponsiveness) que controlan cuánto CPU se reserva para tareas de baja prioridad y cómo se comporta MMCSS.

MMCSS ofrece un mecanismo centralizado por el que aplicaciones multimedia pueden solicitar prioridad temporal en la CPU para sus hilos críticos (por ejemplo, el hilo de audio). El objetivo es maximizar tiempo de CPU para trabajo sensible al tiempo sin “matar” la capacidad de respuesta del resto del sistema. Para aplicaciones que buscan latencia ultra-baja (Pro-Audio, DAWs, motores de audio en juegos), usar MMCSS correctamente reduce la frecuencia de interrupciones audibles y mejora la estabilidad del buffer.

En caso de querer una explicación más amplia, con más ajustes y mejores explicaciones. [MMCSS Research](https://cryptpad.fr/pad/#/2/pad/view/Vqfy09ex1xleJNuwJVUbGbmLKPakJjKLQUAHMkQqOgk/embed/)

Con MMCSS habilitado:

1. Audio threads (audiodg y aplicaciones):

    - Pueden recibir un aumento de prioridad hasta el rango de tiempo real.

  - El nivel de aumento depende del valor PRIORITY en el registro:
    ```HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile\Tasks\Audio.```

    - Ejemplo: con PRIORITY = 6 y la categoría de planificación (Scheduling Category) en Medium, la prioridad sube a 22.

  - Si la categoría de planificación está en Low, la prioridad se calcula con Background Priority, pero nunca supera 15.

    - Background Priority = 1 → prioridad 8

    - Background Priority = 8 → prioridad 15

    - En este caso MMCSS no se activa, ya que no se produce un aumento al rango de tiempo real. Por lo mismo, tampoco se activa el hilo NDIS.

    - A veces el hilo de audio o audiodg puede situarse en prioridad 9 por otro tipo de aumento, pero no cambia la regla general.

2. Hilo de sistema MMCSS:

   - Aparece un hilo del sistema con prioridad 27.

   - Se ejecuta con frecuencia porque se encarga de aumentar las prioridades de los streams de audio y de la red (NDIS).

   - Su duración típica es de 5.000 a 15.000 ns en cada ejecución.

3. Relación con NDIS:

   - Cuando el hilo de MMCSS está activo, el tiempo de ejecución de los DPC de NDIS disminuye.

   - Esto ocurre porque el trabajo se traslada al hilo NDIS, que lo procesa en lugar del DPC.

   - El tiempo total de procesamiento de tareas de red es similar, e incluso suele ser más rápido con MMCSS habilitado.

   - Si un hilo NDIS no termina antes de la siguiente interrupción NDIS (ISR), la ejecución se retrasa porque no puede iniciar un nuevo hilo hasta terminar el anterior.

   - El hilo NDIS tiene por defecto prioridad 8, lo que permite que otros hilos con mayor prioridad lo interrumpan.

   - Este hilo siempre se ejecuta en el núcleo que hospeda el controlador del adaptador de red.

- Su prioridad se puede ajustar en:
  ```HKLM\SYSTEM\ControlSet001\Services\NDIS\Parameters → "ReceiveWorkerThreadPriority".```

   - El valor por defecto es 8.

   - No acepta valores de 0–7 ni de 9–15.

   - El hilo que procesa datos de red permanece en 8, pero otros hilos NDIS inactivos adoptan el valor asignado (1–31).
 
1. Con MMCSS deshabilitado:

   - Los audio threads (audiodg y aplicaciones) tienen siempre prioridad 15.

   - El hilo de sistema MMCSS no se ejecuta.

   - Todo el trabajo pasa a los DPC de NDIS, que tardan más en completarse, y no existen hilos NDIS.

   - Este mismo comportamiento ocurre si se configura el valor del registro

   ```bat
    reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Multimedia\SystemProfile" /v "NetworkThrottlingIndex" /t REG_DWORD /d "ffffffff" /f
    ```
Se han preparado 2 configuraciones pre-configuradas para experimentar: [MMCSS Configs](https://mega.nz/file/c2EHTRxI#oR1TrhraJk_ojYkSamA2Vu3qrZV7ozn7XL6S0L29NoQ)

<h2 id="xhci-interrupt-moderation-imod">11.41. XHCI Interrupt Moderation (IMOD) <a href="#xhci-interrupt-moderation-imod">(permalink)</a></h2>

En la mayoría de los sistemas, Windows 7 utiliza un intervalo IMOD de 1 ms, mientras que versiones más recientes de Windows emplean 0.05 ms (50 μs), a menos que el controlador USB instalado indique lo contrario. Esto significa que, después de que se genera una interrupción, el controlador XHCI espera (período de búfer) durante el intervalo especificado para que llegue más información antes de generar otra interrupción. Esta técnica reduce el uso de CPU, pero puede ocasionar que los datos de un dispositivo se suministren de forma inconsistente si se espera información de otros dispositivos conectados al mismo controlador XHCI dentro de ese mismo período de espera.

Por ejemplo, un mouse con tasa de sondeo de 1 kHz enviará datos cada 1 ms. Si solo estás moviendo el mouse y el intervalo IMOD es de 1 ms, no habrá moderación de interrupciones ya que las interrupciones se generan a una tasa igual o menor al intervalo especificado. Sin embargo, en juegos rápidos, fácilmente superarás las 1000 interrupciones por segundo al mover el mouse mientras usas teclado y audio, lo cual puede derivar en pérdida de información, ya que estarás esperando datos durante el período de espera desde cualquiera de los dispositivos. Aunque esto es poco probable con un intervalo IMOD de 0.05 ms (50 μs), aún puede ocurrir.

Como ejemplo, un intervalo IMOD de 1 ms combinado con un mouse de 8 kHz ya es problemático, porque estás esperando datos cada 0.125 ms, lo cual es significativamente más frecuente que el intervalo especificado, generando un gran cuello de botella ([1](https://www.overclock.net/threads/usb-polling-precision.1550666/page-61#post-28576466)).

- Consulta: [Cómo deshabilitar persistentemente la moderación de interrupciones XHCI | BoringBoredom](https://github.com/BoringBoredom/PC-Optimization-Hub/blob/main/content/xhci%20imod/xhci%20imod.md)

- Es posible que debas desactivar la lista de bloqueo de controladores vulnerables de Microsoft con el siguiente comando para cargar el controlador de [RWEverything](http://rweverything.com) , aunque algunos anticheats no respetan esta desactivación, por lo que deberás probar si el juego en cuestión se ejecuta correctamente.

    ```bat
    reg add "HKLM\SYSTEM\CurrentControlSet\Control\CI\Config" /v "VulnerableDriverBlocklistEnable" /t REG_DWORD /d "0" /f
    ```

- En ciertos casos, el índice de interrupción puede cambiar después de un reinicio, haciendo inválida la dirección si fue codificada manualmente. Como solución, puedes simplemente deshabilitar IMOD para todos los índices de interrupción colocando el script [XHCI-IMOD-Interval.ps1](/bin/XHCI-IMOD-Interval.ps1) en una ubicación segura y configurándolo para que se ejecute al inicio mediante el Programador de tareas ([instrucciones](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Asegúrate de encerrar en comillas cualquier ruta que contenga espacios. Verifica que todo esté funcionando correctamente tras reiniciar el sistema. Debes activar la opción ``Run with highest privileges`` si se requieren privilegios de administrador. Para scripts de PowerShell, establece el programa de inicio como ``PowerShell`` y los argumentos como la ruta del script (por ejemplo: ``C:\XHCI-IMOD-Interval.ps1``)

  ```bat
  PowerShell C:\XHCI-IMOD-Interval.ps1
  ```

- Para comprobar si el cambio del intervalo IMOD está teniendo efecto, puedes configurarlo temporalmente a ``0xFA00`` (62.5 Hz). Si el cursor del mouse presenta tartamudeos visibles al moverse, entonces los cambios se aplicaron correctamente.

<h2 id="control-panel">11.42. Panel de Control <a href="#control-panel">(permalink)</a></h2>

No es mala idea revisar tanto el Panel de control clásico como el moderno para asegurarte de que no haya configuraciones mal aplicadas.

<h2 id="configuring-applications">11.43. Configuración de Aplicaciones <a href="#configuring-applications">(permalink)</a></h2>

- Instala todos los programas y aplicaciones que utilices (incluyendo videojuegos) para preparar el entorno para los próximos pasos.

- Si es posible, prioriza las ediciones portables de los programas, ya que los instaladores suelen dejar residuos incluso después de desinstalar. Esto puede evitarse usando herramientas como [Bulk-Crap-Uninstaller](https://github.com/Klocman/Bulk-Crap-Uninstaller)

<h3 id="nvidia-reflex">11.43.1. NVIDIA Reflex <a href="#nvidia-reflex">(permalink)</a></h3>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

[NVIDIA Reflex](https://www.nvidia.com/en-us/geforce/news/reflex-low-latency-platform) minimiza los fotogramas en cola en la GPU ajustando dinámicamente la tasa de cuadros por segundo en escenarios intensivos gráficamente. Puede activarse en juegos compatibles si el desarrollador ha implementado soporte. Aunque reduce la latencia, funciona como un limitador dinámico de FPS, lo que puede causar microtartamudeos o variaciones en el tiempo de fotogramas. Por esta razón, se recomienda hacer pruebas exhaustivas antes de activarlo de forma predeterminada.

- Consulta: [NVIDIA Reflex Low Latency - How It Works & Why You Want To Use It | Battle(non)sense](https://www.youtube.com/watch?v=QzmoLJwS6eQ)

<h3 id="framerate-limit">11.43.2. Límite de Fotogramas <a href="#framerate-limit">(permalink)</a></h3>

> [!CAUTION]
> 📊 **Do NOT** blindly follow the recommendations in this section. **Do** benchmark the specified changes to ensure they result in positive performance scaling, as every system behaves differently and changes could unintentionally degrade performance ([instrucciones](#benchmarking)).

- Si limitas tu tasa de fotogramas, asegúrate de establecerla como múltiplo de la frecuencia de actualización de tu monitor ([calculadora](https://boringboredom.github.io/tools/fpscapcalculator)) para evitar desincronizaciones de cuadros y tearing desplazado ([1](https://www.youtube.com/watch?v=_73gFgNrYVQ), [2](https://github.com/BoringBoredom/PC-Optimization-Hub/blob/main/content/peripherals/mistiming/mistiming.md)). . También puedes reducir la frecuencia de actualización para evitar desajustes ([instrucciones](https://forums.blurbusters.com/viewtopic.php?t=8946)). Otra alternativa es usar Frecuencia de Actualización Variable (VRR).

- Asegúrate de que la GPU no esté totalmente utilizada, ya que un menor uso de GPU reduce la latencia del sistema ([1](https://www.youtube.com/watch?v=8ZRuFaFZh5M&t=859s), [2](https://www.youtube.com/watch?v=7CKnJ5ujL_Q)).

- Limitar la tasa de fotogramas usando [RTSS](https://www.guru3d.com/files-details/rtss-rivatuner-statistics-server-download.html) en lugar del limitador del propio juego resulta en un ritmo de fotogramas más consistente y una experiencia más fluida, ya que utiliza busy-wait (espera activa), lo cual ofrece mayor precisión que la espera pasiva al 100%, pero a costa de una mayor latencia y posible sobrecarga en CPU ([1](https://www.youtube.com/watch?t=377&v=T2ENf9cigSk), [2](https://en.wikipedia.org/wiki/Busy_waiting)). Desactiva la opción ``Enable dedicated encoder server service`` para evitar que se ejecute ``EncoderServer.exe``.

<h3 id="register-game">11.43.3. Registrar Juego en Config Store <a href="#register-game">(permalink)</a></h3>

Asegúrate de que la Barra de Juegos de Xbox reconozca el juego que estás ejecutando o que has instalado. Si no lo hace, abre la Barra de Juegos con ``Win+G`` y activa la opción ``Remember this is a game`` mientras el juego esté abierto. Esto también garantiza que el Modo Juego funcione correctamente si decides usarlo.

<h3 id="presentation-mode">11.43.4. Modo de Presentación <a href="#presentation-mode">(permalink)</a></h3>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Esto no implica una recomendación sobre el modo de presentación a usar, es meramente informativo.

- Verifica siempre si tu juego está usando el modo de presentación deseado mediante PresentMon  ([instrucciones](https://boringboredom.github.io/Frame-Time-Analysis))

- Puedes experimentar y comparar distintos modos de presentación para evaluar cuál prefieres

  - Consulta: [Presentation Model | Special K Wiki](https://wiki.special-k.info/en/Presentation_Model)

- Si no aparece ningún resultado al buscar el nombre del ejecutable del juego en  ``HKCU\SYSTEM\GameConfigStore`` dentro del Registro, es posible que debas registrar el juego presionando ``Win+G`` y activando ``Remember this is a game`` con el juego abierto. Luego verifica si la entrada fue creada en la clave de registro mencionada.

- Si deseas utilizar el modo de presentación ``Hardware: Legacy Flip`` , marca la casilla ``Disable fullscreen optimizations`` Si eso no funciona, ejecuta los comandos siguientes en CMD y reinicia. Estas claves del Registro suelen ser accedidas por el juego y por Windows al iniciar.

    ```bat
    reg add "HKCU\SYSTEM\GameConfigStore" /v "GameDVR_DXGIHonorFSEWindowsCompatible" /t REG_DWORD /d "1" /f
    ```

    ```bat
    reg add "HKCU\SYSTEM\GameConfigStore" /v "GameDVR_FSEBehavior" /t REG_DWORD /d "2" /f
    ```

- Si se encuentra atascado con «Hardware Composed: Independent Flip» y desea utilizar otro modo de presentación, pruebe a ejecutar el siguiente comando para desactivar los MPO en CMD y reinicie el sistema.

    ```bat
    reg add "HKLM\SOFTWARE\Microsoft\Windows\Dwm" /v "OverlayTestMode" /t REG_DWORD /d "5" /f
    ```

<h3 id="game-mode">11.43.5. Modo de Juego <a href="#game-mode">(permalink)</a></h3>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

El Modo de Juego impide que Windows Update se ejecute y que se muestren ciertas notificaciones al usuario ([1](https://support.xbox.com/en-GB/help/games-apps/game-setup-and-play/use-game-mode-gaming-on-pc)).

El Modo de Juego es un perfil de energía (power profile) diseñado para optimizar el rendimiento del sistema durante sesiones de juego. Este modo prioriza recursos del hardware y ajusta configuraciones de Windows para reducir interferencias, como actualizaciones automáticas o notificaciones, asegurando una experiencia más fluida. Pero en ocasiones puede generar el 

Cabe destacar que el Modo Juego puede interferir con los boost de prioridad de procesos e hilos, dependiendo del valor de PsPrioritySeparation, como se explica en la sección [Thread Quantums and Scheduling](#thread-quantums-and-scheduling). Esto se puede evidenciar replicando el experimento de boost de prioridad de hilos descrito en Windows Internals, usando el Monitor de rendimiento y el contador de prioridad actual de hilos. Por esta razón, se recomienda experimentar con el Modo Juego tanto activado como desactivado.

<h3 id="media-player">11.43.6. Reproductor Multimedia <a href="#media-player">(permalink)</a></h3>

- [mpv](https://mpv.io) or [mpv.net](https://github.com/stax76/mpv.net)
- [mpc-hc](https://mpc-hc.org) ([updated fork](https://github.com/clsid2/mpc-hc))
- [VLC](https://www.videolan.org)

<h3 id="qos-policies">11.43.7. Políticas QoS <a href="#qos-policies">(permalink)</a></h3>

Dependiendo de tu red y configuración del router, pueden establecerse políticas QoS en Windows para priorizar los paquetes de una aplicación.

- Ver: [assets/images/dscp-46-qos-policy.png](/assets/images/dscp-46-qos-policy.png)

  - Ver: [DSCP and Precedence Values | Cisco](https://www.cisco.com/c/en/us/td/docs/switches/datacenter/nexus1000/sw/4_0/qos/configuration/guide/nexus1000v_qos/qos_6dscp_val.pdf)

  - Ver: [The QoS Expedited Forwarding (EF) Model | Network World](https://www.networkworld.com/article/761413/the-qos-expedited-forwarding-ef-model.html)

- Ver también:: [How Can You Verify Whether a DSCP QoS Policy Is Working?](/docs/research.md#2-how-can-you-verify-whether-a-dscp-qos-policy-is-working)

- Microsoft recomienda la siguiente clave del Registro para asegurar que los paquetes estén correctamente marcados con el valor DSCP, especialmente si hay más de un adaptador de red o si la política se usa fuera de un dominio ([1](https://learn.microsoft.com/en-us/skypeforbusiness/manage/network-management/qos/configuring-port-ranges-for-your-skype-clients))

  ```bat
  reg add "HKLM\SYSTEM\CurrentControlSet\Services\Tcpip\QoS" /v "Do not use NLA" /t REG_SZ /d "1" /f
  ```

<h2 id="kernel-mode-scheduling-interrupts-dpcs-and-more">11.44. Optimización en Modo Kernel (Interrupciones, DPCs y más) <a href="#kernel-mode-scheduling-interrupts-dpcs-and-more">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Windows agenda interrupciones y DPCs en el CPU 0 por defecto para varios módulos en modo kernel. Agrupar muchas tareas en un solo CPU puede introducir sobrecarga adicional y mayor jitter debido a la competencia por tiempo de CPU. Para mitigar esto, se pueden configurar afinidades para aislar módulos críticos y distribuir la carga en núcleos menos utilizados..

- Usa el reporte DPC/ISR de xperf generado por el script [xperf-dpcisr.bat](/bin/xperf-dpcisr.bat) o [xtw](https://github.com/valleyofdoom/xtw) para analizar en qué CPU se están ejecutando los módulos en modo kernel. No puedes administrar afinidades si no sabes qué está corriendo ni en qué CPU. Esto también aplica para hilos en modo usuario. Verifica si las políticas de afinidad de interrupción están funcionando analizando el uso por CPU mientras el dispositivo está activo.

- Además, los benchmarks de latencia entre núcleos pueden ayudar en la toma de decisiones sobre afinidades

  - Ver: [CXWorld/MicroBenchX](https://github.com/CXWorld/MicroBenchX)

- Asegúrate de que el DPC correspondiente a una ISR se procese en el mismo CPU ([ejemplo](/assets/images/isr-dpc-same-core.png)). Si se procesan en distintos núcleos, puede generarse sobrecarga adicional por la comunicación entre procesadores e interferencia con la coherencia de caché.

- Usa [Microsoft Interrupt Affinity Tool](https://www.techpowerup.com/download/microsoft-interrupt-affinity-tool) o [GoInterruptPolicy](https://github.com/spddl/GoInterruptPolicy) para configurar afinidades de controladores. El dispositivo puede identificarse comparando la información del campo ``Location`` en la pestaña ``Properties -> General`` de las propiedades del dispositivo en el Administrador de dispositivos.

<h3 id="gpu-and-directx-graphics-kernel">11.44.1. GPU y DirectX Graphics Kernel <a href="#gpu-and-directx-graphics-kernel">(permalink)</a></h3>

[AutoGpuAffinity](https://github.com/valleyofdoom/AutoGpuAffinity) puede usarse para realizar pruebas de rendimiento y determinar qué CPUs asignadas a los módulos relacionados con la GPU ofrecen el mejor desempeño. Configura la opción custom_cpus en el archivo de configuración si es necesario. Esta opción es útil para seleccionar un conjunto específico de núcleos que se desea probar, como los P-Cores o un CCX/CCD específico.

<h3 id="xhci-and-audio-controller">11.44.2. Controlador XHCI y de Audio <a href="#xhci-and-audio-controller">(permalink)</a></h3>

Los módulos relacionados con los controladores XHCI y de audio generan una cantidad sustancial de interrupciones al interactuar con sus respectivos dispositivos. Aislar dichos módulos en una CPU poco utilizada es beneficioso para reducir la contención.

<h3 id="network-interface-card">11.44.3. Tarjeta de Red <a href="#network-interface-card">(permalink)</a></h3>

La NIC (tarjeta de red) debe soportar MSI-X para que la tecnología Receive Side Scaling (RSS) funcione correctamente ([1](https://old.reddit.com/r/intel/comments/9uc03d/the_i219v_nic_on_your_new_z390_motherboard_and)). En la mayoría de los casos, establecer la CPU base de RSS es suficiente para migrar los DPCs e ISRs del controlador de red, eliminando así la necesidad de una política de afinidad por interrupciones. Sin embargo, si tienes dificultades para migrar estos elementos a otras CPUs, intenta configurar ambos parámetros.

Ten en cuenta que la cantidad de colas RSS determina el número de CPUs consecutivas en las que se programa el controlador de red. Por ejemplo, el controlador se programará en las CPUs 2/3/4/5 (o 2/4/6/8 si HT/SMT está habilitado) si se establece la CPU base de RSS en 2 junto con 4 colas RSS configuradas.

- Consulta [Cuántas colas RSS necesitas?](/docs/research.md#4-how-many-rss-queues-do-you-need)

- Consulta la [Configuración de Receive Side Scaling (RSS)](https://github.com/Duckleeng/TweakCollection#receive-side-scaling-rss-configuration)

<h2 id="user-mode-scheduling-processes-threads">11.45. Optimización en Modo Usuario (Processes, Threads) <a href="#user-mode-scheduling-processes-threads">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Existen varios métodos para establecer afinidades para los procesos. Uno de ellos es el Administrador de tareas, pero sólo persiste hasta que el proceso se cierra. Una solución más popular y permanente es [Process Lasso](https://bitsum.com), que permite guardar la configuración, aunque requiere que un proceso se ejecute continuamente en segundo plano, lo que introduce una leve sobrecarga. Para evitar esto, puedes simplemente lanzar la aplicación con una afinidad de CPU especificada, eliminando la necesidad de programas como Process Lasso para gestionar afinidades, a costa de la facilidad de uso.

- Usa el [CPU Affinity Mask Calculator](https://bitsum.com/tools/cpu-affinity-calculator) para determinar la máscara de afinidad en formato hexadecimal deseada.

- En algunos casos, el proceso puede estar protegido, por lo que especificar la afinidad puede fallar. Para solucionar esto, intenta establecer la afinidad en los procesos padre, de modo que el proceso hijo herede la afinidad al iniciarse. Por ejemplo, un lanzador de juegos suele ser el proceso padre del juego. El árbol de procesos en [Process Explorer's](https://learn.microsoft.com/en-us/sysinternals/downloads/process-explorer) puede usarse para identificar procesos padre e hijo.

  - [Process Hacker](https://processhacker.sourceforge.io) y [WindowsD](https://github.com/katlogic/WindowsD) pueden eludir varias protecciones a nivel de proceso mediante exploits, pero no se recomienda su uso ya que interfieren con los anticheats.

- Puede ser útil evaluar cómo escala el rendimiento de tu aplicación con la cantidad de núcleos, ya que puede comportarse de forma diferente debido a implementaciones deficientes del planificador tanto por parte de la aplicación como del sistema operativo. En algunos casos, es posible que la aplicación rinda mejor con menos núcleos asignados a través de una máscara de afinidad ([1](https://developer.nvidia.com/blog/limiting-cpu-threads-for-better-game-performance)). Esto también te dará una idea general de cuántos núcleos puedes reservar. En otros casos, puede perjudicar gravemente el rendimiento si el juego crea más hilos de trabajo de los que hay CPUs disponibles, debido a que el juego sólo considera los núcleos físicos disponibles. Por ello, es vital medir la escalabilidad del rendimiento.

<h3 id="starting-a-process-with-a-specified-affinity-mask">11.44.1. Iniciar un Proceso con una Afinidad Específic Mask <a href="#starting-a-process-with-a-specified-affinity-mask">(permalink)</a></h3>

El siguiente comando inicia ``notepad.exe`` con una afinidad de CPU 1 y CPU 2 como ejemplo, lo cual se reflejará en el Administrador de tareas. Este comando puede colocarse en un script por lotes para facilitar el acceso, y debe usarse cada vez que se desee iniciar la aplicación con la afinidad especificada.

```bat
start /affinity 0x6 notepad.exe
```

<h3 id="specifying-an-affinity-mask-for-running-processes">11.45.2. Especificar Afinidad para Procesos Activos <a href="#specifying-an-affinity-mask-for-running-processes">(permalink)</a></h3>

A veces, los procesos a los que deseas aplicar una máscara de afinidad ya se están ejecutando, por lo que el comando anterior no es aplicable. A modo de ejemplo, el siguiente comando asigna la máscara de afinidad de los procesos ``svchost.exe`` y ``audiodg.exe`` a la CPU 3. Usa este ejemplo para crear un script en PowerShell y haz que se ejecute al inicio mediante el Programador de tareas ([instrucciones](https://www.windowscentral.com/how-create-automated-task-using-task-scheduler-windows-10)). Asegúrate de colocar entre comillas cualquier ruta que contenga espacios. Verifica que todo funcione correctamente después de reiniciar el sistema. Es necesario habilitar la opción ``Run with highest privileges`` si se requieren privilegios de administrador. Para scripts de PowerShell, establece el programa a iniciar como ``PowerShell`` y los argumentos como la ruta al script (por ejemplo ``C:\process-affinities.ps1``).

```powershell
Get-Process @("svchost", "audiodg") -ErrorAction SilentlyContinue | ForEach-Object { $_.ProcessorAffinity=0x8 }
```

<h2 id="reserved-cpu-sets-windows-10">11.46. CPUs Reservados (Windows 10+) <a href="#reserved-cpu-sets-windows-10">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

[ReservedCpuSets](https://github.com/valleyofdoom/ReservedCpuSets) puede usarse para evitar que Windows programe ISRs, DPCs y otros hilos en CPUs específicas. Aislar módulos de las perturbaciones de nivel usuario y kernel ayuda a reducir la contención, el jitter, y permite que los módulos sensibles al tiempo obtengan el tiempo de CPU que requieren.

- Como se menciona en la sección [User-Mode Scheduling (Processes, Threads)](#user-mode-scheduling-processes-threads), deberías determinar qué tan bien o mal escala tu aplicación con la cantidad de núcleos para hacerte una idea general de cuántos núcleos puedes permitirte reservar

- Como las políticas de afinidad por interrupciones, de procesos y de hilos tienen mayor precedencia, puedes usar esto junto con afinidades definidas por el usuario para garantizar que nada excepto lo que hayas asignado se programe en esas CPUs.

- Asegúrate de tener suficientes núcleos para ejecutar tu aplicación en tiempo real y no reservar tantos CPUs que el aislamiento deje de ofrecer mejoras en el rendimiento en tiempo real.

- Dado que los conjuntos de CPU (CPU sets) se consideran políticas suaves (soft policies), la configuración no está garantizada. Un proceso intensivo, como una prueba de estrés, utilizará los núcleos reservados si lo requiere.

> [!IMPORTANT]
> Ocurre un comportamiento inesperado si se asigna afinidad a una combinación de CPUs reservadas y no reservadas. Asegúrate de asignar afinidad exclusivamente a CPUs reservadas o no reservadas, pero no una mezcla de ambas.

<h3 id="use-cases">11.46.1. Casos de Uso <a href="#use-cases">(permalink)</a></h3>

- Se puede dar una sugerencia al sistema operativo para programar tareas en un grupo específico de CPUs. Un ejemplo moderno sería reservar E-Cores (núcleos de eficiencia) o determinados CCX/CCD para que las tareas se programen por defecto en los P-Cores (núcleos de rendimiento) u otros CCX/CCDs. Con este enfoque, puedes forzar explícitamente que las tareas en segundo plano o menos importantes se ejecuten en los CPUs reservados. Este es sólo un ejemplo: la lógica puede invertirse. Sin embargo, algunos procesos y módulos sensibles a la latencia están protegidos, por lo que las políticas de afinidad pueden fallar, lo que representa una limitación importante. Existen varias posibilidades y compromisos a considerar. Ten en cuenta que el rendimiento puede degradarse al reservar E-Cores u otros CCX/CCDs si las aplicaciones hacen uso de ellos. Por ello, es vital que midas la escalabilidad del rendimiento al reservar núcleos, ya sea uno, algunos o un conjunto completo de CPUs. Otro modo en que puede degradarse el rendimiento es si el planificador o las aplicaciones apuntan específicamente a núcleos reservados porque el campo ``RealTime`` está establecido en 1 en la estructura [SYSTEM_CPU_SET_INFORMATION](https://learn.microsoft.com/en-us/windows/win32/api/winnt/ns-winnt-system_cpu_set_information) struct

- Reservar CPUs específicas a las que se han asignado ciertos módulos para su programación.

<h2 id="analyzing-event-viewer">11.47. Analizar el Event Viewer <a href="#analyzing-event-viewer">(permalink)</a></h2>

Este paso no es obligatorio, pero puede ayudarte a justificar problemas de rendimiento inexplicables u otros errores generales. Asegúrate de que no haya errores en el Visor de eventos escribiendo ``eventvwr.msc`` en ``Win+R`` ya que cualquier cambio que hayas hecho en el sistema operativo podría causar errores o excepciones internas de forma periódica.

- Fusiona el archivo ``ets-enable.reg`` generado en la secció [Event Trace Sessions (ETS)](#event-trace-sessions-ets) si aplica, ya que es necesario para el registro de eventos.

<h2 id="virtualization-based-security-vbs">11.48. Seguridad Basada en Virtualización (VBS) <a href="#virtualization-based-security-vbs">(permalink)</a></h2>

La seguridad basada en virtualización (VBS) afecta negativamente al rendimiento ([1](https://www.tomshardware.com/news/windows-11-gaming-benchmarks-performance-vbs-hvci-security)) y, en algunos casos, está habilitada por defecto. Su estado puede consultarse escribiendo ``msinfo32`` en ``Win+R`` y puede deshabilitarse si es necesario ([1](https://www.tomshardware.com/how-to/disable-vbs-windows-11), [2](https://support.microsoft.com/en-us/windows/options-to-optimize-gaming-performance-in-windows-11-a255f612-2949-4373-a566-ff6f3f474613)) Por otro lado, [privacyguides.org](https://www.privacyguides.org/en/os/windows/group-policies/) recomienda mantenerla habilitada. La VBS debería estar desactivada cuando la virtualización esté desactivada en la BIOS, por lo que debes tener cuidado si vuelves a habilitar la virtualización en el futuro.

<h2 id="cpu-idle-states">11.49. Estados de Inactividad del CPU <a href="#cpu-idle-states">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Deshabilitar los estados inactivos fuerza el estado C-State 0, lo que puede observarse en [HWiNFO](https://www.hwinfo.com), , y es parte de las recomendaciones de Microsoft para configurar dispositivos con rendimiento en tiempo real ([1](https://learn.microsoft.com/en-us/windows/iot/iot-enterprise/soft-real-time/soft-real-time-device)). Forzar el estado C0 mitiga el retraso indeseado al ejecutar nuevas instrucciones en una CPU que ha entrado en un estado de ahorro de energía más profundo, a costa de un mayor consumo de energía y temperaturas más altas. Por lo tanto, se recomienda mantener los estados inactivos habilitados para la mayoría de los usuarios, ya que podrían surgir otros problemas debido a estos efectos secundarios (como estrangulamiento térmico o problemas de energía). La temperatura del CPU no debería aumentar hasta el punto de provocar thermal throttling, ya que eso debería haber sido evaluado en la sección [Stability, Hardware Clocking and Thermal Performance](#stability-hardware-clocking-and-thermal-performance).

Si no se establece una frecuencia de CPU estática, los efectos de forzar C-State 0 deben evaluarse en cuanto al comportamiento del boost de frecuencia. Por ejemplo, ciertamente no querrás deshabilitar los estados inactivos si dependes de Precision Boost Overdrive (PBO), Turbo Boost u otras tecnologías similares. Evita desactivar los estados inactivos si tienes Hyper-Threading o SMT habilitado, ya que el rendimiento monohilo suele verse negativamente afectado.

<h3 id="enable-idle-states-default">11.48.1. Activar Estados de Inactividad (por defecto) <a href="#enable-idle-states-default">(permalink)</a></h3>

```bat
powercfg /setacvalueindex scheme_current sub_processor 5d76a2ca-e8c0-402f-a133-2158492d58ad 0 && powercfg /setactive scheme_current
```

<h3 id="disable-idle-states">11.49.2. Desactivar Estados de Inactividad <a href="#disable-idle-states">(permalink)</a></h3>

```bat
powercfg /setacvalueindex scheme_current sub_processor 5d76a2ca-e8c0-402f-a133-2158492d58ad 1 && powercfg /setactive scheme_current
```

<h2 id="thread-quantums-and-scheduling">11.50. Thread Quantums y Scheduling <a href="#thread-quantums-and-scheduling">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Un quantum es el tiempo asignado para que un hilo se ejecute antes de que el planificador evalúe si otro hilo del mismo nivel de prioridad debe ejecutarse. Si un hilo finaliza su quantum y no hay otros hilos en su nivel de prioridad listos para ejecutarse, el planificador permite que el hilo continúe ejecutándose durante un quantum adicional. El quantum puede controlarse con la clave de registro que se muestra a continuación, además de definir cuánto tiempo del quantum se asigna a los hilos en segundo plano y primer plano. El valor está representado como una máscara de 6 bits, donde cada uno de los tres pares de bits determina las características del quantum y la distribución del tiempo entre hilos en segundo y primer plano. Por defecto, está configurado en ``0x2``, lo cual corresponde a``0b000010`` y tiene diferentes significados en ediciones cliente y servidor, como se explicará a continuación.

```
[HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\PriorityControl]
"Win32PrioritySeparation"=dword:00000002
```

<h3 id="bitmask-explaination">11.50.1. Explicación de Bitmask <a href="#bitmask-explaination">(permalink)</a></h3>

- El par de bits más a la izquierda (XXYYZZ) determina la longitud del quantum. Esto está representado por ``PspForegroundQuantum``

  |Value|Description|
  |---|---|
  |00/11|Short Intervals (Windows Client), Long Intervals (Windows Server)|
  |01|Long Intervals|
  |10|Short Intervals|

- El par de bits del medio (XXYYZZ) determina si la longitud del quantum es variable o fija. Si se utiliza un quantum de longitud fija, entonces el par de bits más a la derecha se ignora, ya que la proporción que determina el tiempo asignado a los hilos en segundo plano y en primer plano dentro del quantum es fija. Esto también está representado por ``PspForegroundQuantum``

  |Value|Description|
  |---|---|
  |00/11|Variable-length (Windows Client), Fixed-length (Windows Server)|
  |01|Variable-length|
  |10|Fixed-length|

- El par de bits más a la derecha (XXYYZZ) determina la proporción de tiempo en el quantum asignado a los hilos en segundo plano y en primer plano, en la cual los hilos en primer plano pueden recibir hasta tres veces más tiempo de CPU que los hilos en segundo plano. Como se mencionó anteriormente, esto solo se puede configurar con quantums de longitud variable. Esto está representado por  ``PsPrioritySeparation``

  |Value|Description|
  |---|---|
  |00|1:1|
  |01|2:1|
  |10/11|3:1|

- Usando la información anterior, el valor predeterminado de ``0x2`` corresponde a quantum corto, de longitud variable y proporción 3:1 en Windows Client y quantum largo, de longitud fija y proporción 3:1 en Windows Server.

<h3 id="win32priorityseparation-values">11.50.2. Valores de Win32PrioritySeparation <a href="#win32priorityseparation-values">(permalink)</a></h3>

La siguiente tabla consiste en todos los valores posibles que son consistentes entre ediciones cliente y servidor de Windows, ya que ``00`` o ``11`` no fueron utilizados en XXYYZZ de la máscara de bits, los cuales tienen significados diferentes en las ediciones cliente y servidor. Cualquier valor no especificado en la tabla es idéntico a uno que sí está especificado, como se explica [aqui](/docs/research.md#5-ambiguous-win32priorityseparation-values-explained), ; por tanto, los valores en la tabla son los únicos que deberían utilizarse para mayor simplicidad.

Aunque no se puede usar una mejora para el primer plano cuando se usa un quantum de longitud fija, aún cambia PsPrioritySeparation y otro mecanismo de mejora de prioridad de hilos simplemente utiliza su valor, por lo que en realidad, un quantum fijo con proporción 3:1 debería tener una diferencia perceptible en comparación con uno fijo con proporción 1:1. Véase el siguiente párrafo de Windows Internals:

> Como se describirá a continuación, siempre que un hilo en el proceso en primer plano complete una operación de espera sobre un objeto del kernel, el kernel incrementa su prioridad actual (no base) en el valor actual de PsPrioritySeparation. (El sistema de ventanas es responsable de determinar qué proceso se considera en primer plano). Como se describió anteriormente en esta sección en “Controlando el quantum,” PsPrioritySeparation refleja el índice en la tabla de quantum usado para seleccionar quantums para los hilos de aplicaciones en primer plano. Sin embargo, en este caso, se está utilizando como un valor de aumento de prioridad.

Para la mayoría de los lectores, simplemente recomendaría dejar este valor en su estado predeterminado. Aunque una combinación de la longitud del quantum y la proporción de tiempo entre primer plano y segundo plano puede influir en la frecuencia de cambio de contexto de un hilo dependiendo de si su tiempo de ejecución excede el tiempo asignado en el quantum, como se describió anteriormente, puedes realizar pruebas comparativas para verificar si influye en el rendimiento de tus aplicaciones preferidas. Si estás utilizando Windows Server en un sistema de escritorio, el valor puede establecerse en ``0x26`` , el cual imita el mismo comportamiento que ``0x2`` en ediciones cliente de Windows.

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

<h2 id="clock-interrupt-frequency-timer-resolution">11.51. Clock Interrupt Frequency (Timer Resolution) <a href="#clock-interrupt-frequency-timer-resolution">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

La frecuencia de interrupción del reloj es la tasa a la que el reloj de hardware del sistema genera interrupciones que permiten al planificador realizar varias tareas como el mantenimiento del tiempo. En la mayoría de los sistemas por defecto, la frecuencia mínima es de 64Hz, lo que significa que se genera una interrupción cada 15.625ms. Una frecuencia más baja reduce el overhead de CPU y el consumo de energía debido a menos interrupciones, pero reduce la precisión temporal y puede resultar en una multitarea menos receptiva. La frecuencia máxima es de 2kHz, lo que significa una interrupción cada 0.5ms. Una frecuencia más alta proporciona mayor precisión temporal y potencialmente una mayor capacidad de respuesta, pero incrementa el overhead de CPU y el consumo de energía. Las resoluciones mínima, actual y máxima pueden verse con [ClockRes](https://learn.microsoft.com/en-us/sysinternals/downloads/clockres).

Las aplicaciones que requieren mayor precisión que la resolución predeterminada de 15.625ms pueden aumentar la frecuencia de interrupción del reloj mediante funciones como [timeBeginPeriod](https://learn.microsoft.com/en-us/windows/win32/api/timeapi/nf-timeapi-timebeginperiod) y [NtSetTimerResolution](http://undocumented.ntinternals.net/index.html?page=UserMode%2FUndocumented%20Functions%2FTime%2FNtSetTimerResolution.html) Estos escenarios suelen incluir reproducción multimedia, videojuegos, VoIP y más, lo cual puede verse al ejecutar una traza de energía ([instrucciones](https://support.microsoft.com/en-gb/topic/guided-help-get-a-detailed-power-efficiency-diagnostics-report-for-your-computer-in-windows-7-3f6ce138-fc04-7648-089a-854bcf332810)) durante la ejecución. La precisión de características que dependen de funciones relacionadas con suspensión para marcar eventos está directamente influenciada por la frecuencia de interrupción del reloj ([1](https://randomascii.wordpress.com/wp-content/uploads/2020/10/image-5.png)). Usando [Sleep](https://learn.microsoft.com/en-us/windows/win32/api/synchapi/nf-synchapi-sleep) como ejemplo,  ``Sleep(n)`` debería dormir durante n milisegundos en la práctica y no n más/menos un valor arbitrario, ya que esto podría resultar en eventos mal sincronizados, lo cual no es ideal para funciones como limitadores de FPS basados en suspensión. Cabe señalar que este es un ejemplo, y muchas aplicaciones reales no dependen específicamente de la función ``Sleep`` para el control de eventos. Un valor típico al que los desarrolladores suelen elevar la resolución es 1ms, lo que permite que la aplicación mantenga un ritmo de eventos dentro de una resolución de 1ms. En casos muy raros, los desarrolladores podrían no elevar la resolución en absoluto mientras su aplicación depende de ello, lo que podría causar fallos, aunque esto no es común y puede aplicar a programas poco conocidos como ciertos juegos indie.

La implementación de la resolución del temporizador cambió en Windows 10 versión 2004 y posteriores, de modo que el proceso que solicita una resolución más alta ya no afecta al sistema globalmente. Es decir, si el proceso A solicita una resolución de 1ms, no afecta al proceso B que permanece en la resolución predeterminada de 15.625ms, a diferencia de antes. Este es un gran cambio ya que reduce el overhead, ya que otros procesos en segundo plano no son atendidos innecesariamente y el proceso solicitante recibe mayor precisión cuando lo necesita. Sin embargo, esto presenta limitaciones para el usuario final al querer usar resoluciones mayores como 0.5ms. Dado que los juegos no son de código abierto para modificar y los sistemas antitrampas impiden la inyección de DLLs o modificación binaria para elevar la resolución más allá de 1ms, la única opción restante es recurrir al comportamiento global, el cual es aplicable a Windows Server y Windows 11+ mediante la siguiente clave de registro como se explica en detalle [aqui](/docs/research.md#6-fixing-timing-precision-in-windows-after-the-great-rule-change).

```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\kernel]
"GlobalTimerResolutionRequests"=dword:00000001
```

Esto proporciona la capacidad de aumentar la resolución en un proceso separado, lo que a su vez resulta en que la aplicación deseada, como un juego, reciba mayor precisión. Sin embargo, como se mencionó anteriormente, la implementación por proceso reduce la sobrecarga, lo cual ya no ocurre cuando se restablece el comportamiento global y los procesos en segundo plano también son atendidos innecesariamente con frecuencia. [RTSS](https://www.guru3d.com/download/rtss-rivatuner-statistics-server-download) es una alternativa que utiliza espera híbrida (hybrid-wait), proporcionando gran precisión sin necesidad de restaurar el comportamiento global.

Una resolución más alta proporciona mayor precisión, pero en algunos casos, la resolución máxima soportada de 0.5ms proporciona menos precisión que algo ligeramente más alto como 0.507ms ([1](/docs/research.md#7-micro-adjusting-timer-resolution-for-higher-precision)). Por lo tanto, es sensato determinar qué resolución proporciona la mayor precisión (menores deltas) con el programa [MeasureSleep](https://github.com/valleyofdoom/TimerResolution) mientras se solicitan distintas resoluciones con [SetTimerResolution](https://github.com/valleyofdoom/TimerResolution). Esto debe hacerse bajo carga, ya que los benchmarks en reposo pueden ser engañosos. El script [micro-adjust-benchmark.ps1](https://github.com/valleyofdoom/TimerResolution) puede usarse para automatizar este proceso.

Recomiendo favorecer la implementación por proceso (no global) cuando sea aplicable, ya que reduce el overhead. En su lugar, usa [RTSS](https://www.guru3d.com/download/rtss-rivatuner-statistics-server-download) para limitar el framerate con precisión. Cabe señalar que puede introducir una latencia notablemente mayor ([1](https://www.youtube.com/watch?t=377&v=T2ENf9cigSk), [2](https://en.wikipedia.org/wiki/Busy_waiting)) por lo que recomiendo comparar y hacer pruebas con la técnica de microajuste en la resolución solicitada usando el comportamiento global. Es posible que la estabilidad del frametime no se vea afectada al elevar la resolución más allá de 1ms debido a mejoras en el limitador de framerate del juego, en cuyo caso no se requiere ninguna acción. El punto principal es comparar todas las opciones disponibles, con preferencia por la implementación por proceso (predeterminada desde Windows 10 2004+) si descubres que elevar más la resolución no tiene impacto real.

<h2 id="paging-file">11.52. Archivo de Paginación <a href="#paging-file">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Para la mayoría de los lectores, recomendaría mantener habilitado el archivo de paginación, que es el estado predeterminado. Existe el argumento de que es preferible deshabilitarlo si tienes suficiente RAM para tus aplicaciones, ya que reduce la sobrecarga de E/S y la memoria del sistema es más rápida que el disco. Sin embargo, muchos usuarios han reportado interrupciones (stuttering) en juegos específicos con el archivo de paginación deshabilitado, a pesar de que el uso de RAM no se acerca al máximo. Windows parece asignar el archivo de paginación a discos secundarios en ocasiones, lo cual puede ser problemático si uno de los discos es un HDD. Esto se puede resolver asignando el archivo de paginación a un SSD y configurando su tamaño como “administrado por el sistema”, y luego desasignándolo de las demás unidades.

<h2 id="cleanup-and-maintenance">11.53. Limpieza y Mantenimiento <a href="#cleanup-and-maintenance">(permalink)</a></h2>

No es mala idea revisar este paso periódicamente. Configurar un recordatorio para hacerlo puede ser útil para mantener el sistema limpio.

- Actualizaciones

  - Windows Update: si se estableció disable automatic windows updates en true en la sección [Merging Registry Options](#merging-registry-options), deberás buscar actualizaciones manualmente.

  - Runtimes: como se describe en la sección [Runtimes](#runtimes)

  - Aplicaciones de Microsoft Store: si se estableció disable automatic store app updates en true en la sección [Merging Registry Options](#merging-registry-options), deberás buscar actualizaciones manualmente.

- Desinstala programas no deseados con [Bulk-Crap-Uninstaller](https://github.com/Klocman/Bulk-Crap-Uninstaller) y [AppxPackagesManager](https://github.com/valleyofdoom/AppxPackagesManager)

- Usa [Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns) para evitar que programas no deseados se ejecuten al iniciar el sistema y revísalo con frecuencia, especialmente después de instalar un programa.

- Configura la limpieza de disco

  - Abre CMD e introduce el siguiente comando. Marca todas las casillas excepto ``DirectX Shader Cache`` luego presiona ``OK``

      ```bat
      cleanmgr /sageset:0
      ```

  - Ejecuta la limpieza de disco

      ```bat
      cleanmgr /sagerun:0
      ```

- Algunas ubicaciones que puedes revisar en busca de archivos residuales

  - ``"C:\ProgramData\Microsoft\Windows\Start Menu\Programs"`` - accesos directos del menú de inicio (no borres accesos directos relacionados con Windows)
  - ``C:\Windows\Prefetch`` - archivos de prefetch (esta carpeta no debería estar poblada si Superfetch está deshabilitado)
  - ``C:\Windows\SoftwareDistribution`` - caché de descargas de Windows Update
  - ``C:\Windows\Temp`` - archivos temporales
  - ``"%userprofile%"`` - residuos varios
  - ``"%userprofile%\AppData\Local\Temp"`` - archivos temporales
  - ``"%userprofile%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs"`` - accesos directos del menú de inicio (no borres accesos directos relacionados con Windows)
  - ``Directorios del usuario`` – por ejemplo, Descargas, Documentos, Imágenes, Música, Videos, Escritorio

- Opcionalmente, limpia la carpeta WinSxS para reducir su tamaño ([1](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/clean-up-the-winsxs-folder?view=windows-11)) usando el siguiente comando en CMD. Ten en cuenta que esto puede ser un proceso largo.

    ```bat
    DISM /Online /Cleanup-Image /StartComponentCleanup /ResetBase
    ```

- Opcionalmente, elimina puntos de restauración del sistema obsoletos en la pestaña ``System Protection`` escribiendo ``sysdm.cpl`` en ``Win+R``. Puedes deshabilitarla completamente si no la usas.

- Si ``disable automatic maintenance`` se estableció en ``true`` en la sección [Merging Registry Options](#merging-registry-options), deberás optimizar manualmente tus SSDs (TRIM) o desfragmentar tus HDDs, ya que esta tarea se ejecuta durante el mantenimiento automático.
