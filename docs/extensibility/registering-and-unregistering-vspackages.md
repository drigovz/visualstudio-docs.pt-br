---
title: Registrando e desregistrando VSPackages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: e25e7a46-6a55-4726-8def-ca316f553d6b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 701700ba9d5c6db1e5858a2419e1b2c0fa950ae5
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79303179"
---
# <a name="register-and-unregister-vspackages"></a>Registre e desregistre VSPacotes
Você usa atributos para registrar um VSPackage, mas

## <a name="register-a-vspackage"></a>Registre um VSPackage
 Você pode usar atributos para controlar o registro de VSPackages gerenciados. Todas as informações de registro estão contidas em um arquivo *.pkgdef.* Para obter mais informações sobre o registro baseado em arquivos, consulte [O utilitário CreatePkgDef](../extensibility/internals/createpkgdef-utility.md).

 O código a seguir mostra como usar os atributos de registro padrão para registrar seu VSPackage.

```csharp
[PackageRegistration(UseManagedResourcesOnly = true)]
[Guid("0B81D86C-0A85-4f30-9B26-DD2616447F95")]
public sealed class BasicPackage : Package
{
    // ...
}
```

## <a name="unregister-an-extension"></a>Retirar o registro de uma extensão
 Se você tem experimentado com muitos VSPackages diferentes e deseja removê-los da instância experimental, você pode apenas executar o comando **Reset.** Procure **redefinir a instância experimental do Visual Studio** na página inicial do seu computador ou execute este comando a partir da linha de comando:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe" /Reset /VSInstance=14.0 /RootSuffix=Exp
```

 Se você quiser desinstalar uma extensão instalada na instância de desenvolvimento do Visual Studio, vá para**Extensões e Atualizações de** **Ferramentas,** > encontre a extensão e clique em **Desinstalar**.

 Se, por algum motivo, nenhum desses métodos tiver sucesso em desinstalar a extensão, você pode cancelar o registro do conjunto VSPackage da linha de comando da seguinte forma:

```cmd
<location of Visual Studio 2015 install>\"Microsoft Visual Studio 14.0\VSSDK\VisualStudioIntegration\Tools\Bin\regpkg" /unregister <pathToVSPackage assembly>
```

<a name="using-a-custom-registration-attribute-to-register-an-extension"></a>

## <a name="use-a-custom-registration-attribute-to-register-an-extension"></a>Use um atributo de registro personalizado para registrar uma extensão

Em certos casos, você pode precisar criar um novo atributo de registro para sua extensão. Você pode usar atributos de registro para adicionar novas chaves de registro ou adicionar novos valores às chaves existentes. O novo atributo <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute>deve derivar , <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> e deve substituir os métodos e métodos.

### <a name="create-a-custom-attribute"></a>Como criar um atributo personalizado

O código a seguir mostra como criar um novo atributo de registro.

```csharp
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]
public class CustomRegistrationAttribute : RegistrationAttribute
{
}
```

 O <xref:System.AttributeUsageAttribute> é usado em classes de atributos para especificar o elemento do programa (classe, método, etc.) ao qual o atributo pertence, se pode ser usado mais de uma vez e se pode ser herdado.

### <a name="create-a-registry-key"></a>Criar uma chave de registro

No código a seguir, o atributo personalizado cria uma subchave **Personalizada** a chave para o VSPackage que está sendo registrado.

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

### <a name="create-a-new-value-under-an-existing-registry-key"></a>Crie um novo valor uma chave de registro existente

Você pode adicionar valores personalizados a uma chave existente. O código a seguir mostra como adicionar um novo valor a uma chave de registro VSPackage.

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

## <a name="see-also"></a>Confira também
- [VSPackages](../extensibility/internals/vspackages.md)
