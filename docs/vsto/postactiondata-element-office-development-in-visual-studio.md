---
title: '&lt;postActionData&gt; elemento (desenvolvimento do Office no Visual Studio)'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- <postActionData> element
- application manifests [Office development in Visual Studio], <postActionData> element
- postActionData element
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 58b085e35971fa557d946f3967af4db81b577fff
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804819"
---
# <a name="ltpostactiondatagt-element-office-development-in-visual-studio"></a>&lt;postActionData&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `postActionData` elemento o `vstav3` namespace Especifica os dados associados a qualquer ação de pós-implantação que é executado após a instalação de soluções do Office.

## <a name="syntax"></a>Sintaxe

```xml
<postActionData>
</postActionData>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `postActionData` elemento é opcional e está no `vstav3` namespace. Há um `postActionData` elemento definido em um manifesto de aplicativo para cada ação de pós-implantação.

 O `postActions` elemento não tem atributos.

 `postActions` não tem elementos filho.

## <a name="post-deployment-action-example"></a>Exemplo de ação de pós-implantação

### <a name="description"></a>Descrição
 O exemplo de código a seguir ilustra a `postAction` elemento em um manifesto de aplicativo implantada por meio de uma solução do Office [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

### <a name="code"></a>Código

```xml
<vstav3:postActionData>
  data in any format
</vstav3:postActionData>
```

## <a name="see-also"></a>Consulte também

- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
