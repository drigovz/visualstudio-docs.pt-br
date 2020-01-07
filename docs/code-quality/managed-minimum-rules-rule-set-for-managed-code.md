---
title: Conjunto de regras mínimas gerenciado para código gerenciado
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 95264aafd2467065ee2bc36d463369f19714dd68
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587349"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Conjunto de regras mínimas gerenciado para código gerenciado

As regras mínimas gerenciadas se concentram nos problemas mais críticos em seu código, incluindo possíveis falhas de segurança, falhas de aplicativo e outros erros importantes de lógica e design. Inclua esse conjunto de regras em qualquer conjunto personalizado de regras que você criar para seus projetos.

|Regra|Descrição|
|----------|-----------------|
|[CA1001](../code-quality/ca1001.md)|Tipos com campos descartáveis devem ser descartáveis|
|[CA1821](../code-quality/ca1821.md)|Remover finalizadores vazios|
|[CA2213](../code-quality/ca2213.md)|Campos descartáveis devem ser descartados|
|[CA2231](../code-quality/ca2231.md)|Sobrecarga do operador Equals ao substituir `ValueType.Equals`|
