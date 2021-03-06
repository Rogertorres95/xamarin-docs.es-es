---
title: 'Xamarin.Essentials: Correo electrónico'
description: La clase Email de Xamarin.Essentials permite que una aplicación abra la aplicación de correo electrónico predeterminada con información especificada incluido el asunto, el cuerpo y los destinatarios (PARA, CC, CCO).
ms.assetid: 5FBB6FF0-0E7B-4C29-8F06-91642AF12629
author: jamesmontemagno
ms.author: jamont
ms.date: 11/04/2018
ms.openlocfilehash: d7d2536fca32fe3ae9f9692031645c42edb4ea61
ms.sourcegitcommit: 01f93a34b466f8d4043cef68fab9b35cd8decee6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2018
ms.locfileid: "52898680"
---
# <a name="xamarinessentials-email"></a>Xamarin.Essentials: Correo electrónico

La clase **Email** permite que una aplicación abra la aplicación de correo electrónico predeterminada con información especificada incluido el asunto, el cuerpo y los destinatarios (PARA, CC, CCO).

## <a name="get-started"></a>Primeros pasos

[!include[](~/essentials/includes/get-started.md)]

## <a name="using-email"></a>Uso de Email

Agregue una referencia a Xamarin.Essentials en su clase:

```csharp
using Xamarin.Essentials;
```

Para usar la funcionalidad de Email se llama al método `ComposeAsync` con un valor `EmailMessage` que contiene información sobre el correo electrónico:

```csharp
public class EmailTest
{
    public async Task SendEmail(string subject, string body, List<string> recipients)
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
            };
            await Email.ComposeAsync(message);
        }
        catch (FeatureNotSupportedException fbsEx)
        {
            // Email is not supported on this device
        }
        catch (Exception ex)
        {
            // Some other exception occurred
        }
    }
}
```


## <a name="platform-differences"></a>Diferencias entre plataformas

# <a name="androidtabandroid"></a>[Android](#tab/android)

No todos los clientes de correo electrónico para Android admiten `Html`. Puesto que no hay ninguna manera de detectar este problema, recomendamos usar `PlainText` para enviar correos electrónicos.

# <a name="iostabios"></a>[iOS](#tab/ios)

No hay diferencias entre las plataformas.

# <a name="uwptabuwp"></a>[UWP](#tab/uwp)

Solo admite `PlainText`, ya que el formato `BodyFormat` que intenta enviar `Html` producirá una excepción `FeatureNotSupportedException`.

-----

## <a name="api"></a>API

- [Código fuente de Email](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/Email)
- [Documentación de API para Email](xref:Xamarin.Essentials.Email)
