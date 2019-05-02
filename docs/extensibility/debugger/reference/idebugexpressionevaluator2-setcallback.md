---
title: IDebugExpressionEvaluator2::SetCallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::SetCallback
- SetCallback
ms.assetid: 31e3a99e-e784-44a3-8b19-cc5ef31ed546
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d758d6c34563a2915e295514380cf07c847d86c4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919746"
---
# <a name="idebugexpressionevaluator2setcallback"></a>IDebugExpressionEvaluator2::SetCallback
Permite que o avaliador de expressão (EE) especificar a interface de retorno de chamada que o mecanismo do depurador (DES) usará para ler as configurações de métrica.

## <a name="syntax"></a>Sintaxe

```cpp
HRESULT SetCallback (
    IDebugSettingsCallback2* pCallback
);
```

```csharp
int SetCallback (
    IDebugSettingsCallback2 pCallback
);
```

#### <a name="parameters"></a>Parâmetros
`pCallback`

 [in] Interface a ser usado para o retorno de chamada de configurações.

## <a name="return-value"></a>Valor de retorno
Se for bem-sucedido, retornará `S_OK`; caso contrário, retorna um código de erro.

## <a name="remarks"></a>Comentários
Esse método fornece uma interface para o Gerenciador de depuração de sessão que um avaliador de expressão pode usar para ler configurações de métrica. Ele é útil para depuração remota para ler a métrica a [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] computador.

## <a name="example"></a>Exemplo
Os exemplos a seguir mostra como implementar esse método para um **CEE** objeto que expõe a [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) interface.

```cpp
HRESULT CEE::SetCallback(IDebugSettingsCallback2* in_pCallback)
{
    // precondition
    INVARIANT( this );

    // function body
    if (NULL != this->m_LanguageSpecificUseCases.pfSetCallback)
    {
        EEDomain::fSetCallback DomainVal =
        {
            in_pCallback
        };

        BOOL bSuccess = (*this->m_LanguageSpecificUseCases.pfSetCallback)(DomainVal);
        ENSURE( bSuccess );
    }

    // postcondition
    INVARIANT( this );

    return S_OK;
}
```

## <a name="see-also"></a>Consulte também
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
