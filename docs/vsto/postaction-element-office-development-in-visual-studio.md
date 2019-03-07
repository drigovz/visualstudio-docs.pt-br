---
title: '&lt;postAction&gt; elemento (desenvolvimento do Office no Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <postAction> element
- <postAction> element
- postAction element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 53cf47ef9a78ebb54c377e19b4f7fbad444bbfcd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867099"
---
# <a name="ltpostactiongt-element-office-development-in-visual-studio"></a>&lt;postAction&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `postAction` elemento do `vstav3` namespace contém o `entrypoint` elementos e todos os `postActionData` elementos que estão associados com ações de pós-implantação, que são executados após a instalação de soluções do Office.

## <a name="syntax"></a>Sintaxe

```xml
<postAction>
  <entryPoint>
  </entryPoint>
  <postActionData>
  </postActionData>
</postAction>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `postAction` elemento é opcional e está no `vstav3` namespace. Há um `postAction` elemento definido em um manifesto de aplicativo para cada ação de pós-implantação.

 O `postAction` elemento não tem atributos.

 `postAction` tem os seguintes elementos.

### <a name="entrypoint"></a>entryPoint
 Opcional. A função do `entryPoint` elemento na `vstav3` namespace está definido no [ &#60;pontos de entrada&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md).

### <a name="postactiondata"></a>postActionData
 Opcional. A função do `postActionData` elemento na `vstav3` namespace está definido no [ &#60;postActionData&#62; elemento &#40;desenvolvimento do Office no Visual Studio&#41;](../vsto/postactiondata-element-office-development-in-visual-studio.md).

## <a name="post-deployment-action-example"></a>Exemplo de ação de pós-implantação

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra a `postAction` elemento em um manifesto de aplicativo para uma solução do Office que é implantado usando [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
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
```

## <a name="see-also"></a>Consulte também

- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
