---
title: '&lt;&gt;elemento customHostSpecified (desenvolvimento do Office no Visual Studio)'
description: Saiba como o elemento customHostSpecified indica que essa solução não é um aplicativo autônomo.
titleSuffix: ''
ms.custom: seodec18, SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <customHostSpecified> element
- <customHostSpecified> element
- customHostSpecified element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8327c6e154f051f5ce79d41ceaa696e330c794f
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848125"
---
# <a name="ltcustomhostspecifiedgt-element-office-development-in-visual-studio"></a>&lt;&gt;elemento customHostSpecified (desenvolvimento do Office no Visual Studio)
  O `customHostSpecified` elemento indica que essa solução não é um aplicativo autônomo. As soluções do Office contêm componentes que são hospedados dentro de Microsoft Office aplicativos.

## <a name="syntax"></a>Syntax

```xml
<customHostSpecified />
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `customHostSpecified` elemento é necessário para as soluções do Office. Esse elemento está no `co.v1` namespace e especifica que essa implantação contém um componente que será implantado dentro de um host personalizado e não é um aplicativo autônomo.

 Esse elemento é um filho do primeiro `<entrypoint>` elemento no manifesto do aplicativo. Não pode haver nenhum outro elemento filho nesse `<entrypoint>` elemento ou [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] gerará um erro de validação durante a instalação.

 Este elemento não tem atributos nem elementos filho.

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra o `customHostSpecified` elemento em um manifesto de aplicativo para uma solução do Office. Este exemplo de código faz parte de um exemplo maior fornecido em [manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md).

```xml
<entryPoint>
    <co.v1:customHostSpecified />
</entryPoint>
```

## <a name="see-also"></a>Confira também

- [Manifestos do aplicativo para soluções do Office](../vsto/application-manifests-for-office-solutions.md)
- [Manifestos de implantação para soluções do Office](../vsto/deployment-manifests-for-office-solutions.md)
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)