---
title: Carregando VSPacotes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c221bf06ef3b7e37e2afc1856f3e54fe5ad95e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702960"
---
# <a name="load-vspackages"></a>Carregar VSPacotes
Os VSPackages são carregados no Visual Studio somente quando sua funcionalidade é necessária. Por exemplo, um VSPackage é carregado quando o Visual Studio usa uma fábrica de projetos ou um serviço que o VSPackage implementa. Esse recurso é chamado de carregamento atrasado, que é usado sempre que possível para melhorar o desempenho.

> [!NOTE]
> O Visual Studio pode determinar certas informações do VSPackage, como os comandos que um VSPackage oferece, sem carregar o VSPackage.

 Os VSPackages podem ser configurados para carregar automaticamente em um contexto específico de interface de usuário (Interface do Usuário), por exemplo, quando uma solução está aberta. O <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo define esse contexto.

### <a name="autoload-a-vspackage-in-a-specific-context"></a>Carregue automaticamente um VSPackage em um contexto específico

- Adicione `ProvideAutoLoad` o atributo aos atributos VSPackage:

    ```csharp
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID
    public class MyAutoloadedPackage : Package
    {. . .}
    ```

     Consulte os campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> uma lista dos contextos de Interface do EI e seus valores GUID.

- Defina um ponto <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> de ruptura no método.

- Construa o VSPackage e comece a depurar.

- Carregue uma solução ou crie uma.

     O VSPackage carrega e pára no ponto de partida.

## <a name="force-a-vspackage-to-load"></a>Force um VSPackage a carregar
 Em algumas circunstâncias, um VSPackage pode ter que forçar outro VSPackage a ser carregado. Por exemplo, um VSPackage leve pode carregar um VSPackage maior em um contexto que não está disponível como um CMDUIContext.

 Você pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> usar o método para forçar um VSPackage a carregar.

- Insira este <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> código no método do VSPackage que força outro VSPackage a carregar:

    ```csharp
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;
    if (shell == null) return;

    IVsPackage package = null;
    Guid PackageToBeLoadedGuid =
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);

    ```

     Quando o VSPackage é inicializado, ele forçará `PackageToBeLoaded` a carregar.

     O carregamento de força não deve ser usado para a comunicação VSPackage. Use [use e forneça serviços](../extensibility/using-and-providing-services.md) em vez disso.

## <a name="see-also"></a>Confira também
- [VSPackages](../extensibility/internals/vspackages.md)
