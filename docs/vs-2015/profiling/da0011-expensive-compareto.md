---
title: 'DA0011: CompareTo dispendioso | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0011
- vs.performance.rules.DAExpensiveCompareTo
- vs.performance.11
- vs.performance.rules.DA0011
ms.assetid: 239a381d-0d97-4367-8668-746c93f5af2c
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 281bdbb3ba974b3aacb9c349575727675bb59305
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2019
ms.locfileid: "58354724"
---
# <a name="da0011-expensive-compareto"></a>DA0011: função CompareTo dispendiosa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para a documentação mais recente do Visual Studio, consulte [DA0011: CompareTo dispendiosa](https://docs.microsoft.com/visualstudio/profiling/da0011-expensive-compareto) em docs.microsoft.com.  
  
|||  
|-|-|  
|ID de regra|DA0011|  
|Categoria|Uso do .NET Framework|  
|Métodos de criação de perfil|Amostragem<br /><br /> Memória do .NET|  
|Mensagem|As funções de CompareTo devem ser baratas e podem não alocar nenhuma memória. Reduza a complexidade da função CompareTo se possível.|  
|Tipo de regra|Aviso|  
  
## <a name="cause"></a>Causa  
 O método CompareTo de tipo é dispendioso ou aloca memória.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Os métodos do CompareTo devem ser eficientes e não devem alocar memória.  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Reduza a complexidade do método CompareTo.
