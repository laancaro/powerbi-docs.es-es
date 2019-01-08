---
title: Conexión a QuickBooks Online con Power BI
description: QuickBooks Online para Power BI
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-template-apps
ms.topic: conceptual
ms.date: 10/16/2017
ms.author: sarinas
LocalizationGroup: Connect to services
ms.openlocfilehash: ec13f396ea1a322a79263320a169330f24a2e5f0
ms.sourcegitcommit: 750f0bfab02af24c8c72e6e9bbdd876e4a7399de
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "54008083"
---
# <a name="connect-to-quickbooks-online-with-power-bi"></a>Conexión a QuickBooks Online con Power BI
Cuando conecta sus datos de QuickBooks Online en Power BI, inmediatamente obtiene un panel de Power BI e informes de Power BI que ofrecen información sobre el flujo de efectivo, la rentabilidad y los clientes de su negocio. Use el panel y los informes como están, o bien personalícelos para resaltar la información que más le interesa. Los datos se actualizan automáticamente una vez al día.

Conéctese al [paquete de contenido de QuickBooks Online](https://dxt.powerbi.com/getdata/services/quickbooks-online) para Power BI.

>[!NOTE]
>Para importar los datos de QuickBooks Online en Power BI, debe ser administrador en su cuenta de QuickBooks Online e iniciar sesión con sus credenciales de cuenta de administrador. No se puede usar este conector con el software QuickBooks Desktop. 

## <a name="how-to-connect"></a>Cómo conectarse
1. Seleccione **Obtener datos** en la parte inferior del panel de navegación izquierdo.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getdata.png) 
2. En el cuadro **Servicios** , seleccione **Obtener**.
   
   ![](media/service-connect-to-quickbooks-online/pbi_getservices.png) 
3. Seleccione **QuickBooks Online** y luego **Obtener**.
   
   ![](media/service-connect-to-quickbooks-online/qbo.png)
4. Seleccione **oAuth2** en el Método de autenticación y seleccione **Iniciar sesión**. 
5. Cuando se le solicite, escriba sus credenciales de QuickBooks Online y siga el proceso de autenticación de QuickBooks Online. Si ya inició sesión en QuickBooks Online con el explorador, no se le solicitarán las credenciales.
   >[!NOTE]
   >Necesita credenciales de administrador para su cuenta de QuickBooks Online.
6. Seleccione la compañía que le gustaría conectar con Power BI en la pantalla siguiente.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_almost.png)
7. Seleccione **Autorizar** en la pantalla siguiente para empezar el proceso de importación. Esto puede tardar varios minutos según el tamaño de los datos de su compañía. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_authorizesm.png)
   
   Una vez que Power BI importe los datos, verá un nuevo panel, el informe y el conjunto de datos en el panel de navegación izquierdo. Los nuevos elementos se marcan con un asterisco amarillo \*.
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_leftnavnew.png)
8. Seleccione el panel de QuickBooks Online. Este es el panel que Power BI creó automáticamente para mostrar los datos importados. Puede modificar este panel para que muestre los datos de la forma que desee. 
   
   ![](media/service-connect-to-quickbooks-online/pbi_qbo_dash.png)

**¿Qué más?**

* Pruebe a [hacer una pregunta en el cuadro de preguntas y respuestas](consumer/end-user-q-and-a.md), en la parte superior del panel.
* [Cambie los iconos](service-dashboard-edit-tile.md) en el panel.
* [Seleccione un icono](consumer/end-user-tiles.md) para abrir el informe subyacente.
* Aunque el conjunto de datos se programará para actualizarse diariamente, puede cambiar la programación de actualización o intentar actualizar a petición mediante **Actualizar ahora**

## <a name="troubleshooting"></a>Solución de problemas
**"Vaya, se ha producido un error.**

Si recibe este mensaje después de seleccionar **Autorizar**:

"Lo sentimos, se ha producido un error. Cierre esta ventana y vuelva a intentarlo.

Otro usuario de la compañía ya se suscribió a la aplicación. Póngase en contacto con [correo electrónico del administrador] para realizar cambios a esta suscripción".

![](media/service-connect-to-quickbooks-online/pbi_qbo_oopssm.png)

... esto significa que otro administrador de su compañía ya se conectó a los datos de su compañía con Power BI. Pídale a dicho administrador que le comparta el panel. Actualmente, solo un usuario administrador puede conectar determinado conjunto de datos empresarial de QuickBooks Online con Power BI. Después de que Power BI crea el panel, el administrador puede compartirlo con varios colegas en los mismos inquilinos de Power BI.

**"Esta aplicación no está configurada para permitir conexiones desde su país"**

Actualmente Power BI solo admite las ediciones de Estados Unidos de QuickBooks Online. 

![](media/service-connect-to-quickbooks-online/pbi_qbo_countrynotsupported.png)

## <a name="next-steps"></a>Pasos siguientes
[¿Qué es Power BI?](power-bi-overview.md)

[Power BI: Conceptos básicos](consumer/end-user-basic-concepts.md)

