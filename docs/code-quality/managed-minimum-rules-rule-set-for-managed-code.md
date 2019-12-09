---
title: Conjunto de regras mínimas gerenciado para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: efb282d8876d48d4f8e7eb81963719e2d14e5900
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649261"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Conjunto de regras mínimas gerenciado para código gerenciado

As regras mínimas gerenciadas se concentram nos problemas mais críticos em seu código, incluindo possíveis falhas de segurança, falhas de aplicativo e outros erros importantes de lógica e design. Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para seus projetos.

|Regra|Descrição|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1821](../code-quality/ca1821.md)|Remover finalizadores vazios|
|[CA2213](../code-quality/ca2213.md)|Campos descartáveis devem ser descartados|
|[CA2231](../code-quality/ca2231.md)|Sobrecarga do operador Equals ao substituir `ValueType.Equals`|
