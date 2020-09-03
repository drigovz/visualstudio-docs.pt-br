---
title: Modelagem de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], implementing project objects
- project models, automation
ms.assetid: c8db8fdb-88c1-4b12-86fe-f3c30a18f9ee
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c1ac89baf5bc7582d3430532938a5e5a0c35a4c0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706550"
---
# <a name="project-modeling"></a>Modelagem do projeto
A próxima etapa no fornecimento de automação para seu projeto é implementar os objetos de projeto padrão: <xref:EnvDTE.Projects> as `ProjectItems` coleções e; `Project` os <xref:EnvDTE.ProjectItem> objetos e e os restantes exclusivos da sua implementação. Esses objetos padrão são definidos no arquivo Dteinternal. h. Uma implementação dos objetos padrão é fornecida no exemplo BscPrj. Você pode usar essas classes como modelos para criar seus próprios objetos de projeto padrão que ficam lado a lado com objetos de projeto de outros tipos de projeto.

 Um consumidor de automação presume ser capaz de chamar <xref:EnvDTE.Solution> (" `<UniqueProjName>")` and <xref:EnvDTE.ProjectItems> (), `n` em que n é um número de índice para obter um projeto específico na solução. Fazer essa chamada de automação faz com que o ambiente chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> na hierarquia de projeto apropriada, passando VSITEMID_ROOT como o parâmetro ItemId e VSHPROPID_ExtObject como parâmetro VSHPROPID. `IVsHierarchy::GetProperty` Retorna um `IDispatch` ponteiro para o objeto Automation que fornece a `Project` interface principal, que você implementou.

 Veja a seguir a sintaxe de `IVsHierarchy::GetProperty` .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Os projetos acomodam o aninhamento e o uso de coleções para criar grupos de itens de projeto. A hierarquia é parecida com esta.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 O aninhamento significa que um <xref:EnvDTE.ProjectItem> objeto pode ser <xref:EnvDTE.ProjectItems> coletado ao mesmo tempo porque uma `ProjectItems` coleção pode conter os objetos aninhados. O exemplo de projeto básico não demonstra esse aninhamento. Ao implementar o `Project` objeto, você participa da estrutura do tipo árvore que caracteriza o design do modelo de automação Geral.

 A automação do projeto segue o caminho no diagrama a seguir.

 ![Objetos de projeto do Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automação do projeto

 Se você não implementar um `Project` objeto, o ambiente ainda retornará um `Project` objeto genérico que contém apenas o nome do projeto.

## <a name="see-also"></a>Confira também
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
