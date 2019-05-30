---
title: Projeto de modelagem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11f865a0c39f67b0505a16b209511943756a6981
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328285"
---
# <a name="project-modeling"></a>Modelagem do projeto
A próxima etapa no fornecimento de automação para seu projeto é implementar os objetos de projeto padrão: o <xref:EnvDTE.Projects> e `ProjectItems` coleções; o `Project` e <xref:EnvDTE.ProjectItem> objetos; e os objetos restantes exclusivos para sua implementação. Esses objetos padrão são definidos no arquivo Dteinternal.h. Uma implementação dos objetos padrão é fornecida no exemplo BscPrj. Você pode usar essas classes como modelos para criar seus próprios objetos de projeto padrão que estão no lado a lado com os objetos de outros tipos de projeto do projeto.

 Presume que um consumidor de automação para ser capaz de chamar <xref:EnvDTE.Solution>("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> (`n`) em que n é um número de índice para a obtenção de um projeto específico na solução. Fazer essa chamada de automação faz com que o ambiente chamar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> na hierarquia do projeto apropriado, passando VSITEMID_ROOT como o parâmetro ItemID e VSHPROPID_ExtObject como parâmetro VSHPROPID. `IVsHierarchy::GetProperty` Retorna um `IDispatch` ponteiro para o objeto de automação, fornecer os principais `Project` interface, que você implementou.

 A seguir está a sintaxe de `IVsHierarchy::GetProperty`.

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Projetos de acomodar o aninhamento e usam coleções para criar grupos de itens de projeto. A hierarquia tem esta aparência.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Aninhar significa que um <xref:EnvDTE.ProjectItem> objeto pode ser <xref:EnvDTE.ProjectItems> coleção ao mesmo tempo porque um `ProjectItems` coleção pode conter os objetos aninhados. O exemplo de projeto básico não Demonstre desse aninhamento. Implementando o `Project` do objeto, você participa de estrutura de árvore que caracteriza o design do modelo de automação geral.

 A automação de projeto segue o caminho no diagrama a seguir.

 ![Objetos de projeto do Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") automação de projeto

 Se você implementar uma `Project` do objeto, o ambiente ainda retornará um genérico `Project` objeto que contém apenas o nome do projeto.

## <a name="see-also"></a>Consulte também
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>