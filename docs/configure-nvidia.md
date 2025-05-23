<h1 id="configure-the-nvidia-driver">Configurar el controlador NVIDIA <a href="#configure-the-nvidia-driver">(permalink)</a></h1>

<h2 id="table-of-contents">1. Tabla de contenidos <a href="#table-of-contents">(permalink)</a></h2>

- [1. Tabla de contenidos](#table-of-contents)
- [2. Desmontar e instalar el controlador](#strip-and-install-the-driver)
- [3. Configurar el Panel de Control NVIDIA](#configure-nvidia-control-panel)
  - [3.1. Gestionar la configuración 3D](#manage-3d-settings)
  - [3.2. Cambiar resolución](#change-resolution)
  - [3.3. Ajustar configuración de color de video](#adjust-video-color-settings)
  - [3.4. Frecuencia estática/P-State 0](#lock-gpu-clocksp-state-0)
- [3.5. Configurar NVIDIA Inspector](#configure-nvidia-inspector)

<h2 id="strip-and-install-the-driver">2. Desmontar e instalar el controlador <a href="#strip-and-install-the-driver">(permalink)</a></h2>

- Descarga el último controlador preparado para juegos mediante la página [advanced driver search](https://www.nvidia.com/download/find.aspx). Los controladores DCH son compatibles con Windows 10 1803+ ([1](https://nvidia.custhelp.com/app/answers/detail/a_id/4777/~/nvidia-dch%2Fstandard-display-drivers-for-windows-10-faq)).

- Extraiga el paquete ejecutable del controlador con 7-Zip y elimine todos los archivos y carpetas excepto los siguientes:

    ```
    Display.Driver
    NVI2
    EULA.txt
    ListDevices.txt
    setup.cfg
    setup.exe
    ```

- Elimine las siguientes líneas de ``setup.cfg`` (cerca del final del archivo):

    ```
    <file name="${{EulaHtmlFile}}"/>
    <file name="${{FunctionalConsentFile}}"/>
    <file name="${{PrivacyPolicyFile}}"/>
    ```

- Ejecute ``setup.exe`` para instalar el controlador.

<h2 id="configure-nvidia-control-panel">3. Configurar el Panel de Control NVIDIA <a href="#configure-nvidia-control-panel">(permalink)</a></h2>

<h3 id="manage-3d-settings">3.1. Gestionar la configuración 3D <a href="#manage-3d-settings">(permalink)</a></h3>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

- Low Latency Mode - On

  - Si dejas activados tanto NVIDIA Reflex LLM como LLM en el controlador, NVIDIA Reflex LLM tendrá mayor prioridad automáticamente. ([1](https://www.nvidia.com/en-gb/geforce/news/reflex-low-latency-platform))

- Power management mode - Prefer maximum performance

- Shader Cache Size - Unlimited

- Texture filtering - Quality - High performance

- Threaded Optimization - descarga en la CPU las tareas de procesamiento relacionadas con la GPU ([1](https://tweakguides.pcgamingwiki.com/NVFORCE_8.html)). Puede perjudicar el ritmo de fotogramas, ya que quita tiempo de CPU a la aplicación en tiempo real, pero, aun así, deberías realizar pruebas comparativas. También deberías determinar si ya tienes un cuello de botella en la CPU si decides activar la opción

- Verifica que no se estén sobrescribiendo configuraciones específicas por aplicación en la pestaña  ``Program Settings`` del panel de control de NVIDIA. Por ejemplo, en algunos juegos con Easy Anti-Cheat (EAC), la función de "Nitidez de imagen" puede causar resultados inesperados si está activada a nivel individual.

<h3 id="change-resolution">3.2. Cambiar resolución <a href="#change-resolution">(permalink)</a></h3>

- Output dynamic range - Full

<h3 id="adjust-video-color-settings">3.3. Ajustar configuración de color de video <a href="#adjust-video-color-settings">(permalink)</a></h3>

- Dynamic range - Full

<h2 id="lock-gpu-clocksp-state-0">3.4. Frecuencia estática/P-State 0 <a href="#lock-gpu-clocksp-state-0">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

Forzar el estado de rendimiento máximo (P-State 0) mediante esta clave de [Registro](https://github.com/djdallmann/GamingPCSetup/blob/master/CONTENT/RESEARCH/WINDRIVERS/README.md#q-is-there-a-registry-setting-that-can-force-your-display-adapter-to-remain-at-its-highest-performance-state-pstate-p0), (requiere reinicio) y/o con [este método para minimizar la fluctuación de reloj](https://docs.google.com/document/d/14ma-_Os3rNzio85yBemD-YSpF_1z75mZJz1UdzmW8GE/edit). Esto reduce la latencia no deseada al ejecutar nuevas instrucciones cuando la GPU entra en estados de ahorro energético profundos, a cambio de un mayor consumo y temperatura en reposo.

Con la clave de registro indicada, en algunas GPUs la frecuencia de reloj puede superar levemente el valor configurado. Asegúrate de ajustar la configuración si es necesario para evitar inestabilidad. Verifica que estás editando la clave de controlador correspondiente a tu GPU NVIDIA ([ejemplo](/assets/images/find-driver-key-example.png)).

```bat
reg add "HKLM\SYSTEM\CurrentControlSet\Control\Class\{4d36e968-e325-11ce-bfc1-08002be10318}\0000" /v "DisableDynamicPstate" /t REG_DWORD /d "1" /f
```

<h2 id="configure-nvidia-inspector">3.5. Configurar NVIDIA Inspector <a href="#configure-nvidia-inspector">(permalink)</a></h2>

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

- Descarga y extrae [NVIDIA Profile Inspector]([https://github.com/Orbmu2k/nvidiaProfileInspector](https://github.com/Ixeoz/nvidiaProfileInspector-UNLOCKED))

- Desactiva ``Enable Ansel``, ya que esta función es inyectada automáticamente por los controladores en todos los juegos, incluso si el título no es compatible con Ansel, lo cual puede provocar conflictos con herramientas o inyectores de terceros ([1](https://www.pcgamingwiki.com/wiki/Nvidia#Ansel))

- Si tienes correctamente configurado Resizable BAR, puedes experimentar forzándolo en juegos no compatibles para evaluar posibles mejoras de rendimiento activando las siguientes opciones ([1](https://www.youtube.com/watch?v=ZTOtqWTFSK8)). Ten en cuenta que ReBAR puede causar pérdida de rendimiento en ciertos títulos ([1](https://www.techspot.com/review/2234-nvidia-resizable-bar)), por lo que se recomienda hacer tus propias pruebas.

  - rBAR - Feature
  - rBAR - Options
  - rBAR - Size Limit

- Disable ``CUDA - Force P2 State`` to prevent the memory clock frequency from downclocking during CUDA workloads as it enters P-State 2 despite following the steps in the [Lock GPU Clocks/P-State 0](#lock-gpu-clocksp-state-0) section ([1](/assets/images/cuda-force-p2-state-analysis.png))

- Recomiendo leer la siguiente guia con el fin de optimizar los drivers gráficos de forma más completa:
  - ([Nvidia(ENG)](https://cryptpad.fr/pad/#/2/pad/view/X6i8p0857ZxlnvPEqOeu1vRQFUbUg2lP9W23vcyD8tM/embed/))
