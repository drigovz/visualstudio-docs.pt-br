---
title: Modelagem de projeto | Microsoft Docs
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
ms.openlocfilehash: 42e810a36478e49a578c6713d20f1bfc6be98309
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725569"
---
# <a name="project-modeling"></a>Modelagem do projeto
A próxima etapa no fornecimento de automação para seu projeto é implementar os objetos de projeto padrão: as coleções <xref:EnvDTE.Projects> e `ProjectItems`; os objetos `Project` e <xref:EnvDTE.ProjectItem>; e os objetos restantes exclusivos da sua implementação. Esses objetos padrão são definidos no arquivo Dteinternal. h. Uma implementação dos objetos padrão é fornecida no exemplo BscPrj. Você pode usar essas classes como modelos para criar seus próprios objetos de projeto padrão que ficam lado a lado com objetos de projeto de outros tipos de projeto.

 Um consumidor de automação presume poder chamar <xref:EnvDTE.Solution> ("`<UniqueProjName>")` e <xref:EnvDTE.ProjectItems> (`n`), em que n é um número de índice para obter um projeto específico na solução. Fazer essa chamada de automação faz com que o ambiente chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> na hierarquia de projeto apropriada, passando VSITEMID_ROOT como o parâmetro ItemID e VSHPROPID_ExtObject como parâmetro VSHPROPID. `IVsHierarchy::GetProperty` retorna um ponteiro de `IDispatch` para o objeto de automação que fornece a interface de `Project` principal, que você implementou.

 Veja a seguir a sintaxe de `IVsHierarchy::GetProperty`.

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

 O aninhamento significa que um objeto <xref:EnvDTE.ProjectItem> pode ser <xref:EnvDTE.ProjectItems> coleção ao mesmo tempo porque uma coleção de `ProjectItems` pode conter os objetos aninhados. O exemplo de projeto básico não demonstra esse aninhamento. Ao implementar o objeto `Project`, você participa da estrutura do tipo árvore que caracteriza o design do modelo de automação Geral.

 A automação do projeto segue o caminho no diagrama a seguir.

 ![Objetos de projeto do Visual Studio](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automação do projeto

 Se você não implementar um objeto `Project`, o ambiente ainda retornará um objeto `Project` genérico que contém apenas o nome do projeto.

## <a name="see-also"></a>Consulte também
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>