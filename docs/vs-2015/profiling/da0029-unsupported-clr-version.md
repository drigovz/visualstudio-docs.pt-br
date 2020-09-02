---
title: 'DA0029: versão da CLR sem suporte | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152659"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versão de CLR não compatível
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ID da regra | DA0029 |  
| Categoria | Uso de Ferramentas de Criação de Perfil |  
| Método de criação de perfil | Criação de perfil na linha de comando |  
| Mensagem | Uma versão do CLR sem suporte foi detectada durante a coleta. Os símbolos gerenciados podem não ser resolvidos corretamente.|  
| Tipo de regra | Informações. |  
  
## <a name="cause"></a>Causa  
 Você está tentando criar o perfil de um aplicativo que usa o [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)], que não é suportado pelas ferramentas de criação de perfil.  
  
## <a name="rule-description"></a>Descrição da Regra  
 Você recebeu este aviso porque as ferramentas de criação de perfil são incapazes de resolver os símbolos para o código gerenciado em execução no aplicativo. As ferramentas de criação de perfil não podem resolver os símbolos de código gerenciado para aplicativos que estão executando o [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Como Corrigir Violações  
 Nenhum.
