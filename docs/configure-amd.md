<h1 id="configure-the-amd-driver">Configuración de Driver AMD <a href="#configure-the-amd-driver">(permalink)</a></h1>

> [!IMPORTANT]
> No nos hacemos responsables: No tenemos una GPU AMD, lo que significa que esta sección puede estar incompleta o sin actualizar. Por este motivo, puede visitar la sección de GPU AMD en [Calypto's Latency Guide](https://calypto.us).

> [!CAUTION]
> 📊 **No** apliques ciegamente las recomendaciones de esta sección. Es fundamental evaluar cada cambio para asegurarse de que realmente mejora el rendimiento, ya que el comportamiento puede variar significativamente entre distintos sistemas. Algunos ajustes podrían incluso afectar negativamente si no se prueban adecuadamente ([instrucciones aquí.](#benchmarking)).

<h2 id="table-of-contents">1. Tabla de Contenidos <a href="#table-of-contents">(permalink)</a></h2>

- [1. Tabla de Contenidos](#table-of-contents)
- [2. Preparar e instalar el Driver](#strip-and-install-the-driver)

<h2 id="strip-and-install-the-driver">2. Preparar e instalar el driver <a href="#strip-and-install-the-driver">(permalink)</a></h2>

- Descargar y extraer el último driver recomendado en: [AMD drivers and support page](https://www.amd.com/en/support)

- Mueve ``Packages\Drivers\Display\XXXX_INF`` hacia el escritorio. La carpeta puede nombrarse diferente en otras versiones de driver.

  - Abre Device Manager o Administrador de Dispositivos e instala el driver mediante click derecho en el apartado de display adapter o adaptador de pantalla, luego selecciona ``Update driver`` o ``Actualizar Controlador`` y selecciona la carpeta que contenga el driver.

- Extrae ``XXXX_INF\ccc2_install.exe`` con 7-Zip y ejecuta ``CN\cnext\cnext64\ccc-next64.msi`` para instalar el panel de control de Radeon.

- Descarga [Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns) y dirígete a la sección de ``Everything``, luego deshabilita todas las entradas inecesarias de AMD tales como ``AMD Crash Defender``, ``AMD External Events Utility`` (se requieren para VRR) y más. Asegúrate de no deshabilitar el core del driver kernel-mode u otros componentes importantes.
