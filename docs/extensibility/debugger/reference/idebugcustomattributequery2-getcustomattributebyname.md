---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 47471f2743e705b06fb9a1bda6752b24a7836d1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732566"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtém os bytes de atributos personalizados dado o nome do atributo personalizado.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT GetCustomAttributeByName( 
   LPCOLESTR pszCustomAttributeName,
   BYTE*     ppBlob,
   DWORD*    pdwLen
);
```

```csharp
int GetCustomAttributeByName(
   [In] string        pszCustomAttributeName,
   [In, Out] byte[]   ppBlob,
   [In, Out] ref uint pdwLen
);
```

## <a name="parameters"></a>parâmetros
`pszCustomAttributeName`\
[em] Uma seqüência contendo o nome do atributo personalizado a procurar.

`ppBlob`\
[dentro, fora] Uma matriz que é preenchida com os bytes de atributo personalizado.

`pdwLen`\
[dentro, fora] Especifica o número máximo de bytes `ppBlob` para retornar na matriz e retorna o número de bytes realmente gravados na matriz.

## <a name="return-value"></a>Valor retornado
 Se for bem-sucedido, retorna S_OK ou retorna S_FALSE se o atributo personalizado não existir. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Defina `ppBlob` o parâmetro como um valor nulo para retornar o número de atributos bytes disponíveis. Em seguida, aloque uma `ppBlob` matriz e passe essa matriz para o parâmetro.

 Os bytes de atributo representam os dados brutos do atributo personalizado.

 Se `ppBlob` os `pdwLen` parâmetros e os parâmetros forem definidos como um valor nulo, este método pode ser usado para determinar se o atributo personalizado simplesmente existe. Uma alternativa mais fácil, no entanto, é chamar o método [IsCustomAttributeDefined.](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

## <a name="see-also"></a>Confira também
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
