---
title: '&lt;vstoRuntime&gt; elemento (desenvolvimento do Office no Visual Studio)'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <vstoRuntime> element
- <vstoRuntime> element
- vstoRuntime element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 98f483748cce9c3a053c800f9bdd6e0f3d651da2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982134"
---
# <a name="ltvstoruntimegt-element-office-development-in-visual-studio"></a>&lt;vstoRuntime&gt; elemento (desenvolvimento do Office no Visual Studio)
  O `vstoRuntime` elemento o `vstav3` namespace contém uma versão com suporte do Visual Studio Tools para Office runtime para uma solução específica do Office.

## <a name="syntax"></a>Sintaxe

```xml
<vstoRuntime
    release
    version
    supportUrl />
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `vstoRuntime` elemento é necessário e está no `vstav3` namespace. Se uma solução do Office dá suporte a duas versões do Visual Studio Tools para Office runtime, há dois `vstoRuntime` elementos no manifesto do aplicativo.

 O `vstoRuntime` elemento tem os seguintes atributos.

|Atributo|Descrição|
|---------------|-----------------|
|`release`|Necessário. A versão de lançamento do Visual Studio Tools para Office runtime.|
|`version`|Necessário. Número de versão do Visual Studio Tools para Office runtime.|
|`supportUrl`|Opcional. Link para o local de instalação do Visual Studio Tools para Office runtime.|

 `vstoRuntime` não tem nenhum elemento.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra a `vstoRuntime` elemento em um manifesto de aplicativo implantada por meio de uma solução do Office [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)]. Este exemplo de código é parte de um exemplo maior fornecido no [manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<vstav3:vstoRuntime
    release="VSTOR40Beta1"
    version="10.0.20303"
    supportUrl="http://www.microsoft.com" />
```

## <a name="see-also"></a>Consulte também

- [Manifestos de aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
