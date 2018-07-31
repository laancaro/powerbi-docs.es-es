## <a name="limitations"></a>Limitaciones
Esta es una lista de las limitaciones actuales para la seguridad de nivel de fila en los modelos en la nube.

* Si anteriormente tenía roles y reglas definidos en el servicio Power BI, tendrá que volver a crearlos en Power BI Desktop.
* Solo puede definir RLS en los conjuntos de datos creados con el cliente de Power BI Desktop. Si desea habilitar RLS para conjuntos de datos creados con Excel, debe convertir primero los archivos en archivos PBIX. [Más información](../desktop-import-excel-workbooks.md)
* Solo se admiten conexiones de DirectQuery y ETL. Las conexiones dinámicas con Analysis Services se controlan en el modelo local.
* Preguntas y respuestas y Cortana no se admiten con RLS en este momento. No verá el cuadro de entrada de Preguntas y respuestas en los paneles si todos los modelos tienen configurado RLS. Está en el mapa de ruta, pero no está disponible una escala de tiempo.
* Para un modelo dado, el número máximo de entidades de seguridad de Azure AD (es decir, usuarios individuales o grupos de seguridad) que se pueden asignar a roles de seguridad es 1000. Para asignar roles a una gran cantidad de usuarios, asegúrese de realizar la asignación a grupos de seguridad, en lugar de a usuarios individuales.

## <a name="known-issues"></a>Problemas conocidos
Hay un problema conocido en el que se produce un mensaje de error al intentar publicar desde Power BI Desktop si ya se ha publicado anteriormente. El escenario es el siguiente.

1. Ana tiene un conjunto de datos publicado en el servicio Power BI y ha configurado RLS.
2. Ana actualiza el informe en Power BI Desktop y vuelve a publicarlo.
3. Ana recibe un error.

**Solución alternativa:** vuelva a publicar el archivo de Power BI Desktop desde el servicio Power BI hasta que se solucione este problema. Para ello, seleccione **Obtener datos** > **Archivos**. 

