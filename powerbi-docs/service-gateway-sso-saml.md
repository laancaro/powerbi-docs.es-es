---
title: Uso de SAML para el inicio de sesión único (SSO) en orígenes de datos locales
description: Configure la puerta de enlace con SAML (Lenguaje de marcado de aserción de seguridad) para habilitar el inicio de sesión único (SSO) de Power BI a orígenes de datos locales.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-gateways
ms.topic: conceptual
ms.date: 10/10/2018
LocalizationGroup: Gateways
ms.openlocfilehash: cb4d53166c848bcdb111b667ff413d96da9e72d5
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "54290530"
---
# <a name="use-security-assertion-markup-language-saml-for-single-sign-on-sso-from-power-bi-to-on-premises-data-sources"></a>Uso de SAML (Lenguaje de marcado de aserción de seguridad) para el inicio de sesión único (SSO) de Power BI a orígenes de datos locales

Use [SAML (Lenguaje de marcado de aserción de seguridad)](https://www.onelogin.com/pages/saml) para habilitar la conectividad de inicio de sesión único directa. La habilitación de SSO facilita la tarea de los paneles y los informes de Power BI para actualizar los datos de orígenes locales.

## <a name="supported-data-sources"></a>Orígenes de datos compatibles

Actualmente se admite SAP HANA con SAML. Para obtener más información acerca de cómo instalar y configurar el inicio de sesión único para SAP HANA con SAML, consulte el tema acerca de [SSO de SAML para la plataforma de BI a HANA](https://wiki.scn.sap.com/wiki/display/SAPHANA/SAML+SSO+for+BI+Platform+to+HANA) en la documentación de SAP HANA.

Se admiten orígenes de datos adicionales con [Kerberos](service-gateway-sso-kerberos.md).

## <a name="configuring-the-gateway-and-data-source"></a>Configuración del origen de datos y la puerta de enlace

Para usar SAML, primero genere un certificado para el proveedor de identidades de SAML y, a continuación, asigne un usuario de Power BI a la identidad.

1. Genere un certificado. Asegúrese de usar el FQDN del servidor de SAP HANA al rellenar el *nombre común*. El certificado expira una vez transcurridos 365 días.

    ```
    openssl req -newkey rsa:2048 -nodes -keyout samltest.key -x509 -days 365 -out samltest.crt
    ```

1. En SAP HANA Studio, haga clic con el botón derecho en el servidor de SAP HANA y, a continuación, vaya a **Seguridad** > **Abrir consola de seguridad** > **Proveedor de identidades de SAML** > **Biblioteca de cifrado de OpenSSL**.

1. Seleccione **Importar**, vaya a samltest.crt e impórtelo.

    ![Proveedores de identidades](media/service-gateway-sso-saml/identity-providers.png)

1. En SAP HANA Studio, seleccione la carpeta **Seguridad**.

    ![Carpeta Seguridad](media/service-gateway-sso-saml/security-folder.png)

1. Expanda **Usuarios** y, a continuación, seleccione el usuario al cual quiere asignar su usuario de Power BI.

1. Seleccione **SAML** y, a continuación, **Configurar**.

    ![Configuración de SAML](media/service-gateway-sso-saml/configure-saml.png)

1. Seleccione el proveedor de identidades que creó en el paso 2. Para **Identidad externa** , escriba el UPN del usuario de Power BI y, a continuación, seleccione **Agregar**.

    ![Selección del proveedor de identidades](media/service-gateway-sso-saml/select-identity-provider.png)

A continuación, valide la configuración con una *aserción de SAML*, usando la [herramienta xmlsec1](http://sgros.blogspot.com/2013/01/signing-xml-document-using-xmlsec1.html).

1. Guarde la aserción a continuación como assertion-template.xml. Reemplace \<MyUserId\> por el UPN del usuario de Power BI que escribió en el paso 7.

    ```xml
    <?xml version="1.0" encoding="UTF-8" ?>
    <saml2:Assertion ID="Assertion12345789" IssueInstant="2015-07-16T04:47:49.858Z" Version="2.0" xmlns:saml2="urn:oasis:names:tc:SAML:2.0:assertion">
      <saml2:Issuer></saml2:Issuer> 
      <Signature xmlns="http://www.w3.org/2000/09/xmldsig#">
        <SignedInfo>
          <CanonicalizationMethod Algorithm="http://www.w3.org/TR/2001/REC-xml-c14n-20010315"/>
          <SignatureMethod Algorithm="http://www.w3.org/2000/09/xmldsig#rsa-sha1"/>
          <Reference URI="">
            <Transforms>
              <Transform Algorithm="http://www.w3.org/2000/09/xmldsig#enveloped-signature"/>
              <Transform Algorithm="http://www.w3.org/2001/10/xml-exc-c14n#"/>
            </Transforms>
            <DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1"/>
            <DigestValue />
          </Reference>
        </SignedInfo>
        <SignatureValue />
        <KeyInfo>
          <X509Data />
        </KeyInfo>
      </Signature>
      <saml2:Subject>
        <saml2:NameID Format="urn:oasis:names:tc:SAML:1.1:nameid-format:unspecified"><MyUserId></saml2:NameID>
      </saml2:Subject>
      <saml2:Conditions NotBefore="2010-01-01T00:00:00Z" NotOnOrAfter="2050-01-01T00:00:00Z"/>
    </saml2:Assertion>
    ```

1. Ejecute el siguiente comando. saltest.key y samltest.crt son la clave y el certificado que generó en el paso 1.

    ```
    xmlsec1 --sign --privkey-pem samltest.key, samltest.crt --output signed.xml assertion-template.xml
    ```

1. En SAP HANA Studio, abra una ventana de consola de SQL y ejecute el siguiente comando. Reemplace \<SAMLAssertion\> por el contenido de xml del paso anterior.

    ```SQL
    CONNECT WITH SAML ASSERTION '<SAMLAssertion>'
    ```

Si la consulta se realiza correctamente, significa que la configuración de SSO de SAML de SAP HANA es correcta.

Ahora que tiene el certificado y la identidad configurados correctamente, convertirá el certificado a un formato pfx y configurará el equipo de puerta de enlace para usar el certificado.

1. Para convertir el certificado al formato pfx, ejecute el comando siguiente.

    ```
    openssl pkcs12 -inkey samltest.key -in samltest.crt -export -out samltest.pfx
    ```

1. Copie el archivo pfx en el equipo de puerta de enlace:

    1. Haga doble clic en samltest.pfx y, a continuación, seleccione **Máquina Local** > **Siguiente**.

    1. Escriba la contraseña y, a continuación, seleccione **Siguiente**.

    1. Seleccione **Colocar todos los certificados en el siguiente almacén** y, a continuación, **Examinar** > **Personal** > **Aceptar**.

    1. Seleccione **Siguiente** y, a continuación, **Finalizar**.

    ![Importación de un certificado](media/service-gateway-sso-saml/import-certificate.png)

1. Conceda a la cuenta de servicio de la puerta de enlace acceso a la clave privada del certificado:

    1. En el equipo de puerta de enlace, ejecute Microsoft Management Console (MMC).

        ![Ejecución de MMC](media/service-gateway-sso-saml/run-mmc.png)

    1. En **Archivo** , seleccione **Agregar o quitar complemento**.

        ![Adición de un complemento](media/service-gateway-sso-saml/add-snap-in.png)

    1. Seleccione **Certificados** > **Agregar** y, a continuación, seleccione **Cuenta de equipo** > **Siguiente**.

    1. Seleccione **Equipo local** > **Finalizar** > **Aceptar**.

    1. Expanda **Certificados** > **Personal** > **Certificados** y busque el certificado.

    1. Haga clic con el botón derecho en el certificado y vaya a **Todas las tareas** > **Administrar claves privadas**.

        ![Administración de claves privadas](media/service-gateway-sso-saml/manage-private-keys.png)

    1. Agregue la cuenta de servicio de la puerta de enlace a la lista. De forma predeterminada, la cuenta es **NT SERVICE\PBIEgwService.** Puede averiguar qué cuenta está ejecutando el servicio de puerta de enlace si ejecuta **services.msc** y busca el **Servicio de puerta de enlace de datos local**.

        ![Servicio de puerta de enlace](media/service-gateway-sso-saml/gateway-service.png)

Por último, siga estos pasos para agregar la huella digital del certificado a la configuración de puerta de enlace.

1. Ejecute el siguiente comando de PowerShell para enumerar los certificados en el equipo.

    ```powershell
    Get-ChildItem -path cert:\LocalMachine\My
    ```
1. Copie la huella digital del certificado que ha creado.

1. Navegue hasta el directorio de la puerta de enlace, cuyo valor predeterminado es C:\Archivos de programa\Puerta de enlace de datos local.

1. Abra PowerBI.DataMovement.Pipeline.GatewayCore.dll.config y busque la sección \*SapHanaSAMLCertThumbprint\*. Pegue la huella digital que ha copiado.

1. Reinicie el servicio de puerta de enlace.

## <a name="running-a-power-bi-report"></a>Ejecución de un informe de Power BI

Ahora puede usar la página **Administrar puerta de enlace** en Power BI para configurar el origen de datos y, en su **Configuración avanzada** , habilitar SSO. A continuación, puede publicar los enlaces de los conjuntos de datos y los informes al origen de datos.

![Configuración avanzada](media/service-gateway-sso-saml/advanced-settings.png)

## <a name="next-steps"></a>Pasos siguientes

Para más información sobre la **Puerta de enlace de datos local** y **DirectQuery**, consulte los recursos siguientes:

* [On-premises Data Gateway (Puerta de enlace de datos local)](service-gateway-onprem.md)
* [DirectQuery en Power BI](desktop-directquery-about.md)
* [Orígenes de datos compatibles con DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery y SAP BW](desktop-directquery-sap-bw.md)
* [DirectQuery y SAP HANA](desktop-directquery-sap-hana.md)