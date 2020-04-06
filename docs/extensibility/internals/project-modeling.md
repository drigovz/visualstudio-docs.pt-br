---
title: Modelagem de Projetos | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706550"
---
# <a name="project-modeling"></a>Modelagem do projeto
O próximo passo para fornecer automação para o seu <xref:EnvDTE.Projects> projeto `ProjectItems` é implementar os objetos padrão do projeto: os e coleções; e `Project` <xref:EnvDTE.ProjectItem> os objetos; e os objetos restantes exclusivos de sua implementação. Esses objetos padrão são definidos no arquivo Dteinternal.h. Uma implementação dos objetos padrão é fornecida na amostra BscPrj. Você pode usar essas classes como modelos para criar seus próprios objetos de projeto padrão que ficam lado a lado com objetos de projeto de outros tipos de projeto.

 Um consumidor de automação presume <xref:EnvDTE.Solution>ser`<UniqueProjName>")` capaz <xref:EnvDTE.ProjectItems> `n`de ligar (" e ( ) onde n é um número de índice para a obtenção de um projeto específico na solução. Fazer essa chamada de automação <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.GetProperty%2A> faz com que o ambiente convoque a hierarquia de projeto apropriada, passando VSITEMID_ROOT como parâmetro ItemID e VSHPROPID_ExtObject como parâmetro VSHPROPID. `IVsHierarchy::GetProperty`retorna `IDispatch` um ponteiro para o `Project` objeto de automação que fornece a interface principal, que você implementou.

 A seguir está a `IVsHierarchy::GetProperty`sintaxe de .

 `HRESULT GetProperty (`

 `VSITEMID` `itemid`,

 `VSHPROPID` `propid`,

 `VARIANT` `*pvar`

 `);`

 Os projetos acomodam aninhamento e usam coleções para criar grupos de itens do projeto. A hierarquia é assim.

```
Projects
  |- Project
      |- ProjectItems (a collection of ProjectItem)
          |- ProjectItem (single object) or ProjectItems (another collection)
```

 Aninhamento significa <xref:EnvDTE.ProjectItem> que <xref:EnvDTE.ProjectItems> um objeto pode ser `ProjectItems` coletaao mesmo tempo porque uma coleção pode conter os objetos aninhados. A amostra do Projeto Básico não demonstra esse ninho. Ao implementar `Project` o objeto, você participa da estrutura semelhante a uma árvore que caracteriza o design do modelo geral de automação.

 A automação do projeto segue o caminho no diagrama a seguir.

 ![Objetos de projeto do Estúdio Visual](../../extensibility/internals/media/projectobjects.gif "ProjectObjects") Automação de projetos

 Se você não `Project` implementar um objeto, o `Project` ambiente ainda retornará um objeto genérico que contém apenas o nome do projeto.

## <a name="see-also"></a>Confira também
- <xref:EnvDTE.Projects>
- <xref:EnvDTE.ProjectItem>
- <xref:EnvDTE.ProjectItems>
