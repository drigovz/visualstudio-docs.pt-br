---
title: 'IDebugGenericParamField:: ConstraintCount | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- ConstraintCount
- IDebugGenericParamField::ConstraintCount
ms.assetid: 76bef0cb-8a3c-4ce5-87cc-1809de229f33
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89c538d758b96ee8c5a5240189e6bd518ff2681c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934286"
---
# <a name="idebuggenericparamfieldconstraintcount"></a>IDebugGenericParamField::ConstraintCount
Retorna o número de restrições que estão associadas a esse parâmetro genérico.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT ConstraintCount(
    ULONG32* pcConst
);
```

```csharp
int ConstraintCount(
    ref uint pcConst
);
```

## <a name="parameters"></a>Parâmetros
`pcConst`\
[entrada, saída] Número de restrições associadas a este campo.

## <a name="return-value"></a>Valor retornado
Se bem-sucedido, retorna `S_OK` ; caso contrário, retorna um código de erro.

## <a name="example"></a>Exemplo
O exemplo a seguir mostra como implementar esse método para um objeto **CDebugGenericParamFieldType** que expõe a interface [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md) .

```cpp
HRESULT CDebugGenericParamFieldType::ConstraintCount(ULONG32* pcConst)
{
    HRESULT hr = S_OK;
    CComPtr<IMetaDataImport> pMetadata;
    CComPtr<IMetaDataImport2> pMetadata2;
    HCORENUM hEnum = 0;
    ULONG cConst = 0;

    METHOD_ENTRY( CDebugGenericParamFieldType::ConstraintCount );

    IfFalseGo(pcConst, E_INVALIDARG );
    *pcConst = 0;
    IfFailGo( m_spSH->GetMetadata( m_idModule, &pMetadata ) );
    IfFailGo( pMetadata->QueryInterface(IID_IMetaDataImport2, (void**)&pMetadata2) );
    IfFailGo( pMetadata2->EnumGenericParamConstraints( &hEnum,
              m_tokParam,
              NULL,
              0,
              &cConst) );
    IfFailGo( pMetadata->CountEnum(hEnum, &cConst) );
    pMetadata->CloseEnum(hEnum);
    hEnum = NULL;

    *pcConst = cConst;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::ConstraintCount, hr );
    return hr;
}
```

## <a name="see-also"></a>Confira também
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
