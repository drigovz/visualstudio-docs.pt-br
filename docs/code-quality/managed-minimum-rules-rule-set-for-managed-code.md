---
title: Conjunto de regras mínimas gerenciado para código gerenciado
ms.date: 11/04/2016
description: Saiba mais sobre a regra de regras mínimas gerenciadas no Visual Studio, que se concentra na segurança, na robustez e em outros problemas críticos. Consulte descrições de regra.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e5c59621f948cbb7465a6726fa8c3003480d4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435385"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Conjunto de regras mínimas gerenciado para código gerenciado

As regras mínimas gerenciadas se concentram nos problemas mais críticos em seu código, incluindo possíveis falhas de segurança, falhas de aplicativo e outros erros importantes de lógica e design. Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para seus projetos.

|Regra|Descrição|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Remover finalizadores vazios|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Campos descartáveis devem ser descartados|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Sobrecarga do operador EQUAL na substituição `ValueType.Equals`|
