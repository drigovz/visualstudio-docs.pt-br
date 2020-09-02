---
title: Usando um atributo de registro personalizado para registrar uma extensão | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 98068fa7-bda1-4922-b3f6-28680de58c3d
caps.latest.revision: 3
manager: jillfra
ms.openlocfilehash: a619c5d418df3b9b85ab09cf9b907617ebd81b67
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62935778"
---
# <a name="using-a-custom-registration-attribute-to-register-an-extension"></a>Usando um atributo de registro personalizado para registrar uma extensão
Em alguns casos, talvez seja necessário criar um novo atributo de registro para sua extensão. Você pode usar atributos de registro para adicionar novas chaves do registro ou para adicionar novos valores às chaves existentes. O novo atributo deve derivar de e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute> deve substituir os <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Register%2A> métodos e <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.Unregister%2A> .  
  
## <a name="creating-a-custom-attribute"></a>Criando um atributo personalizado  
 O código a seguir mostra como criar um novo atributo de registro.  
  
```  
[AttributeUsage(AttributeTargets.Class, Inherited = true, AllowMultiple = false)]  
    public class CustomRegistrationAttribute : RegistrationAttribute  
    {  
    }  
  
```  
  
 O <xref:System.AttributeUsageAttribute> é usado em classes de atributo para especificar o elemento Program (classe, método, etc.) ao qual o atributo pertence, se ele pode ser usado mais de uma vez e se pode ser herdado.  
  
### <a name="creating-a-registry-key"></a>Criando uma chave do registro  
 No código a seguir, o atributo personalizado cria uma subchave **personalizada** sob a chave para o VSPackage que está sendo registrado.  
  
```  
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
  
### <a name="creating-a-new-value-under-an-existing-registry-key"></a>Criando um novo valor em uma chave de registro existente  
 Você pode adicionar valores personalizados a uma chave existente. O código a seguir mostra como adicionar um novo valor a uma chave de registro do VSPackage.  
  
```  
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