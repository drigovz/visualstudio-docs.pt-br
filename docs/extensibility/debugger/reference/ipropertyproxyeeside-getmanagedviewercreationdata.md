---
title: iPropertyProxyEESide::GetManagedViewerCreationData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714957"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera informações sobre o visualizador para este tipo de propriedade, a fim de instanciar esse visualizador.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>parâmetros
`assemName`\
[fora] Retorna o nome da montagem segurando este objeto.

`assemBytes`\
[fora] Retorna um objeto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contendo os bytes de montagem deste objeto (este é um valor nulo se não houver bytes disponíveis).

`assemPdb`\
[fora] Retorna `IEEDataStorage` um objeto contendo as informações do armazenamento de símbolos para este objeto (este é um valor nulo se não houver nenhum armazenamento de símbolos disponível).

`className`\
[fora] Retorna o nome da classe que contém este objeto.

`alr`\
[fora] Retorna um valor da [enumeração ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) indicando o local da montagem.

`replacementOk`\
[fora] Retorna não`TRUE`zero ( ) se o valor deste objeto pode ser alterado; zero`FALSE`( ) se o objeto for somente leitura.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
 Este método é usado por visualizadores de tipo para instanciar um visualizador gerenciado.

## <a name="see-also"></a>Confira também
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
