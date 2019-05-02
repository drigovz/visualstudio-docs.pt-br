---
title: Interface IProvideExpressionContexts | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IProvideExpressionContexts interface
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b6ec0d5e17b0d3527252352c2e789adfac4fa859
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63410062"
---
# <a name="iprovideexpressioncontexts-interface"></a>Interface IProvideExpressionContexts
Fornece uma maneira de enumerar os contextos de expressão conhecidos por um determinado componente. Mecanismos de script geralmente implementam essa interface.  
  
 O Gerenciador de depuração do processo usa essa interface para localizar todos os contextos de expressão global associados com um determinado thread.  
  
> [!NOTE]
> Essa interface é chamada de dentro do thread de interesse. Cabe ao implementador para identificar o thread atual e retorna um enumerador apropriado.  
  
## <a name="methods"></a>Métodos  
 Além dos métodos herdados de `IUnknown`, o `IProvideExpressionContexts` interface expõe os métodos a seguir.  
  
|Método|Descrição|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Retorna um enumerador dos contextos de expressão conhecidos por este componente.|