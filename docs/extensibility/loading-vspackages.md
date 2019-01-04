---
title: Carregar VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 477ac9b0b97a7544402f0f70204b8ecf7b43ba95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925822"
---
# <a name="load-vspackages"></a>Carregar VSPackages
Os VSPackages são carregados no Visual Studio apenas quando sua funcionalidade é necessária. Por exemplo, um VSPackage é carregado quando o Visual Studio usa uma fábrica de projeto ou um serviço que implementa o VSPackage. Esse recurso é chamado de carregamento atrasado, que é usado sempre que possível para melhorar o desempenho.  
  
> [!NOTE]
>  Visual Studio pode determinar determinadas informações de VSPackage, como os comandos que oferece um VSPackage, sem carregar o VSPackage.  
  
 Os VSPackages pode ser definidos como autoload em um contexto de (UI) de interface de usuário específico, por exemplo, quando uma solução é aberta. O <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo define neste contexto.  
  
### <a name="autoload-a-vspackage-in-a-specific-context"></a>Carregar um VSPackage em um contexto específico automaticamente  
  
-   Adicionar o `ProvideAutoLoad` de atributo para os atributos de VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Ver os campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obter uma lista de contextos de interface do usuário e seus valores GUID.  
  
-   Defina um ponto de interrupção no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
-   Compile o VSPackage e iniciar a depuração.  
  
-   Carregue uma solução ou crie um.  
  
     O VSPackage carrega e para no ponto de interrupção.  
  
## <a name="force-a-vspackage-to-load"></a>Forçar para carregar um VSPackage  
 Em algumas circunstâncias, um VSPackage talvez precise forçar outro VSPackage a ser carregado. Por exemplo, um VSPackage leve pode carregar um VSPackage maior em um contexto que não está disponível como um CMDUIContext.  
  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forçar um VSPackage ao carregar.  
  
-   Inserir este código para o <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método do VSPackage que força o VSPackage outro ao carregar:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Quando o VSPackage é inicializado, ele forçará `PackageToBeLoaded` para carregar.  
  
     Carregamento de força não deve ser usado para comunicação de VSPackage. Use [uso e fornecer serviços](../extensibility/using-and-providing-services.md) em vez disso.
  
## <a name="see-also"></a>Consulte também  
 [VSPackages](../extensibility/internals/vspackages.md)
