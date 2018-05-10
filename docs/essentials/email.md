---
title: Correo electrónico Xamarin.Essentials
description: La clase de correo electrónico permite a una aplicación abrir la aplicación de correo electrónico predeterminado con una información especificada como asunto, cuerpo y destinatarios (TO, CC, CCO).
ms.assetid: 5FBB6FF0-0E7B-4C29-8F06-91642AF12629
ms.technology: xamarin-crossplatform
author: jamesmontemagno
ms.author: jamont
ms.date: 05/04/2018
ms.openlocfilehash: a23d849131372820a73057b752908886f64b4210
ms.sourcegitcommit: 46d3c9daa45350bdd536d9e105517f3c1c753c5b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="xamarinessentials-email"></a>Correo electrónico Xamarin.Essentials

![La versión preliminar de NuGet](~/media/shared/pre-release.png)

El **correo electrónico** clase permite a una aplicación abrir la aplicación de correo electrónico predeterminado con una información especificada como asunto, cuerpo y destinatarios (TO, CC, CCO).

## <a name="using-email"></a>Uso de correo electrónico

Agregue una referencia a Xamarin.Essentials en la clase:

```csharp
using Xamarin.Essentials;
```

La funcionalidad de correo electrónico funciona mediante una llamada a la `ComposeAsync` método un `EmailMessage` que contiene información sobre el correo electrónico:

```csharp
public class EmailTest
{
    public async Task SendEmail(string subject, string, body, List<string> recipients)
    {
        try
        {
            var message = new EmailMessage
            {
                Subject = subject,
                Body = body,
                To = recipients,
                //Cc = ccRecipients,
                //Bcc = bccRecipients
            }
            await Email.ComposeAsync(message);
        }
        catch (FeatureNotSupportedException fbsEx)
        {
            // Sms is not supported on this device
        }
        catch (Exception ex)
        {
            // Some other exception occured
        }
    }
}
```

## <a name="api"></a>API

- [Código fuente de correo electrónico](https://github.com/xamarin/Essentials/tree/master/Essentials/Email)
- [Documentación de API de correo electrónico](xref:Xamarin.Essentials.Email)