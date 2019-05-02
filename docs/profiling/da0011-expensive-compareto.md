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
ms.workload:
- multiple
ms.openlocfilehash: ee5839e91e2205a98a38ed27823a26a4a127e1ac
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936581"
---
# <a name="da0011-expensive-compareto"></a>DA0011: Função CompareTo dispendiosa

|||
|-|-|
|ID de regra|DA0011|
|Categoria|Uso do .NET Framework|
|Métodos de criação de perfil|Amostragem<br /><br /> Memória do .NET|
|Mensagem|As funções de CompareTo devem ser baratas e podem não alocar nenhuma memória. Reduza a complexidade da função CompareTo se possível.|
|Tipo de regra|Aviso|

## <a name="cause"></a>Causa
 O método CompareTo de tipo é dispendioso ou aloca memória.

## <a name="rule-description"></a>Descrição da regra
 Os métodos do CompareTo devem ser eficientes e não devem alocar memória.

## <a name="how-to-fix-violations"></a>Como corrigir violações
 Reduza a complexidade do método CompareTo.