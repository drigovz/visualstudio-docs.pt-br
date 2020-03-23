---
title: 'DA0011: CompareTo dispendioso | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: d0eb4566fd4c8a513b1492cecffc16cb94a1fd83
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779422"
---
# <a name="da0011-expensive-compareto"></a>DA0011: função CompareTo dispendiosa

|||
|-|-|
|ID de regra|DA0011|
|Categoria|Uso do .NET Framework|
|Métodos de criação de perfil|amostragem<br /><br /> Memória do .NET|
|Mensagem|As funções de CompareTo devem ser baratas e podem não alocar nenhuma memória. Reduza a complexidade da função CompareTo se possível.|
|Tipo de regra|Aviso|

## <a name="cause"></a>Causa
 O método CompareTo de tipo é dispendioso ou aloca memória.

## <a name="rule-description"></a>Descrição da regra
 Os métodos do CompareTo devem ser eficientes e não devem alocar memória.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Reduza a complexidade do método CompareTo.
