---
title: '&lt;postActions&gt; elemento (desenvolvimento do Office no Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postActions> element
- postActions element
- <postActions> element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c2036cf0d632fcf545dfde0ec4c43caa788a85ed
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804806"
---
# <a name="ltpostactionsgt-element-office-development-in-visual-studio"></a>&lt;postActions&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `postActions` elemento do `vstav3` namespace contém tudo o `postAction` elementos que descrevem as ações de pós-implantação, que são executados após a instalação de soluções do Office.

## <a name="syntax"></a>Sintaxe

```xml
<postActions>
  <postAction>
    <entryPoint>
    </entryPoint>
    <postActionData>
    </postActionData>
  </postAction>
</postActions>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `postActions` elemento é opcional e está no `vstav3` namespace. Há apenas um `postActions` elemento definido em um manifesto de aplicativo.

 O `postActions` elemento não tem atributos.

 `postActions` tem o seguinte elemento.

### <a name="postaction"></a>postAction
 Opcional. A função do `postAction` elemento na `vstav3` namespace está definido no [ &#60;postAction&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/postaction-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Exemplo de ação de pós-implantação

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra a `postActions` elemento em um manifesto de aplicativo implantada por meio de uma solução do Office [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstav3:postActions>
  <vstav3:postAction>
    <vstav3:entryPoint
      class="PostDeploymentAction.PostDeploymentActionSample">
      <assemblyIdentity
        name="PostDeploymentAction"
        version="1.0.0.0"
        language="neutral"
        processorArchitecture="msil" />
    </vstav3:entryPoint>
    <vstav3:postActionData>
    </vstav3:postActionData>
  </vstav3:postAction>
</vstav3:postActions>
```

## <a name="see-also"></a>Consulte também

- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
