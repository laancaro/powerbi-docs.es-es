---
title: Envío de un objeto visual de Power BI a AppSource mediante el Panel de vendedores
description: Envío de un objeto visual de Power BI a AppSource mediante el Panel de vendedores
author: KesemSharabi
ms.author: kesharab
ms.reviewer: ''
ms.service: powerbi
ms.topic: conceptual
ms.subservice: powerbi-custom-visuals
ms.date: 12/03/2019
ms.openlocfilehash: 73a6a3d16ae2515af41a3232a37579e18876f38b
ms.sourcegitcommit: 02b05932a119527f255e1eacc745a257044e392f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2019
ms.locfileid: "75223662"
---
# <a name="submit-a-power-bi-visual-to-appsource-using-seller-dashboard"></a>Envío de un objeto visual de Power BI a AppSource mediante el Panel de vendedores

Debe enviar un correo electrónico con los archivos **pbiviz** y **pbix** al equipo de Power BI antes de realizar el envío a AppSource. Esto permite al equipo de Power BI cargar los archivos en el servidor de recursos compartidos público. De lo contrario, la tienda no podrá recuperar los archivos. Debe enviar los archivos con envíos de nuevos objetos visuales de Power BI, actualizaciones de los objetos visuales de Power BI existentes y correcciones de los envíos rechazados.

>[!NOTE]
>El [Panel de vendedores](https://docs.microsoft.com/office/dev/store/use-the-seller-dashboard-to-submit-to-the-office-store) está quedando obsoleto. Lo reemplaza el [Centro de partners](https://docs.microsoft.com/partner-center/). Use el Panel de vendedores solo si está en proceso de enviar un objeto visual de Power BI. Si va a enviar un objeto visual de Power BI nuevo a AppSource, use el [método del Centro de partners](office-store.md#submitting-to-appsource).

### <a name="seller-dashboard-submission-process"></a>Proceso de envío del Panel de vendedores

Para iniciar sesión en el [Centro para desarrolladores de Office](https://dev.office.com/), debe tener una cuenta de desarrollador de Office válida. Una cuenta de desarrollador de Office debe ser una cuenta Microsoft (Live ID, por ejemplo, hotmail.com o outlook.com).

1. Vaya al [centro para desarrolladores](https://sellerdashboard.microsoft.com/Application/Summary).

2. Seleccione **Agregar una nueva aplicación**.

    ![Incorporación de una aplicación](media/office-store/powerbi-custom-visual-add-an-app.png)

3. Seleccione **Objeto visual personalizado de Power BI** y, después, **Siguiente**.

4. Seleccione el signo **+** en **Paquete de la aplicación** y, en el cuadro de diálogo Abrir archivo, seleccione el archivo XML del paquete de la aplicación que le ha enviado el equipo de Power BI.

    ![Adición de un paquete](media/office-store/powerbi-custom-visual-apppackage.png)

5. Debería recibir una aprobación en la que se indica que se trata de un paquete de aplicación de Power BI válido.

    ![Manifiesto aprobado](media/office-store/powerbi-custom-visual-manifest-approved.png)

6. Rellene los detalles de **Información general**.

   * *Título del envío:* cómo se denominará el envío en el centro para desarrolladores.
   * *Versión:* el número de versión se rellena automáticamente desde el paquete de la aplicación del complemento.
   * *Fecha de lanzamiento (UCT):* seleccione la fecha en que se publicará la aplicación en la tienda. Si se elige una fecha futura, la aplicación no estará disponible en la tienda hasta dicha fecha.
   * *Categoría:* la primera categoría se rellenará como "Visualización de datos + BI" de forma automática. Así es como se etiquetan todos los objetos visuales de Power BI. Para ayudar a los usuarios a buscar fácilmente el objeto visual, puede proporcionar hasta dos categorías adicionales.
   * *Notas de pruebas:* opcional, si desea proporcionar instrucciones para los evaluadores de Microsoft
   * *Mi aplicación llama, admite, contiene o usa criptografía o cifrado*: déjela desactivada
   * *Establecer este complemento como disponible en el catálogo de complementos de Office para iPad*: déjela desactivada
7. Cargue el logotipo del objeto visual, para lo que debe seleccionar el signo **+** de **Logotipo de la aplicación**. Después, seleccione el archivo del icono en el cuadro de diálogo Abrir archivo. El archivo debe tener una de las siguientes extensiones: .png, .jpg, .jpeg o .gif. Debe ser tener, exactamente, 300 px (ancho) x 300 px (ancho) y su tamaño no puede superar los 512 KB.

    ![Logotipo de la aplicación](media/office-store/powerbi-custom-visual-app-logo.png)

8. Rellene los datos de **Documentos de soporte técnico**.

   * Vínculo de documento de soporte técnico
   * Vínculo de documento de privacidad
   * Enlace de vídeo
   * Contrato de licencia de usuario final (CLUF)

       Debe cargar un archivo con el CLUF. Puede ser su propio CLUF, o bien puede usar el CLUF predeterminado de la Tienda Office para objetos visuales de Power BI. Para usar el CLUF predeterminado, pegue la siguiente dirección URL en el cuadro de diálogo de carga del archivo del "Contrato de licencia para el usuario final" del panel del vendedor: [https://visuals.azureedge.net/app-store/Power BI - Default Custom Visual EULA.pdf](https://visuals.azureedge.net/app-store/Power%20BI%20-%20Default%20Custom%20Visual%20EULA.pdf).

9. Seleccione **Siguiente** para pasar a la página **Detalles**.

10. Seleccione **Idioma** y elija uno de los idiomas de la lista.

    ![Idioma](media/office-store/powerbi-custom-visual-language.png)

11. Rellene los datos de "Descripción".

    * *Nombre de la aplicación (para este idioma):* escriba el título de la aplicación, tal como debe aparecer en escaparate.
    * *Descripción breve:* especifique una descripción breve de la aplicación, de hasta 100 caracteres, como debe aparecer en el escaparate. Esta descripción se mostrará en las primeras páginas, junto con el logotipo. Puede utilizar la descripción del paquete pbiviz.
    * *Descripción larga:* proporcione una descripción más detallada de la aplicación, que es la que los clientes verán en la página de detalles de la aplicación. Si quiere permitir que la comunidad mejore el objeto visual convirtiéndolo en código abierto, proporcione el vínculo al repositorio público, como GitHub, aquí.

12. Cargue al menos una captura de pantalla. Su formato puede ser .png, .jpg, .jpeg o .gif. Debe ser exactamente de 1366 px (ancho) x 768 px (alto). El tamaño del archivo no puede superar los 1024 KB. *Si el uso va a ser mayor, agregue burbujas de texto para articular la propuesta de valor de las características clave que se muestran en cada captura.*

12. Si desea agregar más idiomas, seleccione **Agregar un idioma** y repita los pasos 10 y 11. La incorporación de más idiomas ayudará a los usuarios a ver la información del objeto visual personalizado en su propio idioma. Si el idioma no aparece en la lista, se utilizará de manera predeterminada el primer idioma seleccionado.

13. Cuando haya terminado de agregar idiomas, seleccione **Siguiente** para pasar a la página **Bloquear acceso**.

14. Si desea impedir que clientes de determinados países o regiones usen o compren la aplicación, active la casilla y selecciónelo en la lista.

15. Seleccione **Siguiente** para pasar a la página **Precios**.

16. En estos momentos, solo se permiten los objetos visuales *gratuitos*, pero no las compras adicionales integradas ellos (compras desde la aplicación). Seleccione **Esta aplicación es gratuita**.

    > [!NOTE]
    > Si selecciona cualquier otra opción que no sea la gratuita, o bien si en el objeto visual enviado hay contenido para compras desde la aplicación, el envío se rechazará.

17. Ahora puede seleccionar **Guardar como borrador** o **Enviar para aprobación** para enviar el objeto visual personalizado a la Tienda Office.

## <a name="seller-dashboard-certification-submission-process"></a>Proceso de envío de la certificación del Panel de vendedores

Siga las instrucciones que aparecen en esta sección para enviar un objeto visual de Power BI para su certificación en el Panel de vendedores. Use este método si anteriormente envió un objeto visual de Power BI a AppSource mediante el Panel de vendedores.

1. Envíe un correo electrónico al equipo de soporte técnico de objetos visuales de Power BI (pbicvsupport@microsoft.com). En el correo electrónico, incluya la siguiente información:
    * Título: Solicitud de certificación visual
    * Vínculo al repositorio de GitHub donde se hospeda el código fuente en un lenguaje natural
    * [Cumplimiento de los requisitos](power-bi-custom-visuals-certified.md#certification-requirements)
    * Pase la revisión del código

2. El equipo de objetos visuales de Microsoft Power BI le notificará cuando el objeto visual de Power BI se haya certificado y agregado a la lista de [objetos visuales certificados de Power BI](power-bi-custom-visuals-certified.md#certified-power-bi-visuals), o bien se haya rechazado con un informe de las incidencias que se deben corregir. Es responsabilidad del desarrollador mantener una línea abierta de comunicación con Microsoft y actualizar sus objetos visuales certificados según sea necesario.

## <a name="tracking-submission-status-and-usage"></a>Seguimiento del uso y estado del envío

Puede revisar las [directivas de validación](https://dev.office.com/officestore/docs/validation-policies#13-power-bi-custom-visuals).

Después del envío, el estado del envío se puede ver en el [panel de la aplicación](https://sellerdashboard.microsoft.com/Application/Summary/).

## <a name="certify-your-visual"></a>Certificación del objeto visual

Una vez creado el objeto visual, si lo desea, puede obtener su [certificación](../developer/power-bi-custom-visuals-certified.md).

## <a name="next-steps"></a>Pasos siguientes

[Desarrollo de objetos visuales personalizados de Power BI](visuals/custom-visual-develop-tutorial.md)  
[Visualizaciones en Power BI](../visuals/power-bi-report-visualizations.md)  
[Visualizaciones personalizadas en Power BI](../developer/power-bi-custom-visuals.md)  
[Obtención de un objeto visual de Power BI certificado](../developer/power-bi-custom-visuals-certified.md)

¿Tiene más preguntas? [Pruebe a preguntar a la comunidad de Power BI](https://community.powerbi.com/)
