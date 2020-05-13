---
title: 'Como: Serviços de solução de problemas | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 49560acdf57f5dad2c57f2a8e4649f194d6d8298
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710745"
---
# <a name="how-to-troubleshoot-services"></a>Como: Serviços de solução de problemas
Existem vários problemas comuns que podem ocorrer quando você tenta obter um serviço:

- O serviço não está [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]registrado com .

- O serviço é solicitado por tipo de interface e não por tipo de serviço.

- O VSPackage solicitando o serviço não foi localizado.

- O provedor de serviço errado é usado.

  Se o serviço solicitado não puder ser <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> obtido, a chamada para devoluções é nula. Você deve sempre testar para nulo depois de solicitar um serviço:

```csharp
IVsActivityLog log =
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;
if (log == null) return;
```

## <a name="to-troubleshoot-a-service"></a>Para solucionar problemas de um serviço

1. Examine o registro do sistema para ver se o serviço foi registrado corretamente. Para obter mais informações, consulte [Como: Fornecer um serviço](../extensibility/how-to-provide-a-service.md).

    O fragmento de arquivo *.reg* a seguir mostra como o serviço SVsTextManager pode ser registrado:

   ```
   [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]
   @="{F5E7E720-1401-11d1-883B-0000F87579D2}"
   "Name"="SVsTextManager"
   ```

    No exemplo acima, o número [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]da versão é a versão de , como 12.0 ou 14.0, a chave {F5E7E71D-1401-11d1-883B-0000F87579D2} é o identificador de serviço (SID) do serviço, SVsTextManager, e o valor padrão {F5E7E720-1401-11d1-883B-0000F87579D2} é o guia do pacote GUID do gerenciador de texto VSPackage, que fornece o serviço.

2. Use o tipo de serviço e não o tipo de interface quando você chamar GetService. Ao solicitar um [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]serviço <xref:Microsoft.VisualStudio.Shell.Package> de , extrai o GUID do tipo. Um serviço não será encontrado se existirem as seguintes condições:

   1. Um tipo de interface é passado para getservice em vez do tipo de serviço.

   2. Nenhum GUID é explicitamente atribuído à interface. Portanto, o sistema cria um GUID padrão para um objeto conforme necessário.

3. Certifique-se de que o VSPackage solicitando o serviço foi site. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]sites de um VSPackage depois <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>de construí-lo e antes de chamar .

    Se você tiver um código em um construtor VSPackage `Initialize` que precise de um serviço, mova-o para o método.

4. Certifique-se de que está usando o provedor de serviços correto.

    Nem todos os provedores de serviços são iguais. O provedor [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] de serviços que passa para uma janela de ferramenta difere do que passa para um VSPackage. O provedor de serviços de janela de ferramenta sabe sobre <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, mas não sabe sobre <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Você pode <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ligar para obter um provedor de serviços VSPackage dentro de uma janela de ferramenta.

    Se uma janela de ferramenta hospeda um controle do usuário ou qualquer outro recipiente de controle, o contêiner será localizado pelo modelo de componente do Windows e não terá acesso a nenhum [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] serviço. Você pode <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ligar para obter um provedor de serviços VSPackage de dentro de um contêiner de controle.

## <a name="see-also"></a>Confira também
- [Lista de serviços disponíveis](../extensibility/internals/list-of-available-services.md)
- [Usar e prestar serviços](../extensibility/using-and-providing-services.md)
- [Essenciais de serviço](../extensibility/internals/service-essentials.md)
