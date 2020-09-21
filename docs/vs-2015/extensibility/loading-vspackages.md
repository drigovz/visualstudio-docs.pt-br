---
title: Carregando VSPackages | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, loading
ms.assetid: f4c3dcea-5051-4065-898f-601269649d92
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e20caff476e116ad59430692719bdbbe22c4914c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90838442"
---
# <a name="loading-vspackages"></a>Carregando VSPackages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackages são carregados no Visual Studio somente quando sua funcionalidade é necessária. Por exemplo, um VSPackage é carregado quando o Visual Studio usa uma fábrica de projetos ou um serviço que o VSPackage implementa. Esse recurso é chamado de carregamento atrasado, que é usado sempre que possível para melhorar o desempenho.  
  
> [!NOTE]
> O Visual Studio pode determinar determinadas informações de VSPackage, como os comandos que um VSPackage oferece, sem carregar o VSPackage.  
  
 VSPackages pode ser definido como AutoLoad em um contexto de interface do usuário específico (IU), por exemplo, quando uma solução é aberta. O <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> atributo define esse contexto.  
  
### <a name="autoloading-a-vspackage-in-a-specific-context"></a>Carregamento automático de um VSPackage em um contexto específico  
  
- Adicione o `ProvideAutoLoad` atributo aos atributos VSPackage:  
  
    ```csharp  
    [DefaultRegistryRoot(@"Software\Microsoft\VisualStudio\14.0")]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [ProvideAutoLoad(UIContextGuids80.SolutionExists)]  
    [Guid("00000000-0000-0000-0000-000000000000")] // your specific package GUID  
    public class MyAutoloadedPackage : Package  
    {. . .}  
    ```  
  
     Consulte os campos enumerados de <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> para obter uma lista dos contextos da interface do usuário e seus valores GUID.  
  
- Defina um ponto de interrupção no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método.  
  
- Compile o VSPackage e inicie a depuração.  
  
- Carregue uma solução ou crie uma.  
  
     O VSPackage é carregado e interrompido no ponto de interrupção.  
  
## <a name="forcing-a-vspackage-to-load"></a>Forçando a carga de um VSPackage  
 Em algumas circunstâncias, um VSPackage pode ter que forçar outro VSPackage a ser carregado. Por exemplo, um VSPackage leve pode carregar um VSPackage maior em um contexto que não está disponível como um CMDUIContext.  
  
 Você pode usar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsShell.LoadPackage%2A> método para forçar o carregamento de um VSPackage.  
  
- Insira esse código no <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> método do VSPackage que força a carga de outro VSPackage:  
  
    ```csharp  
    IVsShell shell = GetService(typeof(SVsShell)) as IVsShell;  
    if (shell == null) return;  
  
    IVsPackage package = null;  
    Guid PackageToBeLoadedGuid =   
        new Guid(Microsoft.PackageToBeLoaded.GuidList.guidPackageToBeLoadedPkgString);  
    shell.LoadPackage(ref PackageToBeLoadedGuid, out package);  
  
    ```  
  
     Quando o VSPackage for inicializado, ele forçará `PackageToBeLoaded` a carga.  
  
     O carregamento forçado não deve ser usado para comunicação VSPackage. Use o [usando e fornecendo serviços](../extensibility/using-and-providing-services.md) em vez disso.  
  
## <a name="using-a-custom-attribute-to-register-a-vspackage"></a>Usando um atributo personalizado para registrar um VSPackage  
 Em alguns casos, talvez seja necessário criar um novo atributo de registro para sua extensão. Você pode usar atributos de registro para adicionar novas chaves do registro ou para adicionar novos valores às chaves existentes. O novo atributo deve derivar de e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> deve substituir os <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> métodos e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-registry-key"></a>Criando uma chave do registro  
 No código a seguir, o atributo personalizado cria uma subchave **personalizada** sob a chave para o VSPackage que está sendo registrado.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + @"}\Custom");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
    }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveKey(@"Packages\" + context.ComponentType.GUID + @"}\Custom");  
}  
  
```  
  
## <a name="creating-a-new-value-under-an-existing-registry-key"></a>Criando um novo valor em uma chave de registro existente  
 Você pode adicionar valores personalizados a uma chave existente. O código a seguir mostra como adicionar um novo valor a uma chave de registro do VSPackage.  
  
```csharp  
public override void Register(RegistrationAttribute.RegistrationContext context)  
{  
    Key packageKey = null;  
    try  
    {   
        packageKey = context.CreateKey(@"Packages\{" + context.ComponentType.GUID + "}");  
        packageKey.SetValue("NewCustom", 1);  
    }  
    finally  
    {  
        if (packageKey != null)  
            packageKey.Close();  
                }  
}  
  
public override void Unregister(RegistrationContext context)  
{  
    context.RemoveValue(@"Packages\" + context.ComponentType.GUID, "NewCustom");  
}  
```  
  
## <a name="see-also"></a>Consulte Também  
 [VSPackages](../extensibility/internals/vspackages.md)
