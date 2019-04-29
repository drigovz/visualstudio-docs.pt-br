---
title: Interface ISetNextStatement | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786302"
---
# <a name="isetnextstatement-interface"></a>Interface ISetNextStatement
Essa interface é implementada por um interpretador para permitir que o Gerenciador de depuração do processo atualizar a instrução atual. Ele é implementado de um objeto de quadro de pilha e o PDM obtém essa interface por meio de QueryInterface.  
  
 interface fornece métodos que são úteis para definir o ponto de execução, que determina a próxima instrução a ser executada.  
  
 Além dos métodos herdados de `IUnknown`, o `ISetNextStatement` interface expõe os métodos a seguir.  
  
## <a name="methods-in-vtable-order"></a>Métodos na ordem de Vtable  
  
|Método|Descrição|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Determina se o ponto de execução pode ser definido para o local especificado.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Define o ponto de execução para o local especificado.|