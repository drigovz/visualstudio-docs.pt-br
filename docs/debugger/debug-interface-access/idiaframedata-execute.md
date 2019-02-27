---
title: IDiaFrameData::execute | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::execute method
ms.assetid: 7a6c7d03-1ff1-4059-bd54-5f407eeebc26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 78440c703ece2aa54e54594d57156dbb17848915
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617698"
---
# <a name="idiaframedataexecute"></a>IDiaFrameData::execute
Executa o desenrolamento de pilha e retorna os resultados em uma interface de quadro de movimentação de pilha.

## <a name="syntax"></a>Sintaxe

```C++
HRESULT execute ( 
   IDiaStackWalkFrame* frame
);
```

#### <a name="parameters"></a>Parâmetros
 `frame`

[in] Uma [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) o objeto que mantém o estado de registradores do quadro.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro. A tabela a seguir mostra os possíveis valores retornados para esse método.

|Valor|Descrição|
|-----------|-----------------|
|E_DIA_INPROLOG|Não é possível executar um quadro de pilha no código de prólogo.|
|E_DIA_SYNTAX|Erro encontrado no programa de quadro de análise.|
|E_DIA_FRAME_ACCESS|Não é possível a registros de acesso ou memória.|
|E_DIA_VALUE|Erro no cálculo de um valor (por exemplo, a divisão por zero).|

## <a name="remarks"></a>Comentários
 Este método é chamado durante a depuração para desenrolar a pilha. O [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md) objeto é implementado pelo aplicativo cliente para receber atualizações para os registros e fornecer métodos usados pelo `execute` método.

## <a name="see-also"></a>Consulte também
- [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
- [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)