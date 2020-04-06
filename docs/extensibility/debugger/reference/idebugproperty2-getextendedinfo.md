---
title: IDebugProperty2::GetExtendedInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetExtendedInfo
helpviewer_keywords:
- IDebugProperty2::GetExtendedInfo
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 34d6cd880ccae520bf000ad01b52223857f4f10f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721492"
---
# <a name="idebugproperty2getextendedinfo"></a>IDebugProperty2::GetExtendedInfo
Obtém informações estendidas para a propriedade.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetExtendedInfo ( 
   REFGUID* guidExtendedInfo,
   VARIANT* pExtendedInfo
);
```

```csharp
int GetExtendedInfo ( 
   ref Guid guidExtendedInfo,
   out object pExtendedInfo
);
```

## <a name="parameters"></a>parâmetros
`guidExtendedInfo`\
[em] GUID que determina o tipo de informação estendida a ser recuperada. Consulte observações para obter detalhes.

`pExtendedInfo`\
[fora] Retorna `VARIANT` um (C++) ou objeto (C#) que pode ser usado para recuperar as informações de propriedade estendida. Por exemplo, esse parâmetro `IUnknown` pode retornar uma interface que pode ser consultada para uma interface [IDebugDocumentText2.](../../../extensibility/debugger/reference/idebugdocumenttext2.md) Consulte observações para obter detalhes.

## <a name="return-value"></a>Valor retornado
 Se for `S_OK`bem sucedido, retorna; caso contrário, retorna código de erro. Retorna `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` se não houver informações estendidas para recuperar.

## <a name="remarks"></a>Comentários
 Esse método existe com o propósito de recuperar informações que não se prestam a serem recuperadas chamando o método [GetPropertyInfo.](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)

 Os GUIDs a seguir são tipicamente reconhecidos por este método (os valores GUID são especificados para C# já que o nome não está disponível em nenhum conjunto). GuiDs adicionais podem ser criados para uso interno.

|Nome|GUID|Descrição|
|----------|----------|-----------------|
|guidDocument|{3f98de84-fee9-11d0-b47f-00a0244a1dd2}|Retorna `IUnknown` uma interface para o documento. Normalmente, a interface [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) pode `IUnknown` ser obtida a partir desta interface.|
|guidCodeContext|{e2fc65e-56ce-11d1-b528-00aax004a8797}|Retorna `IUnknown` uma interface ao contexto do documento. Normalmente, a interface [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) pode `IUnknown` ser obtida a partir desta interface.|
|guidCustomViewersuportado|{d9c9da31-ffbe-4eeb-9186-23121e3c088c}|Retorna uma seqüência contendo o CLSID de um visualizador personalizado, normalmente implementado por um avaliador de expressão.|
|guidExtendedInfoSlot|{6df235ad-82c6-4292-9c97-7389770bc42f}|Retorna um número de 32 bits representando o número de slot desejado se esta propriedade representar um endereço local de código gerenciado.|
|guidExtendedInfoSignature|{b5fb6d46-f805-417f-96a3-8ba737073ffd}|Retorna uma seqüência contendo a assinatura da variável associada ao objeto de propriedade.|

## <a name="see-also"></a>Confira também
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)
