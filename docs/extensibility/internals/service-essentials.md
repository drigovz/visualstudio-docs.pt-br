---
title: Essenciais de serviço | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e2947cb4cd6a347d8e010340f8689eb1907a28a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705496"
---
# <a name="service-essentials"></a>Conceitos básicos do serviço
Um serviço é um contrato entre dois VSPackages. Um VSPackage fornece um conjunto específico de interfaces para outro VSPackage consumir. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]é em si uma coleção de VSPackages que fornece serviços para outros VSPackages.

 Por exemplo, você pode usar o serviço SVsActivityLog para obter uma interface IVsActivityLog, que você pode usar para gravar no registro de atividades. Para obter mais informações, [consulte Como: Usar o Registro de Atividades](../../extensibility/how-to-use-the-activity-log.md).

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]também fornece alguns serviços incorporados que não estão registrados. Os VSPackages podem substituir serviços integrados ou outros, fornecendo uma substituição de serviço. Apenas uma substituição de serviço é permitida para qualquer serviço.

 Os serviços não têm capacidade de descoberta. Portanto, você deve conhecer o identificador de serviço (SID) de um serviço que você deseja consumir, e você deve saber quais interfaces ele fornece. A documentação de referência para o serviço fornece essas informações.

- VsPacotes que fornecem serviços são chamados de provedores de serviços.

- Os serviços que são fornecidos a outros VSPackages são chamados de serviços globais.

- Os serviços disponíveis apenas para o VSPackage que os implementa, ou para qualquer objeto que ele cria, são chamados de serviços locais.

- Serviços que substituem serviços ou serviços integrados fornecidos por outros pacotes, são chamados de substituições de serviço.

- Os serviços, ou substituições de serviço, são carregados sob demanda, ou seja, o provedor de serviços é carregado quando o serviço que ele fornece é solicitado por outro VSPackage.

- Para suportar o carregamento sob demanda, um provedor [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de serviços registra seus serviços globais com . Para obter mais informações, consulte [Como: Fornecer um Serviço](../../extensibility/how-to-provide-a-service.md).

- Depois de obter um serviço, use [QueryInterface](/cpp/atl/queryinterface) (código não gerenciado) ou casting (código gerenciado) para obter a interface desejada, por exemplo:

  ```vb
  TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)
  ```

  ```csharp
  GetService(typeof(SVsActivityLog)) as IVsActivityLog;
  ```

- O código gerenciado refere-se a um serviço por seu tipo, enquanto o código não gerenciado refere-se a um serviço por seu GUID.

- Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carrega um VSPackage, ele passa um provedor de serviços para o VSPackage para dar ao VSPackage acesso a serviços globais. Isso é chamado de "siting" do VSPackage.

- VsPackages podem ser provedores de serviços para os objetos que criam. Por exemplo, um formulário pode enviar uma solicitação de um serviço [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de cor para seu quadro, que pode passar a solicitação para .

- Objetos gerenciados que estejam profundamente aninhados, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> ou não estejam localizados, podem exigir acesso direto aos serviços globais.

<a name="how-to-use-getglobalservice"></a>

## <a name="use-getglobalservice"></a>Use GetGlobalService

Às vezes, você pode precisar obter um serviço de uma janela de ferramenta ou contêiner de controle que não tenha sido localizado, ou então tenha sido sited com um provedor de serviços que não sabe sobre o serviço que você deseja. Por exemplo, você pode querer escrever para o registro de atividades de dentro de um controle. Para obter mais informações sobre esses e outros cenários, consulte [Como: Serviços de solução de problemas](../../extensibility/how-to-troubleshoot-services.md).

Você pode obter a maioria dos <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> serviços do Visual Studio chamando o método estático.

<xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A>depende de um provedor de serviços em cache que é inicializado na primeira vez que qualquer VSPackage derivado do Pacote é sited. Você deve garantir que esta condição seja cumprida, ou então esteja preparado para um serviço nulo.

Felizmente, <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> funciona corretamente na maioria das vezes.

- Se um VSPackage fornecer um serviço conhecido apenas para outro VSPackage, o VSPackage solicitando o serviço será siteed antes que o VSPackage que fornece o serviço seja carregado.

- Se uma janela de ferramenta for criada por um VSPackage, o VSPackage será localizado antes da janela da ferramenta ser criada.

- Se um contêiner de controle estiver hospedado por uma janela de ferramenta criada por um VSPackage, o VSPackage será localizado antes que o contêiner de controle seja criado.

### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>Para obter um serviço dentro de uma janela de ferramenta ou recipiente de controle

- Insira este código no construtor, na janela da ferramenta ou no recipiente de controle:

    ```csharp
    IVsActivityLog log = Package.GetGlobalService(typeof(SVsActivityLog)) as IVsActivityLog;
        if (log == null) return;
    ```

    ```vb
    Dim log As IVsActivityLog = TryCast(Package.GetGlobalService(GetType(SVsActivityLog)), IVsActivityLog)
    If log Is Nothing Then
        Return
    End If
    ```

    Esse código obtém um serviço SVsActivityLog e o lança para uma interface IVsActivityLog, que pode ser usada para gravar no registro de atividades. Para um exemplo, [veja como: Usar o registro de atividades](../../extensibility/how-to-use-the-activity-log.md).

## <a name="see-also"></a>Confira também

- [Lista de serviços disponíveis](../../extensibility/internals/list-of-available-services.md)
- [Usando e fornecendo serviços](../../extensibility/using-and-providing-services.md)
- [Conversões cast e conversões de tipo](/dotnet/csharp/programming-guide/types/casting-and-type-conversions)
- [Conversão](/cpp/cpp/casting)
