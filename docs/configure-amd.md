<h1 id="configure-the-amd-driver">Configuración de Driver AMD <a href="#configure-the-amd-driver">(permalink)</a></h1>

> [!IMPORTANTE]
> Disclaimer: I no longer own an AMD GPU meaning this section may be incomplete/unmaintained. For this reason, you can visit the AMD GPUs section in [Calypto's Latency Guide](https://calypto.us).

> [!PRECAUCIÓN]
> 📊 **NO** seguir ciegamente las recomendaciones en esta sección. **REALIZA** benchmarks hacia los cambios específicos que realices para asegurar que resultan en una escala positiva de rendimiento, ya que todos los sistemas se comportan de manera diferente y los cambios pueden degradar el rendimiento ([instrucciones](/README.md#3-benchmarking)).

<h2 id="table-of-contents">1. Tabla de Contenidos <a href="#table-of-contents">(permalink)</a></h2>

- [1. Tabla de Contenidos](#table-of-contents)
- [2. Preparar e instalar el Driver](#strip-and-install-the-driver)

<h2 id="strip-and-install-the-driver">2. Preparar e instalar el driver <a href="#strip-and-install-the-driver">(permalink)</a></h2>

- Descargar y extraer el último driver recomendado en: [AMD drivers and support page](https://www.amd.com/en/support)

- Mueve ``Packages\Drivers\Display\XXXX_INF`` hacia el escritorio. La carpeta puede nombrarse diferente en otras versiones de driver.

  - Abre Device Manager o Administrador de Dispositivos e instala el driver mediante click derecho en el apartado de display adapter o adaptador de pantalla, luego selecciona ``Update driver`` o ``Actualizar Controlador`` y selecciona la carpeta que contenga el driver.

- Extrae ``XXXX_INF\ccc2_install.exe`` con 7-Zip y ejecuta ``CN\cnext\cnext64\ccc-next64.msi`` para instalar el panel de control de Radeon.

- Descarga [Autoruns](https://learn.microsoft.com/en-us/sysinternals/downloads/autoruns) y dirígete a la sección de ``Everything``, luego deshabilita todas las entradas inecesarias de AMD tales como ``AMD Crash Defender``, ``AMD External Events Utility`` (se requieren para VRR) y más. Asegúrate de no deshabilitar el core del driver kernel-mode u otros componentes importantes.
