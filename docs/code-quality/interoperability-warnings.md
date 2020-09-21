---
title: Avisos de portabilidade e interoperabilidade
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808594"
---
# <a name="portability-and-interoperability-rules"></a>Regras de portabilidade e interoperabilidade

As regras de portabilidade dão suporte à portabilidade em diferentes plataformas. As regras de interoperabilidade dão suporte à interação com clientes COM.

## <a name="in-this-section"></a>Nesta seção

| Regra | Descrição |
| - | - |
| [CA1401: P/Invokes não devem estar visíveis](../code-quality/ca1401.md) | Um método público ou protegido em um tipo público tem o atributo System.Runtime.InteropServices.DllImportAttribute (também implementado pela palavra-chave declare em Visual Basic). Esses métodos não devem ser expostos. |
| [CA1416: validar a compatibilidade da plataforma](../code-quality/ca1416.md) | O uso de APIs dependentes de plataforma em um componente faz com que o código não funcione mais em todas as plataformas. |
| [CA1417: não usar `OutAttribute` em parâmetros de cadeia de caracteres para P/Invokes](../code-quality/ca1417.md) | Parâmetros de cadeia de caracteres passados por valor com o `OutAttribute` podem desestabilizar o tempo de execução se a cadeia de caracteres for uma cadeia de caracteres interna. |
