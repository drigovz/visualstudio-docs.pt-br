---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7d874a00c3c82108c224f18922f2b4853279beaa
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322210"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
Obtém os bytes de atributos personalizados, considerando o nome do atributo personalizado.

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

## <a name="parameters"></a>Parâmetros
`pszCustomAttributeName`\
[in] Uma cadeia de caracteres que contém o nome do atributo personalizado a ser procurado.

`ppBlob`\
[no, out] Uma matriz que é preenchida com os bytes de atributo personalizado.

`pdwLen`\
[no, out] Especifica o número máximo de bytes a serem retornados no `ppBlob` de matriz e retorna o número de bytes realmente gravados na matriz.

## <a name="return-value"></a>Valor de retorno
 Se for bem-sucedido, Retorna S_OK ou retornará S_FALSE se o atributo personalizado não existe. Caso contrário, retornará um código de erro.

## <a name="remarks"></a>Comentários
 Defina o `ppBlob` atributos de parâmetro para um valor null para retornar o número de bytes disponíveis. Em seguida, aloque uma matriz e passar a matriz em para o `ppBlob` parâmetro.

 Os bytes de atributo representam os dados brutos do atributo personalizado.

 Se o `ppBlob` e `pdwLen` parâmetros são definidos como um valor nulo, esse método pode ser usado para determinar se o atributo personalizado simplesmente existe. No entanto, é uma alternativa mais fácil chamar o [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) método.

## <a name="see-also"></a>Consulte também
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)