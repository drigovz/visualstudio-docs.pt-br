---
title: Usando o modelo de automação | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], automation model
ms.assetid: 0c7f7889-fbfb-4b19-804f-b742138baecd
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be793e5cc4db30fa410e0218a7f780b6c2826838
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324591"
---
# <a name="using-the-automation-model"></a>Usando o modelo de automação
Depois que você conectou o VSPackage automação, você pode obter as propriedades e métodos chamando o <xref:EnvDTE.DTEClass.GetObject%2A> método no <xref:EnvDTE._DTE> objeto, passando uma cadeia de caracteres que representa o objeto que você deseja recuperar.

## <a name="obtaining-project-objects"></a>Obtendo objetos do projeto
 A seguir estão dois exemplos de código que mostram como um consumidor de automação obtém o projeto de objetos de automação. Para obter informações sobre como obter o objeto DTE, consulte [como: Obter referências para os objetos DTE e DTE2](https://msdn.microsoft.com/Library/c92e3c8e-82e6-4a67-85da-e43c50ffd8e4).

```vb
Sub DoAutomation()
    Dim MyProjects As Projects
    MyProjects = DTE.GetObject("AcmeProject")
End Sub
```

```cpp
void DoAutomation(void)
{
  CComQIPtr<Projects> pMyPkg; // Use an IDispatch-derived object type.
    pMyPkg = pDTE->GetObject("AcmeProjects");

   // The '=' performs a Query Interface.
   // Assumes pDTE is already available as a global.
   // Use pMyPkg to access your projects object's properties and methods.
}

```

 Neste ponto, você pode usar os objetos de projeto padrão que fazem parte de um VSPackage específico para mover para baixo o modelo de hierarquia.

 O exemplo de código a seguir mostra como obter um objeto personalizado que é uma propriedade de um tipo de projeto personalizado.:

```vb
Dim MyPrj As Project
Dim MyPrjItem As ProjectItem
Dim objMyObject as MyExtendedObject

MyPrj = MyProjects.Item(1) 'use the Projects collection to get a project
objMyObject = MyPrj.Object 'You call .Object to get to special Project
                           'implementation
objMyObject.MySpecialMethodOrProperty
```

 O código a seguir lista os nomes de todas as propriedades na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente **gerais** opção o **ferramentas** menu:

```vb
dim objDTE
dim objEnv
set objDTE = CreateObject("VisualStudio.DTE")
set objEnv = objDTE.Properties("Environment", "General")
for each obj in ObjEnv
MsgBox obj.Name
Next

```

## <a name="see-also"></a>Consulte também
- <xref:EnvDTE.DTEClass.GetObject%2A>