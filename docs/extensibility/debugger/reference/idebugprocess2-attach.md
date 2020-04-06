---
title: IDebugProcess2::Anexar | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fb6ea896285c784021402400597ba168f6ccf716
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724185"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
Anexa o Gerenciador de depuração de sessão (SDM) ao processo.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT Attach( 
   IDebugEventCallback2* pCallback,
   GUID*                 rgguidSpecificEngines,
   DWORD                 celtSpecificEngines,
   HRESULT*              rghrEngineAttach
);
```

```csharp
int Attach( 
   IDebugEventCallback2 pCallback,
   Guid[]               rgguidSpecificEngines,
   uint                 celtSpecificEngines,
   int[]                rghrEngineAttach
);
```

## <a name="parameters"></a>parâmetros
`pCallback`\
[em] Um objeto [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) que é usado para depurar notificação de evento.

`rgguidSpecificEngines`\
[em] Uma matriz de GUIDs de motores de depuração para serem usados para depurar programas em execução no processo. Este parâmetro pode ser um valor nulo. Consulte observações para obter detalhes.

`celtSpecificEngines`\
[em] O número de motores `rgguidSpecificEngines` de depuração `rghrEngineAttach` na matriz e o tamanho da matriz.

`rghrEngineAttach`\
[dentro, fora] Uma matriz de códigos HRESULT retornados pelos motores de depuração. O tamanho desta matriz é `celtSpecificEngines` especificado no parâmetro. Cada código é `S_OK` tipicamente ou `S_ATTACH_DEFERRED`. Este último indica que o DE está atualmente anexado a nenhum programa.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro. A tabela a seguir mostra outros valores possíveis.

|Valor|Descrição|
|-----------|-----------------|
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|O processo especificado já está anexado ao depurador.|
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Uma violação de segurança ocorreu durante o procedimento de anexação.|
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Um processo de desktop não pode ser anexado ao depurador.|

## <a name="remarks"></a>Comentários
 A anexação a um processo anexa o SDM a todos os programas em execução nesse processo `rgguidSpecificEngines` que podem ser depurados pelos mecanismos de depuração (DE) especificados no array. Defina `rgguidSpecificEngines` o parâmetro como um `GUID_NULL` valor nulo ou inclua na matriz para anexar a todos os programas do processo.

 Todos os eventos de depuração que ocorrem no processo são enviados para o objeto [IDebugEventCallback2.](../../../extensibility/debugger/reference/idebugeventcallback2.md) Este `IDebugEventCallback2` objeto é fornecido quando o SDM chama esse método.

## <a name="see-also"></a>Confira também
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
